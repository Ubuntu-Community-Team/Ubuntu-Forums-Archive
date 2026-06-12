---
title: "GParted Crashed(?) During Resize"
date: 2010-10-30
forum: General Help
---

### Post by shoot2kill on 2010-10-30
Hi, I was just using GParted to resize a NTFS partition on one of my hard disks. initially it estimated the time it would take at 2 hours. after an hour it was around 40%ish and i went out and left it. when i came back a couple of hours later it was at 10% and had 4 hours remaining. i kept it running as i didn't want to lose any of the data on the NTFS part.

an hour later and i noticed that there was no GParted window(GUI) on my desktop. I clicked on the hard disk icon and i got a very long error message that basically said it couldn't mount the partition.
i opened a console and 'top' told me that 'parted' was still running as top process, but the figures were not changing as would happen with any other running process.
as i still wanted to use the data on my drive, i left the machine alone hoping that parted was still actively resizing the partition.

it is now another hour since GParted vanished and parted is still running with the same figures of:
*Edit: the time value changes, but nothing else. and although i thought it had only been about 4 hours since i first started the whole process, its been running for approx 7 hours if my maths are right*
```

 PID USER PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                
2511 root 20   0 27196  812  400 R  100  0.0 434:58.55 parted

```

when i open up the GUI system monitor i see the values are changing constantly, which would indicate that its still running however the icon for the hard disk has gone from my Places menu.

Disk Utility says that the partition is Unknown with a size of 657GB (what i wanted it to be after the resize) and its of type HPFS/NTFS(0x07)

could anyone tell me how i could find out if (G)Parted is actually still resizing the partition or if the program has actually crashed. i have tried launching GParted again but after authenticating, nothing happens.
due to the size of the hard disk i didn't make a backup before i resized, and i would really like to recover the data that was on the partition (about 400GB worth :\ )

thanks in advance.

---

### Post by Quackers on 2010-10-30
Wow, that sounds dodgy.
Firstly I don't think you'll be able to see or mount the drive while gparted is "using" it.
7 hours is a long time for it to be running, but it is a large drive.
You report that CPU usage is 100%, is the disk activity light on solid? Are the fans running at high speed?
If something has gone badly wrong it seems data loss may be a real prospect, I'm afraid.

---

### Post by shoot2kill on 2010-10-30
yes, 7 hours doe seem long, however when i saw it at 10% i checked the details of how far it had got, and it looked like it had resized the partition then for some reason resized it again with a difference of only a few MB's :s
will there be some sort of log on my system from gparted that i could look at/post?

top shows it as constant 100% CPU usage however the GUI based system monitor shows it varying between 80 and 110 (of 400 with it being a quad core, i think). I don't have any HDD lights in my system and the noise doesn't seem anything out of the ordinary.

---

### Post by Quackers on 2010-10-30
Obviously I can't make a decision for you. What I would say (with 400GB of data at stake) is that I wouldn't touch it while there is any sign of life at all :-)
If it's still showing CPU cycles it sounds like it's still at it. From memory I think gparted reads the data, which takes about 40% of the time and then re-writes it, which takes about 60% of the time.

Just to clarify things a bit, did you start gparted from within your Linux system or from a live cd?

---

### Post by shoot2kill on 2010-10-30
everything has been done from within my ubuntu instalation... but i maybe should give you some drive information.

```

-HDD1 (74GB)
--100MB System Reserved
--74GB NTFS Windows7 Installation

-HDD2 (750GB)
--657GB NTFS Used for data ****Unknown/gparted/frozen****
--43GB Free (which was freed when i resized)
--44GB ext4 Ubuntu Installation
--6GB swap for above ubuntu installation

-HDD3 (500GB)
--500GB NTFS Used for data

```

---

### Post by Quackers on 2010-10-31
So you are shrinking a 700GB partition to 657GB.
To be honest I would leave it until the morning at least, if it were my pc.
Hopefully it will be ok, but if the worst happens you can try testdisk, which is available through Synaptic.
In Windows Vista or 7 this would have taken about 20 seconds using the Disk Management tool if the partition hadn't been shrunk previously.
Whatever happens it may be worth trying that.

---

### Post by shoot2kill on 2010-10-31
The 7GB disk was originally one large partition. a while ago i shrunk the partition to give myself 50GB for ubuntu. (as i recall, this took only a few seconds using GParted on the LiveCD)
Now, In ubuntu, i tried to re-resize the large partition to gain an extra 40GB partition.

thanks for your help, and i will update here if theres any progress later/tomorrow.

---

### Post by Quackers on 2010-10-31
Ok, good luck with it :-)

---

### Post by shoot2kill on 2010-10-31
14 Hours Later... Still no sign of a working partition, and the process is still busy! :/

---

### Post by Quackers on 2010-10-31
Oh dear. Does System Monitor still show the process as using resources?

---

### Post by shoot2kill on 2010-10-31
Yeah!
[img]http://img5.imagebanana.com/img/okbssvy4/Untitled.jpg[/img]

---

### Post by Quackers on 2010-10-31
Ouch! If you kill the process and it is actually still doing what it's supposed to be doing data loss is likely. 14 hours is a looooooooong time though.
Have you tried running gparted from a terminal to see if the gui returns? Just an idea.

---

### Post by Quackers on 2010-10-31
Forget that, only sudo parted works, not sudo gparted, but no gui for that.

---

### Post by shoot2kill on 2010-10-31
sudo gparted launched fine, but gave me a nasty looking erroe..
going to try the windows check, may be gone some time lol

[[IMG]http://img5.imagebanana.com/img/rfq47511/thumb/Selection_003.png[/IMG]](http://www.imagebanana.com/view/rfq47511/Selection_003.png)

---

### Post by Elfy on 2010-10-31
Not sure what win version you use - but if it is post XP then once you have done your check I would use the windows disk tools to shrink the drive. Then use gparted to do your other work.

---

### Post by shoot2kill on 2010-10-31
[[IMG]http://img185.imageshack.us/img185/5548/devsdbgparted001.th.png[/IMG]](http://img185.imageshack.us/i/devsdbgparted001.png/)
:D :D :D

Was expecting it to be a nightmare, but windows did its own CHKDSK on boot, fixed a few hundred errors :\ and all booted up fine.

there doesnt seem to be any obvious corruption of the drive or files / dir structure.

opened windows disk management and the resize had already been applied.

thanks Quackers for your help! dont know how long i'd have kept my system online for if i was waiting for it. :D

---

### Post by Quackers on 2010-10-31
Good result though under the circumstances :-)

---

