---
title: "Need usbserial driver for the problink usb modem?"
date: 2009-10-21
forum: General Help
---

### Post by shamsat on 2009-10-21
Hi,
I have ubuntu 9.04 desktop and server installed, i want to use prolink phs100 usb modem for my internet connection, to setup this modem it need the usbserial driver or module which is not compiled in the present ubuntu kernel, is there any way to insert this driver to the runing kernel and how? or is there any way to solve this problem?

---

### Post by superdav42 on 2009-10-21
What you are looking for is ```
sudo modprobe usbserial
``` which will insert your module into your kernel. 
You'll probably need more than this to get it working see [http://nmlaxaman.blogspot.com/2009/04/prolink-phs100-hsdpa-workout-for-debian.html]("http://nmlaxaman.blogspot.com/2009/04/prolink-phs100-hsdpa-workout-for-debian.html")

---

### Post by shamsat on 2009-10-22
Thanks for the reply, the problem is the usbserial modules is removed from the ubuntu 9.04, this is the command result:

# modprobe usbserial
FATAL: Module usbserial not found

any solution please?

---

### Post by GeorgeVita on 2009-10-27
Hi **shamsat**,
due to bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345002)
initial kernel of 9.04 (LiveCD) has usbserial driver encapsulated into kernel and needs the parameters into grub.

Read: [http://ubuntuforums.org/showpost.php?p=7691132&postcount=2](http://ubuntuforums.org/showpost.php?p=7691132&postcount=2)

Later kernel, which comes to you after update (you need internet connection) restores usbserial as an external driver and can be used as usual.

Regards,
George

---

