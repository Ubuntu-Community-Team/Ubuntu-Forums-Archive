---
title: "Bluecove on netbeans"
date: 2010-04-02
forum: General Help
---

### Post by pix3l on 2010-04-02
Good morning,

I'm working on netbeans and i'm using the jsr82 apis to establish a bluetooth connection and send data from the computer to another device. When I try to execute the program it stops at the line:

local=LocalDevice.getLocalDevice();

The error is:
Native Library bluecove not available

I've already put all the bluecove libraries within the lib folder of the project. This program works on Windows but not on Ubuntu 9. I don't know what's wrong because the Bluetooth device works and I can use it.

---

### Post by sproon on 2010-09-08
Hello,

This is very easy to fix, you are just missing the library for Bluecove to work.

apt-get install libbluetooth-dev

Thats it.

---

