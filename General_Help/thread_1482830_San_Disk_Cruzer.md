---
title: "San Disk Cruzer"
date: 2010-05-14
forum: General Help
---

### Post by wojox on 2010-05-14
Anyone know how to format and wipe all the preinstalled stuff of a San Disk Cruzer in linux?

---

### Post by finlost on 2010-05-14
I think I hit the del key.  It has been many years though.  Have you checked the properties to ensure they are not read only files/folders?

---

### Post by kid1000002000 on 2010-05-14
run gparted on your disk. there are many options there to do what you want.  just make sure you wipe the right disk so you don't loose anything important!!

---

### Post by wojox on 2010-05-14
> **finlost said:**
> I think I hit the del key.  It has been many years though.  Have you checked the properties to ensure they are not read only files/folders?

I didn't even think of that. Seems so simple, but no it didn't work. It belonged to root, so I **gksudo nautilus** but no go. The delete, move to trash and mv are all greyed out.

---

### Post by wojox on 2010-05-14
> **kid1000002000 said:**
> run gparted on your disk. there are many options there to do what you want.  just make sure you wipe the right disk so you don't loose anything important!!

Tried that. Gparted didn't want anything to do with it.

I tried formatting from the Start Up Disk Creator as well.

---

### Post by DJonsson2008 on 2010-05-14
I ran GParted & reformated a San Disk Cruiser USB 4GB. 

Then I unplugged my HD, rebooted with the Xubuntu install CD, and installed onto the USB Flash disk just like it was a hard drive.

Actually you may not need to run Gparted if you simply do the
formating via the install CD process. Which I landed up doing
or redoing anyways selecting use entire disk for ubuntu option.

This worked for 4GB Cruiser, Xubuntu boots a little slow but
is completely functioning.

---

### Post by uRock on 2010-05-14
> **wojox said:**
> Anyone know how to format and wipe all the preinstalled stuff of a San Disk Cruzer in linux?
I had a great answer until I seen the "in Linux" part of your question.

---

### Post by wojox on 2010-05-14
> **uRock said:**
> I had a great answer until I seen the "in Linux" part of your question.

I do have my wife's Vista machine.

---

### Post by wojox on 2010-05-14
> **DJonsson2008 said:**
> I ran GParted & reformated a San Disk Cruiser USB 4GB. 

Then I unplugged my HD, rebooted with the Xubuntu install CD, and installed onto the USB Flash disk just like it was a hard drive.

Actually you may not need to run Gparted if you simply do the
formating via the install CD process. Which I landed up doing
or redoing anyways selecting use entire disk for ubuntu option.

This worked for 4GB Cruiser, Xubuntu boots a little slow but
is completely functioning.

I'll try that.

---

### Post by DJonsson2008 on 2010-05-14
Another method is boot the Sandisk on a Windows machine and delete the partitions there. Gparted did though delete the partitions for me and allowed reformating, when I was logged on as root.

---

### Post by uRock on 2010-05-14
> **wojox said:**
> I do have my wife's Vista machine.
I think on XP and 7 there is the format option when you right click. You might lost the U3 software when doing so. Also Windows might just ignore those Linux permissions and delete the files for you.

---

### Post by wojox on 2010-05-14
> **uRock said:**
> I think on XP and 7 there is the format option when you right click. You might lost the U3 software when doing so. Also Windows might just ignore those Linux permissions and delete the files for you.

It's formatted to Fat32. I want that U3 software off it right?

---

### Post by DJonsson2008 on 2010-05-14
If you are going to use this as a boot USB disk and you have backed up what you need from it, delete all the partitions on the Sancruzer, would be my advice. I was very very happy to get rid of the U3 software. If I ever use it again for a standard storage flash disk I'll likely just format it to FAT. 

For now though my San Cruzer is a dedicated USB boot drive, 
if that is your goal then remove all of the original U3 partitions, and reformat just like any ubuntu install on a
fresh HD.

---

### Post by mc4man on 2010-05-14
Best way to remove the U3 partition (isofs) is in windows with either method 1 or 2

[http://kb.sandisk.com/app/answers/detail/a_id/2550/sno/0](http://kb.sandisk.com/app/answers/detail/a_id/2550/sno/0)

---

### Post by standingwave on 2010-05-14
U3-Tool: [http://packages.ubuntu.com/lucid/u3-tool](http://packages.ubuntu.com/lucid/u3-tool)

---

### Post by wojox on 2010-05-14
Well I just fired up Vista and that took care of that. 

Thanks a lot my friends.

---

