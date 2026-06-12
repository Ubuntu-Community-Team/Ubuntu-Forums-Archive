---
title: "network dd"
date: 2011-07-05
forum: General Help
---

### Post by conradin on 2011-07-05
Greeting all!
I want to clone an SGI IRIX  hard drive over the network. The hardware is ancient, no usb, and the CD rom is shot, its scsi and Im worried I wont be able to get it to boot a live cd.  

if I run dd on a running computer, what consequences might there be?



```
dd if=/dev/sda | gzip -1 - | ssh user@hostname dd of=image.gz
```

where /dev/sda is the local IRIX computer and of=image.gz is a free partition else where.

---

### Post by Habitual on 2011-07-05
n/m. I'm an idiot.

---

### Post by wildmanne39 on 2011-07-05
> **conradin said:**
> Greeting all!
I want to clone an SGI IRIX  hard drive over the network. The hardware is ancient, no usb, and the CD rom is shot, its scsi and Im worried I wont be able to get it to boot a live cd.  

if I run dd on a running computer, what consequences might there be?



```
dd if=/dev/sda | gzip -1 - | ssh user@hostname dd of=image.gz
```

where /dev/sda is the local IRIX computer and of=image.gz is a free partition else where.Hi, it might be safer to use clonezilla, I have seen a lot of posts where people have said that dd can be dangerous to use, it works but I do not think it is the first choice.
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by conradin on 2011-07-11
Bump.
Alt boot disks aren't really an option. I guess I have to just find out.

---

### Post by psusi on 2011-07-11
The image will be corrupt unless the disk is mounted read only.

---

### Post by conradin on 2011-07-11
Is there anyway to boot into a system in read only mode without an external boot disk?

---

### Post by tredegar on 2011-07-11
Using dd to clone a drive that is mounted and running (even in single-user mode) is most unlikely to work.

Going to single-user mode and copying all the files over the network with **cp -a *source destination*** is likely to work.> Code:

dd if=/dev/sda | gzip -1 - | ssh user@hostname dd of=image.gz


I think that if you want to try things like that, you need to use [netcat]("http://nc110.sourceforge.net/").
On destination machine, start netcat listening on port 4040
```
nc -l 4040  | dd of=file.img
```
On old machine, send dd's output to netcat
```
dd if=/dev/sda bs=16M | nc IP.OF.NEW.MACHINE 4040
```
Wait for it to finish. This works brilliantly if you have a fast network.

If you could physically remove the HDD from your SGI IRIX, and install it somewhere else, it would be easier to clone.

What hardware is the SGI IRIX? Is it Intel / AMD ?

---

### Post by psusi on 2011-07-11
> **conradin said:**
> Is there anyway to boot into a system in read only mode without an external boot disk?

Yes: pass the kernel the "ro" boot argument.

---

### Post by conradin on 2011-07-13
The IRIX Achetecure is MIPS. I thin I will try the netcat option. 
I had a pci scsci device I used to use for cloning old hard drives, but that think died 2 years back. This stuff is getting to the point where if you turn the computer off, you have to prepare for the idea it might never boot again. This computer came out in 1996. thats like 150 years ago in computer years. 

We are siting on an OC-24 so the network bottle-neck will be at the IRIX box.

---

