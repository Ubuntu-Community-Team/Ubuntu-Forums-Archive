---
title: "Install Windows 7 Within Ubuntu?"
date: 2011-12-27
forum: General Help
---

### Post by Serson_Person on 2011-12-27
Usually I spend mass amounts of time searching on-line, but tonight I am lazy and unmotivated.

Ubuntu 11.10 is what I have on my computer right now, but I want to install Windows 7 on it as well so I can run a specific program that isn't working in Wine.

Is this possible?  How can I dual-boot and use Windows 7 alongside Ubuntu, with Ubuntu as the mighty master and Windows 7 as the little sex slave?  :P

---

### Post by QIII on 2011-12-27
If it's a single program and it's not graphics intensive, you could install Virtualbox and virtualize Windows.  Just be sure to read the EULA because the OEM disks (that is, not the retail disks) often proscribe installation on a virtual machine.  

A Linux first dual boot with Windows can require a lot of work and frustration -- unless you have separate physical disks.

---

### Post by Ms. Daisy on 2011-12-27
> **QIII said:**
> A Linux first dual boot with Windows can require a lot of work and frustration -- unless you have separate physical disks. +1 my one-disk experience with it was NOT fun.

---

### Post by WorMzy on 2011-12-27
+1 for [virtualisation]("https://help.ubuntu.com/community/VirtualBox").

Multi-booting isn't as hard as people make it out to be though. I currently have nine operating systems installed on a single disk, and two of those are Windows operating systems which were installed *after* several Linux ones. One of the Windows is installed to a logical partition, which some people would have you believe is impossible.

Of course, it may depend on your Windows installation media. I use OEMs, not recovery disks. Recovery disks might be a bit more finicky.

---

### Post by snowpine on 2011-12-27
The Sticky threads at the top of our Virtualization sub-forum are a good place to start your research:

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by sdowney717 on 2011-12-27
ok, you need virtualbox from the oracle virtualbox website, not the one in the repos. And you need the extensions, which are downloaded from them and installed after you set up the VM.

---

### Post by Ms. Daisy on 2011-12-27
> **WorMzy said:**
> +1 for [virtualisation]("https://help.ubuntu.com/community/VirtualBox").

Multi-booting isn't as hard as people make it out to be though. I currently have nine operating systems installed on a single disk, and two of those are Windows operating systems which were installed *after* several Linux ones. One of the Windows is installed to a logical partition, which some people would have you believe is impossible.

Of course, it may depend on your Windows installation media. I use OEMs, not recovery disks. Recovery disks might be a bit more finicky. 
Too bad I didn't find you when I was flailing around with this failed dual boot LOL :D

I couldn't get virtualbox to recognize my Windows 7 recovery disk.  A more learned person might be able to fenagle it, but I'm not that person.

---

### Post by codebraker007 on 2011-12-27
I use Ubuntu along with Windows 7.
 
The first installation didn't work.  I might have not completed the installation.  I think I unplugged the laptop by accident, I'm not sure.
 
The second installation went smoothly.  It picked up my DSL modem and installed the system files.  Restarted and completed the installation.
 
The video graphics were not too good so I changed the settings in the Display.
 
I like to use Ubuntu when surfing the Net.  And I think I will use my other non-Ubuntu programs with Windows 7, trying not to be connected to the internet if it's possible.
 
I hope that Ubuntu will take over some day as a standard to system usage world wide.

---

### Post by QIII on 2011-12-27
> **Ms. Daisy said:**
> I couldn't get virtualbox to recognize my Windows 7 recovery disk. 

Unfortunately, you need an install disk.  :(

---

### Post by collisionystm on 2011-12-27
> **QIII said:**
> Unfortunately, you need an install disk.  :(

Depends on the manufacture

---

### Post by snowpine on 2011-12-27
> **QIII said:**
> Unfortunately, you need an install disk.  :(

Why do you say this is "unfortunate" out of curiosity?

---

### Post by collisionystm on 2011-12-27
> **snowpine said:**
> Why do you say this is "unfortunate" out of curiosity?

because it did not work for him

---

### Post by snowpine on 2011-12-27
> **collisionystm said:**
> because it did not work for him

That makes sense. :)

---

### Post by Ms. Daisy on 2011-12-27
> **collisionystm said:**
> Depends on the manufacture
What do you mean, manufacturer of what? :?

Do I smell spam?

---

### Post by QIII on 2011-12-27
> **snowpine said:**
> Why do you say this is "unfortunate" out of curiosity?

Because it is unfortunate that those who have only a restore disk cannot  use it to install Windows in VirtualBox -- which means they have to buy  a disk.  It is unfortunate that OEMs do not supply a full install disk that is legal to use on any machine -- provided it is installed on only one machine at a time, like the retail disk.  But Microsoft likes OEM disks, and the EULA it insists on, because that puts the onus of support for the OS on the OEM.

No, you can't install from an OEM restore disk (if anyone doubts that, they are welcome to peruse the virtualbox.org forums) unless you want to go through the process of creating an iso "install disk" from it -- which is of dubious legality -- and it works, and you illegally use the key from the sticker on the machine you bought.  You can, of course, google how to do nearly anything.  But since you would then be installing the OS on a machine for which you have no license ...

Some manufacturers supply an OEM install disk, which is, as it says, an install disk.  However, most of them have a Microsoft EULA that says it cannot be used to install in a virtual machine.  Again, refer to the virtualbox.org forums.

I wouldn't know if it worked for me or not since I have never tried it.  As much as I detest Microsoft, I wouldn't want somebody stealing my intellectual property so I won't steal theirs.

collisionystm, if you wish to impugn someone's integrity, even in jest,  I'll ask you to find someone else to be your foil.

---

