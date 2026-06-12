---
title: "Ubuntu not finding Win7"
date: 2011-06-03
forum: General Help
---

### Post by InfectedPhreak on 2011-06-03
I'm trying to duel-boot Win 7 and Ubuntu. When I go into the installation of Ubuntu it tells me "No other Operating Systems Found" and tells me to erase disc, or do something else. Now, I'm not the smartest when it comes to dealing with partitions and all of that. So my question is, how do I fix this? I want to alongside Win 7 with Ubuntu.

---

### Post by linuxinstalledfromhdd on 2011-06-03
[http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/](http://cinderbox.net/2011/03/10/how-to-recover-grub2-after-windows-installation/)

Give that a try

---

### Post by Rubi1200 on 2011-06-03
Hi and welcome to the forums InfectedPhreak :)

Before you do anything else, open a terminal on the LiveCD/USB and run the following command:

```
sudo fdisk -l
```

(lowercase L not 1)

Post the output here please.

Thanks.

---

### Post by InfectedPhreak on 2011-06-03
I originally started doing this with the alongside with wubi, and that gave me the error. Now I've uninstalled, and reinstalled the wubi about 5 times now. Also, I've tried live disc quite a few times and when I go to the partition section of the installation it gives me the same thing "no root defined", or just doesn't let me install it. 

Now after doing all of that, I pop the live CD in and it gives me "panic occured: now using text console" or something along those lines. So, I have no idea what I've done to get it to do this. Think I'm about ready to just give up.

Would it be easier to reformat, and then install Ubuntu first and then Windows 7?

---

### Post by Rubi1200 on 2011-06-03
A first step to helping you figure this out would be to post the output of the command I asked for please.

Also, system specifications would be good too, especially RAM and graphics card.

---

### Post by InfectedPhreak on 2011-06-03
Well, I can't even access the terminal to give you such information. I said in my post when I try the live disc it gives me "Panic occurred: switching to text console". 

RAM 4GB, Graphics: nVidia GTX 460.

---

### Post by Rubi1200 on 2011-06-03
Two possibilities to look at:

check the integrity: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

burn to CD at the lowest speed: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

The other thing to check is go into Windows and take a screenshot of how Windows sees your disks from the Disk Management utility.

---

