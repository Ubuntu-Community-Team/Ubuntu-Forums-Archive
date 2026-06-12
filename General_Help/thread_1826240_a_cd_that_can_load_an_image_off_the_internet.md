---
title: "a cd that can load an image off the internet"
date: 2011-08-16
forum: General Help
---

### Post by mosesaro on 2011-08-16
Is it possible to build an image on a cd that can allow me to load an image of an internet on the computer. without installing it. Like a dummy terminal.

---

### Post by mosesaro on 2011-08-16
Is it possible to build an image on a cd that can allow me to load a Ubuntu image off a network folder to run on a pc.

---

### Post by graphius on 2011-08-16
Are you wanting to install over the network? for example on a remote server? or do you want to run the image from a remote location (not sure why you would want to do this...)
If you just want to run linux on a "dumb terminal" you could set up NFS or other shared folders. It would be slow though, and possibly unstable.
Installing would be a bit harder. If you had, or could get physical contact, ie get someone else to go to the machine, I would just use a USB or CD/DVD, or even ghost a hard drive image (using ddclient?) and install the hard drive in the remote machine.

---

### Post by graphius on 2011-08-16
If you download the ubuntu cd image and burn it to disk, you can run ubuntu off the cd without installing it. It will of course run slower than if it were installed on the hard drive, and installing programs or saving preferences is not really possible. 
You can also install Ubuntu to run within windows (wubi) or to dual boot, in other words, when you start the computer you can choose to boot into ubuntu, windows or any other operating system you have installed. 
I use the latter for when I want to get pissed off with Windows...:D
These systems do not affect each other.

Is this what you are asking?

---

### Post by mosesaro on 2011-08-16
I want to run from a remote location. How can I do that? Or at least load it into the memory of the machine.

---

### Post by Iowan on 2011-08-16
Threads merged.
From Code of Conduct:
> Do not cross post, or post the same thing in multiple locations.

---

### Post by mosesaro on 2011-08-16
No I dont want the cd to have everything I want the things to run of a network folder but have the cd just to boot

---

### Post by graphius on 2011-08-16
Theoretically, and I am NOT a linux guru, you should be able to install a version of Linux normally, set up a NFS for file sharing and then point the various folders (/home, /usr, /var, etc) to the network shares.
You would have to be careful though, or you could get some recursive linking. Also, if the network goes down you would be foobar...

---

