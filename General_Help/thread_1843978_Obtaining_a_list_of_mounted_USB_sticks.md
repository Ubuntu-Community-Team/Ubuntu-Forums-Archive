---
title: "Obtaining a list of mounted USB sticks"
date: 2011-09-14
forum: General Help
---

### Post by Azdour on 2011-09-14
Hi,

Does anyone have any ideas how I can detect the USB sticks mounted on Ubuntu 10.04. I need to do this through a script that will not be run as sudo. 

I've played about with various things but I have not found anything I can ask what USB sticks are currently mounted.

Thanks in advance.

---

### Post by haqking on 2011-09-14
> **Azdour said:**
> Hi,

Does anyone have any ideas how I can detect the USB sticks mounted on Ubuntu 10.04. I need to do this through a script that will not be run as sudo. 

I've played about with various things but I have not found anything I can ask what USB sticks are currently mounted.

Thanks in advance.

```
lsusb -vt
```lsusb lists usb devices, the v means verbose and the t displays tree format where it should list is a mass stroage device or not

you might want to pipe that with less or to a file though

---

### Post by Azdour on 2011-09-14
Hi,

Cheers for the quick reply. Just a few more questions :)

I have played with lsusb, it was the first thing I tried to use. There are two problems with it:

[LIST=1]
[*]How do I tell the difference between a USB Stick and USB HDD
[*]I need to be able to find the path it is mounted at
[/LIST]

Thanks.

---

### Post by haqking on 2011-09-14
> **Azdour said:**
> Hi,

Cheers for the quick reply. Just a few more questions :)

I have played with lsusb, it was the first thing I tried to use. There are two problems with it:

[LIST=1]
[*]How do I tell the difference between a USB Stick and USB HDD
[*]I need to be able to find the path it is mounted at
[/LIST]

Thanks.


oh i dont think thats possible,  The system dont know what shape the device is...LOL

a USB Stick and a HDD are merely seen as a USB storage device (the system is shape agnostic ;-)

The path should be /media or /mnt usually /media

though a lsusb should identify it as a flash in its description

---

### Post by Azdour on 2011-09-14
Hi,

On this system they will be mounted under /media but there is the potential that a usb device other that a usb stick is plugged in as well so I wanted to avoid user error :)

The Disk Utility can tell the difference between USB Flash Memory and a USB Harddisk so there must be a way, perhaps its too low level for scripting?

---

### Post by haqking on 2011-09-14
> **Azdour said:**
> Hi,

On this system they will be mounted under /media but there is the potential that a usb device other that a usb stick is plugged in as well so I wanted to avoid user error :)

The Disk Utility can tell the difference between USB Flash Memory and a USB Harddisk so there must be a way, perhaps its too low level for scripting?


well you could pipe it to a text file and grep for the idProduct field which is where flash is denoted usually.

---

### Post by Azdour on 2011-09-14
Hi,

When you talk about piping, are we still talking about lsusb or the GUI palimpsest (Disk Utility)?

---

### Post by haqking on 2011-09-14
> **Azdour said:**
> Hi,

When you talk about piping, are we still talking about lsusb or the GUI palimpsest (Disk Utility)?

piping means using a pipe (filter) in a command to pipe it to another command such as:

```
ls -l | less
```where it is piped to the less command to filter the display

redirection is when you change the default output device such as
```

ls -l > filename
```

which instead of displaying locally onscreen (default device) it sends the results to a text file

---

### Post by nitstorm on 2011-09-14
Sorry lil too late, irrelevant now

---

### Post by Azdour on 2011-09-14
Hi,

LOL I know about piping just want to know what to pipe :)

I can pipe lsusb and grab the product id, I would then need to know how to find out the mount point.

Its a shame that the id in lsusb is not the same id in /dev/disk/by-id otherwise that would be the solution...

---

### Post by haqking on 2011-09-14
> **Azdour said:**
> Hi,

LOL I know about piping just want to know what to pipe :)

I can pipe lsusb and grab the product id, I would then need to know how to find out the mount point.

Its a shame that the id in lsusb is not the same id in /dev/disk/by-id otherwise that would be the solution...

oh sorry, didnt mean to teach to you to suck eggs...LOL...well it helps if someone else is reading and didnt know how to pipe ;-)

i meant you could script a lsusb redirected to a text file.  Then grep or pipe the lsusb to grep to find the idProduct where the description contains Flash (as most i think that ive seen have a descriptor of Flash in it

of course im thinking out loud, someone will come on in a second with a much easier method im sure ;-)

---

### Post by Azdour on 2011-09-14
Hi,

:) No worries.

The problem is that lsusb does not always show flash in the product name for usb sticks. I have several here that I have already played with to see it is inconsistent enough not to be useable.

I've come to my limit of my understanding of the underlying mechanics of Ubuntu to know how to do this and Google has not been my friend :) That's why I turned to the forum to see if anyone else can point me in the right direction :)

---

