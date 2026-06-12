---
title: "Mounting an Asus Eeepad Transformer"
date: 2011-06-23
forum: General Help
---

### Post by buddyd16 on 2011-06-23
I am having some trouble with my android tablet I connect it via USB and it does not auto-mount like a usb hard drive would. when I run lsusb in the terminal I can see the device listed but when I check fstab it does not show up as a disk.

Does anyone have any incite on how to get the internal storage of the device to mount as an external usb drive?

thanks for any help

---

### Post by iGregory on 2011-06-25
I just got a Transformer Tablet.  Very neat little toy.

I can get it to mount and transfer files back and fourth.  It's fairly easy.

Just open a terminal and type the following;

[INDENT]sudo mkdir /media/transformer
sudo chmod 775 /media/transformer
sudo mtpfs -o allow_other /media/transformer[/INDENT]

I had to also install mtpfs;
[INDENT]sudo apt-get install mtpfs
[/INDENT]The problem I have is that in order to unmount it, I had to go back into the terminal and type;
[INDENT]sudo umount /media/transformer
[/INDENT]I tried to left click and 'unmount' but I didn't have access, so I had to go the 'sudo' route.

Also, if you want to mount it again, then you have to repeat the whole process.  Hopefully somebody with much more experience and knowledge has some insight into this...

Greg

---

### Post by buddyd16 on 2011-07-06
awesome thank you very much for sharing how to mount the device.

---

### Post by stinkeye on 2011-07-06
...and a thank you from me.

Have an Acer iconia A500 tablet.

Plugged in the tablet and
ran **lsusb** which gave me 
```
Bus 001 Device 007: ID 0502:3325 Acer, Inc.
```

Substituted **Acer** for **transformer** in iGregory's post
and worked perfectly.
=D>

---

### Post by Lod on 2011-07-21
Worked for me and my transformer as well. Although I had to reboot first.

---

### Post by lain80 on 2011-07-30
Thanks, it working fine!
(transformer on ubuntu 2.6.38-8)

---

### Post by abprie on 2011-08-04
mounting works, thank you!

---

### Post by geo909 on 2011-08-12
Perfect! Worked like a charm! Thanks a lot..

---

### Post by charlesvr on 2011-08-15
I am getting jealous reading all positive reactions. So hopefully I started, typing     sudo mkdir /media/transformer
No problem. So I continued with    sudo chmod 775/media/transformer
 Then it went wrong. My terminal said: 
