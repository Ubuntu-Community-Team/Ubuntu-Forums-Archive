---
title: "need help - did somethings wrong"
date: 2009-07-22
forum: General Help
---

### Post by tjockarn on 2009-07-22
Hello. I start with, SORRY for my bad english, im swedish!

Anyway, yesterday i installed Ubuntu to my computer. 
I downloaded the CD and tried it live, it seemed nice so i pressed install. And before that i watched movies on youtube how to do and got some help from other ways how to do it.

There was no problem until the partition. There it was my HDD on 355gb and an partition on 10gb (with vista) so i made an new partition of the big one. But when it asked for size it was the entire space on 355gb, but i changed to 10gb. And i think this is why i got one of the problems. So after ive done that partition i got 3, the big one, the vista and this new.

So it installed and when that was finished i tried to look if i had something on my computer. My wireless internet didnt work in Linux (:o) and i didnt have any wire so i couldnt get any connection. And my HDD was gone, couldnt find it, only my CD and card reader were there. So i was thinking, i reboot to vista again to get some help. Restarting computer, and when i was in the reboot menu. There was only ONE HDD there and the CD (ofc i did remove the CD as said after install).
It was something like:
-Hard drive..(strange text with numbers etc).....
   *Hard drive (.........)
-CD-Rom..(text).....
    *CD-Rom (.........)


Here a movie on a restart:
[http://www.youtube.com/watch?v=tcwiRaEtygg](http://www.youtube.com/watch?v=tcwiRaEtygg)

And when i press in to the GRUB menu, this is what i get up (no vista? :():
[http://sv.tinypic.com/view.php?pic=21b4yhf&s=3](http://sv.tinypic.com/view.php?pic=21b4yhf&s=3)

An picture on "systemviewer" or what it  can be in english:
[http://sv.tinypic.com/view.php?pic=34xizdf&s=3](http://sv.tinypic.com/view.php?pic=34xizdf&s=3)

So i really need help, is my Vista and all there gone forever now? And allso i wanna know, the problem is that because i made an 10gb partition instead of an partition of all the space ?

---

### Post by nothingspecial on 2009-07-22
Open a terminal in ubuntu (in your menu accesories > terminal) and type 

```
sudo fdisk -l
```

and copy and paste the output here

---

### Post by tjockarn on 2009-07-22
Well i got the swedish version so i get this in swedish. Maybe it works with google translate. Well i try it anyway and hope you will understand that. But it seems good as i got the 360gb, but the bad is that there is an Linux on sda1, that one was vista yesterday. Craap!

The one i get:
Disk /dev/sda: 360,0 GB, 360080695296 byte
255 huvuden, 63 sektorer/spår, 43777 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x1549f232

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1           42563       43777     9759487+  83  Linux
/dev/sda2   *       41347       42562     9767520   83  Linux

Posterna i partitionstabellen är inte i diskordning

Disk /dev/sdb: 16,0 GB, 16028794368 byte
254 huvuden, 63 sektorer/spår, 1956 cylindrar
Enheter = cylindrar av 16002 · 512 = 8193024 byte
Diskidentifierare: 0x00000000

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1               1        1955    15641929    c  W95 FAT32 (LBA)


Google version:
Disk / dev / sda: 360.0 GB, 360080695296 bytes  
 255 heads, 63 sectors / track, 43777 cylinders  
 Units = cylinders of 16065 512 = 8225280 bytes  
 Diskidentifierare: 0x1549f232  

     Unit Start Start End Blocks Id System  
 / dev/sda1 42563 43777 9759487 + 83 Linux  
 / dev/sda2 * 41347 42562 9767520 83 Linux  

 The entries in the partition table is not in disk order  

 Disk / dev / sdb: 16.0 GB, 16028794368 bytes  
 254 heads, 63 sectors / track, 1956 cylinders  
 Units = cylinders of 16002 512 = 8193024 bytes  
 Diskidentifierare: 0x00000000  

     Unit Start Start End Blocks Id System  
 / dev/sdb1 1 1955 15641929 c W95 FAT32 (LBA)

---

### Post by rbc on 2009-07-22
Yes.You did indeed nuke Vista. If there was anything important on it, please stop booting to the drive, and we can give some tips to try and recover files before they get overwriiten too much. There's no guarantee, but it's worth a shot

---

### Post by tjockarn on 2009-07-23
> **rbc said:**
> Yes.You did indeed nuke Vista. If there was anything important on it, please stop booting to the drive, and we can give some tips to try and recover files before they get overwriiten too much. There's no guarantee, but it's worth a shot

aah okey :/ That would be great, what you mean stop booting to the drive? What shall i do?

Booting from CD? And to get the HDD back do i reinstall Ubuntu and do an partition on the big disk or? 

I saved all my pictures on my USB memory (bad translate?). But theres few things i still wanna have from Vista. But thats only ALL my links i saved in Firefox. Cause they are realy important to me :/

Please help me on what to do and how :)

---

### Post by rbc on 2009-07-23
Photorec is what you are going to run from the Ubuntu LiveCD, to attempt file recovery, but it is not going to search for web browswer links. So if that is all you were after, don't bother. If you still want help with photorec, post back. If not, I would simply reinstall , first Vista, then Ubuntu

---

### Post by tjockarn on 2009-07-23
> **rbc said:**
> Photorec is what you are going to run from the Ubuntu LiveCD, to attempt file recovery, but it is not going to search for web browswer links. So if that is all you were after, don't bother. If you still want help with photorec, post back. If not, I would simply reinstall , first Vista, then Ubuntu

Hmm okey, but then theres no big idea of recover. Then i will have to get the vista CD to my computer and then reinstall it. 
Thats all to do? just reinstall Vista, and then Ubuntu. Then i would like some help with how to do the partition in Ubuntu so it wont get wrong again.

I got an link to a movie on youtube that seemed good and how to do the partition and i did like that but then i didn't have anything left or any HDD so that can't be rigt.

So if someone could  give me some good tips on how to do i would be very happy :)

---

### Post by rbc on 2009-07-23
Find the Vista DVD, boot up, and install Vista. After that, use Vista's disk manager to shrink the Windows partition, then follow this guide:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
If you come across a step that you are unsure of, post here and ask for advice.

---

### Post by edu1962 on 2009-07-24
As for your links (bookmarks) i can recommend [Xmarks]("https://addons.mozilla.org/nl/firefox/search?q=xmarks&cat=all").

---

### Post by tjockarn on 2009-07-25
Thanks guys :) I will look more tomorrow or on monday when i fix the Vista CD :)

---

