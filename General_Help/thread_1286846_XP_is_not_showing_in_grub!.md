---
title: "XP is not showing in grub!"
date: 2009-10-09
forum: General Help
---

### Post by mickmouse13 on 2009-10-09
I just reinstalled ubuntu and windows XP today do to switching hard drives. they are in two difrent drives. 
I have read other tutorials for this but i want to make sure the commands and things i change are relavent to my system. 
Windows XP does not show up in the grub loader. from what i read its because windows does not like being the slave instead of the master. anyway i ran 
 sudo fdisk -l 
and got this ```
mick@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f0d72e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38161   306528201   83  Linux
/dev/sda2           38162       38913     6040440    5  Extended
/dev/sda5           38162       38913     6040408+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x62626262

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9728    78140128+   7  HPFS/NTFS

```

Also when i open boot/grub/menu.lst.save 
its blank. is this a problem? 
anyway if anyone knows what i needa do to get windows XP back in the grub loader tell me =) thanks.

Im running ubuntu studio 9.10

---

### Post by undecim on 2009-10-09
I believe putting this in /boot/grub/menu.lst will do it for you (put it below your Ubuntu entry in menu.lst):

```
# Windows XP
title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1

```

---

### Post by mickmouse13 on 2009-10-09
i dont have a menu.lst file the closest there is is menu.lst.save and in that file there is no ubuntu, its just a blank document

---

### Post by mickmouse13 on 2009-10-09
i found the previous out by navigateing to the /boot/grub/ folder and than running "sudo gedit menu.lst.save" and it opens and is completely blank.

---

### Post by SACHINVD on 2009-10-09
U r seeing menu.lst blank as u have not opened it using root privilages.

Its system file so need prvilages.

to run it from terminal "sudo gedit /boot/grub/menu.lst"

and do changes as told in above post

---

### Post by mickmouse13 on 2009-10-09
okay i opened it and it useing a copy and past of SACHINVD's post. it was still blank. I copy and pasted the text into the file and saved. It made a new file named menu.lst i am rebooting now to see the effects.

---

### Post by mickmouse13 on 2009-10-09
I hate to say it, but there is no improvement. and im fairly certain i did everything correctly. The only thing that does not mesh is that i did not have a boot.lst i do now but grub still loaded up and just had 2 ubuntus and 2 mem tests

---

### Post by mickmouse13 on 2009-10-09
If i just switched my Hds would this fix the problem do you all think? like make the 80GB windows one the master?

---

### Post by snowpine on 2009-10-09
Ubuntu 9.10 uses Grub 2, which doesn't use menu.lst any more.

Check it out:

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

I personally will not be using 9.10 until it is out of beta, so I can't give you more specific help, sorry. :)

---

### Post by mickmouse13 on 2009-10-09
Thanks. Whether it fixes my problem or not i should of read this anyway by now. I will mark this as solved for now.

---

### Post by oldfred on 2009-10-09
If you switch hard drives and windows is still in the MBR it should just boot to windows, you will not see Ubuntu.

If you pasted the windows stanza in a blank file, you did not open the correct menu.lst.  Also if your windows is on the second drive you need map commands in addition.

Ok, just saw post by snowpine & he is correct that grub2 does not have a menu.lst.


This is how it is supposed to work but grub2 is new and still not always working:
Even still, the latest Karmic Alpha needs some help to find other os.
sudo apt-get install os-prober
sudo os-prober
sudo update-grub2

---

### Post by snowpine on 2009-10-09
ps A little off-topic, but what's your experience so far with Karmic Studio? I am planning to wait until the official release to upgrade, but I am curious what to look forward to? :)

---

### Post by QIII on 2009-10-09
> **oldfred said:**
> 
sudo apt-get install os-prober
sudo os-prober
sudo update-grub2

+1

That is how I have been telling everyone to do it, and have always gotten positive feedback.  

This worked both when I upgraded my 32 and 64 bit Jaunty machines to GRUB2 and the whole time I have been reinstalling 32 and 64 bit Karmic since the first Alpha.

---

### Post by mickmouse13 on 2009-10-09
the apt-get gives me this (i have ran it a couple of times)

```
Reading state information... Done
os-prober is already the newest version.
The following extra packages will be installed:
  ubuntustudio-default-settings
The following packages will be upgraded:
  ubuntustudio-default-settings
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B/6,608B of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 122512 files and directories currently installed.)
Preparing to replace ubuntustudio-default-settings 0.26 (using .../ubuntustudio-default-settings_0.26ubuntu1_all.deb) ...
Unpacking replacement ubuntustudio-default-settings ...
dpkg: warning: old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
dpkg: error processing /var/cache/apt/archives/ubuntustudio-default-settings_0.26ubuntu1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 1
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntustudio-default-settings_0.26ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` it has seen errors both times. 

