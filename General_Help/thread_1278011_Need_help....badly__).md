---
title: "Need help....badly  :)"
date: 2009-09-29
forum: General Help
---

### Post by Ghot on 2009-09-29
Ok...just got Ubuntu 8.10 installed on a Gateway MT6723 laptop, which has the original Vista recovery partition....somewhere on the hard drive....from googling "how to get to the vista recovery partition...many sources suggested doing it through Ubuntu..

1. I know nothing about Ubuntu, except that its a great open source OS.
2. This is NOT my laptop.
3. Can someone please explain, if possible, how to locate and then somehow RUN the Vista recovery console, through Ubuntu
4. When I installed Ubuntu I purposely left the 10Gb and the 13Gb partitions alone on the 160Gb hard drive....as one of them IS the Vista recovery partition.

...I would very much appreciate a simple (if possible) to follow set of directions for accessing and running the Vista Recovery Console....thx in advance.

P.S.  at boot I do NOT see any OS choices...just three GRUB choices.

P.S.S  Following the boot options link from another post I opened a terminal and typed: sudo gedit /boot/grub/menu.lst

Then it said look for a line like this:

# kopt=root=/dev/sda1 ro  .....mine doesn't look like that it looks like this:

# kopt=root=UUID=186d9ae4-b9a4-4772-be24-316c3e8263e5 ro noapic

the next line in the instructions said I would have to add the noapic at the end of this line....so I am kinda lost  :/

P.P.P.S  When I installed Ubuntu 8.10 I used the F6 option to add....noapic on the end of the line that was there.

...anyways, I need help with this...as I'm sure you can see  ;)

---

### Post by KlinerDraken on 2009-09-29
Maybe this is what you are looking for?

[http://support.gateway.com/s/software/MICROSOF/vista/7515418/7515418su539.shtml]("http://support.gateway.com/s/software/MICROSOF/vista/7515418/7515418su539.shtml")

---

### Post by Ghot on 2009-09-29
not if I can help it...this is a friends comp that hasnt been used in a year, and rather than spend 20$ for the recovery CD...I'd like to fix it some other way.   My grub loader does NOT look like this:

1. Ubuntu 8.10
2. ununtu 8.10(recovery)
3. memtest
4. vista/longhorn loader
5. vista longhorn loader

...rather it looks like this:

1. Ubuntu 8.10
2. ununtu 8.10(recovery)
3. memtest


from another googling I've found that option #4 is the one I need...but as it doesn't appear.....I need help  :)

---

### Post by Ghot on 2009-09-29
> **walter0515 said:**
> [http://google.com]("http://google.com/")

and what did I ever do to you....funny guy   :/

---

### Post by Arquis on 2009-09-29
I may be saying something stupid so bear with me. Somewhere in this forum you might find what you're looking for already answered, but I know its search feature is not the best in its category. Not trying to sound like the guy above, but if you wish to search the forums for an answer, you should try google [B]but with "site:ubuntuforums.org" added to the query.

[/B]It will search this forum in an easier manner. 

Sorry if this sounds redundant. I wish I had your answer straight. :/

---

### Post by P4man on 2009-09-29
I dont know who suggested *installing* ubuntu to be able to boot your recovery partition, but thats kind of .. silly. 

Since you're unfamiliar with ubuntu, talking you through the commands to get grub working with windows and the recovery is probably far more complicated than needed, so the easy answer is probably to make a bootable cd (or stick) with "super grub". The main site is down for the moment, but I found these mirrors:

[http://sites.google.com/site/supergrubdiskmirrorlist/](http://sites.google.com/site/supergrubdiskmirrorlist/)

---

### Post by lisati on 2009-09-29
I'm surprised no-one has suggested something like this before:
Open up a terminal (Applications->Accesories->Terminal), and type in the following command:```
sudo fdisk -l
```
If the recovery partition is still there it will show up, probably as a FAT32 or NTFS partition. Feel free to post the output of the command if you get stuck interpreting the results or figuring out what to do next.

---

### Post by Ghot on 2009-09-29
here's the output:


 sudo fdisk -l
Disk /dev/sda: 160.0 GB, 160041885696 bytes 255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes 
Disk identifier: 0x95702011     Device Boot      Start         End      Blocks   Id    System 
                                             /dev/sda1    1             1344    10795648+   7      HPFS/NTFS 
                                             /dev/sda2   *       10750       19457    69947010   83      Linux
                                             /dev/sda3            8995       10749    14097037+   7       HPFS/NTFS  
                                             /dev/sda4            1345        1830     3903795       5       Extended 
                                             /dev/sda5            1345        1830     3903763+    82      Linux swap / Solaris 

 
Partition table entries are not in disk order root@xp-laptop:/home/xp#


now understand..plz   i have no idea how or what to do with this knowledge  :)

I do know that the top NTFS is a 10Gb partition and the lower NTFS is 13gb....ya see he installed Windows 7 RC overtop of Vista....apparently it didnt wipe the recovery partition...OR....one of the partitions is Vista and the other is WIN 7 and he may have wiped the recovery partition  ???


.and to the above poster i already tried the Super grub Disc   ...all night as a matter of fact  lol

---

### Post by KlinerDraken on 2009-09-29
> **Ghot said:**
> not if I can help it...this is a friends comp that hasnt been used in a year, and rather than spend 20$ for the recovery CD...

Here is a free recovery CD download, if it'll help.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

---

### Post by Ghot on 2009-09-29
> **KlinerDraken said:**
> Here is a free recovery CD download, if it'll help.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")

well its NOT free....and YES there are many torrents of this CD....and I got it tonight....reboot with freshly burned Vista recovery iso in laptop and it did nothing...I don't know whether it a bad torrent  or I needed to make it bootable first?

Personally I think the Win7 over Vista (NOT on its own partition) borked the recovery partition....cause the guy said after he had Win 7 installed, he decided he didnt like it so did the F8 thing at boot to get to the Gateway recovery Option....didnt work....and messed up Win 7 too  lol


.and before any1 suggests it...I've also got the ultimate Boot CD....no help   :(

---

### Post by nothingspecial on 2009-09-29
Why don`t you mount the partitiond and see what`s on them?
```

sudo mkdir /media/windows
```
```
sudo mkdir /media/windows1
```
```
sudo mount -t ntfs /dev/sda1/ /media/windows/
```
```
sudo mount -t ntfs /dev/sda3/ /media/windows1/
```
```
ls /media/windows
```
```
ls /media/windows1
```

Once they are mounted you can see what size they are by typing df -h

---

### Post by KlinerDraken on 2009-09-29
Sorry that didn't help.

When you burned the ISO file to the CD did you burn it as data or as an image?

---

### Post by P4man on 2009-09-29
What nothingspecial said, although its probably a lot easier than that, if you go to "places" you will probably see the different drives and just click to access them and see whats on them. Its probably in vain though.

A cd costs maybe 10 cents ? to produce in volume (if that much), I find there is no excuse for OEM's to skimp on that.

Anyway, to save the $20 and avoid (likely) illegal alternatives, might as well use the occasion to have your friend try out ubuntu. Its already installed, maybe he likes it.

---

