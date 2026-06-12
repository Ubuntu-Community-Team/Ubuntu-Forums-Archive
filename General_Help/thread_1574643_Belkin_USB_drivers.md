---
title: "Belkin USB drivers"
date: 2010-09-14
forum: General Help
---

### Post by surrealillusions on 2010-09-14
Hi all,

I've had a quick Google around, but everything I find seems to be a bit out of date (from over 2 years ago).

I'm running Ubuntu 10.04 and have tried to use a Belkin N USB Wireless adapter but it doesn't recognise it, nor can I find any drivers.

Is there a way to get the laptop to recognise the Belkin adapter?

Thanks

:)

---

### Post by surrealillusions on 2010-09-16
Any help at all?

Would like this working tomorrow...

---

### Post by davidmohammed on 2010-09-16
Please can you plug in your usb device and in a terminal session type the following

lsusb

dmesg

for each of those commands, please copy and paste the output into a reply here - use CODE TAGS for your reply so that the output is properly formatted.

---

### Post by surrealillusions on 2010-09-16
Bus 002 Device 002: ID 050d:815f Belkin Components

for the first one (amongst a few other lines). The 2nd one though produced ALOT of stuff...which I dont like to post on a public forum...seems to contain a few bit of info about the computer. Anyway...couldn't see anything with Belkin in it from a scan down it.

---

### Post by davidmohammed on 2010-09-16
before you plug in the usb device type

dmesg

Note where the last line display is.

then plug in the usb device.

retype dmesg

copy and paste here new lines displayed.

The reason we need this is to find out how (or even if) the kernel is trying to recognised your device.

---

### Post by jshepherd on 2010-09-16
Belkin drivers are a big problem with versions from 9.10 on. I tried everything I know including ndiswrapper to no avail. In the end I installed 9.04 and it works faultlessly.

---

### Post by surrealillusions on 2010-09-16
Ah right, here are the 2 new lines:

[  831.184037] usb 2-2: new high speed USB device using ehci_hcd and address 6
[  831.318841] usb 2-2: configuration #1 chosen from 1 choice

---

### Post by surrealillusions on 2010-09-16
> **jshepherd said:**
> Belkin drivers are a big problem with versions from 9.10 on. I tried everything I know including ndiswrapper to no avail. In the end I installed 9.04 and it works faultlessly.

ohh... :( Dont think I want to install 9.04...could i install it side by side with 10.04 ?? If so..where do i download it from?

---

### Post by jshepherd on 2010-09-16
Maybe try this [http://ubuntuforums.org/showthread.php?t=863591](http://ubuntuforums.org/showthread.php?t=863591)

It didn't work for me but maybe you'll have more success.

---

### Post by davidmohammed on 2010-09-16
...

9.04 will not help with your device.  Its too new for lucid - in fact I don't think even maverick will help you with this.  If i've just read this correct, its just gone into the 2.6.36-rc1 kernel.

You device is using the [RTL8192SU]("http://cateee.net/lkddb/web-lkddb/RTL8192SU.html") chipset

Here is a [link]("http://ubuntuforums.org/archive/index.php/t-1425697.html") I've found that describes how to download and install the device driver for your belkin - look at the last few posts from where to download and how to compile and install.

---

### Post by surrealillusions on 2010-09-16
> **jshepherd said:**
> Maybe try this [http://ubuntuforums.org/showthread.php?t=863591](http://ubuntuforums.org/showthread.php?t=863591)

It didn't work for me but maybe you'll have more success.

Wooo...it seems to have worked :D The blue light is now flashing away...never been so pleased to see a blue flashing light lol

---

### Post by jshepherd on 2010-09-16
> **surrealillusions said:**
> Wooo...it seems to have worked :D The blue light is now flashing away...never been so pleased to see a blue flashing light lol

Lol! Fingers crossed then:)

---

### Post by surrealillusions on 2010-09-16
Seems to be abit slow..but im not sure if its the site as others seems to be working ok...but then this site works ok here on my main desktop..

Connection seems to be intermittent (sp??). Getting alot of "connection timed out" messages

---

### Post by davidmohammed on 2010-09-16
ndiswrapper is just a workaround - it works for some, not for others.  The real answer is downloading, compiling and installing the linux device driver - see my post earlier.

---

### Post by surrealillusions on 2010-09-16
Ah right. That thread all looks confusing to me. It works at the moment, so hopefully I'm able to use the internet over the weekend away from home.

Thanks for the help.

:)

---

