---
title: "lm-sensors - I need help with new mobo sensors"
date: 2009-07-04
forum: General Help
---

### Post by VastOne on 2009-07-04
Been using lm-sensors for quite a while and no issues with all of my gigabyte motherboards

After reading great reviews for a MSI AMD 790FX-GD70 motherboard I am very happy with it...

If I can get lm-sensors to work again.  With the channels version 3.02 I was getting the message no driver for Fintek F75387SG/RG yet and sensors reported "No sensors found"

After reading here and everywhere about the issues with 2.5 kernels and above with 3.02 lm-sensors, I have upgraded to 3.1.1 and now the Fintek is found 

Driver `to-be-written':
  * Chip `AMD K10 thermal sensors' (confidence: 9)
  * ISA bus, address 0x600
    Chip `Fintek F71889FG Super IO Sensors' (confidence: 9)
  * Bus `SMBus PIIX4 adapter at 0b00'
    Busdriver `i2c_piix4', I2C address 0x2e
    Chip `Fintek F75387SG/RG' (confidence: 7)

Note: there is no driver for AMD K10 thermal sensors yet.
Check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for updates.

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK

And I am back to No Sensors found..

I cannot get to the root of this and nee help, please

Thank you

---

### Post by VastOne on 2009-07-14
> **VastOne said:**
> Been using lm-sensors for quite a while and no issues with all of my gigabyte motherboards

After reading great reviews for a MSI AMD 790FX-GD70 motherboard I am very happy with it...

If I can get lm-sensors to work again.  With the channels version 3.02 I was getting the message no driver for Fintek F75387SG/RG yet and sensors reported "No sensors found"

After reading here and everywhere about the issues with 2.5 kernels and above with 3.02 lm-sensors, I have upgraded to 3.1.1 and now the Fintek is found 

Driver `to-be-written':
  * Chip `AMD K10 thermal sensors' (confidence: 9)
  * ISA bus, address 0x600
    Chip `Fintek F71889FG Super IO Sensors' (confidence: 9)
  * Bus `SMBus PIIX4 adapter at 0b00'
    Busdriver `i2c_piix4', I2C address 0x2e
    Chip `Fintek F75387SG/RG' (confidence: 7)

Note: there is no driver for AMD K10 thermal sensors yet.
Check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for updates.

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK

And I am back to No Sensors found..

I cannot get to the root of this and nee help, please

Thank you

Bump

---

### Post by VastOne on 2009-07-19
Bumpity Bump

---

### Post by VastOne on 2009-07-25
bump

---

### Post by VastOne on 2009-07-29
Is there anybody out there....



Driver `to-be-written':
  * Chip `AMD K10 thermal sensors' (confidence: 9)
  * ISA bus, address 0x600
    Chip `Fintek F71889FG Super IO Sensors' (confidence: 9)

All of these are allegedly supported but I cannot get any of them to load and the LM forums are of no help at all

Has any one ever seen the AMD K10 or the Fintek Super chip loaded and working? 

This really should not be this difficult....

---

### Post by VastOne on 2009-08-10
> **vastone said:**
> is there anybody out there....



Driver `to-be-written':
  * chip `amd k10 thermal sensors' (confidence: 9)
  * isa bus, address 0x600
    chip `fintek f71889fg super io sensors' (confidence: 9)

all of these are allegedly supported but i cannot get any of them to load and the lm forums are of no help at all

has any one ever seen the amd k10 or the fintek super chip loaded and working? 

This really should not be this difficult....

help!!!!!!!!!!!

---

### Post by VastOne on 2009-08-13
Weekly Bump

---

### Post by BigBananaMan on 2009-08-18
I've been looking around for the same and haven't found much.  [[COLOR="Blue"]This[/COLOR]]("http://lists.lm-sensors.org/pipermail/lm-sensors/2008-April/022909.html") popped up in a mailing list so Rudolph Marek and an AMD employee are working on it as we speak.

---

### Post by raffytaffy on 2009-09-16
> **VastOne said:**
> Been using lm-sensors for quite a while and no issues with all of my gigabyte motherboards

After reading great reviews for a MSI AMD 790FX-GD70 motherboard I am very happy with it...

If I can get lm-sensors to work again.  With the channels version 3.02 I was getting the message no driver for Fintek F75387SG/RG yet and sensors reported "No sensors found"

After reading here and everywhere about the issues with 2.5 kernels and above with 3.02 lm-sensors, I have upgraded to 3.1.1 and now the Fintek is found 

