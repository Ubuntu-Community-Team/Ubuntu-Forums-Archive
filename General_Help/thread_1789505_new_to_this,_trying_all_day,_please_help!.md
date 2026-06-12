---
title: "new to this, trying all day, please help!"
date: 2011-06-23
forum: General Help
---

### Post by barkerb23 on 2011-06-23
ive been trying all day to install Kubuntu but it says i only have 255mb (which i dont, i have 256mb) and i really want it, tried it with usb, said there was no configuration file found, i just want it to replace windows xp, please **_[COLOR="Red"]help[/COLOR]_** anyone :/

---

### Post by tgalati4 on 2011-06-23
Replacing XP is certainly a priority.  You should create a swap partition on your disk, this will add to the 256 MB of RAM and help the installer.

Back up your data.  These changes are non-destructive, but you can also screw up and destroy any data on the disk.

Boot the LiveCD, open a terminal:

sudo gparted

Use the partition manager to shrink the existing partition by 1 GB.

Take the free space and create a new swap partition with a /swap mount point.  Write the changes to disk.  Then reboot the LiveCD so the swap disk partition gets discovered.  Open a terminal and run:

free

It should look something like:

tgalati4@tpad-Gloria7 ~ $ free
             total       used       free     shared    buffers     cached
Mem:       1867260    1124452     742808          0      65016     489848
-/+ buffers/cache:     569588    1297672
Swap:      2562356          0    2562356

If you have swap then you can proceed with the installation.

When you get to the partitioner, use the manual or advanced method and make smart decisions on how you want to set up your partition.  If you want to wipe out XP entirely, then you can choose to use entire disk and it will not disturb your swap partition because it is in use.

Good luck.

---

### Post by barkerb23 on 2011-06-23
:confused: soo confused, can we do it Via Teamviewer? :popcorn:

---

### Post by Vaphell on 2011-06-23
your machine has only 256MB of RAM? Ubuntu/Kubuntu is a bad idea then.

---

### Post by barkerb23 on 2011-06-23
Why? i like ubuntu.. im using xp.

---

### Post by Vaphell on 2011-06-24
because xp is 10 years old and 256Mb of RAM was quite a respectable amount then. Ubuntu is a modern OS and in terms of hardware requirements it is more in w7 ballpark than in xp's. Have you seen a win7 machine with 256MB of RAM? I don't think so, crappiest w7 computers start at 1GB. I think Ubuntu/Kubuntu would work fine with 512MB, but 256MB is simply not enough. It would mean constant disk thrashing which would translate to pathetic performance (assuming you can get it installed in the first place).
You can try installing some lighter desktop environment like xfce (though xubuntu is not that light) or lxde (lubuntu). They have less bling and features but don't tax the machine as much so your ancient computer should be able to run them.

according to the page linked below lubuntu requires at least 128MB
[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/NattyNarwhal#System_Requirements](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/NattyNarwhal#System_Requirements)

---

### Post by mastablasta on 2011-06-24
what works on 256 MB ram is:
 
Ubuntu 10.04 (i can't even boot 11.04)
Xubuntu 10.04 (perhaps even Xubuntu 11.04 but i had graphics card issue here so i can't confirm it)
Lubuntu 
 
Another alternatives for low ram to Ubuntu based systems and easy enough for newbies are Debian 6 stable XFCE & LXDE
Crunchbang linux (don't mind the disclaimer it's a joke, the whole thing is based on Debian stable)
Mint Linux XFCE 11 (but this one uses debian testing as base, however it is possible to lock it in stable)
Mint linux LXDE
 
An even lighter alternatives (but not so good on applications) are:
SliTaz
Puppy Linux
These two however are quite different from Ubuntu.
 
KDE (Kubuntu) as you've found out won't work on such low ram.
 
before instalkation you can test them by booting directly from live CD (or if possible USB) without doing any changes to your system. in this case the whole system loads from CD to ram (so it might be much slower than install later on). it doesn't use the hard disk i this case. On the plus side to get rid of it you just reboot and take out the CD.

---

### Post by juggernautxtr on 2011-06-24
> **Vaphell said:**
> because xp is 10 years old and 256Mb of RAM was quite a respectable amount then. Ubuntu is a modern OS and in terms of hardware requirements it is more in w7 ballpark than in xp's. Have you seen a win7 machine with 256MB of RAM? I don't think so, crappiest w7 computers start at 1GB. I think Ubuntu/Kubuntu would work fine with 512MB, but 256MB is simply not enough. It would mean constant disk thrashing which would translate to pathetic performance (assuming you can get it installed in the first place).
You can try installing some lighter desktop environment like xfce (though xubuntu is not that light) or lxde (lubuntu). They have less bling and features but don't tax the machine as much so your ancient computer should be able to run them.

according to the page linked below lubuntu requires at least 128MB
[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/NattyNarwhal#System_Requirements](https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/NattyNarwhal#System_Requirements)

he's quite right, you need at minimal 1 gig ram for modern software.... and even at that amount your computer may  be slow. everything is heavily graphics intensive anymore. plus all the back ground software that runs.
even linux programs have a multitude of layers to run now.
for a respectable speed computer you need 2 gigs ram.(windows 7)
my kubuntu seems ok with one gig, but I am going to add a second to see if it picks up a bit more.it does lag a little, on some things.
Ram is cheaper than arguing with the software.

---

### Post by idoitprone on 2011-06-24
always remember this quote, when installing oses and software

The most amazing achievement of the computer software industry is its continuing cancellation of the steady and staggering gains made by the computer hardware industry.

        &#8212; Henry Petroski

also called wirth law

and gates's law opposite of moores law

---

### Post by owiknowi on 2011-06-24
you could first try several species of penguins as live cd's.
that way you can find out what does and doesn't work.

and don't forget to back up your personal data before installing anything ;)

---

### Post by jfbooth on 2011-06-30
I just want to add, .. I am running Xubuntu 11.04 on an old Windows ME machine with 512MB of ram.  It runs just fast enough to be useable.  Any slower, and it would not be acceptible.

You need a G (1024MB) of ram at least to get decent performance from Ubuntu 11.04.

---

### Post by life in color on 2011-06-30
I recommend Debian it looks good, has a good amount of software, and its what Ubuntu is based off of. Linux is definitely gonna be an option for your computer but a new form of Ubuntu definitely not, you could try something old like Hardy Heron but I wouldn't recommend it.

---

