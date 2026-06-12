---
title: "Having trouble creating USB."
date: 2010-11-25
forum: General Help
---

### Post by thebarisaxkid on 2010-11-25
Hey all,

I am currently undergoing some trouble with creating a bootable USB.  I am in Ubuntu 10.10 Maverick Meekrat and I want to move to Debian 5 Lenny.  When I try the built in StartUp Disk Creator, it takes longer than it usually does with other distros (about 1% every 3-7 seconds).  Not only that but towards the end of the write, it gives me an error:

```
Installation Failed
Could not move syslinux files in "/media/2C5B-9FFE": [Errno 2] No such file or directory. 
Maybe "/tmp/tmpw4Jree" is not an Ubuntu image?
```

So I try this in the terminal to make the USB instead:

```
sudo dd if=Downloads/debian-506-alpha-CD-1.iso of=/dev/sdb
```

*if=...* being where my iso is located and *of=...* being the device I want it on.

However, when I restart, the BIOS tells me that there is no boot sector on the USB device, and boots into my OS.  I tried this with Arch Linux before and it worked.

I also tried UNetBootin, but that was an epic fail.  After it downloaded the files to the USB, it told me to move the iso to the USB or /(root) of my hd.  I did it on my USB, as I could not see how it would work if I placed it on my HD.  However, when I booted into the USB, it searched for the ISO but did not find it at all.  (I clicked and dragged the iso to the USB, could that be the problem?)

What should I do?  Is there something that I can add to the *dd if=... of=...* command to make the drive bootable?

Or should I try a different program?  Any reccomendations will be accepted.

Big thanks to everybody!!

---

### Post by Foxheadz on 2010-11-25
Move the .iso to the / part of your computer. Then open unetbootin and select it from there and then continue making the startup disk

---

### Post by 12apennachi on 2010-11-25
> **Foxheadz said:**
> Move the .iso to the / part of your computer. Then open unetbootin and select it from there and then continue making the startup disk

unetbootin is the best and you don't need to move the iso. you can navigate to the home folder and go from there

---

### Post by Foxheadz on 2010-11-25
It's quite good but i find that the selecting of iso(s) could be made better. And dude you might not want to go around with that signature

---

### Post by ajgreeny on 2010-11-25
The ubuntu startup disk creator is only for the ubuntu family of OSs.  No others will work, so debian will never be successfully made that way.

Unetbootin is the way to go.

---

### Post by thebarisaxkid on 2010-11-25
I tried the second option in the Unetbootin, but it gave me an error saying "invalid kernel image" 

I noticed when I pressed tab on the "Default" boot option, it shows that kernel initrd (or whatever it is called) is pointing to ubninit.  Shouldn't it be pointing to something like 2.26.2.6-26?

How can I fix this, do I just type in the right kernel name? What is the kernel name?

> **Foxheadz said:**
> And dude you might not want to go around with that signature

But it is true... (Well, maybe windows is better than Mac)

---

### Post by Foxheadz on 2010-11-25
Hmm maybe you have a corrupted iso i would try re downloading it. Also i was talking about the other guy:that command wipes your hard drive

---

### Post by thebarisaxkid on 2010-11-25
> **ajgreeny said:**
> The ubuntu startup disk creator is only for the ubuntu family of OSs.  No others will work, so debian will never be successfully made that way.

When I looked at the description in the repository, it said that it works for Debian and any other Debian-based distros.

---

### Post by thebarisaxkid on 2010-11-25
> **Foxheadz said:**
> Hmm maybe you have a corrupted iso i would try re downloading it. Also i was talking about the other guy:that command wipes your hard drive

Hmm, I'll try that.  

Yea, I would take off that signature right now, or else he gonna get his **** wooped.

---

### Post by Foxheadz on 2010-11-25
Also have you tried just burning the iso to a cd/dvd?

---

### Post by thebarisaxkid on 2010-11-25
> **Foxheadz said:**
> Also have you tried just burning the iso to a cd/dvd?

Yeaaah, about that...

I currently do not have any working cd drives.  I will be getting a new computer (replacing an old dell dimension 8300, about 5/6years old), so I might have to wait until then.  And the cd drive on my laptop is a little funky.  Might have to look for a USB optical drive.

But for now, USB is only option.

---

### Post by thebarisaxkid on 2010-11-25
Hey, while we're at it, Debian or Fedora?

Yeah I know, wrong place...

---

