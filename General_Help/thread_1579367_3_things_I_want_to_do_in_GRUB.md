---
title: "3 things I want to do in GRUB"
date: 2010-09-21
forum: General Help
---

### Post by garner_nc on 2010-09-21
1. Change default boot timeout to 30 seconds from 10.
2. Change default boot system to Windows XP
3. Change Grub boot menu so Windows XP is at top.

I do NOT find the changes made to the new GRUB 2 system advantageous to ME in the least. On the old GRUB I'd have these changes made in 2 minutes  simply editing a text file and saving it.

If anyone cares to provide any insight on how the new configuration is better/easier for the average user I'd sure like to hear it.

Is it possible to downgrade to a previous version? Are there other boot loader options? 

Ubuntu 10.04.1 I386

All the Best,
D. White

---

### Post by drs305 on 2010-09-21
1 and 2 can still be accomplished with StartUp-Manager - see the "SUM" link in my signature line. 

If you would prefer to edit the configuration files, how to edit them is provided in the link "G2-Tasks", which details how to accomplish 5 of the basic changes users might make to Grub2.

You can do both in about 30 seconds if you know the commands - Grub2 is just different and it takes a bit of time to learn - just as Grub legacy did. Hint: "gksudo gedit /etc/default/grub /boot/grub/grub.cfg"; then "sudo update-grub".

Reordering the sequence of menuentries is probably best done by creating a custom menu. If you run and post the bootinfo script by *meierfra* I can put one together for you in about a minute.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by Jesus_Valdez on 2010-09-21
The Grub 2 Guide 

[http://gutsywww.ubuntuforums.org/showthread.php?t=1195275](http://gutsywww.ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Quackers on 2010-09-21
drs305 I've just been using your guide to re-install grub2 ---- twice :-)
Thanks to you sir!

---

### Post by drs305 on 2010-09-21
> **Quackers said:**
> drs305 I've just been using your guide to re-install grub2 ---- twice :-)
Thanks to you sir!

Twice? - I don't know if that's a dig or a compliment.  :shock:

But we'll leave this thread for the OP...

---

### Post by garner_nc on 2010-09-21
I'm really sorry but it seems the GRUB developers took a really beautiful, simple, easy to manage system and turned it into .................. I'd really rather not use that term.

I don't see the new system as an improvement.

I may just go back to 9.10, where things are simple and easy. 

Thanks.

---

### Post by Dustin2128 on 2010-09-21
> **garner_nc said:**
> Are there other boot loader options? 
LILO's been largely replaced by grub (except in slackware), but it's still actively developed; last release was less than 3 months ago.

---

### Post by drs305 on 2010-09-21
> **garner_nc said:**
> I'm really sorry but it seems the GRUB developers took a really beautiful, simple, easy to manage system and turned it into .................. I'd really rather not use that term.

I don't see the new system as an improvement.

I may just go back to 9.10, where things are simple and easy. 

Thanks.

I hope I didn't come off as being curt with you. The developers decided that Grub needed an overhaul. Whether we want it or not, they are not devoting any more time/effort on Grub legacy and have moved on to Grub2. You can certainly use Grub legacy for a bit longer if you wish.

For accomplishing the basics, though, there is a bit to learn but not much. Many users, including me, will be very happy when a simple GUI app is released which does all the basics in a comfortable manner.

There is seldom only one way to accomplish things in Linux, which is good. We are here to help if you decide to pursue Grub 2.

---

### Post by garner_nc on 2010-09-21
drs305,

   You did not come off as curt. I appreciate your help. Thank You. 

   It just seems the GRUB people decided to put the fuel tank cap under the back seat with a special wrench required to remove it . I learned a long time ago that "new and improved" doesn't always mean "better".

  I got 1 and 2 fixed by editing /etc/default/grub and re-running "update-grub". It seems a shame I have to install another piece of software now (Startupmanager) to simply change the menu order. I'll do it but it really seems a lot more complicated than it used to be.

  Thanks to everyone for their help!

All the Best,
D. White

---

### Post by drs305 on 2010-09-21
> **garner_nc said:**
> It seems a shame I have to install another piece of software now (Startupmanager) to simply change the menu order. I'll do it but it really seems a lot more complicated than it used to be.

  Thanks to everyone for their help!

All the Best,
D. White

Before you run off to install software you don't really want, SUM will not reorder your menu- it will only change the default OS - the one highlighted when and if the Grub menu displays. You can change the order of the menu entries to have Grub2 display Windows first with a custom menu or some serious script editing.

There is another way - renaming /etc/grub.d/30_os-prober to 09_os-prober. That would put the Windows entry first (if you have only one Ubuntu partition). I don't know 100% that there would be no long-term effects of doing this but I believe it will work as you can completely disable the 30_os-prober and things work fine without it.

---

