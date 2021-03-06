# Protocol Buffers + Docker
All inclusive protoc suite, powered by Docker and Alpine Linux.

## What's included:
- protobuf 3.3.1
- gRPC 1.4.1
- Google Well Known Types are automatically included (via `google/`)
- Go related tools compiled with 1.8.1, gRPC support is built-in:
  - github.com/golang/protobuf/protoc-gen-go
  - github.com/gogo/protobuf/protoc-gen-gofast
  - github.com/gogo/protobuf/protoc-gen-gogo
  - github.com/gogo/protobuf/protoc-gen-gogofast
  - github.com/gogo/protobuf/protoc-gen-gogofaster
  - github.com/gogo/protobuf/protoc-gen-gogoslick
  - github.com/grpc-ecosystem/grpc-gateway/protoc-gen-swagger
  - github.com/grpc-ecosystem/grpc-gateway/protoc-gen-grpc-gateway
- Ruby related tools with glibc support
  - gem install grpc
  - gem install grpc-tools

## Supported languages
- C++
- C#
- Java / JavaNano (Android)
- JavaScript
- Objective-C
- Python
- Ruby
- Go
- Swift

## Usage
```
$ docker run --rm zhouzhuojie/protoc protoc -I/protobuf --help
Usage: /usr/bin/protoc [OPTION] PROTO_FILES
```

Don't forget you need to bind mount your files:
```
$ docker run --rm -v $(pwd):$(pwd) -w $(pwd) zhouzhuojie/protoc protoc -I/protoby -I. --python_out=. myfile.proto
```

## Google Well Known Types
They are embedded in the image and are included by `protoc` automatically.
They accessible via `google/protobuf/`:
```protobuf
syntax = "proto3";

import "google/protobuf/timestamp.proto";
import "google/protobuf/duration.proto";
```

## Gogo
`gogo.proto` is embedded in the image and can be included with:
```protobuf
syntax = "proto3";

import "github.com/gogo/protobuf/gogoproto/gogo.proto";
```

## Credit
Base image is from znly/protoc, frolvlad/alpine-glibc
