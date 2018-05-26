# Envconf to CLI

 > Automatically convert envconfig projects to urfave/cli flags.
 
## Introduction

Many old projects use [envconfig](https://github.com/kelseyhightower/envconfig) to configure with environment variables:

```go
// Config is the environment-supplied config.
type Config struct {
	ServiceURL string `envconfig:"SERVICE_URL"`
}
```

We might want to format this as a cli flag:

```go
cli.StringFlag{
	Name: "service-url",
	EnvVar: "SERVICE_URL",
	Destination: &config.ServiceURL,
}
```

This package generates this relation automatically:

```go
// GenerateCliFlags builds flags for the envconfig tagged fields.
// Obj must be a struct pointer.
func GenerateCliFlags(obj interface{}) []cli.Flag
```

## Development Status

Status: **design/concept phase**
