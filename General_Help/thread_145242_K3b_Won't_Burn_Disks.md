---
title: "K3b Won't Burn Disks"
date: 2006-03-15
forum: General Help
---

### Post by tstrickland on 2006-03-15
I can't get K3b to burn a CD. No CD icon appears on the desktop when I insert a disk into the drive (I was expecting it to); K3b tries to write, but nothing happens.:-? 

What to do?

Thanks!

---

### Post by tstrickland on 2006-03-15
Ooops!! I forgot to note that I get an error message when I insert a blank CD into the drive. It says:

An error occurred while loading **media:/hdc:[B]**[/B]
The file or frolder **:/hdc[B]**[/B]does not exist.

---

### Post by incubus on 2006-03-15
Hello there,

Did you switch cables or drives by any chance?

What do you get from:
$ ls /dev/cdrom -l

incubus

---

### Post by tstrickland on 2006-03-16
[QUOTE=incubus]Hello there,

Did you switch cables or drives by any chance?

What do you get from:
$ ls /dev/cdrom -l

incubus[/QUOTE]

I got:

[INDENT]lrwxrwxrwx 1 root toot 3 2006-03-16 02:44  /dev/cdrom->hdc[/INDENT]

I inserted two different CDs but got the same error message previously noted about the missing folder. Nevertheless, I attempted to burn some files to the CD. K3b started and indicated:

[INDENT]Starting TAO writing at 12x speed[/INDENT]

Then nothing happened.:confused: 

My computer has two internal drives: a CD burner and a DVD reader. I have also connected by USB an external DVD burner. 

Then I tried to burn a DVD. I couldn't find a way to erase the DVD, and it didn't like my attempt to overwrite a file already on it, so I got a clean DVD and tried it. Got lots of error messages from K3b. If you think they're important, I'll go back and copy them.

As yo can see, I've made no progress.:( 

Your help is appreciated!

---

### Post by sbassett on 2006-03-16
If it would not be to much trouble, please post these messages.

Thanks.

Also, please check your settings within K3b, as your DVD burner would be a /dev/sdX device.
You stated that when you insterted a blank CD, you receive errors regarding media:/hdc, did you put the blank disk into the Secondary Master (more than likely your CD burner) or your external DVD Burner. And lastly (sorry for all this) would you be able to post your /etc/fstab file. To the best of my memory, KDE should be calling media:/cdrom rather than media:/hdc (if this is incorrect, someone please give me a virtual slap in the face and correct me).

Thanks.

---

### Post by Kyle- on 2006-03-16
You may not have permission to access your CD drive as a normal user with k3b.  In a terminal, type:

```
sudo k3b
```

Then enter your password.  K3b will start.  Now try to burn a CD with it - it should work.

Good luck,

Kyle-

---

### Post by MJN on 2006-03-16
[quote=tstrickland]Ooops!! I forgot to note that I get an error message when I insert a blank CD into the drive. It says:

An error occurred while loading **media:/hdc:**
The file or frolder **:/hdc**does not exist.[/quote]

That error (presumably in Konqueror) in itself is not a problem - it's merely indicating (in a roundabout kind of way) that the CD is blank i.e. no files or rather not even a filing system.

It happens to me for every blank disc I put in too. (however I can burn okay so can't help you there - other than pointing out the above is likely a red herring)

Mathew

---

### Post by tstrickland on 2006-03-16
Lots of replies to your comments:

**sbassett:**

K3b Setup shows four devices. These are:

[INDENT]ATAPI DVD DD 2X16X4X16/dev/scd0
ATAPI DVD DD 2X16X4X16/dev/sg0
CyberDrv CW 078D CD-R/RW/dev/hdc
JLMS DVD-ROM LTD-166S/dev/hdd[/INDENT]


The output by K3b while trying to burn to the DVD was:
[INDENT]
i  Waiting for media ...
i  Growing ISO 9660 file system on DVD+RW
i  Using growisofs 5.21
i  Starting writing...
i  Writing speed: 5678 KB/s (4.10x)
i  Flushing the cache may take some time
i  Writing to lead-out may take some time
x  frowisofs did not exit clearly

[/INDENT]
(NOTE: 1. Overall progress was shown to be 91%, and 2. some of the files were copied to the DVD)

**Kyke**

I ran the "sudo k3b" code you suggested, but I couldn't copy to the CD. However, I got lots of error messages as output on the terminal. They are shown below.


tom@Tom:~$ sudo k3b
Password:
ERROR: Communication problem with k3b, it probably crashed.
tom@Tom:~$ k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
k3b: ERROR: (K3bDevice::Device) Unable to do inquiry.
Error: "/var/tmp/kdecache-tom" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
Error: "/tmp/kde-tom" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/kde-root"
Error: "/tmp/ksocket-tom" is owned by uid 1000 instead of uid 0.
Link points to "/tmp/ksocket-root"


I hope this is meaningful. Does this tell anyone anything?

Thanks!

---

### Post by sbassett on 2006-03-18
tstrickland -
Have you run the k3bsetup program. If this is not available with kubuntu (stock) then please forgive. But if it is, try sudo k3bsetup. If this spot up, then please go through the quick setup routine. Also, are your usb ports 2.0? It looks like the growisofs almost made it there, and barring a system bork, it looks as if:

1. The buffer ran out near the end (did you see any evidence?)
2. Too much data for the disc (again, any possibility?)

Let us know.

---

