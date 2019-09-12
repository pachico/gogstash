FROM golang:1 AS build
RUN go get -u -v "github.com/tsaikd/gobuilder"
WORKDIR /go/src/github.com/tsaikd/gogstash
ADD go.mod /go/src/github.com/tsaikd/gogstash
ADD go.sum /go/src/github.com/tsaikd/gogstash
RUN go mod download

ADD . /go/src/github.com/tsaikd/gogstash
RUN gobuilder --all --check --test

FROM busybox:1-glibc
COPY --from=build /go/src/github.com/tsaikd/gogstash/gogstash /usr/local/bin/
CMD ["gogstash"]
