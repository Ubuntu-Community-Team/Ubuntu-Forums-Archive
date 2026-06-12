---
title: "Warning ! Be careful when u are in dual boot !"
date: 2012-01-13
forum: General Help
---

### Post by nipunshakya on 2012-01-13
Hi. I don't know where to post this kinds of threads, but i would like to address a problem.

30 minutes ago, i tried to make my unity look a bit comfortable. Due to aut-hide feature, i was annoyed of clicking several links for accessing even a single app. So i decided to go to the configuration editor, and then i set the value(don't remember of what) to 0. Anyways, my work was done, there was no autohide function of Unity Bar.

But then, i booted to my windows 7(I have a dual-boot on my pc ,each os on different partition). Bam ! windows didnt boot, instead restarted. 
I again selected windows 7 and then it prompted me with startup repair.
After roughly 10 minutes of anxious waiting, windows 7 booted. 
The machine was restored to some early point(according to the startup repair solution). 

Between these events, i totally don't know what happened. All i did was set a value to 0 using the configuration editor and that changed the whole way of how my machine boots. 
Although everything is fine now, i would really like to know if anyone has an answer to this error or problem.:)

Thanks
Regards, WinuxUser.

---

### Post by TeoBigusGeekus on 2012-01-14
The incident is almost with certainty irrelevant with the fact that you changed a value in the unity configuration.
You should look for its cause somewhere else...

---

### Post by Habitual on 2012-01-14
> **teobigusgeekus said:**
> ...you should look for its cause somewhere else...

+1

---

### Post by bluexrider on 2012-01-14
What you did in Ubuntu has no bearing on how your Windows 7 started. Separate OS's. The only commonplace would be using the bootloader.

I don't see the relationship here.

Glad you got back a working machine

---

### Post by foska on 2012-01-14
Yup. Widows 7 does not play nice when it comes to dual booting

---

