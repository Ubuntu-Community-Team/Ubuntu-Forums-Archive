---
title: "Ubuntu won't Start"
date: 2010-11-28
forum: General Help
---

### Post by saharasaidi on 2010-11-28
I run Ubuntu on a partition with Vista. I was running Ubuntu, and all of a sudden, my computer shuts off. I turn it back on, choose Ubuntu, then the screen goes black. Help! Vista runs just fine.

---

### Post by sikander3786 on 2010-11-28
Is it installed inside Windows using the Wubi installer? Did you recently install some updates?

---

### Post by saharasaidi on 2010-11-28
Yes on both counts.

---

### Post by sikander3786 on 2010-11-28
See this.

[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

---

### Post by saharasaidi on 2010-11-28
So I guess I was not running Ubuntu as a partition but rather as an application of windows. I tried following bcbc's directions, but I think I was missing something vital. In any case, I uninstalled ubuntu and I'm now re-installing as a partition.

---

### Post by sikander3786 on 2010-11-28
> I uninstalled ubuntu and I'm now re-installing as a partition.

Good Luck for that :-)

Yes that is the better and the long-term solution.

Please feel free to ask if you need any kind of help :D

---

### Post by hyper_klev on 2010-11-28
i updated my linux this morning and have the problem.. simply it just restarts itself everytime i select to load Ubuntu.

now, i'm not a computer genius and i use Linux because i enjoy using it..

i just wish people could put "how to fix this" instructions in simple terms so i know how to fix..

i had a problem with my linux and an update a while ago and lost everything.. 

i only have windows on my computer because i can't get skype to work with linux..

Is some one able to Translate that above link to something a little more simple for me please?

---

### Post by sikander3786 on 2010-11-28
> **hyper_klev said:**
> i updated my linux this morning and have the problem.. simply it just restarts itself everytime i select to load Ubuntu.

now, i'm not a computer genius and i use Linux because i enjoy using it..

i just wish people could put "how to fix this" instructions in simple terms so i know how to fix..

i had a problem with my linux and an update a while ago and lost everything.. 

i only have windows on my computer because i can't get skype to work with linux..

Is some one able to Translate that above link to something a little more simple for me please?
You too have installed Ubuntu inside Windows using Wubi?

---

### Post by hyper_klev on 2010-11-28
> **sikander3786 said:**
> You too have installed Ubuntu inside Windows using Wubi?

Yes i Have.. Usuing windows at the moment

---

### Post by sikander3786 on 2010-11-28
> **hyper_klev said:**
> Yes i Have.. Usuing windows at the moment
Which version of Ubuntu is that and did you upgrade it to another version or just did the regular updates?

Regarding simple terms, everything in this thread seems pretty self explanatory.

[http://ubuntuforums.org/showpost.php?p=10159040&postcount=5](http://ubuntuforums.org/showpost.php?p=10159040&postcount=5)

Please go through the post and then I might be able to answer the queries regarding that.

Remember, the real Wubi expert is **bcbc**. I would just try to explain their post up to my knowledge.

---

### Post by hyper_klev on 2010-11-28
i think i have 10.04.. not 100% sure

it was just a regular update...

i don't have a CD rom on my laptop and can't run the LiveCD :S

no i didn't do the 10.04 to 10.10 update so i guess i can't do the wubildr file swap..

---

### Post by sikander3786 on 2010-11-28
If you've got a USB drive and your machine is capable of booting that, see here.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

Yes if you didn't upgrade, you only need to edit grub.cfg as mentioned on the linked post.

---

### Post by linguine89 on 2010-11-28
Hi- I'm having a similar problem. I recently updated my grub and restarted my netbook. After the restart my grub disappeared and I can not boot at all. I have a dual OS Win 7 along with 10.10 netbook remix and neither of them are booting. 
I've booted from my external HD and trying to fix the grub. 
Any suggestions ???
Thanks, Matilda

---

### Post by hyper_klev on 2010-11-28
now just to remember where i have put my USB stick :S

---

### Post by hyper_klev on 2010-11-28
i think i might have 9.10... just found an old ISO file in windows from where i installed Ubuntu to begin with. 

how can i tell what version of Ubuntu i actually have? through windows..

---

### Post by linguine89 on 2010-11-28
Reinstalled ubuntu, seems to be ok now

---

### Post by sikander3786 on 2010-11-28
> **linguine89 said:**
> Reinstalled ubuntu, seems to be ok now
Good Luck for the new install :-)

When updating next time, make sure you don't update any package related to grub, grub-common, grub-pc etc or you might be in the same trouble again ;-)

---

### Post by hyper_klev on 2010-11-28
i'll remember to stay clear of grub updates too..

Just out of interest..

if i was to install the newest version of Ubuntu via Wubi.. would it wipe my other version of Ubuntu or could have them both? 

PS i am currently running from the USB stick with Ubuntu 9.10 netbook edition

---

### Post by sikander3786 on 2010-11-28
> if i was to install the newest version of Ubuntu via Wubi.. would it wipe my other version of Ubuntu or could have them both? 

I haven't tried that, so can't actually say if that will wipe the existing one or not.

But I'd recommend a proper dual boot if you want it as a long term solution.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by hyper_klev on 2010-11-28
> **sikander3786 said:**
> I haven't tried that, so can't actually say if that will wipe the existing one or not.

But I'd recommend a proper dual boot if you want it as a long term solution.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

that links recomends backing up everything.. which is in Ubuntu, and i can only access it if i boot from my USB stick..my only USB stick..

:( last time i had a problem with my update i lost everything.. photos, important documents, MP3's, Movies.. the lot..

My wife is telling me to go and use Windows saying linux is crap and un-realiable.. but i don't like windows, and the only time i have a problem with linux is when it updates..

---

### Post by sikander3786 on 2010-11-28
> the only time i have a problem with linux is when it updates..

Update problems with a proper install are very rare. Wubi gets messed up with nearly every update, I agree.

You can also move your current Wubi install to a separate partition.

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

---

### Post by hyper_klev on 2010-11-29
how can i access my Linux files to back up my stuff before playing around with partitions? i have alot of important files and lots of photos of my daughter in there....

---

### Post by hyper_klev on 2010-11-30
well oddest thing just happened..

i haven't actually tried anything to fix it and all of a sudden it's fixed :S

i'm going to back up everything and do a proper Ubuntu install with the lastest version..:popcorn:

---