Driver `to-be-written':
  * Chip `AMD K10 thermal sensors' (confidence: 9)
  * ISA bus, address 0x600
    Chip `Fintek F71889FG Super IO Sensors' (confidence: 9)
  * Bus `SMBus PIIX4 adapter at 0b00'
    Busdriver `i2c_piix4', I2C address 0x2e
    Chip `Fintek F75387SG/RG' (confidence: 7)

Note: there is no driver for AMD K10 thermal sensors yet.
Check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for updates.

No modules to load, skipping modules configuration.

Unloading i2c-dev... OK

And I am back to No Sensors found..

I cannot get to the root of this and nee help, please

Thank you
Same mobo as you with amd phenom2, also cannot get sensors to work. Any updates on this? Using 8.04

---

### Post by VastOne on 2009-09-16
> **raffytaffy said:**
> Same mobo as you with amd phenom2, also cannot get sensors to work. Any updates on this? Using 8.04

None...Nothing at all...

I also upgraded to a latest kernel with one of my gigabyte mobo's that always worked and now I am getting the same message with that mobo...

Very frustrating as I have always liked lm-sensors and showed it off to so many people...

---

### Post by raffytaffy on 2009-10-01
> **VastOne said:**
> None...Nothing at all...

I also upgraded to a latest kernel with one of my gigabyte mobo's that always worked and now I am getting the same message with that mobo...

Very frustrating as I have always liked lm-sensors and showed it off to so many people...
I sent MSI a tweet on twitter asking for an update on the F71889FG chip...let's see what they say * got my flippers crossed* [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

---

### Post by dcstar on 2009-10-01
> **raffytaffy said:**
> Same mobo as you with amd phenom2, also cannot get sensors to work. Any updates on this? **Using 8.04**

New hardware support will only appear in new kernels - older Ubuntu releases will only get security updates to their existing kernels and it is very unlikely that they will get the updates for new hardware support.

If you want the latest hardware to be supported then the best chance is to get an OS version running the latest kernel - like 9.10.

---

### Post by bruno9779 on 2009-11-30
There is a fix I have found [here]("http://http://blog.morrigan.ch/?p=9")

> Step for step (I’m not sure if this the newest k10temp version!):

$ wget [http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin](http://lists.lm-sensors.org/pipermail/lm-sensors/attachments/20080718/d51be536/attachment.bin)
$ mkdir k10temp && mv attachment.bin k10temp/k10temp.c

Now create the Makefile with following lines:

    obj-m := k10temp.o
    KDIR := /lib/modules/$(shell uname -r)/build
    PWD := $(shell pwd)
    default:
    $(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules

$ make -C /lib/modules/$(uname -r)/build M=$(pwd) modules
$ cp k10temp.ko /lib/modules/$(uname -r)/kernel/drivers/hwmon
$ depmod && modprobe k10temp

Enjoy it!

It workes fine for me.

I have yet to test it when the CPU is under heavy load, and to test the alarms, but sensors-applet is working fine, and the readings are consistent with the CPU load.

One thing only puzzles me: I get one sensor only for a 3 core?

---

### Post by jhenager on 2009-12-01
Have you tried installing xsensors? I just was searching on lm-sensors to add temp and fans to gkrellm, and saw this in Ubuntu Software (9.10).
I only mention this because I didn't see what you have tried so far.

---

### Post by Brewfreak on 2010-03-07
> **bruno9779 said:**
> There is a fix I have found [here]("http://http://blog.morrigan.ch/?p=9")



It workes fine for me.

I have yet to test it when the CPU is under heavy load, and to test the alarms, but sensors-applet is working fine, and the readings are consistent with the CPU load.

One thing only puzzles me: I get one sensor only for a 3 core?

Hello Bruno9779:

When you say
"Now create the Makefile with following lines:

obj-m := k10temp.o
KDIR := /lib/modules/$(shell uname -r)/build
PWD := $(shell pwd)
default:
$(MAKE) -C $(KDIR) SUBDIRS=$(PWD) modules"

How do you exactly do that.  I try the command $makefile obj-m := k10temp.o
but I get an error on the terminal screen
"
abcd@abcd-ubuntu-desktop:~$ makefile obj-m := k10temp.o
bash: makefile: command not found".

Some clarification would be greatly appreciated.  Thanks!

---

### Post by fragos on 2010-03-07
Different mobo but got the same message for K10 CPU but my CPU temp comes up with the Gnome Sensors Applet.

---

