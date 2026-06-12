---
title: "Kernal crash corrupted , how to fix ?"
date: 2009-10-26
forum: General Help
---

### Post by ubfu on 2009-10-26
Using ubuntu 8.04.This evening , while opening a file ubuntu freeze and I have to press reset button to restart.

Once I restart I receive an error message on the log of booting 
```

[ 463.189492] ata3.00: exception Emask 0x100 SAct 0x0 SErr action 0x6
[ 463.189568] ata3.00: BMDMA stat 0x25
[ 463.189668] ata3.00: cmd c8/00:80:77:e3:0a/00:00:00:00:00/ee tag0 dma 65536

[ 463.189735] ata3.00: { DRDY ERR }
[ 463.189806] ata3.00: { ICRC ABRT }
```

And the desktop character are in square unreadable.Similar to this picture all are in square block 
[http://ubuntuforums.org/archive/index.php/t-907278.html](http://ubuntuforums.org/archive/index.php/t-907278.html)
[IMG]http://img48.imageshack.us/img48/9766/screenshotml0.png[/IMG]

Thank you for reading .hope someone will help me out.

---

### Post by arrange on 2009-10-26
I would suggest this: boot into LiveCD, run GParted, and check the partition for errors (do not mount it). 

If you see any errors, save the log (GParted should prompt you) and try to boot into Ubuntu again. If you can't, post the saved log here.

---

### Post by ubfu on 2009-10-27
> **arrange said:**
> I would suggest this: boot into LiveCD, run GParted, and check the partition for errors (do not mount it). 

If you see any errors, save the log (GParted should prompt you) and try to boot into Ubuntu again. If you can't, post the saved log here.

```
GParted 0.3.5

Libparted 1.7.1

Check and repair filesystem (ext3) on /dev/sda4  01:01    ( SUCCES )
     	
calibrate /dev/sda4  00:00    ( SUCCES )
     	
path: /dev/sda4
start: 208700415
end: 286824509
size: 78124095 (37.25 GiB)
check filesystem on /dev/sda4 for errors and (if possible) fix them  01:01    ( SUCCES )
     	
e2fsck -f -y -v /dev/sda4
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

177792 inodes used (7.26%)
1510 non-contiguous inodes (0.8%)
# of inodes with ind/dind/tind blocks: 7412/77/0
1037003 blocks used (10.62%)
0 bad blocks
1 large file

137988 regular files
20166 directories
69 character device files
26 block device files
3 fifos
494 links
19459 symbolic links (18016 fast symbolic links)
72 sockets
--------
178277 files
e2fsck 1.40.8 (13-Mar-2008)
grow filesystem to fill the partition  00:00    ( SUCCES )
     	
resize2fs /dev/sda4
     	
resize2fs 1.40.8 (13-Mar-2008)
The filesystem is already 9765511 blocks long. Nothing to do!


========================================
```

No error on it.Suspecting is kernel error.What should I do now ?:(

---

### Post by nothingspecial on 2009-10-27
I have no idea weather it`s a kernel problem or not, but you could boot into your previous kernel then remove and reinstall your current one.

---

### Post by arrange on 2009-10-27
One more question: it's just the fonts that give you trouble or it's more things?

---

### Post by ubfu on 2009-10-27
> **nothingspecial said:**
> I have no idea weather it`s a kernel problem or not, but you could boot into your previous kernel then remove and reinstall your current one.
I just sudo aptitude upgrade-full to kernel 2-6-24-25 but still those font are in square.

> **arrange said:**
> One more question: it's just the fonts that give you trouble or it's more things?

Previously I did changing fonts to vista segoe Ui

Yeh , beside fonts , I am not able to right click on desktop and click on application , place system and etc.When I right click it just freeze but the clock is still ticking.
It's like the whole desktop freeze but screenlet clock still moving , slideshow still changing , I still can move my mouse but everything right click and etc not going to work.

I am really out of idea.When I boot into GUI there's an error message but all character font are in square block.I dont even know how to read it.

I really hope someone can tell me what's happening .I dont think it's bug where I just update my kernel 10 min ago.

---

### Post by arrange on 2009-10-27
I would suggest refreshing the font cache.

Reboot and go to *recovery mode*. Then type```

fc-cache -fv 2>&1 | tee -a /fc.log
reboot

```This will refresh the cache, create a *fc.log* file and reboot.

If that didn't help, boot into LiveCD again and post the contents of the *fc.log *file here. Also try to find any errors in */var/log/Xorg.0.log* and */var/log/syslog* files, or upload them in full somewhere (pastebin.com) so that we can have a look at them.

---

### Post by P4man on 2009-10-27
try booting in to recovery mode, then select root shell and make a new user

adduser testuser
passwd testuser
reboot

try logging in with test user, I suspect it will work fine and the problem is sonewhere with gnome settings and that font.

---

### Post by ubfu on 2009-10-27
> **arrange said:**
> I would suggest refreshing the font cache.

Reboot and go to *recovery mode*. Then type```

fc-cache -fv 2>&1 | tee -a /fc.log
reboot

```This will refresh the cache, create a *fc.log* file and reboot.

If that didn't help, boot into LiveCD again and post the contents of the *fc.log *file here. Also try to find any errors in */var/log/Xorg.0.log* and */var/log/syslog* files, or upload them in full somewhere (pastebin.com) so that we can have a look at them.

Boot with live CD , copy both xorg log and sys log.Then went to recovery mode and dro pto root shell and type "fc-cache -fv 2>&1 | tee -a /fc.log"

reboot but still the same square character still no change.

Here are both of the log .Hope to fix it.

[http://pastebin.com/d3bf6ca4c](http://pastebin.com/d3bf6ca4c) xorg

Pastebin said my syslog is too long.Fatal error: Allowed memory size of 16777216 bytes exhausted (tried to allocate 2156681 bytes) in /home/pastebin/lib/geshi/geshi.php on line 2474

---

### Post by ubfu on 2009-10-27
> **P4man said:**
> try booting in to recovery mode, then select root shell and make a new user

adduser testuser
passwd testuser
reboot

try logging in with test user, I suspect it will work fine and the problem is sonewhere with gnome settings and that font.

I reboot but at the userlogin screen all the character is square I dont even know which I should for new user.I can't read a thing

Update: I am able to login to testuser but the problem still there all character are still in square.

Any help please

---

### Post by ubfu on 2009-10-27
> **arrange said:**
> I would suggest refreshing the font cache.

Reboot and go to *recovery mode*. Then type```

fc-cache -fv 2>&1 | tee -a /fc.log
reboot

```This will refresh the cache, create a *fc.log* file and reboot.

If that didn't help, boot into LiveCD again and post the contents of the *fc.log *file here. Also try to find any errors in */var/log/Xorg.0.log* and */var/log/syslog* files, or upload them in full somewhere (pastebin.com) so that we can have a look at them.

Here is the pastebin for fc.log
[http://pastebin.com/m8d3c4ac](http://pastebin.com/m8d3c4ac)

---

### Post by arrange on 2009-10-27
Fonts and Xorg.log look OK. Just one thing - why are you using an unsupported version of Xorg?

> [COLOR="Gray"]This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.
 
X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)[/COLOR]

[COLOR="Gray"]Pastebin said my syslog is too long.[/COLOR]
Come on, be a little creative. Post it somewhere else, it doesn't matter where.

---

### Post by ubfu on 2009-10-27
> **arrange said:**
> Fonts and Xorg.log look OK. Just one thing - why are you using an unsupported version of Xorg?



[COLOR="Gray"]Pastebin said my syslog is too long.[/COLOR]
Come on, be a little creative. Post it somewhere else, it doesn't matter where.

Sorry , I didn't think of zipping since I am too busy finding for answer.
Thank you for helping :)

what is unsupported Xorg ? I dont know ,I am using ubuntu 8.04.I dont know much about xorg.Sorry I am new

---

### Post by arrange on 2009-10-27
As I saw this problem is usually connected with bad font cache or Xorg incompatibility. In your case it seems to be a harder nut to crack (at least for me :)). In your *syslog* I can see several *segfaults*, for example```
$ awk '/segfault/ {print $8}' syslog | cut -d[ -f1 | sort | uniq
bonobo-activati
compiz.real
evolution-alarm
ld_static
seahorse-agent
update-notifier
```If nobody comes up with a better idea (and I wish they would :)), I would opt for a reinstall/upgrade.

