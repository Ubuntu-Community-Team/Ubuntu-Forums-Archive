---
title: "Remove all Windows&amp;HP partitions, stay with only ubuntu partition with full HDD Space"
date: 2012-07-30
forum: General Help
---

### Post by demetroman on 2012-07-30
Hi every1, this is my 1st post, signed up for this :] :KS

So today i installed Xubuntu on my HP Pavilion G6 laptop VIA UBUNTU WINDOWS INBSTALLER, :) it's a really cool os for especially laptops. :popcorn:

So yeas, i really like this os and i wanna remove windows, remove ALL partitions and have only one, ubuntu.  I'm so confused, where did the windows ubuntu installer install ubuntu, in what partition, how can i remove all partitions and have only the ubuntu partition? also hp has recovery partition and this useles stuff... u know... so i wanna format all the partitions  except the ubuntu one, and join them into the ubuntu partition, but i dont know which is the ubuntu and which is the windows partition ,im using a partition program its confusing pls help :/

:D
I wanna have Ubuntu partition only with full space of all my hard disk! thnnx.

pls help if u cant i will await replies

---

### Post by HeinS5 on 2012-07-30
What i do is this :
download ubuntu installer file. It is an iso file.
download unetbootin. ( can work both on windows or in ubuntu )
start over again. so make a start-up usb with unetbootin. and during installing
resize all the partitions.

Another option is to use : disk utility. this is a program that runs in ubuntu.
I use this program to delete and make partitions on my externel hard drives.

and good luck! I also do not use windows ever again!

---

### Post by argief on 2012-07-30
You can also use a live distro like gparted or part magic to resize your disks.  You will see all windows partitions are labelled as NTFS, so it will be easy to find them.  You can resize your ubuntu partition and stretch it across the entire disk.  However this is quite an advanced function, and may break your current installation because your mount points will change after you make adjustments like these.  I have not yet found the end of the rainbow that it Linux, if it's conceivable you can do it and chances are someone else has already beat you to it...

---

### Post by oldfred on 2012-07-30
Welcome to the forums.

If you installed inside Windows it is a file root.disk inside the Windows NTFS partition. Not a true dual boot as it uses the Windows boot loader to start and relies on the NTFS partition.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

If you have configured you system and want to move it to a full partitioned install.

HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

Be sure to backup Windows. We get some users who have that one application that they have to have and it is only in Windows. Dual booting is ok, we  will not bite. I only just recently stopped booting my XP after dual booting for years. Finally decided I did not need the bells on whistles on the last Windows app and fully converted.

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by miegiel on 2012-07-30
Welcome to ubuntu forums you all :D

Just 4 points I'd like to make:
[LIST=1]
[*]If you boot the ubuntu live CD you'll find it has gParted too.
[*]When removing the windows partition, be aware that you might need to make the linux root partition bootable.
[*]You also might need to [repair the GRUB bootloader]("https://help.ubuntu.com/community/Grub2/Troubleshooting#General_Troubleshooting_Preparation")
[*]Backup all the data you don't want to loose before moving/resizing partitions.
[/LIST]

Lol, **[COLOR="DarkOrange"]oldfred[/COLOR]** beat me again (and I forgot all about wubi).

---

### Post by demetroman on 2012-07-30
Thanks for replying guys, BUT the PROBLEM IS NOT SOLVED YET.

I booted into windows, formatted the recovery partition and the other one and merged it to the ubuntu partition.

Now I am left with 2 partitions, ubuntu and windows.

I booted intoubuntu and it couldnt start because of the merge :/ 

So im downloading the .iso, then, ill put it on the usb and boot from usb., so i just download .iso file , delete everything on a usb , cut it and paste it there and then boot from it..? :).

ill try that and i will try to install xubuntu over windows.

PLS tell me if what im doing is right

---

### Post by miegiel on 2012-07-30
> **demetroman said:**
> ok thanks for answering, the PROBLEM IS NOT SOLVED YET,  

i booted windows, , formatted the recovery partition and the other one and merged it to the ubuntu partition, 

then i had  2 partitions, windows and ubuntu.  

i booted ubuntu and it couldnt start, so tomorrow im gonna download the .sio, put it on the usb and boot from usb., so i just download .sio file , delete everything on a usb , cut it and paste it there and then boot from it..? :)
ill try that and i will try to install xubuntu over windows.

[How to create a bootable USB stick on Windows]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")

[How to create a bootable USB stick on Ubuntu]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu")

The methods work for any bootable .iso not just ubuntu .iso's

---

### Post by oldfred on 2012-07-30
Much better to use the installers. You do not just copy an ISO as it is an image. You have to copy & extract it so it is bootable.  The installers as posted above do that.

There is an advanced way to use grub to boot an ISO, but you have to have a way to install grub2's boot loader to the flash drive, edit a grub menu and copy the ISO. You really need to have a Linux install to be able to install grub and some knowledge of editing grub files first.

---

### Post by yuvraj23 on 2012-07-30
very easy.. first live boot Ubuntu, On ubiquity installer choose Erase disk.. This will erase whole hardrive and will create two partitions. one root and other swap.. 

I had done this to get rid of windows :)

Thankx 
Yuvraj

---

### Post by demetroman on 2012-07-31
great! :(, now i can not boot neither windows nor xubuntu :( , i extracted the iso intro the usb, and booted from flash with my latpop, then it goes there where you choose what os to run,.... i got stuck there D: , is my laptop destroyed????
:mad: 

pls heeeeelp

i even inserted the windows installation disk to format the hard disk but it does not boot :O i choose boot from cd/dvd and then  i takes me where i have to choose ubuntu or windows to boot, and none of them can boot! AM I DOOMED?

---

### Post by miegiel on 2012-07-31
> **demetroman said:**
> great! :(, now i can not boot neither windows nor xubuntu :( , i extracted the iso intro the usb, and booted from flash with my latpop, then it goes there where you choose what os to run,.... i got stuck there D: , is my laptop destroyed????
:mad: 

pls heeeeelp

i even inserted the windows installation disk to format the hard disk but it does not boot :O i choose boot from cd/dvd and then  i takes me where i have to choose ubuntu or windows to boot, and none of them can boot! AM I DOOMED?

Make sure that the BIOS settings allow you to to boot from something else than your harddisk. Some machines give you the choice to boot from a different device in the BIOS phase of the boot by pressing a key (like F12).

And you're never doomed, unless you surrender ;)

---

### Post by demetroman on 2012-07-31
yea :) , now i did it with theinstaller and it boots ine, gonna install  dis over windows an dxubuntu yaya, didnt do it yet, thnnx guys :)
God bless u <3

---

### Post by demetroman on 2012-07-31
ok solved thanks you all guys :) especially th one that gave me the link with the usb installer :)) THNNXXXX
now i am running only xubuntu
:)))))))

:guitar:

---

### Post by miegiel on 2012-07-31
> **demetroman said:**
> ok solved thanks you all guys :) especially th one that gave me the link with the usb installer :)) THNNXXXX
now i am running only xubuntu
:)))))))

:guitar:

You're welcome :D enjoy!

---

### Post by demetroman on 2012-07-31
thanks!~ :]

---

