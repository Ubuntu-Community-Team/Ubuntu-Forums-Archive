---
title: "unable to enumerate USB device (ft232r)"
date: 2012-03-09
forum: General Help
---

### Post by hundred1906 on 2012-03-09
The USB to Serial coverter ft232r is fitted onto a Rainbowduino which is an Arduino shield device.

My 11.10 desktop will happily chat to the Arduino via USB but will not recognise the Rainbowduino. From DMESG I get the following:


```
[ 6323.428040] usb 6-3: new full speed USB device number 21 using ohci_hcd
[ 6323.612042] usb 6-3: device descriptor read/64, error -62
[ 6323.900045] usb 6-3: device descriptor read/64, error -62
[ 6324.180040] usb 6-3: new full speed USB device number 22 using ohci_hcd
[ 6324.364040] usb 6-3: device descriptor read/64, error -62
[ 6324.652045] usb 6-3: device descriptor read/64, error -62
[ 6324.932041] usb 6-3: new full speed USB device number 23 using ohci_hcd
[ 6325.340034] usb 6-3: device not accepting address 23, error -62
[ 6325.516049] usb 6-3: new full speed USB device number 24 using ohci_hcd
[ 6325.924035] usb 6-3: device not accepting address 24, error -62
[ 6325.924067] hub 6-0:1.0: unable to enumerate USB device on port 3
```

