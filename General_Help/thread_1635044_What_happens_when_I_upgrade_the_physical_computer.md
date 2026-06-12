---
title: "What happens when I upgrade the physical computer?"
date: 2010-12-01
forum: General Help
---

### Post by 0949er on 2010-12-01
Ok so I am currently using linux on my old system (store bought Gateway). I am building a new computer for Christmas. This is how I want things to go down:

Set up new computer > install new hard-drive (as primary) > install (this) hard-drive (as secondary) > copy full contents from current drive to new drive > boot from new drive > Use (this) hard-drive from there on out as a backup/storage. 

Will this work? Will a new mobo/processor combo mess any with my current system as a whole? I know that when I use to use gentoo everything was compiled "system specific", however, I do not believe ubuntu operates this way (well they are both goign to be a 64bit capable processor, which I think is about as specific as ubuntu gets) 

Furthermore, I will be transfering my current videocard (GeForce 9800 GTX+) into the new system, so I will not need to configure any new video drivers. 

But what about audio? I currently use onboard audio, and will be using the new mobos audio as well. 

What issues do you think I will run into? (if any)

Thanks for your input.

---

### Post by cannywizard on 2010-12-01
This might or might not work - it depends on how similar your old computer is to your new one. 

The best idea is to reinstall ubuntu from scratch on the new computer, install the packages and copy over your files (or whatever) from /home from the older computer. 

Actually, here's a link.

[http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html)

---

### Post by 0949er on 2010-12-01
> **cannywizard said:**
> This might or might not work - it depends on how similar your old computer is to your new one. 

The best idea is to reinstall ubuntu from scratch on the new computer, install the packages and copy over your files (or whatever) from /home from the older computer. 

Actually, here's a link.

[http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html)

physically reinstall every package I have installed since I installed ubuntu the first time? No way haha.

The systems should be quite similar, in the sense that:

1) both will be 64bit amd processors (different # cores)
2) using the same video card
3) DDR-3 ram (instead of ddr-2)
4) new harddrive
5) different (possibly same?) onboard audio configurations

What would be holding me back from a exact copy/transfer? I dont think ubuntu complies anything from source, so nothing is really system specific, except for the fact I am using a 64bit OS, which will work on the new system as well.

---

### Post by Grenage on 2010-12-01
Does GRUB use UUIDs?  Either way, it will 'probably' work; I'd personally use a fresh install, but I can't imagine there being insurmountable problems with what you propose.

---

### Post by coffeecat on 2010-12-01
> **0949er said:**
> What would be holding me back from a exact copy/transfer?

Nothing. Linux probes hardware on each bootup and loads appropriate drivers (kernel modules) as needed. The main issue is when you have installed a proprietary video driver, but you have taken this into account by transferring the video card. A complete clone of the OS and apps into a different machine **will** work - no argument - except perhaps you may have to reconfigure sound, and so long as you are not trying to run a 64-bit OS in a 32-bit machine.

Where you may come unstuck is in the copy process. How were you going to do this? You must allow for the UUID of the partition you are copying to and change this or edit /etc/fstab and configure grub. Also - you will have to install grub to the mbr of the new drive.

---

### Post by lobralleo on 2010-12-01
I have the feeling that copying your whole installation to the new system could not be that easy: sometimes, I had problems with as little as one single component upgrade.

If you could just backup and copy your personal data, then I would suggest the clean install; it will usually take less than an hour to reinstall all additional packages you have installed now, and will probably save you a few headaches.
I have done the very same thing several times and found it easier that way, even including packages that I have to compile myself or install manually.

---

### Post by oldsoundguy on 2010-12-01
I just moved the old hard drive into the new box and made it the default drive and slaved the new drive.  Everything went smooth as glass and it saw all of the newer hardware and installed it instead of the older stuff when I booted up.

BUT .......  YMMV!!!!

---

### Post by akand074 on 2010-12-01
Yeah I've taken my hard drive and put into a completely new system and it booted just fine with no issues. Then again, reinstalling Ubuntu and all your apps doesn't even take that long. Do whatever you prefer, but yeah it should work just fine.

