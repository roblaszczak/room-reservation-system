# Room Reservation System

Example application created for the presentation on GopherCon Russia 2019.

There are 3 versions of this application:

- `v1.0` - just HTTP handler
- `v2.0` - using [Watermill](https://watermill.io/) to handle payment initialization in the background
- `v3.0` - using CQRS component for initializing payments and counting bookings

Database adapters (in memory in this case) and domain layer is shared by all application versions.

## Up and running

For v2.0 and v3.0 you need Kafka. You can use docker-compose to run it:

    docker-compose up

If you need some help with docker-compose setup, you should check our article about local [Golang development environment](https://threedots.tech/post/go-docker-dev-environment-with-go-modules-and-live-code-reloading/).

And then you should run `cmd/main.go` from application version which you want to run.

    cd 3.0/cmd/
    go run .

### Booking a room

You can book a room using REST API using [https://httpie.org/](HTTPie).

    http POST localhost:6060/book-room RoomID=10 StartTime=2018-09-22T12:42:31Z EndTime=2018-09-22T12:42:31Z GuestsCount:=2 PaymentChannel="paypal" -v

## Support

Please join us on the `#watermill` channel on the [Gophers slack](https://gophers.slack.com/): You can get invite [here](https://gophersinvite.herokuapp.com/).
