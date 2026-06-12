---
title: "Major problem"
date: 2009-08-08
forum: General Help
---

### Post by Vignesh S on 2009-08-08
After a major problem last time (see this thread [http://ubuntuforums.org/showthread.php?t=1216914](http://ubuntuforums.org/showthread.php?t=1216914) to see what I mean), I was stuck with Ubuntu 8.10, and I wanted 9.04 to work on my computer. However, after I upgraded to 9.04 and restarted it, my computer is stuck at "Loading please wait" screen. Now, I know that 9.04 32 bit wouldn't install even after I replaced the faulty RAM modules, and I think that it is that incompatibility issue again. 

Now, I have just recently transfered all of my files onto my fixed PC, but now I can't even access them. And this is valuable data I am talking about. So my last resort is to take the files out again via a Live CD, but I forgot, I can't do that because I have to change the permissions for me to do that, and I clearly can't do that if I can't even access the files in the first place to do that!

This computer is not exactly essential to do my school work with because I have a laptop I am currently typing this on, but if I need any of the files on it at the moment, which might just be anytime, then I can't even access them.

I really need answers, for as I said before, this is very valuable data, and there is no way I can lose them.

Does there happen to be a way around this permission thing? On the file's current setting, I can't even copy them onto my USB.

In case you need them, here are my computer specs...
Asus P5VD2-X motherboard 
2GB DDR2 (single RAM module)
Nvidia GeForece 7600GT (or something like that for a graphics card)
Pentium Dual Core

I wander what I have done to this computer now... 

Oh, and one more thing. Even after the 15 minutes or so it took for me to type this up, that "Loading please wait" thing is still on the screen...

---

### Post by Vignesh S on 2009-08-08
This may seem impatient, but I need answers NOW! My very faith in Ubuntu is being put under the test here, as I made it clear, very valuable data is at stake here, which I simply cannot afford to lose!!!

Oh and one more thing, I can't even access the hard drive because I don't know the Ubuntu 9.10 Alpha 3 root password for mounting my hard drive!!! To all of the community out there, PLEASE HELP!! I am at my wit's end here!!!

---

### Post by Iowan on 2009-08-08
No guarantees (at all), but you *might* be able to use something like [tomsrtbt]("http://www.toms.net/rb/") to access the system.

---

### Post by yeeeev on 2009-08-08
I don't understand why you can't access the data using a liveCD ans sudo from there. Is the FS encrypted?

---

### Post by Vignesh S on 2009-08-08
Alright then, let's do this one step at a time.

Firstly, how on Earth do I use tomsrtbt? I have absolutely no experience with recovering data, and this is the first time I have even heard of it. If I can use it, then can you give me the instructions as to how I should use it?

Secondly, I presume that FS means my hard drive. No, it isn't, and I think that its a good thing too.

Now, I am going to try the 8.10 live CD. See if it wants to mount...

EDIT: I just remembered something. I made the permissions for the files to be readable and writable to anyone other than the user when I last had a 9.04 glitch. See if it is still holding up, because it just might work...

---

### Post by Vignesh S on 2009-08-08
Didn't seem to work. It still won't let me copy the files! Isn't there some sort of Ubuntu recovery disc to let me fix up the installation without me losing my files? If not, can I get around the permissions? I really need this data.

Oh and by the way, the /home directory is not a separate partition. The entire installation is one file.

---

### Post by snowpine on 2009-08-08
Boot with an Ubuntu 9.04 Live CD and back up your important data to an external drive.

Take a deep breath.

Boot into "recovery mode" and:

```

sudo apt-get update 
sudo apt-get upgrade
sudo do-release-upgrade

```

This should complete your upgrade to 9.04, good luck!

---

### Post by Vignesh S on 2009-08-08
I have a few questions about the recovery CD thing:

1. How do I get into the recovery mode for 9.04?
2. Since I can't really take my valuable data off the hard drive, will the upgrade via the Live CD format that data clean?
3. If the answer to the above question is yes, then is there any way to get around that annoying write protect function?

---

### Post by Vignesh S on 2009-08-08
Another quick thing. I hope that the recovery mode is by the live CD because it also gets stuck at the loading please wait in recovery mode provided by the GRUB menu!

EDIT: If I was to put the hard drive into a drive enclosure and boot it from another computer, would it boot without that annoying error? I think that it is a hardware incompatibility and not a problem with the hard drive.

---

### Post by Vignesh S on 2009-08-11
Does anyone out there know if this will work? I'll see about booting the hard drive from another computer via a hard drive enclosure. Having my fingers crossed for this one...

---

### Post by P4man on 2009-08-11
Calm down mate :) Grab a coffee and relax a bit :)

