# go-tinytime
A tiny time object in Go. Tinytime uses **4 bytes** of memory vs the **24 bytes** of a standard time.Time{}

A tinytime only has *day* precision. It has no knowledge of hours, minutes, seconds, or timezones.

[![](https://godoc.org/github.com/lane-c-wagner/go-tinytime?status.svg)](https://godoc.org/github.com/lane-c-wagner/go-tinytime)

## ⚙️ Installation

```bash
go get github.com/lane-c-wagner/go-tinytime
```

## 🚀 Quick Start

```golang
package main

import (
    tinytime "github.com/lane-c-wagner/go-tinytime"
)

func main(){
    tt, err := tinytime.New(1585750374)
	if err != nil {
		fmt.Println(err.Error())
    }
    
    tt = tt.Add(time.Hour * 48)
    fmt.Println(tt)
    // prints 2020-04-05
}
```

## Need More Date Ranges? Go-TinyTime

Unix timestamps only supports dates from `1970` to `2106`. Day-month-year supports dates from year `0` to year `65535`.
If you need a larger date range, take a look at [go-tinydate](https://github.com/lane-c-wagner/go-tinydate) which
uses `day-month-year` underneath. Keep in mind go-tinydate doesn't support more than `day` precision.

## Why?

If you don't have resource constraints, then don't use tinytime! Use the standard [time](https://golang.org/pkg/time/) pacakge.

go-tinytime works well in the following situations:

* You are working in embedded systems where memory is a luxury
* You are storing many dates and smaller memory footprint is desired
* You are 101% sure you don't need a date range larger than 1970-2106

## 💬 Contact

[![Twitter Follow](https://img.shields.io/twitter/follow/wagslane.svg?label=Follow%20Wagslane&style=social)](https://twitter.com/intent/follow?screen_name=wagslane)

Submit an issue (above in the issues tab)

## API

Godoc: https://godoc.org/github.com/lane-c-wagner/go-tinytime

Tinytime mirrors the [time.Time](https://golang.org/pkg/time/) API for the most part. The only methods that are *not* included are the ones that makes no sense without timezone support.

## Formatting 

All formatting is done via the time.Time package's formatting capabilites.

## Transient Dependencies

None! And it will stay that way, except of course for the standard library.

Note: Currently the testify package is used **only** for testing, but that dependency will be removed in coming updates.

## 👏 Contributing

I love help! Contribute by forking the repo and opening pull requests. Please ensure that your code passes the existing tests and linting, and write tests to test your changes if applicable.

All pull requests should be submitted to the "master" branch.

```bash
go test
```

```bash
go fmt
```
