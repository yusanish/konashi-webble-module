# konashi Web Bluetooth module

This repository mainly forked from the official repository [YUKAI/konashi-web-bluetooth](https://github.com/YUKAI/konashi-web-bluetooth)

## Requirements

This module uses Web Bluetooth API. The support of API is limited.
Please confirm the link (https://caniuse.com/#feat=web-bluetooth).

## Usage

Before run below script, please get konashi board and turn on the power.

```js
import Konashi from 'konashi-web-bluetooth'

Konashi.find(true).then(k => { // find konashi board and try to connect
  k.pinModeAll("0xFF") // make all pins to OUTPUT mode.
    .then(() => {
      k.digitalWrite(Konashi.consts.PIO1, Konashi.consts.HIGH); // write HIGH to PIO1
    });
    .then(() => {
      setTimeout(() => {
        k.digitalWrite(Konashi.consts.PIO1, Konashi.consts.LOW); // after 1sec write LOW to PIO1
      }, 1000);
    })
});
```

## TODO

- test uart functions
- test i2c functions
- support SPI