I saw here [http://forums.fedoraforum.org/showthread.php?t=213447](http://forums.fedoraforum.org/showthread.php?t=213447) advice to install libftdi but this has not helped as yet.

lsusb does not show the device.

Any help welcome. I have searched around but found little I can make use of.

---

### Post by matt_symes on 2012-03-09
Hi

Try adding ```
irqpoll
``` as a boot option on the kernel command line. If that does not work then remove it.

You may also try to read the device using the other method defined in the USB standard. 

Open a terminal and type

```
echo Y | sudo tee /sys/module/usbcore/parameters/old_scheme_first
```

Then insert the USB device. If it's detected correctly then add this to the kernel command line.

```
usbcore.old-scheme-first=1
```

Kind regards

---

### Post by hundred1906 on 2012-03-10
Thanks for that advice. I have not tried the IRQPOLL recommendation for a couple of reasons, firstly my /boot/grub/menu.lst is empty, plus there are reported problems with IRQPOLL on 11.10 so am hesitant to go down that path with my limited understanding (see [http://ubuntuforums.org/showthread.php?t=1870003](http://ubuntuforums.org/showthread.php?t=1870003))

I did try your second recommendation "old_scheme_first" but it had no effect.

The Arduino (which does chat with my USB) has the large square type USB connection. The Rainbowduino has a microUSB connector. Could this be relevant? I have swapped cables and ports to no effect.

My thanks.

---

### Post by matt_symes on 2012-03-10
Hi

> **hundred1906 said:**
> Thanks for that advice. I have not tried the IRQPOLL recommendation for a couple of reasons, firstly my /boot/grub/menu.lst is empty, plus there are reported problems with IRQPOLL on 11.10 so am hesitant to go down that path with my limited understanding (see [http://ubuntuforums.org/showthread.php?t=1870003](http://ubuntuforums.org/showthread.php?t=1870003))

Thanks for this above. I was not aware of it. I will have a look at the sources.

> 
I did try your second recommendation "old_scheme_first" but it had no effect.

I did wonder.

> 
The Arduino (which does chat with my USB) has the large square type USB connection. The Rainbowduino has a microUSB connector. Could this be relevant? I have swapped cables and ports to no effect.

My thanks.

That should not have much of effect (at least i don't think so). 

Just to prove it's not a hardware problem, you have tried it on a different platform (Windows or MAC) ?

Kind regards

---

### Post by hundred1906 on 2012-03-11
I have tried on a different computer but that was also running 11.10 (Windows free zone here). If I found a Windows machine and it worked I would still have the problem so what I think I need to do is find some way of understanding what these error codes are telling me. So for example what are "address 24" and "error -62" in the DMESG dump above. Where do you find the meaning of these codes because they are not showing up for me on a google search.

Alternatively (or as well) should I reload the driver software, in which case how?

My thanks.

---

### Post by matt_symes on 2012-03-11
Hi

> **hundred1906 said:**
> I have tried on a different computer but that was also running 11.10 (Windows free zone here). If I found a Windows machine and it worked I would still have the problem so what I think I need to do is find some way of understanding what these error codes are telling me. So for example what are "address 24" and "error -62" in the DMESG dump above. Where do you find the meaning of these codes because they are not showing up for me on a google search.

Alternatively (or as well) should I reload the driver software, in which case how?

My thanks.

The error codes are defined in include/asm-generic/errno.h in the linux sources.

Error code 62 is 

```
#define ETIME           62      /* Timer expired */
```

-ETIME is returned hence -62.

device descriptor read/64 is the 64 byte descriptor the kernel sends to the device. It is not getting a response hence the timeout.

Having a look in drivers/usb/core/hub.c, it has a number of tries at sending and recieving the descriptor hence the USB device number xx entries.

That is what is happening i think but I would need more time to look at the code to be totally sure though. 

Not sure why it's happening though.

Kind regards

---

### Post by hundred1906 on 2012-03-13
I took a look at the code in drivers...hub.c and noted that it also had the ability to try both old and new schemes (use_both_schemes) so I tried that - without any apparent effect.

Looking in more detail at the two modules (Arduino Uno, Rainbowduino) I see that the Arduino Uno version, unlike its predecessors, does not use the ft232r but has the USB functionality embedded within an Atmega16U2.

Bottom line - I can ignore the fact the Arduino works via USB and concentrate on why my 11.10's do not drive the ft232r on the Rainbowduino.

First question; how do I find out if I have a driver installed for the ft232r and whether it is the latest version.

The web site here [http://www.pluggy.me.uk/arduino-ubuntu/](http://www.pluggy.me.uk/arduino-ubuntu/) instructs loading up avr-libc. Would this include a driver?

My thanks.

---

### Post by matt_symes on 2012-03-14
Hi

> **hundred1906 said:**
> I took a look at the code in drivers...hub.c and noted that it also had the ability to try both old and new schemes (use_both_schemes) so I tried that - without any apparent effect.

It defaults to the new method. If old_style_first did not work then use_both_schemes would be unlightly to work.

> 
Looking in more detail at the two modules (Arduino Uno, Rainbowduino) I see that the Arduino Uno version, unlike its predecessors, does not use the ft232r but has the USB functionality embedded within an Atmega16U2.

Bottom line - I can ignore the fact the Arduino works via USB and concentrate on why my 11.10's do not drive the ft232r on the Rainbowduino.

Were you planning on using the Arduino to control the Rainbowduino ?

> 
First question; how do I find out if I have a driver installed for the ft232r and whether it is the latest version.

According to this page...

[http://www.ftdichip.com/Drivers/VCP.htm](http://www.ftdichip.com/Drivers/VCP.htm)

the driver is in the kernel.

It's a usb to serial driver. It looks like the driver is called ftdi_sio. If  this is the correct driver, then it is included in a Precise install.

```
matthew@matthew-Aspire-7540:~/my_documents/router/dlink_dir_615$ modprobe -l | grep ftdi_sio
kernel/drivers/usb/serial/ftdi_sio.ko
matthew@matthew-Aspire-7540:~/my_documents/router/dlink_dir_615$
```

It does not seem to be loaded by default.

```
matthew@matthew-Aspire-7540:~/my_documents/router/dlink_dir_615$ lsmod | grep ftdi_sio
matthew@matthew-Aspire-7540:~/my_documents/router/dlink_dir_615
```

Therefore load it.

```
sudo modprobe ftdi_sio
```

See this.

```
matthew@matthew-Aspire-7540:~/my_documents/router/dlink_dir_615$ sudo modprobe ftdi_sio
[sudo] password for matthew: 
matthew@matthew-Aspire-7540:~/my_documents/router/dlink_dir_615$ lsmod | grep ftdi_sio
ftdi_sio               40715  0 
usbserial              47077  1 ftdi_sio
matthew@matthew-Aspire-7540:~/my_documents/router/dlink_dir_615$ 
```

It seem you need this driver loaded.

> 
The web site here [http://www.pluggy.me.uk/arduino-ubuntu/](http://www.pluggy.me.uk/arduino-ubuntu/) instructs loading up avr-libc. Would this include a driver?

```
matthew@matthew-Aspire-7540:~/my_documents/router/dlink_dir_615$ apt-cache show avr-libc
Package: avr-libc
Priority: extra
Section: universe/otherosfs
Installed-Size: 33360
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Hakan Ardo <hakan@debian.org>
Architecture: all
Version: 1:1.7.1-2
Depends: gcc-avr (>= 1:4.5.3-1), binutils-avr (>= 2.20.1-2)
Filename: pool/universe/a/avr-libc/avr-libc_1.7.1-2_all.deb
Size: 4665316
MD5sum: d39b60d6a1e15de19d35a9bbfe02a57a
SHA1: be62d26d8776973db1ced474d82ebf66fd0481d8
SHA256: 4537037f14299be1388567eda98906bf5398320a5db94f27ea90e69d2280a2ec
Description-en: [B]Standard C library for Atmel AVR development
 Standard library used to the development of C programs for the
 Atmel AVR micro controllers. This package contains static
 libraries as well as the header files needed[/B].
Description-md5: f8da43e684408fb968aa4789b21feef2
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

matthew@matthew-Aspire-7540:~/my_documents/router/dlink_dir_615$ 
```

It would seem this is the cross compiled C libraries used for write software to the device.

Please bear in mind, i don't own either device you have.

EDIT:

Read through this thread for a comment by the maintainer of the driver.

[http://www.linuxquestions.org/questions/linux-hardware-18/using-the-ftdi_sio-driver-with-a-device-that-is-new-and-not-recognized-798178/](http://www.linuxquestions.org/questions/linux-hardware-18/using-the-ftdi_sio-driver-with-a-device-that-is-new-and-not-recognized-798178/)

I assume udev will create a device node for it.

Kind regards

---

### Post by hundred1906 on 2012-03-15
Thanks for that response. Today the machine I am doing the Arduino work on crashed out with what looks like a PSU problem so I am going to have to drag out an old unit as a replacement.

What I think you were advising me is that ftdi_sio is present in the kernel Precise install (not sure precisely what that is) but is not enabled and that Modprobe...(etc) loads/enables it.

I went through the sequence you recommended last night (modprobe... then lsusb... with the result pretty much as you showed in your > ftdi_sio               40715  0 
usbserial              47077  1 ftdi_sio. Unfortunately it did not result in any change to the result - as indicated by DMESG.

I had previously checked out the other references you gave, particularly that from the driver team. But what I took from that is that the driver is already in the kernel and that the ft232r does not require the latest driver.

What I am trying to achieve here is a unique lighting solution. I have both the Arduino and the Rainbowduino in order to explore the art of the possible, how they are going to work together I have not yet worked out, indeed I expected that and programming either device to be the the problem to be tackled. Delving into Kernel code etc was not on my agenda at all.

Recognising the amount of support you have given already I would really appreciate knowing how I can tell whether or not I have the driver installed because this message > ftdi_sio               40715  0 
usbserial              47077  1 ftdi_sio does not make it entirely clear to this particular numpty.

Meantime I plan to send the Rainbowduino back for testing, though in my experience the problem is more likely to be related to the driver than to the device.

My thanks. Keep watching.

---

### Post by matt_symes on 2012-03-15
Hi

> **hundred1906 said:**
> Thanks for that response. Today the machine I am doing the Arduino work on crashed out with what looks like a PSU problem so I am going to have to drag out an old unit as a replacement.

That's a right pain. Dig out the backup machine.

> 
What I think you were advising me is that ftdi_sio is present in the kernel Precise install (not sure precisely what that is) but is not enabled and that Modprobe...(etc) loads/enables it.


Precise is the name of Ubuntu 12.04. This is the next version of Ubuntu to come out in May this year.

According to that web site i linked.

> Included in 2.6.31 kernel and later

ftdi_sio is included in the kernel 2.6.31 and later. Lucid is 2.6.32, so it should be included in 10.04 and later.

You can check your current kernel release using

```
uname -r
```

> 
I went through the sequence you recommended last night (modprobe... then lsusb... with the result pretty much as you showed in your . Unfortunately it did not result in any change to the result - as indicated by DMESG. I had previously checked out the other references you gave, particularly that from the driver team. But what I took from that is that the driver is already in the kernel and that the ft232r does not require the latest driver.

We first need to ensure this driver is the correct driver for the device. I was using what you posted.

> 
What I am trying to achieve here is a unique lighting solution. I have both the Arduino and the Rainbowduino in order to explore the art of the possible, how they are going to work together I have not yet worked out, indeed I expected that and programming either device to be the the problem to be tackled. Delving into Kernel code etc was not on my agenda at all.

Nice little project.

You should not need to delve into the kernel code at all to communicate with this device.

> 
Recognising the amount of support you have given already I would really appreciate knowing how I can tell whether or not I have the driver installed because this message  does not make it entirely clear to this particular numpty.

You can check if the driver is available to the kernel you have by using modprobe

```
modprobe -l ftdi_sio
```

(Small L after modprobe). You should see something like this.

```
matthew@matthew-Aspire-7540:~$ modprobe -l ftdi_sio
kernel/drivers/usb/serial/ftdi_sio.ko
matthew@matthew-Aspire-7540:~$
```

My point is that this kernel module is available but is not loaded by default so you will have to load it to communicate with the device.

As i stated in my previous post, this will load the driver into the kernel.

```
sudo modprobe ftdi_sio
```

Assuming this is the correct driver then it has to be loaded before anything will happen.

> 
Meantime I plan to send the Rainbowduino back for testing, though in my experience the problem is more likely to be related to the driver than to the device.

I would be very surprised if the device was faulty.

I am more than prepared to spend some time doing some research for you with this device. 

I will not have the time to read up for you until the weekend but i will do some research for you then.

Kind regards

---

### Post by hundred1906 on 2012-03-25
Just to close down this thread. The problem turned out to be a faulty USB device on the Rainbowduino, not my first thought but it happens. The vendor (Cool Components) were quick to respond and I am now up and running.

I took the extra helpfull advice from Matt_Symes and executed > sudo modprobe ftdi_sio to load up the driver into the kernel and that was all it took.

---

### Post by matt_symes on 2012-03-25
Hi

> **hundred1906 said:**
> Just to close down this thread. The problem turned out to be a faulty USB device on the Rainbowduino, not my first thought but it happens. The vendor (Cool Components) were quick to respond and I am now up and running.

I took the extra helpfull advice from Matt_Symes and executed  to load up the driver into the kernel and that was all it took.

Nicely done ! I'm glad you fixed it :)

It sounds like a very interesting project. Have fun with it.

Kind regards

---

### Post by AustinMarton on 2012-08-05
I had the exact same problem trying to connect my Seeeduino on Ubuntu 12.04... turn out to be a bad USB cable!!

---

### Post by pvsuja on 2013-03-20
I have similar problem. My syslogs are getting filled with message:[11670.968036] hub 4-0:1.0: unable to enumerate USB device on port 2
[11671.216038] hub 4-0:1.0: unable to enumerate USB device on port 2
[11671.464036] hub 4-0:1.0: unable to enumerate USB device on port 2
[11671.712038] hub 4-0:1.0: unable to enumerate USB device on port 2
[11671.960038] hub 4-0:1.0: unable to enumerate USB device on port 2
[11672.208037] hub 4-0:1.0: unable to enumerate USB device on port 2
[11672.456038] hub 4-0:1.0: unable to enumerate USB device on port 2
[11672.704037] hub 4-0:1.0: unable to enumerate USB device on port 2



I tried with a different cable also. still the same. I am using FT2232D in debian squeeze. The device is working properly in a Windows machine.

---

### Post by matt_symes on 2013-03-20
Hi

Try this. Unplug the device and open a terminal and type

```
echo -1 | sudo tee /sys/module/usbcore/parameters/autosuspend
```

Plug the device back in. Is it recognised ?

Also unplug your Ubuntu machine so it is totally disconnected from any power. If it's a laptop also remove the battery.

Lean for 10 minutes. Plug the machine back in and start up Ubuntu. Plug the device back in. Is it recognised?

I have to be honest, i don't expect either of these ideas to work in your case but it is always worth trying.

Kind regards

---

### Post by pvsuja on 2013-03-22
Thanks for the response. But it dint work out. I tried autosuspend, old_scheme_first, rmmod ehci_hcd... everything without success. It is working in a windows xp machine. so definitely the problem is not with the device. The system is unable to detect the usb device at all. lsusb and lspci returns nothing relevant and dmesg n syslog full with unable to enumerate messages.
 Hitting my head!

---

### Post by matt_symes on 2013-03-22
Hi

> ....rmmod ehci_hcd....

That command will not work under Ubuntu anymore. You have to unbind the driver in sysfs instead, but you will lose USB2 capability on that port. However, i'm not sure if that is your problem.

Can you explain exactly your setup. what do you have connected in that port ? What type of port (USB 1, 2 or 3) ?

Post the output of...

```
dmesg | grep -i -E "usb|hci_hcd"
```

You have tried all the ports ? Are you using a USB hub ? If so, is the hub powered or not ?

Are you dual booting windows on the same PC ? If so, are you using the same USB port as from windows ? (This is an important couple of questions).

If the windows box is a different PC, have you tried to see if it is recognised from a LiveCD/USB on the windows box when plugged into the same port that windows works with ?

Kind regards

---

### Post by pvsuja on 2013-04-03
Hi,

I tried both rmmod ehci_hcd and unbinding all ehci devices.
I am using USB 2. Its a powered hub.

The Windows box is a different PC. And I tried other two Linux machines also.
In one machine its working perfectly. But not in the second, even though both having same configuration.

---

