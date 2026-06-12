---
title: "need to reinstall windows xp pro :/"
date: 2010-03-04
forum: General Help
---

### Post by deathfinderxx on 2010-03-04
Ok well i just deleted the partitions of my lappy which is a toshiba m205 and so i dont have a windows xp pro that came with it but i still have the key. Theres nuthin installed in this and im needing to get the installer. I dont have money to rebuy it and dont really have local computer shops around here. Can someone point me into the direction so i can get the toshiba oem windows xp pro installer?

---

### Post by deathfinderxx on 2010-03-04
Alright i need the Windows Xp tablet pc installer please help me out :/

---

### Post by captain_171 on 2010-03-04
With out money you can NOT  get any CD just a FYI
Install ubuntu and that will work the best

---

### Post by NightwishFan on 2010-03-04
You will have to contact your vendor for support or a replacement. You could also purchase Windows at many stores though I am unsure where Xp is still sold. You might have to use Vista or 7.

---

### Post by deathfinderxx on 2010-03-04
yea that just wont work.... this pc is old. Ubuntu doesnt even work for what i need it to be. I need it to draw. I tried photoshop,sai, and the gimp in there. Gimp lags horribly, photoshop and sai donteven have pressure sensitivity and photoshop keeps giving me errors on scratch disks. There has to be someone with a uploaded disk ...

---

### Post by NightwishFan on 2010-03-04
I advise you to use something like Debian LXDE, or puppy Linux. Debian would be best if you manage to run it, the others are lighter though.

After you install Debian, do this command, then reboot. First log in as root or run this:
```
su
```
Then as root type:
```
echo 'vm.swappiness = 100' >> /etc/sysctl.conf
```
Then reboot.

Debian: [http://wiki.lxde.org/en/Debian#Lightweight_systems_CD](http://wiki.lxde.org/en/Debian#Lightweight_systems_CD)

Puppy: [http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm)

For help on Debian:
> Before the installation starts put desktop=lxde as boot parameter to install lxde instead of xfce. 

To install Gimp on puppy:
[http://blip.tv/file/1195797](http://blip.tv/file/1195797)

If all else fails try Damn Small Linux, which is based on a 2.4 kernel and is similar to Debian. That will definitely be fast enough!
[http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)


Some background info:
[http://en.wikipedia.org/wiki/Lxde](http://en.wikipedia.org/wiki/Lxde)
[http://en.wikipedia.org/wiki/Xfce](http://en.wikipedia.org/wiki/Xfce)
[http://en.wikipedia.org/wiki/Debian](http://en.wikipedia.org/wiki/Debian)
[http://en.wikipedia.org/wiki/Puppy_Linux](http://en.wikipedia.org/wiki/Puppy_Linux)
[http://en.wikipedia.org/wiki/Damn_small_linux](http://en.wikipedia.org/wiki/Damn_small_linux)

---

### Post by pricetech on 2010-03-04
If you can't get a restore disk from the manufacturer, you're out of luck.  Most of them charge shipping even if they give the disk away, which they might not.

---

### Post by chris_l_13 on 2010-03-04
Find a friend with a windows xp pro cd or just download a windows xp pro cd from torrents (im pretty sure thats legal since you will be using your own legal cd key to actually activate it) Then just install all the necessary drivers yourself, most come with xp but things like webcam, and microphone you will probably need to find them on the toshiba website.

---

### Post by NightwishFan on 2010-03-04
Not to shoot down your idea, but it may not be strictly legal. Also that is unwise since sometimes the disk is compromised. I would say nearly all the time it would be.

NOTE: I am not linking this because I want to help the poster break the law. I want to warn him of the potential legality issues and even security and privacy issues of using pirated software. (Whether you have a legal key or not). Also let it be known that the key likely corresponds to the EXACT version. If your Xp was a newer bought it may be under the Vista Business license which may conflict with that of the software download.

[http://blogs.zdnet.com/Bott/?p=1817](http://blogs.zdnet.com/Bott/?p=1817)

---

### Post by coldraven on 2010-03-04
You will almost certainly need an original install disk, on my laptop I could not get XP to activate with a borrowed install disk.
See here why: [http://keznews.com/6173_How_to_Backup_and_Restore_to_Preserve_OEM_Offline_Pre-Activation_When_Reinstall_Windows_XP](http://keznews.com/6173_How_to_Backup_and_Restore_to_Preserve_OEM_Offline_Pre-Activation_When_Reinstall_Windows_XP)

Getting a copy from ebay or torrents is not a good idea, probably full of malware.

---

### Post by Objekt on 2010-03-04
There are two possibilities:

1) Your laptop originally came with a "recovery" disc.  This is mostly a normal Windows install disc, except it will only work on the brand of computer it came with.  Perhaps Toshiba will sell you a replacement recovery disc.  I'm sure you can find the answer to that at their website ([http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/home.jsp]("http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/home.jsp")) or by calling or emailing them.

2) Your laptop had a recovery partition on the hard drive.  Computer manufacturers began using these because it was cheaper than supplying a recovery disc.

Since you said you wiped all the partitions, any recovery partition would be gone.  So it's down to whether Toshiba will supply a recovery disc.

Please let us know what you find out.  I am curious as to whether Toshiba will be helpful.  Their response will assist my future purchase decisions.

---

### Post by deathfinderxx on 2010-03-05
Well Toshiba wouldn't give me a recovery disk or anything even tho i still have my key. I had to resort to getting it off a torrent and wasnt even the same copy but aslong as it works. The laptop is strickly for graphics and not going to be on the internet or anything.

---

