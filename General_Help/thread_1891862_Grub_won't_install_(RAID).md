---
title: "Grub won't install (RAID)"
date: 2011-12-06
forum: General Help
---

### Post by asvestomix on 2011-12-06
Hello people,

Tday i tried to replace fedora 15 with ubuntu 11.10 ( it was a dual-boot with win7 and i used windows boot manager instead of grub legacy)
what i did was to remove the partitions that fedora was installed and installed ubuntu on them. When the installation finished i get a fatal error that said grub failed to install and i had to install a boot loader manually, after that i tried to fix it with EasyBCD by adding a new entry on windows boot manager but the entry failed to start ubuntu.. what should i do? is there any way to install the grub to the first sector of boot partition that i installed ubuntu in order to use windows boot-manager? Or if it is not possible how should i fix grub without reformat the HDD or loose my data?

Sorry for long or complicated Post.

---

### Post by bluexrider on 2011-12-06
are you able to boot from the live CD and if so repair grub

---

### Post by asvestomix on 2011-12-06
> **bluexrider said:**
> are you able to boot from the live CD and if so repair grub
Can you guide me how to fix grub from live cd?
I think it's no gonna fix because it maybe conflict with windows boot loader.

---

### Post by drs305 on 2011-12-06
From the LiveCD, please download the Boot Repair app and see if that can fix your system. If it can't, then it has an option to run the Boot Info Script. This script prepares a report we can view to check your boot files.

Click the "Boot Repair" link in my signature line to go to the thread about Boot Repair.

---

### Post by bluexrider on 2011-12-06
> **asvestomix said:**
> Can you guide me how to fix grub from live cd?
I think it's no gonna fix because it maybe conflict with windows boot loader.

**Here’s the quick and easy way to re-enable Grub.**
 1) Boot off the LiveCD
 2) Open a Terminal and type in the following commands, noting that  the first command will put you into the grub “prompt”, and the next 3  commands will be executed there. Also note that hd0,0 implies the first  hard drive and the first partition on that drive, which is where you  probably installed grub to during installation. If not, then adjust  accordingly.
 [INDENT]sudo grub
 > root (hd0,0)
 > setup (hd0)
 > exit
 [/INDENT] Reboot (removing the livecd), and your boot menu should be back.

---

### Post by asvestomix on 2011-12-06
> **drs305 said:**
> From the LiveCD, please download the Boot Repair app and see if that can fix your system. If it can't, then it has an option to run the Boot Info Script. This script prepares a report we can view to check your boot files.

Click the "Boot Repair" link in my signature line to go to the thread about Boot Repair.

i tried that but when i started boot repair it gave me this message but i am still waiting it to enable raid.. ( see the picture)

---

### Post by drs305 on 2011-12-06
I've not used RAID. I do know that when I ran Boot Repair and it was checking my disks for other OS's it took about 4 minutes to complete the search. I thought it had frozen, but it just took a while.

If you can't get Boot Repair to work, you can go to the Boot Info Script page at the following link to download and run the script. It will generate a file called RESULTS.txt. 

Paste the contents in a new post, highlight it, and then press the # icon in the post's menu, it will add 'code' formatting tags that will make it easier for us to read.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by asvestomix on 2011-12-06
> **drs305 said:**
> I've not used RAID. I do know that when I ran Boot Repair and it was checking my disks for other OS's it took about 4 minutes to complete the search. I thought it had frozen, but it just took a while.

If you can't get Boot Repair to work, you can go to the Boot Info Script page at the following link to download and run the script. It will generate a file called RESULTS.txt. 

Paste the contents in a new post, highlight it, and then press the # icon in the post's menu, it will add 'code' formatting tags that will make it easier for us to read.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

well i used auto fix but it made the situation even worse..

it installer grub 1.97 but it is not seems to have any entries.. now i cant even boot windows 7 :S

---