chmod: cannot access `/media/transformer': Transport endpoint is not connected
I have mtpfs installed..... No idea what to do next. In my  filebrowser a new item was created called "transformer", but clicking it gives the same error. Can you help me out?

---

### Post by Sam Lars on 2011-08-18
Same error here.
I restarted after adding the rule mentioned, and that got it showing up as a device, but it's still giving the same error.

---

### Post by BcRich on 2011-09-01
I'm getting the same error as charlesvr and Sam Lars, have either one of you found a solution to this? or has anyone else got any suggestions?
i'm using ubuntu 10.10 with asus eee pad transformer101

---

### Post by BcRich on 2011-09-01
after following your post iGergory
> **iGregory said:**
> I just got a Transformer Tablet.  Very neat little toy.

I can get it to mount and transfer files back and fourth.  It's fairly easy.

Just open a terminal and type the following;
[INDENT]sudo mkdir /media/transformer
sudo chmod 775 /media/transformer
sudo mtpfs -o allow_other /media/transformer[/INDENT]I had to also install mtpfs;[INDENT]sudo apt-get install mtpfs
[/INDENT]The problem I have is that in order to unmount it, I had to go back into the terminal and type;[INDENT]sudo umount /media/transformer
[/INDENT]I tried to left click and 'unmount' but I didn't have access, so I had to go the 'sudo' route.

Also, if you want to mount it again, then you have to repeat the whole process.  Hopefully somebody with much more experience and knowledge has some insight into this...

Greg
my transformer was still not mounting, so I rebooted and now my ubuntu is have problems accessing all my usb devices! in fact i can't actually use ubuntu any more because my keyboard and mouse are usb devices.
please post instructions on how to undo these changes, it would be most appreciated.

---

### Post by aldeby on 2011-09-02
The very only thing that may have caused any trouble in the commands iGregory have suggested is installing mtpfs. Reversing the changes is as easy as typing 
```
sudo dpkg -R mtpfs 
```in whatever console.
You can select "recovery" at the boot screen and then when prompted with a menu choose to show the terminal root console. Then just type this command and then press CTRL-D or simply reboot with
```
reboot
```

---

### Post by aldeby on 2011-09-02
for every MTP device I suggest using gMTP. It's easy, it does not involve any terminal command and has an ugly but usable graphic user interface.

you may find it in the standard reporistories.

_However_ the version shipped with Ubuntu 11.04 is broken. You have to use the one from the forthcoming Ubuntu 11.10. You may download it from [http://packages.ubuntu.com/oneiric/gmtp](http://packages.ubuntu.com/oneiric/gmtp)

but also ensure you download the updated libmtp9 as this is a compulsory dependency.
[http://packages.ubuntu.com/oneiric/libmtp9](http://packages.ubuntu.com/oneiric/libmtp9)

install first libmtp9 then gmtp (just click on the downloaded package).

---

### Post by Sam Lars on 2011-09-11
Thanks for the suggestion of gMTP.
I tried those packages on 11.04, but libmtp9 needed libmtp-common.
[http://packages.ubuntu.com/oneiric/libmtp-common](http://packages.ubuntu.com/oneiric/libmtp-common)
And then that package conflicted with libmtp8 which is needed by Banshee, Rhythmbox...
So I'm not able to install that. Guess I have to wait until I feel like upgrading to Oneiric...

---

### Post by BcRich on 2011-09-11
hi Sam Lars
If u dont mind installing the sdk and using terminal u could use _Aries_  suggestion 3rd post [http://ubuntuforums.org/showthread.php?t=1840353](http://ubuntuforums.org/showthread.php?t=1840353)
Bit of round about method, but abd works perfectly 4 me. I'm using ubuntu 10.10

---

### Post by Sam Lars on 2011-09-11
Thanks for the adb suggestion, that worked for me. It's better than nothing.
I tried the mtp method again, and it didn't give me an error right away. I just saw an empty Playlist folder when I browsed it, though, and I couldn't write anything. After that it would just cause my /media folder to show up empty...

---

### Post by bfmetcalf on 2011-11-13
I have tried this and been at it for about 3 hours.  All I can get to come up using the MTPFS method is it looks like it mounts and when i open it all i can see is 1 empty playlist folder.  I have gotten it to connect via bluetooth, but it only has like a 150kb/s transfer speed and doesn't really work too well for movies...  any help would be appreciated.

---

### Post by BcRich on 2011-11-13
hi bfmetcalf
using  adb [http://developer.android.com/guide/developing/tools/adb.html](http://developer.android.com/guide/developing/tools/adb.html) you can connect to your transformer via usb, which will be faster than bluetooth. unfortunately there is no GUI option for this method as of yet so you'll need to use the cli. this method does not require the use of gmtp or mtpfs

---

### Post by Sam Lars on 2011-11-13
For most things I've been using the network to transfer files. I set up some Samba shares on the Ubuntu machine, and I use ES File Explorer on the Transformer to browse them and copy files. It can even stream HD video files that way (usually). Haven't tried pushing files from the tablet to the shares yet, but that may work too.

---

### Post by JoeBrewski on 2013-02-13
> **iGregory said:**
> I just got a Transformer Tablet.  Very neat little toy.

I can get it to mount and transfer files back and fourth.  It's fairly easy.

Just open a terminal and type the following;
[INDENT]sudo mkdir /media/transformer
sudo chmod 775 /media/transformer
sudo mtpfs -o allow_other /media/transformer[/INDENT]I had to also install mtpfs;[INDENT]sudo apt-get install mtpfs
[/INDENT]The problem I have is that in order to unmount it, I had to go back into the terminal and type;[INDENT]sudo umount /media/transformer
[/INDENT]I tried to left click and 'unmount' but I didn't have access, so I had to go the 'sudo' route.

Also, if you want to mount it again, then you have to repeat the whole process.  Hopefully somebody with much more experience and knowledge has some insight into this...

Greg

Worked great to me, would be nice if they used native support tho. Google, you listening?

---

### Post by oldos2er on 2013-02-13
Old thread closed.

---

