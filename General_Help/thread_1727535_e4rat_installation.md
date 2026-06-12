---
title: "e4rat installation"
date: 2011-04-12
forum: General Help
---

### Post by iconoclast hero on 2011-04-12
On Friday LifeHacker put out a bit about e4rat for quicker bootups in linux.  Has anyone managed to do this in ubuntu?  I think I got to the point where I've gotten it compiled, but the next step is to modify the grub file.  It asks that i modify the kernel line...  I've figured out that I don't have a /boot/grub/menu.lst file since i'm in 10.10 and have grub2 but I don't see a corresponding kernel line in my /boot/grub/grub.cfg.  I hit ^W in nano and searched for kernel and it did not return a result.  Am I missing something?  Is there another line where I should add  init=/sbin/e4rat-collect?  For some reason I do not have the option to hit E when the grub menu pops up since it doesn't pop up.  I did install startup manager and clicked on show boot splash, but I still don't see the same GRUB boot manager I do when I was dual booting with XP or vista.

---

### Post by oaxacamatt1 on 2011-04-19
Hey IH,
Well, I took the easy way and downloaded the .deb file.  BUT when I tried to install I got an error message that said, Error: Conflicts with the installed package 'ureadahead'. So I went to came here.  Actually went to the Sourceforge site which had nothing then found the Arch site had some stuff but not what I was looking for, maybe you'll find something.  I actually saw at least one post that said 'No sig. delta'  (science talk for 'No significant change'.
[https://bbs.archlinux.org/viewtopic.php?id=115976](https://bbs.archlinux.org/viewtopic.php?id=115976)

---

### Post by iconoclast hero on 2011-04-19
Well, this is kind of embarrassing.  I figured it out over a couple of beers and took no notes, it just kinda worked all of a sudden.  A day or two later, my HDD melted down and I have nothing to go back and look at.  So since then I've been working on getting a system up and running on an 8 GB flash chip and to get a netboot server set up.  This computer runs too hot and burns through HDDs about once a year or something like that.  I'm not putting another in but it is still a good console.  Anyway, I'm running on the 8 gb chip so e4rat is probably not going to help much.  To be honest, I though that while it probably sped up the linux boot up, the time it took to load itself at least ate up the savings.   I'm still struggling with the netboot at the moment.

I think that once I got the ruby script figured out it was rather straight forward.  I'll take a look on the heels of my success with getting rubyripper compiled yesterday and see if I can remember what I did.  I guess the long and short of it is, it does work and I'm pretty sure that I got it to work via ruby.  At least on 10.10 desktop.

---

### Post by iconoclast hero on 2011-04-19
> **oaxacamatt1 said:**
> Hey IH,
Well, I took the easy way and downloaded the .deb file.  BUT when I tried to install I got an error message that said, Error: Conflicts with the installed package 'ureadahead'. So I went to came here.  Actually went to the Sourceforge site which had nothing then found the Arch site had some stuff but not what I was looking for, maybe you'll find something.  I actually saw at least one post that said 'No sig. delta'  (science talk for 'No significant change'.
[https://bbs.archlinux.org/viewtopic.php?id=115976](https://bbs.archlinux.org/viewtopic.php?id=115976)

Ok, let's start with the README in the package:
> DEPENDENIES
-----------
The e4rat toolset has the following external dependencies:
 - Linux Kernel (>= 2.6.31)  **[COLOR=Red]part of ubuntu[/COLOR]**
 - CMake (>= 2.6) **[COLOR=Red]apt-get install cmake[/COLOR]**
 - pod2man  [COLOR=Red]**Somehow included...?**[/COLOR]
 - Boost Library (>=1.41): You need the following components installed:
       system, filesytem, regex, signals2 [COLOR=Red]**apt-get install libboost-all-dev**[/COLOR]
 - Linux Audit Library (libaudit >=0.1.7) [COLOR=Red]**apt-get install libaudit-dev**[/COLOR]
 - Block Device Identification Library (libblkid)  [COLOR=Red]**apt-get install libblkid-dev**[/COLOR]
 - Ext2 File System Utilities (e2fsprogs) [COLOR=Red]**apt-get install e2fslibs-dev**[/COLOR]

I, of course stumbled on this thread as I was the last step of finding all of this: [http://ubuntuforums.org/showthread.php?p=10656848](http://ubuntuforums.org/showthread.php?p=10656848)

and wbar2 put it nicely to do it all in one shot:
```
sudo apt-get install cmake libblkid-dev e2fslibs-dev libboost-all-dev libaudit-dev

```Anyway, after that do your
```
cmake . -DCMAKE_BUILD_TYPE=release
make
sudo make install
```If the cmake .-DCMAKE_BUILD_TYPE=release doesn't work for you, it will tell you what it is missing...

```
/usr/local/src/e4rat-0.2.1$ cmake . -DCMAKE_BUILD_TYPE=release
-- Found ext2fs: /usr/lib/libext2fs.so
CMake Error at src/cmake/Findblkid.cmake:17 (MESSAGE):
  Could not find blkid
Call Stack (most recent call first):
  src/CMakeLists.txt:61 (find_package)


-- Configuring incomplete, errors occurred!

```One more thing, I chose to use /usr/local/src because I was looking at [this tutorial]("https://help.ubuntu.com/community/CompilingEasyHowTo") last night.  You do have to make sure you give yourself access with chmod and chown as it says there.  Pain in the ***, but whatever.  If it's easier, extract it to your desktop and drop to the command line.  Hopefully, I'll figure out how to run it again later.

Oh, yeah, this is what you want to be looking at for how to actually use it once you have it compiled:
[http://e4rat.sourceforge.net/wiki/index.php/Main_Page](http://e4rat.sourceforge.net/wiki/index.php/Main_Page)

---

### Post by iconoclast hero on 2011-04-19
Alright, I got the **/var/lib/e4rat/startup.log **file.  The way I got e4rat to run was to comment out the line ```
[B]linux   /boot/vmlinuz-2.6.35-28-generic root=UUID=2c1e414a-bb1f-4050-ab07-40866f12c7a0 ro   quiet splash
[/B]
```and then add 
      ```
 linux   /boot/vmlinuz-2.6.35-28-generic init=/sbin/e4rat-collect root=UUID=2c1e414a-bb1f-4050-ab07-40866f12c7a0 ro   quiet splash

```Now I just went back in and swapped the commented line out for the new one, so it will boot properly.  This is not the correct way to do it, but for one boot, I didn't think it would hurt anything.  There are warnings everywhere about this.  Now the next step is to reorder the disc, which in my case is irrelevant since it is an SD chip.  However, if you do it this way once you get your drive optimized, it will probably work until the next time the grub.cfg refreshes itself, but I don't know how to do it properly but it looks like it's somewhere in here:
[https://help.ubuntu.com/community/Grub2#File%20Structure]("https://help.ubuntu.com/community/Grub2#File%20Structure")

---

### Post by iconoclast hero on 2011-04-20
If you cannot drop into 
```
sudo init 1
```
there is this trick:
[http://ubuntuforums.org/showthread.php?t=1640304](http://ubuntuforums.org/showthread.php?t=1640304)

---