First of all, to get to your data, I dont know what "permission thing" you changed, but a 9.04 live cd should let you boot, mount the drive, and copy your files somewhere else. IF this doesn't seem to work, please be precise what it is thats not working.

Now I see you had bad ram, its possible your harddisk got corrupted by that. Doesn't mean you can't get any data off it, but you'll have to check your filesystem, or likely ubuntu is not going to be able to mount it. Run "fsck /dev/sda1" (or whatever the name of the harddisk). Do this from the live cd.

To answer your question about booting on a different machine; yes, you probably can. Or I should say could. If you got a working installation, it will almost always boot on any other machine. I just doubt you have a working bootable disk right now. Also, its not a good idea to boot it anyway, if you suspect trouble with the disk. Better to boot off a cd, and access the drive from there.

---

### Post by zkriesse on 2009-08-11
> **jim.licy said:**
> not sure
Jim.licy....don't just answer posts like that...if you don't have at least a possible answer or solution don't even bother posting.....come on man.

---

### Post by Vignesh S on 2009-08-12
I don't know who Jim.licy is, Zachk18. However, the problem is now solved. I asked my good friend who introduced me to linux and via the Ubuntu 8.10 live CD, he told me to go to the terminal and type this:

sudo nautilus

This then opened up a nautilus file browser but with root permissions. Then, after mounting the hard drive via the places menu, I then went into the files I was after in the home folder, and was able to copy folders previously unaccessible under the normal Nautilus. I also opened up a normal Nautilus just to keep the USB from randomly disappearing on the root-run Nautilus. 

I saved myself $17, but it looks like I am stuck with transferring files by my USB again! Oh well, at least they are now recoverable.

P4Man, when I mean file permissions, right click on a folder, click properties, then go to the Permissions tab. Hopefully, you will see what I mean. And I thought they were meant to protect from users from accessing files. Oh well, at least I have my valuable data now.

Now, to prevent this from happening again (and rendering my powerful PC unusable), I am going to the /home folder a separate partition. Also, I am going to dual-boot it with Vista. Windows may not be my favourite OS, but remember, there are other people in my family that aren't quite computer geeks, and if they need power, then they need to use the desktop, and an OS they are familiar with (don't exactly know how to make GNOME look like Windows Vista yet, but that's another thread starter.)

I'll think about that one. But I think I will stick with 8.10 until 9.10 comes out. And hopefully by then, I would have my central data server up and running so I would have nothing to lose 9.10 wreaked havoc just like 9.04 has. Looks like I have to stick with the not so sleek looks...

Thanks to all that have helped me. The community of Ubuntu is just great, and that also includes my Ubuntu-savvy friend.

---

### Post by zkriesse on 2009-08-12
So you know...Jim.Licy put a post on your thread yesterday...he didn't answer your question in any way and then suddenly his post was removed...as to your problem I'm glad it was solved.

---

### Post by lisati on 2009-08-12
> **Vignesh S said:**
> I have a few questions about the recovery CD thing:

1. How do I get into the recovery mode for 9.04?


Boot your system without a CD or usb stick inserted.Press "Esc" to get a "Grub" menu. At least one of the options should be a recovery mode, which in turn should be able to provide you with a command prompt to use snowpine's suggestion.

---

### Post by P4man on 2009-08-12
> **Vignesh S said:**
> 

sudo nautilus


Dont ever run "sudo nautilus", its a sure recipe for disaster. If you need nautilus with root privileges, run:

```
**gk**sudo nautilus 
```

It does the same as what you typed, except it doesn't tend to brick your system. sudo is to run console apps, gksudo is the command to run graphical apps with admin rights. For many (graphical) apps, sudo works too, but its a bad habit that can really ruin your system. *Especially* running nautilus that way. I know, cause I learned the hard way and bricked my system a few times with the strangest issues before I even heard of gksudo.

more info on that:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Vignesh S on 2009-08-12
lisati, as I previously mentioned, I couldn't access the recovery mode because it was also stuck at that loading please wait screen.   The problem may be solved, but since running sudo nautilus wouldn't let me copy files to my USB, I just changed all of the file permissions so that it would copy under normal nautilus.   Once again, thanks for the useful tip, P4man. I'll surely remember it for next time.

EDIT: That gksudo tip is a lifesaver! Thanks for that, P4man :-D

---