### Post by Frogs Hair on 2012-01-14
See this page . [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by nipunshakya on 2012-01-14
One question gurus, i guess changing some values affected the way that the grub loads. Can that be a reason for windows 7 refusing to boot? Please correct me if i got it wrong.

Regards,WinuxUser

---

### Post by nipunshakya on 2012-01-14
> **bluexrider said:**
> What you did in Ubuntu has no bearing on how your Windows 7 started. Separate OS's. The only commonplace would be using the bootloader.

I don't see the relationship here.

Glad you got back a working machine

Sir, just a simple question. Can changing Configuration editor's values affect the way Ubuntu loads itself?

If yes, i guess that windows 7 will also be affected at some point because it loads via Grub2, isnt it?(correct me if i get it wrong.)

If no, i would like to get deep into this problem. Maybe sevenforums.org might be of some help regarding this topic.

Thanks.
Regards,WinuxUser

---

### Post by jasonrisenburg on 2012-01-14
changing of the Unity bar is alot easier and safer in Compiz. I have to dual boot on some computers that my wife uses. I have not had a problem and the first thing I do is take it off dodge and make it auto hide and reduce the size of the bar to 32. 
 I do not think that the 2 systems connect on that level.

---

### Post by jasonrisenburg on 2012-01-14
I wish there was a way to like comments

---

### Post by xyzzyman on 2012-01-14
> **WinuxUser said:**
> Sir, just a simple question. Can changing Configuration editor's values affect the way Ubuntu loads itself?

If yes, i guess that windows 7 will also be affected at some point because it loads via Grub2, isnt it?(correct me if i get it wrong.)

If no, i would like to get deep into this problem. Maybe sevenforums.org might be of some help regarding this topic.

Thanks.
Regards,WinuxUser

We'll say the same thing over there (Those of us that are on both), that what you told us you changed would have nothing to do with Windows 7 or grub2.

---

### Post by bluexrider on 2012-01-14
> **WinuxUser said:**
> Sir, just a simple question. Can changing Configuration editor's values affect the way Ubuntu loads itself?

NO. Changing the Configuration Editor values effects the settings and applications AFTER the boot process has finished, not before nor during. 

The Configuration Editor can be accessed WITHOUT sudo permission and therefore effects ONLY user settings. NOT SYSTEM SETTINGS. Changes within the Configuration Editor are reversible using USER permissions. 

> If yes, i guess that windows 7 will also be affected at some point because it loads via Grub2, isnt it?(correct me if i get it wrong.)Somewhat Correct! Windows DOES load via GRUB however GRUB does not have the ability to effect changes in which Windows OS operates. If Windows fails to load during GRUB its because the MBR code was not changed to point to the boot loader in Ubuntu. 

Read >>>>>Master Boot Record and Boot Manager
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Hope this clears things up

---

### Post by nipunshakya on 2012-01-15
> **bluexrider said:**
> NO. Changing the Configuration Editor values effects the settings and applications AFTER the boot process has finished, not before nor during. 
Maybe a reason could be that i didn't reboot to ubuntu and booted straight to  to windows 7 after i made changes in the Configuration Editor... Maybe that might be a reason that grub couldn't adjust itself to the new settings and so a direct boot of windows 7 led to misplace of stuffs in the MBR. ???

> **bluexrider said:**
> The Configuration Editor can be accessed WITHOUT sudo permission and therefore effects ONLY user settings. NOT SYSTEM SETTINGS. Changes within the Configuration Editor are reversible using USER permissions. 
I got a bit confused about loading the unity bar here. If i am the only administrator of the machine and i edit the Editor using sudo in the terminal, my settings might be changed to user level. However, when ubuntu prepares to load at next startup, won't it look if i had made any changes to the way my screen loads at next session?? I guess if it doesn't look, then the settings i implied on my machine also wouldn't have been effective, isn't it? 

> **bluexrider said:**
>  If Windows fails to load during GRUB its because the MBR code was not changed to point to the boot loader in Ubuntu. 

Thats what i was wanting to say. I didn't boot straight to ubuntu after i changed the values at Configuration Editor. Instead, i went directly to windows 7. So i wonder that probably the settings messed some addresses and so MBR got a bit disturbed and caused to repair startup for windows ? ? ? 


I read the link prescribed. There at the MBR section of the link says GRUB installs main parts of the boot loaders inside Ubuntu. So doesn't that mean somehow windows 7's startup process is linked to ubuntu? Or did i get things wrong?

Please forgive me for asking too much, but this is the only way to clear up my head.

Thanks.
Regards,WinuxUser.

---

### Post by Paqman on 2012-01-15
> **WinuxUser said:**
> Maybe a reason could be that i didn't reboot to ubuntu and booted straight to  to windows 7 after i made changes in the Configuration Editor... Maybe that might be a reason that grub couldn't adjust itself to the new settings and so a direct boot of windows 7 led to misplace of stuffs in the MBR. ???


You didn't make any changes to Grub. As mentioned above, the changes you made to your interface do not affect the boot process at all. Your individual user settings are applied when you _log in_, by which time the boot process is long finished.

In short what happens is:
[list=1] 
[*]Grub starts
[*]Loads kernel
[*]Kernel brings up all the parts of the system
[*]You log in and your settings are applied. 
[/list]

By the time you're logging in Grub has done it's thing and isn't running at all. It's only used for the initial part of the boot process.

> 
Thats what i was wanting to say. I didn't boot straight to ubuntu after i changed the values at Configuration Editor. Instead, i went directly to windows 7. So i wonder that probably the settings messed some addresses and so MBR got a bit disturbed and caused to repair startup for windows ? ? ? 


Something went wrong with Windows, but it wasn't any changes that you made in Ubuntu. It's a coincidence.

---

### Post by ottosykora on 2012-01-15
> **WinuxUser said:**
> One question gurus, i guess changing some values affected the way that the grub loads. Can that be a reason for windows 7 refusing to boot? Please correct me if i got it wrong.

Regards,WinuxUser

negative, unity desktop is just one of many programs on your linux partition. In fact it is just a plugin for compiz.
You can have number of desktop environments on your linux. How you configure each of them has no influence on windows, it is the same as if you change a color of your particular desktop, nothing will change on my computer...

The grub does not affect windows at all, the grub will just call up the windows bootloader and this one first does anything with any windows files.
(as grub does  not even load windows directly)

---

### Post by nipunshakya on 2012-01-15
Keeping all those suggestions and gyaan-sharing in my mind, i shall move on to seven forums for this error's help.

Thanks everyone who has helped and shared their knowledge.Thanks for your time.Im marking this thread as [SOLVED]

Regards,WinuxUser

---

### Post by nipunshakya on 2012-01-15
Hi. First off all, welcome to the forum. I don't know about subscriptions to the posts as i usually subscribe by selecting 'Subscribe To This Thread' under Thread Tools. The Thread Tools menu is located at top right corner of the page, just above the first post of this thread. Have u tried subscribing from there? 

If problem persists, try posting your problem under ' Forum Feedback & Help ' section of this forum. This section is dedicated for such helps.

Regards,WinuxUser

---

### Post by gowings83 on 2012-01-15
I had the same kind of issue after mixing with Winblows XP, I went to load XP and it did a chkdsk, no biggie and it's booted straight in since.  I've never had Win7, probably won't for a while, if ever, just thought I'd add in that XP had an issue booting as well.

---

### Post by oldfred on 2012-01-15
Were you hibernating in Windows and used Ubuntu to write anything into the Windows partition?

There also used to be some issues as grub2 was larger than old grub legacy and grub2 used some of the sectors after the MBR for additional boot code (core.img). But some Windows DRM software would also write into those same sectors to hide serial numbers or settings. Grub has been fixed for flexnet but some HP or Dell software also used that same area. But those issues often caused Ubuntu/grub not to boot as Windows overwrote part of grub2's core.img.

Details on how Windows boots, multi-boots and MBR/BIOS boot process in general. 
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by nipunshakya on 2012-01-15
> **oldfred said:**
> Were you hibernating in Windows and used Ubuntu to write anything into the Windows partition?

That was not the case. I did this :
1. Booted Ubuntu, disliked Unity as always. :D Decided to remove auto-hide feature.
2. Changed something in Configuration Editor (Forgot what i did ,sorry. ! :D ) and saw the change take effect.
3. Booted to windows 7**(directly without getting to ubuntu first,its where i have confusions)**. It was at this moment that i got the startup error and had to run the startup repair as windows recommended.
4. Repair succeeded and i got my machine fit and fine.

> **oldfred said:**
> There also used to be some issues as grub2 was larger than old grub legacy and grub2 used some of the sectors after the MBR for additional boot code (core.img). But some Windows DRM software would also write into those same sectors to hide serial numbers or settings. Grub has been fixed for flexnet but some HP or Dell software also used that same area. But those issues often caused Ubuntu/grub not to boot as Windows overwrote part of grub2's core.img.

If those issues caused Ubuntu not to boot, can't the effect be seen as in a reverse order? i.e. ubuntu causing windows not to boot? Sorry if my queries are getting too high. 

> **oldfred said:**
> Details on how Windows boots, multi-boots and MBR/BIOS boot process in general. 
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Still on it. Will Post as soon as i have find something new to share.

Regards,WinuxUser

---

