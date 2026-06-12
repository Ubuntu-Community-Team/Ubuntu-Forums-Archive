---
title: "remove grub"
date: 2010-04-17
forum: General Help
---

### Post by ltdf50 on 2010-04-17
hi,

i have installed crunchbang (which is based on ubuntu) in a dual boot configuration along  windows xp. even though i liked crunchbang, and the idea of a  minimalistic os, i decided that it's just not for me. so i formatted my  harddrive, to make  a new, clean windows xp installation. what i  didn't think of was that grub is still there, and now i don't know how  to get rid of it and boot my xp with it's original bootloader. i followed this instruction: [http://www.chrisburgess.com.au/reinstal  … ootloader/]("http://www.chrisburgess.com.au/reinstalling-or-repairing-the-windows-xp-bootloader/")
and now i have 4 or 5 xp's to choose from (not  totally the instruction's fault, i did something wrong during this  procedure, i know, but it is still no solution, even when done  correctly)...now please, can anyone tell me how i clean up this  mess and have my xp booting by it's own like it did when i got my  netbook (it's a samsung nc10 by the way)?


oh, and, unfortunately, samsung recovery solution is not an option, it seems that  i have somehow managed to wipe the recovery partition...
that means i  have to get this done manually...


help would really be  appreciated, because i need this netbook in school.

---

### Post by cufflink87 on 2010-04-17
you don't have the recovery disk that came with the computer?

---

### Post by ltdf50 on 2010-04-17
hi, thanks for your answer.

i do have the recovery cd, but it seems like it wouldn't be much help...
when i start the recovery cd in windows, it asks me if i want to install xp,
and if i do so, it tells me to delete the windows folder... i somehow refuse to do
that, because this seems really weird to me. is this normal and should i follow
this instruction?

however, as i mentioned above, i formatted my harddrive and installed windows completely new, and i used my recovery cd for that, so, i'm not entirely sure if the solution for my problem is on the recovery cd...

---

### Post by howefield on 2010-04-17
Installing windows should put it's own bootloader in place of anything else on the disk.

Can you load the Ubuntu Live cd and post a screen shot of your disk as seen by GParted ? (System > Administration > GParted)

---

### Post by cufflink87 on 2010-04-17
[http://arstechnica.com/civis/viewtopic.php?f=16&t=158228](http://arstechnica.com/civis/viewtopic.php?f=16&t=158228)

here you go buddy, I had the same problem. Let me know if you have any questions

EDIT: I just realized that you're using XP. I'd recommend either (1) reinstalling crunchbang so that it will reinstall the booter or (2) following what the recovery disk tells you. Like howefield said, it will put the default bootloader in

---

### Post by ltdf50 on 2010-04-17
> [http://arstechnica.com/civis/viewtop...?f=16&t=158228]("http://arstechnica.com/civis/viewtopic.php?f=16&t=158228")

here you go buddy, I had the same problem. Let me know if you have any  questionshuh, now that is interesting...
it really is the same problem, but your solution doesn't work at all...
along with my several XPs to choose from when booting, i can also access the windows recovery console, which is where i am supposed to write the command **Bootrec.exe /FixMbr**, according to your instruction. this is an unknown command and can therefore not be executed. to write a new mbr, the (in my case) accurate command is just fixmbr, and it can be successfully executed. but still, nothing changes, the situation stays the same...

> Installing windows should put it's own bootloader in place of anything  else on the disk.i also thought so, but it looks like it didn't...

> Can you load the Ubuntu Live cd and post a screen shot of your disk as  seen by GParted ? (System > Administration > GParted)     if really neccessary, i can do that, but i need to get my external cd drive working before i can do that, because for whatever reason, my nc10 refuses to boot from this drive, even when it is on top of the list with my bootdevices...

[edit] ok, fixed the cd-drive issue...

[edit]

I followed the instructions given by the recovery cd now, which brings me to where i was yesterday evening:
I now can choose between two windows xps (whereas only the first one is working, i think that the second one is the old windows installation that i had simultaneously with crunchbang) and the recovery console.
so, grub is still there...

now, isn't there some way (maybe with some sort of 3rd party program), to just wipe the harddrive and it's bootsector clean?

---

### Post by howefield on 2010-04-17
> **ltdf50 said:**
> if really neccessary, i can do that, but i need to get my external cd drive working before i can do that, because

Try opening a terminal and post the results of 

```
sudo fdisk -l
```

---

### Post by cufflink87 on 2010-04-17
I'm sorry, but I don't really know how to do it using xp. There has to be some way to restore the windows boot through command prompt though.

I got this from another site:

*"It is very simple to restore a DOS or Windows MBR. Just enter the MS-DOS command (available since DOS version 5.0) fdisk /MBR. These commands only write the first 446 bytes (the boot code) into the MBR and leave the partition table un*touched."

[http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html](http://www.ntcompatible.com/How_to_remove_GRUB_loader_t28242.html)

---

### Post by ltdf50 on 2010-04-17
ok, i owe you an apology for wasting your time.
obviously, my "problem" is solved, and the solution is more than  embarrassing.
grub actually was overwritten all the time, it just looks quite like the  xp bootloader...
and since i am not used to a bootloader when i have only xp installed, i  thought that it had to be grub. well, i was wrong... the only problem  was a (for whatever reason) messed-up boot.ini file, in which a second  xp that doesn't actually exist is shown.

for the sake of completeness (in case anyone ever stumbles upon this now  quite ridiculous thread), i will post the working boot.ini:

[boot loader]
 timeout=30
 default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
 [operating systems]
 multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP  Professional" /fastdetect

here's how you can access it:
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

thank you very much for your time anyway, i really appreciate it.

---