and this is the other two commands
```
mick@ubuntu:~$ sudo os-prober
mick@ubuntu:~$ sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-6-rt
Found initrd image: /boot/initrd.img-2.6.31-6-rt
Found memtest86+ image: /boot/memtest86+.bin
done

```

as for what i think snowpine. i font know. i just got it today. the background is the same as it has been for a while (but its cool) and the menus at the top are very space saving. although will take a tad of getting used to. although i use terminal for alot of stuff so i dont think it will be a problem.  

PS. i dont like grub2 much anyway.. i liked the old look better and i dont like problems (of course) anyone know how to revert to legacy? i have been searching around but have not found much.

---

### Post by mickmouse13 on 2009-10-09
i thought a full remove and retry was in order but after trying to un-install os-prober i get this. 

```
E: /var/cache/apt/archives/ubuntustudio-default-settings_0.26ubuntu1_all.deb: subprocess new post-removal script returned error exit status 1
```meh.. same errors from the install...

---

### Post by QIII on 2009-10-09
Might give this a try ...

```
sudo apt-get install --reinstall os-prober
```

... but since you were told you had the latest version, I'm not sure that will help.

---

### Post by mickmouse13 on 2009-10-09
thanks for all the help. i will keep it all in mind for later

and i still got the errors with re-install.

---

### Post by mickmouse13 on 2009-10-09
okay i reverted back and now i have grub legacy. Atfrist windows did nto show up but then i did what i was told and it showed up in grub (text was "windows XP") i press enter on it and it says "starting up" or something liek that.. and it stays that way. never fully boots up. 

this is what that part looks like (did i putt it in the right place?) 
```
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#
# Windows XP
title Windows XP
rootnoverify (hd1,0)
makeactive
chainloader +1

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
```

i also just found this 
```
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-3-rt
uuid        cc9019da-eef4-418a-9d6a-86849e13a7de
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=cc9019da-eef4-418a-9d6a-86849e13a7de ro quiet splash 
initrd        /boot/initrd.img-2.6.28-3-rt
quiet

title        Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid        cc9019da-eef4-418a-9d6a-86849e13a7de
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=cc9019da-eef4-418a-9d6a-86849e13a7de ro  single
initrd        /boot/initrd.img-2.6.28-3-rt

title        Ubuntu 9.04, memtest86+
uuid        cc9019da-eef4-418a-9d6a-86849e13a7de
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```
might this be the place? idk sorry for all the trouble XD

---

### Post by scuttleclun on 2009-10-09
> **mickmouse13 said:**
> i thought a full remove and retry was in order but after trying to un-install os-prober i get this. 

```
E: /var/cache/apt/archives/ubuntustudio-default-settings_0.26ubuntu1_all.deb: subprocess new post-removal script returned error exit status 1
```meh.. same errors from the install...


I get this too trying to update karmic. After much investigation and hair pulling I found that the .postrm script in the package is trying to use the utility /usr/sbin/update-gconf-defaults but its actually in /usr/bin !!
A quick dirty fix is to do a 

sudo ln -s /usr/bin/update-gconf-defaults /usr/sbin/update-gconf-defaults

then do

sudo dpkg -i  /var/cache/apt/archives/ubuntustudio-default-settings_0.26ubuntu1_all.deb

hope that helps sort out that problem!

---

### Post by oldfred on 2009-10-09
You can put the windows stanza before or after the automagic area, as every time a kernel is updated everything in the automagic area is rewritten.

If windows is on the second drive you need to map it back so windows thinks it still is first. Add the map lines, the makeactive should be not required if the partition is flagged as boot (*) when you do a fdisk -l.

title        Microsoft Windows XP Professional
rootnoverify    (hd1,0)
savedefault
[COLOR=DarkRed]map        (hd0) (hd1)
map        (hd1) (hd0)[/COLOR]
chainloader    +1

---

### Post by mickmouse13 on 2009-10-09
sooo like this? this seems to be right. 


```
### END DEBIAN AUTOMAGIC KERNELS LIST

title Microsoft Windows XP Professional
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

```

---

### Post by oldfred on 2009-10-09
The real test is does it work? If not back to the drawing board.

---

### Post by mundo on 2009-11-04
So, did it work??

---

