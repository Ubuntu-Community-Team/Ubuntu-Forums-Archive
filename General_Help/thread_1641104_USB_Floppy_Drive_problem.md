---
title: "USB Floppy Drive problem"
date: 2010-12-08
forum: General Help
---

### Post by Habeouscorpus on 2010-12-08
I have a Dell Floppy Drive Module that I am trying to use. When I plug it in, I see "Floppy Drive" in the Computer screen. However, when I try to click on it, nothing happens. So I went to the Disk Utility to see if it wasn't mounted, but there was nothing to mount! I know the floppy disk in there is okay, because it works on another computer. There are no Propriety Drivers listed for this device. Any solution?

---

### Post by coffeecat on 2010-12-08
There is a long standing, unresolved bug in Ubuntu (most irritatingly) that means that if you have an **internal** floppy drive (yes, I know you have a USB one - we'll get to that), although the icon appears in 'Computer', when you click on it you simply get an error and the floppy disc is not read. The workaround for an internal floppy drive is this command from the terminal:

```
udisks --mount /dev/fd0
```I have no experience of USB floppies, but I suspect there may be a similar problem. The above code may or may not work because your drive may or may not be designated as fd0. Try it anyway. If it doesn't work, plug the drive in, switch it on and then do this command from the terminal:

```
dmesg | tail
```You'll get a few lines of output with, hopefully, the device name which you can substitute in the above command. Not elegant, but it might work.

**Edit:** I should add that if you are used to Windows, Linux writing to floppies is a bit un-nerving at first. You drag and drop, but nothing much seems to happen - usually. When you're finished, right-click on the desktop icon and choose unmount and only then does the write occur. You must remember not to remove the floppy before you unmount it.

---

### Post by Habeouscorpus on 2010-12-08
YES! You are the man/woman/other!

The first command worked with the aid of the second (it wasn't labeled fd0). It's now mounted and buzzing happily. 

Thank you. I am used to Windows, and Linux is refreshing but unfamiliar.

---

### Post by coffeecat on 2010-12-08
I'm glad it worked. Out of interest...

> **Habeouscorpus said:**
> The first command worked with the aid of the second (it wasn't labeled fd0).

What was it? fd1? Or something else?

---

### Post by Habeouscorpus on 2010-12-08
sdc. (I dunno... I just plugged it in and went for it.)

---

### Post by Sly Cooper on 2011-02-05
if anyone is still having problems

try
```
udisk --mount /dev/sdc
```

worked for me

---

