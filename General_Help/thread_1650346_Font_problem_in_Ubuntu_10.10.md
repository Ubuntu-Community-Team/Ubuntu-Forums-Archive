---
title: "Font problem in Ubuntu 10.10"
date: 2010-12-21
forum: General Help
---

### Post by Mick21367 on 2010-12-21
Hi,
I've been having an intermittent problem with font degredation in Ubuntu 10.10 more or less since I upgraded back in October. I've attached a couple of screenshots which may help to illustrate the problem better than I can. . I've been meticulous in updating the system, hoping that it would go away, but ot no avail. My setup is fairly standard, (P4D @ 3.2GHZ, 1GB RAM, Dual boot with XP, ATi 9600 Graphics Card (AGP) running off the standard drivers (not the ATi ones - they won't work with such an old setup). Compiz desktops effects are enabled. I had no problem at all with 10.04 or 9.10 (both of which were upgraded 'live', i.e. over the internet, rather than performing a fresh install), with exactly this setup. I can (temporarily) fix this by logging out, restarting X, or fiddling with the font properties in Appearances, but sooner or later it comes back to bug me. Does anyone have any ideas as to what is causing it, and how I can fix it?

Mick

---

### Post by dl1000v on 2010-12-21
I've got the same problem and have been struggling to get it fixed since about October as well on a fresh install of 10.10. I've searched quite a bit and haven't found anything that fixed it. Changed fonts, sizes, disabled compiz, etc, nothing has helped. I'm using an ATI Radeon Mobility HD 4650 card without the proprietary drivers. The proprietary drivers actually make it worse. I run fine for about a day, then it progressively gets worse until I have to reboot because I can't read anything. In addition, sometimes my font color will randomly change to the same color as the background, making text invisible. If you highlight the text you can see that it is in fact there. This mostly occurs in Pidgen and the terminal, but sometimes in evolution and Open office documents. I'd be very interested in some tips to fix this!

---

### Post by amusis on 2011-01-01
me too, i have changed all the font so the problem seem to be partial solved but not in firefox, i have updated today( 1/1/11) so, i have search but seem that few people have this problem and they are all here( O.O? possible?).

---

### Post by lidex on 2011-01-01
This looks exactly like a thread I was just working. Have a look here:
[http://ubuntuforums.org/showthread.php?t=1648407](http://ubuntuforums.org/showthread.php?t=1648407)

BTW, it's not the fonts.

---

### Post by Mick21367 on 2011-01-03
Hi Lidex,
Thanks for the reply - I've followed the post for the nomodeset option (your post on page 3 of the thread). ATM the problem seems to have gone away :p. I'll report back here in a couple of days to let you all know how it's going.
Just for info, the GRUB_CMDLINE_LINUX line in my GRUB file held the value =" vga=769". I changed it anyway (after making a back up, of course!!). It seems to have caused a couple of problems with Cairo-Dock and the Sysmonitor Screenlet, but I'm a lot less concerned about those than unreadable text!
Thanks again for posting
Mick

---

### Post by lidex on 2011-01-03
OK, sounds good so far then. Something you may want to look into is the r300 gallium driver - it may help with your other issues. From what you've posted it looks like your graphics chip is supported. You will also find info about tweaking the driver which may be all you need:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Mick21367 on 2011-01-05
Hi All,
Well, after two days of fairly intensive use, the font problem seems to be solved - at any rate I haven't had any problems since I changed the GRUB file. For anyone else having the same problem, and who wished to try this fix, please follow the link in lidex's post - go to Page 3, and then follow the next link to another post by ELoXL. 
A quick summary is:-
Edit the GRUB file located at etc/default/grub (after making a backup!!)
change the value in the line GRUB_CMDLINE_LINUX to "nomodeset". It should now look like this:-
GRUB_CMDLINE_LINUX="[COLOR=Black]nomodeset[/COLOR]"
save the file
Update grub (sudo update-grub)
However, I would strongly advise following the links / discussions.
Many, many thanks to lidex / ELoXL / brumorino (referenced in ELoXL's post).

Mick

PS Thanks, lidex, for the heads-up re the gallium driver. I've switched to it (well, I think I have! I'm still quite new at this, even after five years!!). It seems to have helped a bit, though I've also switched to the no-OpenGL Cairo-Dock, which has calmed that down.

---

### Post by amusis on 2011-01-08
seguendo il link non l'ho trovato ma grazie al tuo riassunto funziona tutto, grazie mick

---

### Post by wik+ on 2011-01-12
> **lidex said:**
> OK, sounds good so far then. Something you may want to look into is the r300 gallium driver - it may help with your other issues. From what you've posted it looks like your graphics chip is supported. You will also find info about tweaking the driver which may be all you need:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Thanks, I've had exactly the same problem and switching to ati driver solved issue.

I simply entered the following commands and viola, after restart everything works just fine:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch)

p.s.
RS880 Radeon HD 4250

---

