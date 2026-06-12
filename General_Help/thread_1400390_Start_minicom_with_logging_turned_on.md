---
title: "Start minicom with logging turned on?"
date: 2010-02-06
forum: General Help
---

### Post by goodrench on 2010-02-06
I am using a [ts-7200]("http://www.embeddedarm.com/products/board-detail.php?product=TS-7552") board from Technologic Systems. I am running under the debian system loaded onto the sd card. I was just wondering if there was a way to start minicom on the board with logging enabled by default.
I have minicom installed and configured on the board.
I have a USB device plugged in and it is /dev/ttyUSB0.
I have successfully changed the default configuration file of minicom to use the /dev/ttyUSB0 device but I cannot find a way to have 'AT commands" issued to the device on startup of minicom as well as logging enabled.
I can run minicom and communicate with the device perfectly but not without the interaction of logging in remotely and manually launching minicom.

The purpose of the device I am building is to just power up the device and it will launch minicom, issue one single 'AT' command to the usb device and log the feedback from the usb device to a timestamped file.

Is there a way to do this through the use of ".profile" or are there any arguments to minicom that will accomplish this.
If minicom will not to this, is there another program that will?
Maybe screen?

---

