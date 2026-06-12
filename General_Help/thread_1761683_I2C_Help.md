---
title: "I2C Help"
date: 2011-05-18
forum: General Help
---

### Post by waddle77 on 2011-05-18
I am fairly new to linux and am just getting familiar with Ubuntu.  I have a PCM3362 SBC from Advantech and recently installed command line Ubuntu 10.10 on it.  My goal is to get comms to a digital potentiometer (Microchip MCP4541) to control a thruster.  My problem is I am unfamiliar on how the generalities of getting I2C working between the pot and the sbc I am used to using MCUs.  A little direction or help would help out immensely, thanks.

---

### Post by dino99 on 2011-05-18
im not sure to help you alot but looking at synaptic for "i2c", you find:

i2c-tools
eep24c

---

### Post by waddle77 on 2011-05-18
Thanks for the reply.  I have been looking around and going through some tutorials and have installed i2c-tools and lm-sensors.  I was writing a sample program and attempted to open the i2c bus by:

sprintf(filename,"/dev/i2c-%d",0);
if ((file = open(filename,O_RDWR)) < 0)
    perror("Failed to open the i2c bus");
    exit(1);

When I compile and run I always get the message "Failed to open the i2c bus".  My problem is I have no i2c bus in /dev/, again I am really new with this whole concept so this could be a ridiculous problem.  Any suggestions?

---

### Post by dargaud on 2011-09-23
First, check the capabilities of your current running kernel:
```
$ grep -i "i2c\|iic" /boot/config-$(uname -r)
```
Do you see one that matches ?
If necessary, find and load the module, for instance:
```
$ locate *.ko | grep -i "i2c\|iic"
$ sudo insmod [...]i2c-dev.ko
```
You may have to create you own i2c devices with
```
$ sudo mknod /dev/i2c-0 89 c
```
From there try to play with
```
$ i2cdetect -l
$ i2cdetect -F 0
```

---