### Post by asvestomix on 2011-12-06
> **bluexrider said:**
> **Here’s the quick and easy way to re-enable Grub.**
 1) Boot off the LiveCD
 2) Open a Terminal and type in the following commands, noting that  the first command will put you into the grub “prompt”, and the next 3  commands will be executed there. Also note that hd0,0 implies the first  hard drive and the first partition on that drive, which is where you  probably installed grub to during installation. If not, then adjust  accordingly.
 [INDENT]sudo grub
 > root (hd0,0)
 > setup (hd0)
 > exit
 [/INDENT] Reboot (removing the livecd), and your boot menu should be back.

this commands seems that are not working with live cd

---

### Post by asvestomix on 2011-12-06
I tried to repair windows boot with windows dvd but it didn't work,

here is the Boot Info Scriptreport [http://paste.ubuntu.com/762292/](http://paste.ubuntu.com/762292/)

---

### Post by asvestomix on 2011-12-06
Right now from the little i can understand from the report it seems that the boot repair installed grub 1.99 at the mbr but when i pass post screen and start grub i dont see any entry.. boot repair and windows recovery seems to have created a big chaos.

---

### Post by drs305 on 2011-12-06
I don't want to wade too deep in this thread as I can't speak about RAID.

Grub was installed on the Windows cgg2 partition. Several of the Grub 2 files are missing from your Ubuntu cgg5 partition.

For a non-RAID system, what you would do in this case is boot the LiveCD and install Grub. 

In many cases, all that is necessary is to mount the Ubuntu partition and install grub. In your case, you are also missing the Grub menu file (grub.cfg), so a more detailed reinstallation is preferred.

Normally I would recommend 'chrooting' into your Ubuntu partition since you are missing both core.img and the grub menu itself (grub.cfg). To do this, you mount your Ubuntu partition, copy some of the LiveCD system files over to the mounted partition, and then 'chroot' into it. 

My 'chroot' guide (see signature link) discusses purging and then reinstalling, but in your case all you would have to do is install grub-pc in the 'chroot' and update grub. This would generate both the core.img and Grub menu files, and you would reinstall Grub on the MBR.

Unfortunately I can't tell you how you mount your cgg5 partition, and whether or not there are additional considerations for a RAID setup that would invalidate this procedure. Hopefully others will know.

---

### Post by asvestomix on 2011-12-06
i am not very sure but stripped raid arrays like mine are like a bigger hdd for the ubuntu witch i spit it to partitions like a normal hard drive ..

---

### Post by asvestomix on 2011-12-06
> **drs305 said:**
> 
For a non-RAID system, what you would do in this case is boot the LiveCD and install Grub. 

In many cases, all that is necessary is to mount the Ubuntu partition and install grub. In your case, you are also missing the Grub menu file (grub.cfg), so a more detailed reinstallation is preferred.

Normally I would recommend 'chrooting' into your Ubuntu partition since you are missing both core.img and the grub menu itself (grub.cfg). To do this, you mount your Ubuntu partition, copy some of the LiveCD system files over to the mounted partition, and then 'chroot' into it. 

My 'chroot' guide (see signature link) discusses purging and then reinstalling, but in your case all you would have to do is install grub-pc in the 'chroot' and update grub. This would generate both the core.img and Grub menu files, and you would reinstall Grub on the MBR.


Please can you guide me stepbystep to do that? It seems to advanced for me

Thank you anyway for your responses

---

### Post by cbowman57 on 2011-12-06
Software RAID0?  I'm guessing you used the alternate iso to do the install, the simplest way to make sure it works is make sure you have a non-RAID /boot partition. I've read that isn't necessary but it sure makes life easier.

---

### Post by drs305 on 2011-12-06
> **asvestomix said:**
> Please can you guide me stepbystep to do that? It seems to advanced for me

Thank you anyway for your responses

I don't know how you mount RAID drives and wouldn't want to walk you through that unless I knew that it would work and that there are not more steps involved. I'd prefer we wait for someone with RAID experience to help out.

---

### Post by asvestomix on 2011-12-06
> **cbowman57 said:**
> Software RAID0?  I'm guessing you used the alternate iso to do the install, the simplest way to make sure it works is make sure you have a non-RAID /boot partition. I've read that isn't necessary but it sure makes life easier.

i dont have software raid, i stripped 2 640gb hdds into a big one from my raid bios , this controller loads just after post so operating systems identifying it as one big drive (1.2tb). when i installed windows i used 1 partition for windows 1 for data and left some free space for linux and then i spitted it into 3 logical partitions 1 for root 1 for swap and 1 for home.. i know it is complicated with all of those partitions :S. Well this worked fine until i decided to delete fedora and install ubuntu instead.

---

### Post by cbowman57 on 2011-12-06
Sorry, been 10 years since I used fake RAID.
Did you use the live CD or the alternate install iso?  If not the alternate iso might fix you up.  It's worth a try.

Also until you get it figured out you could install grub to a flash drive.

Another good rescue disk is called Rescatux, much easier than trying to reinstall grub from liveCD.

---

### Post by asvestomix on 2011-12-06
> **cbowman57 said:**
> Sorry, been 10 years since I used fake RAID.
Did you use the live CD or the alternate install iso?  If not the alternate iso might fix you up.  It's worth a try.

Also until you get it figured out you could install grub to a flash drive.

Another good rescue disk is called Rescatux, much easier than trying to reinstall grub from liveCD. i used live cd, i don't even know what is the alternative iso or how to install Grub manually.

---

### Post by cbowman57 on 2011-12-06
No problem, get an alternate iso [here]("http://www.ubuntu.com/download/ubuntu/alternative-download") in case you need to install to RAID again.

You can get Rescatux [here]("http://www.supergrubdisk.org/rescatux/")

---

### Post by asvestomix on 2011-12-06
> **cbowman57 said:**
> No problem, get an alternate iso [here]("http://www.ubuntu.com/download/ubuntu/alternative-download") in case you need to install to RAID again.

You can get Rescatux [here]("http://www.supergrubdisk.org/rescatux/")

ok, i am now downloading Rescatux,  

thanks you anyway!

---

### Post by asvestomix on 2011-12-07
Rescatux was unable to identify the Raid array.

---

### Post by cbowman57 on 2011-12-07
> **asvestomix said:**
> Rescatux was unable to identify the Raid array.

I was hoping it would, I don't know what else to suggest at this point.

All I can come up with is reinstalling linux with the alternate iso and hope it gets detected properly.

---

### Post by asvestomix on 2011-12-07
Well i could not fix it so i did it the hard way, I backed up my data and reformat my disks installed windows etc.. Now my question is if i can install manually grub at the first sector of boot partition that i installed ubuntu in order to use windows boot-manager instead of grub?

---

### Post by asvestomix on 2011-12-07
It seems i still have the same problem, when i finish the ubuntu setup i get a message saying grub failed to install no mater where i choose to be installed always it fails.. maybe something is wrong with the 11.10 live cd, i didnt had this problem the last time when i used 11.04.. How can i install grub manually?

---

### Post by cbowman57 on 2011-12-07
You didn't even try the  alternate iso did you.

---

### Post by asvestomix on 2011-12-07
well,i fill sorry to say that but i ran out of cds :S, if i fail to do it manually i will try it tomorrow,

---

### Post by cbowman57 on 2011-12-07
That always happens at the worst time.

I wish I could guarantee that the alternate will work but I'm not positive.

From what I remember though Ubuntu won't properly install to RAID with the LiveCD.

---

### Post by asvestomix on 2011-12-08
Alternative ISO worked fine, i kinda fill a little stupid because i didn't use this alternative earlier! thank you for for the help.

---

### Post by cbowman57 on 2011-12-08
That's good news, glad my suggestion paid off.

There really isn't that much reliable info available for those of us that want to use RAID for desktop machines.  

Now you verified it & can help the next guy. :)

---

### Post by asvestomix on 2011-12-08
Yeah of course, btw 11.4 and earlier versions worked fine.. it seems that the 11.10 live disk does not support the raid very well. btw i am using nvidia raid controller

---