### Post by Foxheadz on 2010-11-25
Lol ive only ever tried ubuntu and linux mint so id have to go with debian

---

### Post by C.S.Cameron on 2010-11-26
I personally do not like Fedora's method for pendrive persistence.
Debian uses casper-rw and home-rw files or partitions for persistence, which works well.

---

### Post by thebarisaxkid on 2010-11-26
Ok so I tried redownloading it.  I actually chose a different version (lxde+xfce) while I was at it to make sure it wasn't the ISO that was to blame.  Gave me same error in Unetbootin.

This is exactly what it said:

```
invalid or corrupt kernel image
boot:_
```

When I pressed tab on the default option, this is the path it gave me:

```
/ubnkern initrd=/ubninit 
```

Ugh, this is a pain in the buttt.

---

### Post by thebarisaxkid on 2010-11-26
Ok, so I used the *dd* command, but this time I used Fedora 14 and it worked 100%.  So now I'm in Fedora.  I kinda like it, not too much comes pre-installed.  It looks good, I didn't need to find any drivers for wireless, which is awesome.

Now I need to hop my way over to debian.

Can I use the same *dd* command, or is it different in Fedora?

I probably should ask this in Fedora Forums (if there is one) but let's keep it simple and in one place.

---

### Post by Foxheadz on 2010-11-26
I just did a quick google and from what i can tell yeah it's the same.Most bash commands will be

---

### Post by thebarisaxkid on 2010-11-26
found a tutorial on the debian website, except I can't get the last package under 4.3.3, not available in fedora.  Ill see if it is available in the ubuntu repository.  But in order to get to Ubuntu, I have to edit grub.

If not, I'll have to do some crazy virtualbox stuff.

Man, all this work, just to get debian...

Tutorial: [http://www.debian.org/releases/lenny/i386/ch04s03.html.en](http://www.debian.org/releases/lenny/i386/ch04s03.html.en)

---

### Post by thebarisaxkid on 2010-11-27
Errg, Fedora isn't letting me use virtualbox or edit grub.  GRRRRR!

---

### Post by thebarisaxkid on 2010-11-27
Well, after a lot of reinstalling OS's, I managed to get the MBR tool.  I used it on my flash drive, rebooted, and what do you know... another failure!

It gave me this:

```
MBR FA:
```

I'll just wait until I can get a working CD drive and do it that way.  I do have a few other ideas, but I doubt they will work at all.
One idea: use the same dd command and use the MBR tool.
Another: Retry the Unetbotin, maybe the actual program had a glitch.

Thanks for the help, but I guess it wasn't meant to be.

---

### Post by thebarisaxkid on 2010-11-28
Apperently the actual program had a glitch.  I tried UNetbootin again, and it worked.  Well almost.

At least I got into the installer.  I choose the graphical installer because I am lazy.  But before it loaded the installer, it said the USB device could not be enumerated in port*X*.  So when it came to the step where it had to find where the packages were, it said 
"could not mount/find cd/dvd" (thats what it was basically saying)

Try again (yes/no)?

It has to do with the enumerating the USB device, if I am not mistaken.  I tried in different ports, I will try more of them.

---

### Post by thebarisaxkid on 2010-11-28
Well, I tried all the ports.  Some gave me the "USB enumerator" message, while others didn't.  I tried all different install types (graphical/nongraphical) but not one of them saw the USB.  It was looking for a CD, but there wasn't any.

I will post this on debianforums, as this is becoming debian's problem.

---

### Post by Yellow Pasque on 2010-11-28
Did you boot with this boot argument:?
```
cdrom-detect/try-usb=true
```

---

### Post by thebarisaxkid on 2010-11-29
Boom!

[http://forums.debian.net/viewtopic.php?f=10&t=53256](http://forums.debian.net/viewtopic.php?f=10&t=53256)

If only I found that a couple days earlier.

---

### Post by C.S.Cameron on 2010-11-29
> **thebarisaxkid said:**
> Boom!

[http://forums.debian.net/viewtopic.php?f=10&t=53256](http://forums.debian.net/viewtopic.php?f=10&t=53256)

If only I found that a couple days earlier.


Does it end up as a persistent install? Does it save changes?

---

### Post by thebarisaxkid on 2010-11-30
> **C.S.Cameron said:**
> Does it end up as a persistent install? Does it save changes?

:/ not sure about that.  As you could tell, I am no expert in this subject.

I think it would, but don't quote me on that.

---