---

### Post by ubfu on 2009-10-27
> **arrange said:**
> As I saw this problem is usually connected with bad font cache or Xorg incompatibility. In your case it seems to be a harder nut to crack (at least for me :)). In your *syslog* I can see several *segfaults*, for example```
$ awk '/segfault/ {print $8}' syslog | cut -d[ -f1 | sort | uniq
bonobo-activati
compiz.real
evolution-alarm
ld_static
seahorse-agent
update-notifier
```If nobody comes up with a better idea (and I wish they would :)), I would opt for a reinstall/upgrade.

Yeh ,I did remember installing seguo UI font while playing around customizing fonts and theme.
Is there any terminal command line which can revert back to original Sans and Arial fonts setting ?

Really hope to find a solution to fix it.I also plan to upgrade to the latest 9.10 that'll be release tomorrow but at lease I wanted to solve and fix this error so I can backup my file .

Thank you hope there'll be someone that can solve it :)

---

### Post by ubfu on 2009-10-27
Anyone know any terminal command line which can revert back to original Sans and Arial fonts setting ?

---

### Post by arrange on 2009-10-28
> **ubfu said:**
> ... I wanted to solve and fix this error so I can backup my file .
...
You can always back up your files from LiveCD.

---

### Post by ubfu on 2009-10-28
> **arrange said:**
> You can always back up your files from LiveCD.

I have one dvd-burner , I can't burn my file out if while my livecd occupied my dvdrw.Those files and picture is very large.

---

### Post by P4man on 2009-10-28
just a wild shot in the dark here, but perhaps try
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

If reinstalling is the only solution, then you could from the live cd resize and repartition your drive, so you can install ubuntu a new partition and keep your current one, copy files over and then delete the old one. Of course this is not without risk, so making a backup would be best. If your only backup medium is cd/dvd then perhpas boot from a usb stick?

I would also use the occasion to create a separate /home partition so that next time it will be a lot easier to install without losing your data. You could in fact probably use your existing ubuntu partition as /home partition, and delete everything from it except the stuff you need in /home.

---

### Post by ubfu on 2009-10-28
> **P4man said:**
> just a wild shot in the dark here, but perhaps try
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

If reinstalling is the only solution, then you could from the live cd resize and repartition your drive, so you can install ubuntu a new partition and keep your current one, copy files over and then delete the old one. Of course this is not without risk, so making a backup would be best. If your only backup medium is cd/dvd then perhpas boot from a usb stick?

I would also use the occasion to create a separate /home partition so that next time it will be a lot easier to install without losing your data. You could in fact probably use your existing ubuntu partition as /home partition, and delete everything from it except the stuff you need in /home.

Just tested dropping to recovery , shell , still doesn't work.
yeh , I install ubuntu last year with /home together without separating it.Maybe that's my first time installing ubuntu.So does that mean programs that store at home able to work too ?

Right now , I am eager to know whether it's a font error ? I really wanted to know , able or not able to fix I wanted to know what causing it.

Hope someone would explain to me thank you

---

### Post by ubfu on 2009-11-10
Still having Font error , any other way to fix it ?

---

