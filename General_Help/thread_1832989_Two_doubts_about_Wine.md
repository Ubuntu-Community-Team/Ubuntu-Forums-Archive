---
title: "Two doubts about Wine"
date: 2011-08-25
forum: General Help
---

### Post by Nuno098 on 2011-08-25
Hello Ubuntu community friends, i'm kinda new in Ubuntu, i started to use ubuntu because it fascinates me ubuntu's philosophy. Well as i'm a Windows user for many years i started to use some programs that i would like to transfer to Ubuntu, such as utorrent, i know that there is other p2p programs to use but i kinda like it so i tried it. Well i installed it through Wine but i cant emulate my partition D where i keep my downloads and the background of utorrent 3.0 its black, i cant read the torrent name, only the percentage of download completion. Any one can help me with both problems? thanks a lot

---

### Post by debd on 2011-08-25
either install "deluge" (torrent client) from synaptic or look here: [http://www.utorrent.com/downloads/linux](http://www.utorrent.com/downloads/linux)

AFAIK, utorrent.exe doesn't work in wine.

---

### Post by Nuno098 on 2011-08-25
With that deluge i can send the download files for my drive D? for drive D i mean D:/ on windows. Thanks

---

### Post by The Cog on 2011-08-25
There is some work involved in doing that. Firstly, you have to get D: mounted into the Ubuntu filesystem. 
[https://encrypted.google.com/?q=mount+windows+drive+in+ubuntu](https://encrypted.google.com/?q=mount+windows+drive+in+ubuntu)

And then you have to configure deluge to save to wherever D: was mounted. I've never used deluge, so can't help there.

---

### Post by debd on 2011-08-25
I think you are talking about drive letters in wine (?). 

If so, remember the drive letters shown in wine aren't actual drives, those letters are mapped to a drive.
like you can assign D: for a partition- suppose /dev/sda1 (partitions in linux terms) and E: to /dev/sda2 and so on in wine..  

So, the drive letters in wine may or may not represent the drives you have in windows with corresponding drive letters. 
Open Wine> Configure wine , open the "drives" tab to take a look.

Mount the drive if its not already mounted; now open the same torrent file with deluge, choose the download folder same as before(the one you chose with utorrent in wine), deluge should check for downloaded part files and resume download. In case it doesn't check, right click on the torrent in deluge and select 'force re-check'

---

### Post by Nuno098 on 2011-08-25
> **debd said:**
> 
So, the drive letters in wine may or may not represent the drives you have in windows with corresponding drive letters. 
Open Wine> Configure wine , open the "drives" tab to take a look.


I know that, i just want to put Wines D drive mapped as my windows D drive. Is that possible? I tried and i couldn't

---

### Post by jwbrase on 2011-08-25
> **The Cog said:**
> There is some work involved in doing that. Firstly, you have to get D: mounted into the Ubuntu filesystem. 
[https://encrypted.google.com/?q=mount+windows+drive+in+ubuntu](https://encrypted.google.com/?q=mount+windows+drive+in+ubuntu)

And then you have to configure deluge to save to wherever D: was mounted. I've never used deluge, so can't help there.

When I had Ubuntu dual booted with Windows on our family computer the Windows drive always automounted without any need for setup by me. Let's try and see if his D:\ partition has automounted for him before confusing him with the details of trying to mount it himself.

@Nuno098:

As long as your D:\ partition is mounted, deluge should be able to write to it, but it won't be called "D:\". Open up Nautilus and go to the /media directory. If your D:\ partition has mounted automatically, it should be one of the folders in that directory (once again, though, it won't be called D:\, so you'll have to identify it by what's in it). If none of your Windows drives have been automounted and you don't have any USB drives plugged in, then you'll probably only see a folder called "cdrom" (or nothing, if you don't have a CD drive).

---

### Post by jwbrase on 2011-08-25
> **Nuno098 said:**
> I know that, i just want to put Wines D drive mapped as my windows D drive. Is that possible? I tried and i couldn't

Was it that you tried to find the Windows D drive and couldn't, or that you found it but ran into problems when you tried to use it in Wine? If so, what sort of problems? Please include any error messages you got.

---

### Post by debd on 2011-08-25
>  i just want to put Wines D drive mapped as my windows D drive. Is that possible?   why not?
but first, you have to find out the partition (D: in windows) in ubuntu. Disk lebels'll be helpful. 

Once you found it, mount the drive, open "configure wine", under the drives tab select 
'add' , select the drive letter (D in your case); 
now click on the browse button beside the path field and point to /media/<your drive>

---

### Post by Nuno098 on 2011-08-25
Thanks to all that helped me, well i could put my D drive in Wine. Well the drive was mounted i just didnt know how to configure it in wine.. I did as [debd]("http://ubuntuforums.org/member.php?u=1187415") said, in configure wine i putted the path /media/"D" :P

I just didnt knew how to putted, so i went to media folder and found my partition C and D, both with strange names like "B42OLJ3B42L4B52" for example. So i putted in wine configuration the path /media/B42OLJ3B42L4B52 with the letter D and now i can save files to my drive D while running programs in Wine. Once again thanks to all of you.

---

### Post by debd on 2011-08-25
you're welcome.

mark this thread as solved.

---

