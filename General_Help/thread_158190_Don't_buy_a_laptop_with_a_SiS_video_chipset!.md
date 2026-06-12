---
title: "Don't buy a laptop with a SiS video chipset!"
date: 2006-04-10
forum: General Help
---

### Post by brallan on 2006-04-10
I bought an  [ASUS Z92 laptop ]("http://wiki.ubuntu.com/LaptopTestingTeam/AsusZ92U?highlight=%28ASUS%29")with a SiS760 after trying it out with a breezy liveCD to be sure it would work with linux, and everything seemed fine, until I tried to run programs (like stellarium) which use OpenGL drivers, and it seems there is no luck to be had.

AAAARGH! anybody wanna buy a laptop? 

Perhaps I being premature, but [Thomas Winischhofer]("http://www.winischhofer.net/sisdri.shtml") says there's no Direct Rendering Support for any of the following chipsets...

SiS315 SiS550 SiS650 SiS651 SiS740 SiS661 SiS741 SiS760 SiS330

---

### Post by slipk487 on 2006-04-10
is it a 3d graphis card or just a graphics accrelator

---

### Post by Jefim on 2006-04-11
Yeah, everything's right. I had a PC with SiS video and I assure everyone, that this is a bad choise. You will get no 3D support since there are no good drivers. This was very disappointing when I decided to try installing Xgl and compiz.

---

### Post by lynnhavencc on 2006-04-18
that sucks.... then thats the problem i have here
I did find drivers from SIS  but dont know how to install a BIN  file

---

### Post by brallan on 2006-04-19
[QUOTE=slipk487]is it a 3d graphis card or just a graphics accrelator[/QUOTE]
I'm not really sure. One of the particular problems with the SiS760 is that the memory is shared between the processor and video card, if I understand it right, and do hooking up extra screens can be problematic, even in wondows. How would I go about finding out the answer to your question? If anyone can have a look at [Thomas's site]("http://www.winischhofer.net/sisdri.shtml") maybe they can tell me...

---

### Post by aaronjlwebb on 2006-07-18
Sorry guys - I know this isn't Ubuntu related, but I have looked all over the web and this is the first time i've heard of anyone having a similar problem with an SiS laptop card!  I'm running windows (I have to, much to my chagrin) and can't get multiple monitors working right - trying to use both monitors at once always results in both monitors getting all squashed up.

Anyway, just wondering if anyone has seen any other people with this problem anywhere on the web!

Sorry again to post here,

A

---

### Post by mithion on 2006-07-24
> **lynnhavencc said:**
> that sucks.... then thats the problem i have here
I did find drivers from SIS  but dont know how to install a BIN  file

Could you post the link where you found these drivers?  Maybe there is a way to do something with those bin files.  It's trully frustrating that SiS isn't doing any effort at all to better support it's hardware in linux.

---

### Post by gos1 on 2007-03-14
I have a laptop with sis video card too and still cannot install graphic devices properly. 
 So my suggestion is to send a mail with all of our names and serial number of graphic devices  under it and send it to sis. Because companies like NVidia provides full support to linux and i think SIS should do the same too .  So if you are with me please send me a mail from [email]cbaykam@gmail.com[/email] and I will send you the mail template . I think it would be the best way of getting proper support...

---

### Post by Spyder on 2007-03-19
[QUOTE=brallan]
Don't buy a machine with a SiS 315/550/650/651/740/661/741/760/330 video chipset!
[/QUOTE]

I second this whole heartedly

---

### Post by slayerboy on 2007-03-19
Generally, you're going to have problems if you are buying a machine with an integrated video card.  You're best to stick with ATI/NVIDIA, but even then YRMV.

This is the whole reason why I've been holding off on getting a laptop for the last few months.  New hardware + Linux = unusable hardware for at least 6 months generally.  It's getting better, but not great.  Then again, Windows is proving to be the same way.

Are you able to get a different graphics card?  Probably very unlikely without switching motherboards, but worth a shot.

---

### Post by Henry Rayker on 2007-03-19
I'm in about the same boat, only I don't really mind whatsoever. My laptop is strictly for school work and the like...as such, Beryl isn't needed (and I've never encountered anything else that needed accelerated graphics).

---

