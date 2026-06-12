---
title: "wubi..... I think"
date: 2011-07-17
forum: General Help
---

### Post by thisisgonnahurt on 2011-07-17
Hi all, 

not new to linux, certainly not an expert, but trying to do something stupid.... 

ok I was given an old Toshiba portege 3500 tablet, which has no optical drive, and for some reason cannot be booted from anything other then the "official" toshiba usb floppy-and/or-DVD drive. (apparently toshiba thought they were mac for awhile) 

Anyway regardless the way I finally got it up and running was to sysprep the hdd, in another machine with dos, and copied over the xp install disk's then ran the install, got it up and running and have now "upgraded" the thing to Win7 although it actually does run fairly decent, I would like to minimize the machine throw it on the wall a a digital picture frame, with probably an SSH tunnel and proxy in background for when I am at work. 

now my question... this wubi business, do I have an option during the install to just say nuke it all, and use the whole disk, or does it repartition and just dual boot? 

If no is there a way for me to do like a sysprep on a hdd for a minimal install for ubuntu then swap the drive to the Toshiba? 

Thanks

---

### Post by idoitprone on 2011-07-17
> **thisisgonnahurt said:**
> Hi all, 

  

now my question... this wubi business, do I have an option during the install to just say nuke it all, and use the whole disk, or does it repartition and just dual boot? 


wubi does none of that. It use the same ntfs partition that your windows use. No repartition required. Just enough space in your windows harddrive When you install wubi, good tip go to synapathic package manager and restrict all updates for grub.

---

### Post by thisisgonnahurt on 2011-07-17
ok so that gets question one of out of the way..... 
now how far will I get if I do a ubuntu install on another laptop with an optical drive, or usb key pull the hdd, then put it in the toshiba, will it go completely insane on me, or will I (hopefully) be able to log in and maybe use apt to pull down the drivers updates etc for the box?

---

### Post by idoitprone on 2011-07-17
> **thisisgonnahurt said:**
> ok so that gets question one of out of the way..... 
now how far will I get if I do a ubuntu install on another laptop with an optical drive, or usb key pull the hdd, then put it in the toshiba, will it go completely insane on me, or will I (hopefully) be able to log in and maybe use apt to pull down the drivers updates etc for the box?

If your talking about live cd, then your probably not talking about wubi. Here is the link for downloading wubi. If you want wubi, if not then you need to partition your drive
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)

Other thing, your decribing a full install on its own partition.
btw, your directions sound like it waaaaaaayyyyyyyyyyyyyy toooo much work. If you dont have an optical drive, just boot a live usb

To make a live usb, get ubuntu iso, 2 gb usb or more, and unetbootin. It is simple as that. Just go to your bios and boot off of the usb.

---

### Post by srisharan on 2011-07-18
Wubi only gives you a maximum of 30gb space for ubuntu,so good luck with that.It is not enough for serious usage

---

### Post by idoitprone on 2011-07-18
> **srisharan said:**
> Wubi only gives you a maximum of 30gb space for ubuntu,so good luck with that.It is not enough for serious usage

well, i been using linux will a full bloated kde desktop, apps, little goodies, eye candy, video player, and all i come down to is 20 gb. It matters only if you are storing videos

---

### Post by thisisgonnahurt on 2011-07-18
> **idoitprone said:**
> 
If you dont have an optical drive, just boot a live usb


As I said in my first post this machine will ONLY boot off the toshiba floppy/optical drive....cannot boot from live usb if I could I would be done by now. 

Anyway I will keep looking to see if I can do anything with it thanks

---

### Post by Frogs Hair on 2011-07-18
> **idoitprone said:**
> wubi does none of that. It use the same ntfs partition that your windows use. No repartition required. Just enough space in your windows harddrive When you install wubi, good tip go to synapathic package manager and restrict all updates for grub.

Restricting Grub updates from synaptic is not necessary on current versions of Wubi .  I think this may have been a problem in older versions .  I was helping a friend install 10.04 via Wubi and there was a Grub option that you had to make a selection for ,  so pay attention if installing that version .  That was on the first release of 10.04 , which has had distribution updates since .

---

