---
title: "device-mapper: remove ioctl failed: Device or resource busy Command failed"
date: 2011-02-02
forum: General Help
---

### Post by Keypel on 2011-02-02
[IMG]http://img51.imageshack.us/img51/614/screenshotp.gif[/IMG]

How do I find out "why" the mounted virtual drive is busy? All windowed programs are closed out. I assume a background program is using the resource? 

All was fine until about a week ago. Now I'm ready to re-install the whole system just to fix this problem but I thought I would seek help (understanding) from the experts here first.

---

### Post by Keypel on 2011-02-03
Ok, I re-did a fresh Ubuntu 10.10 install and it fixed the problem but when I installed the 264 updates the problem is back.

How do I find out which update is causing the problem? Install them one by one until the problem occurs again? What's the best way to trouble shoot this?

---

### Post by nosehat on 2011-02-07
I am experiencing the same problem, and I would also like to understand how to go about troubleshooting it.

This seems to me like a good opportunity to learn the way Ubuntu handles open files, etc.

Where would I start to troubleshoot this?

---

### Post by Keypel on 2011-02-07
With a fresh 10.10 install it works but after the 264 updates it fails.

Instead of installing the 264 updates at once I just installed the first 30 and the problem happened again. Problem is I didn't note which updates I installed. 

All I know so far is it doesn't seem to be kernel related.

Is there some sore to update history I can go through? At least I could limit the problem to one of 30 updates instead of 264+

There is a workaround for the problem although not the best one. You can format the TC container in anything "but" NTFS. 

example: make a fat or ext3 then mount both and transfer everything to the other volume and delete the NTFS one.

---

### Post by sauferkel on 2011-04-07
i've got the same problem, also after installing the updates.
but it helps to first unmount the folder, and then dismount it via truecrypt

sudo umount /media/truecrypt1  was it for me

---

### Post by nosehat on 2011-04-11
> **sauferkel said:**
> i've got the same problem, also after installing the updates.
but it helps to first unmount the folder, and then dismount it via truecrypt

sudo umount /media/truecrypt1  was it for me

Sauferkel, thanks!  I can confirm this works.  Apparently it was just a permissions issue, which generated this unhelpful error message.

If the original poster is still around, this can be marked Solved.

---

### Post by Keypel on 2011-04-11
> **nosehat said:**
> Sauferkel, thanks!  I can confirm this works.  Apparently it was just a permissions issue, which generated this unhelpful error message.

If the original poster is still around, this can be marked Solved.

Yes, Still around. :D

I could have swore I tried sudo unmount but if you guys say it's solved I'll mark it.

I solved it a different way by using a ext3fs instead of ntfs so I can not confirm if this works.

---

### Post by WatsonDE on 2011-04-12
I hope this isn't reviving a dead post, but I had this problem no matter what my encrypted volumes were formatted as, even after I dismounted all TC volumes, when I tried to do the "safely remove drive" thing with the LUKS container the TC containers are stored in, I got the same message

---

### Post by d_darlac on 2011-05-16
both solutions worked for me - but switching to ext4 appears to be a permanent solution

---

### Post by Keypel on 2011-05-18
> **d_darlac said:**
> both solutions worked for me - but switching to ext4 appears to be a permanent solution

yup, that's what I ended up doing.

---