---

### Post by a-user on 2010-12-01
except for some minor special things there is no problem switching totally your hardware.

what you must/should consider is:
1. graphic card. if you change the vendor (say from nvidia to ati) i recommend first do uninstall the proprietary ones and switch to the default installation one.
2. add your drives in the same order. so they are named as before (sda, sdb etc.). this is only needed if you have entries in fstab that don't use uuids but /dev/sdx...
3. eventually you have to check if the right disk/partition is set to boot. must be the one with grub installed.

the rest should work with no issues. ofcourse, if you have installed / configured software specifically to some hardware you previously had but not anymore there is adjustion needed after the new "start".

---

### Post by oldfred on 2010-12-01
I put a new motherboard and a new Nvidia card (7600 to 9600) card into my system and it just booted without issue. Windows of course had lots of issues, most with calling home to make sure it was ok.

But I am a fan of clean installs. I used to upgrade and had done so from about 6.06. But with Karmic and a new hard drive I decided to do a clean install. I now do clean installs, but keep all data out of the system partition and have 3 system partitions that I am using in rotation. Then I can boot old, new or beta and link same data files into each.

Full install takes about an hour, plus some configuration.
I easily reinstall all apps with this:

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

 dpkg --get-selections | grep -v deinstall > ubuntu-files
or
 dpkg --get-selections > ubuntu-files

If I customize some system setting in /etc I also save that so I do not lose that info on a reinstall.

---

### Post by coffeecat on 2010-12-01
> **lobralleo said:**
> I have the feeling that copying your whole installation to the new system could not be that easy

In fact it is very easy. I have done it several times to clone an installation. I've even used 'sudo cp -av' to copy everything (and preserve permissions) and it all works. The only things you have to deal with are the UUID of the destination partition(s) and grub.

---

### Post by deserthowler on 2010-12-01
I often move Ubuntu disks between computers without problem.  Going from PIII to P4 and from 512 memory to 2 GB.  No proprietary drivers.  The best way to check is try it.  If it works, HOORAY!!!  If it doesn't, then you can reinstall.

Might try remastersys just in case it bricks your machine.

Earl

---

### Post by 0949er on 2010-12-01
Ok thanks for all the input guys. I think we have covered all bases in regards to any potential problems. the only real problem seems to be in the event of video card/drivers, which wont be an issue since I will be transfering video cards from the current computer to the new one.

> **oldfred said:**
> I put a new motherboard and a new Nvidia card (7600 to 9600) card into my system and it just booted without issue. Windows of course had lots of issues, most with calling home to make sure it was ok.

But I am a fan of clean installs. I used to upgrade and had done so from about 6.06. But with Karmic and a new hard drive I decided to do a clean install. I now do clean installs, but keep all data out of the system partition and have 3 system partitions that I am using in rotation. Then I can boot old, new or beta and link same data files into each.

Full install takes about an hour, plus some configuration.
I easily reinstall all apps with this:

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

 dpkg --get-selections | grep -v deinstall > ubuntu-files
or
 dpkg --get-selections > ubuntu-files

If I customize some system setting in /etc I also save that so I do not lose that info on a reinstall.

What this is saying is you can grep a list of all your installed packages, and then do a install based off that list? I just want to avoid "apt-get install <whatever>" a 100 times. I know a new install is easy (very easy) but there are a lot of "small" packages that I use that I would never notice were missing until I actually had to use them (if that makes sense)

---

### Post by oldfred on 2010-12-01
The first new install I did install to a new partition, but did not know about the dpkg list. I copied screens and manually reinstalled apps, real hassle. I also reallized I wanted the same install to my portable, so the first time I tried to do as much as I could from the command line. Then I copied history into a bash file so I could automate most of the reinstall.

I now plan if I ever have a hard drive crash to do a full reinstall, but as part of my rsync backup of /home and some data I run the dpkg so I have a current list of installed apps and rerun bootinfo script so I have a full configuration of my system backed up.

---

