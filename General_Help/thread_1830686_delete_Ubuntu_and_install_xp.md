---
title: "delete Ubuntu and install xp"
date: 2011-08-22
forum: General Help
---

### Post by dusanmil on 2011-08-22
Hi everyone, 

I tried to delete Ubuntu (the newest version, the only one OS on my PC) and install XP after that. I booted from USB and deleted one partition that contained Linux (formated it to ntfs) files using gparted. When I wanted to boot from Windows installation CD, i got the following message:


Unknown file system:
Grub rescue> 


I dont know how to proced with installation of XP, it seems it can not boot from my CD.

Please help me, I am really a beginner...

Thank you very much!

---

### Post by sanderd17 on 2011-08-22
if you see the grub resque prompt, that means it is booting from your (empty) hard disk. Go in the BIOS to make it boot from your CD.

---

### Post by Primefalcon on 2011-08-22
You didn't need to do anything from Ubuntu....

Start your computer with XP in your rom drive and during boot press the boot selection key (typically f12)

and select boot from cd-rom, and then just at the option screen delete the Ubuntu (probally say unrecognised or unknown or whatever) partition.

and create a new ntfs and install windows to it... simple

---

### Post by elliotn on 2011-08-22
> **Primefalcon said:**
> You didn't need to do anything from Ubuntu....

Start your computer with XP in your rom drive and during boot press the boot selection key (typically f12)

and select boot from cd-rom, and then just at the option screen delete the Ubuntu (probally say unrecognised or unknown or whatever) partition.

and create a new ntfs and install windows to it... simple

that's how its done

---

### Post by dusanmil on 2011-08-22
Thanks for effort. I tried that and it did not work out. 

When I enter BIOS and change primary booting to CD ROM, it starts booting it (CD ROM makes noise), but then continues booting from Hard Drive and gives me again the same error message:

Unknown file system:
Grub rescue> 


It seems that it jumps over booting from CD and that is strange to me. CD is working properly (I completely installed xp from it yesterday to my another computer). 

Is there anything more that I could try?

Thanks for help!

---

### Post by sanderd17 on 2011-08-22
hmm, the CD starts spinning?

I've seen BIOSes where the CD drive was called HDD (only in the description you could see DVD) and there was also a CD entry, but that one wasn't connected to anything.

Maybe try other configs.

---

### Post by dusanmil on 2011-08-22
Thanks.

I've put Hard drive to be the last one that should be booted from. Then some boot procedure started that showed the following message:

Intel(R) Boot Agent GE v1.2.44 Beta-1
Copyright (C) 1997-2006, Intel Corporation

Intel(R) Boot Agent PXE Base Code (PXE-2.1 build 086)
Copyright (C) 1997-2006, Intel Corporation 

PXE-E61: Media test failure, check cable
PXE-MOF: Exiting Intel Boot Agent.



Seems like it can not make it to boot from CD ROM.

---

### Post by gandaran on 2011-08-22
one question? the computer has SATA  or IDE hardware? and which windows XP service pack is on the CD? you may need service pack 3 to install on SATA hardware because of missing SATA drivers on the other service packs.

---

### Post by dusanmil on 2011-08-22
I have XP SP3 on my disk. How can I check if its SATA or IDE hardware? I BIOS there's one entry where is written:

SATA native mode : Disabled

---

### Post by sanderd17 on 2011-08-22
> **dusanmil said:**
> How can I check if its SATA or IDE hardware? 

Open your computer and check if the drives are connected with SATA fiches or with IDE fiches:
[IDE]("http://www.google.be/search?q=SATA+fiche&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&ie=UTF-8&tbm=isch&source=og&sa=N&hl=nl&tab=wi&biw=1600&bih=778#um=1&hl=nl&client=firefox-a&rls=org.mozilla:en-US%3Aofficial&tbm=isch&sa=1&q=ide+cable&oq=ide+cable&aq=f&aqi=g1&aql=&gs_sm=e&gs_upl=3633l5186l0l5385l10l10l0l3l3l2l264l1031l3.2.2l7l0&bav=on.2,or.r_gc.r_pw.&fp=6bf06f5ee068a29a&biw=1600&bih=778")

[SATA]("http://www.google.be/search?q=SATA+fiche&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&ie=UTF-8&tbm=isch&source=og&sa=N&hl=nl&tab=wi&biw=1600&bih=778#um=1&hl=nl&client=firefox-a&rls=org.mozilla:en-US%3Aofficial&tbm=isch&sa=1&q=sata+cable&oq=sata+cable&aq=f&aqi=g1&aql=&gs_sm=e&gs_upl=1264l1422l4l1690l2l2l0l0l0l0l249l456l2-2l2l0&bav=on.2,or.r_gc.r_pw.&fp=6bf06f5ee068a29a&biw=1600&bih=778")

The difference is quite clear.

---

### Post by dusanmil on 2011-08-22
Its actually Laptop, HP Compaq 6820s, but under specs I found that inside is SATA Drive.

---

