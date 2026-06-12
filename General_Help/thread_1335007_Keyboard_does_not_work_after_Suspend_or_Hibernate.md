---
title: "Keyboard does not work after Suspend or Hibernate"
date: 2009-11-23
forum: General Help
---

### Post by Kjasontu on 2009-11-23
When I wake my computer up from Suspend or Hibernate my keyboard no longer works and I can not log back in.  I have to restart my computer down to get back in.

I am using the power button to wake my computer up.  My mouse works fine.  I can try to log on as another use or changes my keyboard to another language setup, but I can not get it to respond.  Because I can not use the keyboard to type my password I can not log in and have to restart.

---

### Post by Elaztic on 2009-11-23
Is this after upgrade to Karmic?
I have the same issue for my laptop and as far as I can see several others have the problem as well.
Please post back if anyone finds a workaround.
Will clean install work?

---

### Post by Kjasontu on 2009-11-23
I have not been able to figure it out so far.  It seems like everyone who uses Ubuntu would have the same problem.

---

### Post by harperd on 2009-12-23
Having the same problem. Has there been any progress on this?

---

### Post by levis lover on 2010-01-13
having same problem?
anyone knows how to sort it out?

---

### Post by CompyTheInsane on 2010-01-13
I have the same problem on my PC.

For those who aren't on laptops, is the keyboard that you use a USB keyboard?
If it is a USB keyboard, have you already tried getting around the keyboard issue by disconnecting, then reconnecting the keyboard after resuing from standby/hibernation?

---

### Post by levis lover on 2010-01-14
^^
what if we are on laptops? any help plz.. it is really irritating..

---

### Post by efflandt on 2010-01-14
I have had no issues with suspend or hibernate on any desktop or laptop except an older Compaq Presario V2000.  And that one gives no clue what the issue is.  It is using all standard modules with 32-bit Ubuntu 9.10 except B43 for its BCM4318 wireless.

Initially suspend appeared to try to resume to the gui password prompt, but keyboard and mouse were dead.  The first time I tried hibernate with Bluetooth keyboard/mousepad combo, that worked fine (/var/log/pm-suspend.log showed the "thawing" processes, and everything worked).

Trying suspend again with Bluetooth keyboard/mousepad did not work (ended up in black screen with no backlight and no response).  The suspend was logged in pm-suspend.log, but nothing about waking up.  After that I could no longer recover from hibernate.  It showed the splash screen and something like "Waking...please wait", but then black screened with no response, and no longer anything in pm-suspend.log about thawing.  So I cannot tell if something lurking from failed resume from suspend is interfering with thawing from hybernate.  With no logging about waking up, it is tough to tell what is going wrong.

---

### Post by Jugantor on 2010-02-13
I have been facing the same problem, but I have 'temporarily' resolved the problem. 

Upon starting/booting up/restarting your system, select your ubuntu version and press e to edit. scroll down and add the following after 'quick splash' (leave a space in between) : 
**atkbd.reset** 

Now, press ctrl+x to boot up your system from thereon. Next time you suspend your system, you should be able to use your keyboard upon resuming. 

I am still searching for a permanent solution though. 

Cheers, 
Jug

---

### Post by Nicolas.Perrault on 2010-03-05
Same problem here. I use 64-bit by the way, and my mother uses 32-bit and doesn't have the problem in question. Will this be resolved on Lucid Lynx?

---

### Post by jmkhenka on 2010-04-25
Found a permanent solution!
 Edit /etc/default/grub
and change the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash atkbd.reset"
 and run update-grub, reboot and when you press E in grub you will se  the entry there.


This is with grub2 and on 10.04.

---

### Post by DougInWA on 2010-05-31
Huzzah!  This totally works.  Installed 10.04 on my wife's Sony Vaio after she got some hideous virus on her Win7 install and everything worked, except for the keyboard on wake.  Now that this is working, she may just be amenable to living on a Linux laptop.   :P

---

### Post by MatMan on 2010-06-01
I have the same problem on a HP Pavilion laptop with 10.04

i am interested in this fix that involves editing the grub, but can't seem to?

I typed gedit /etc/default/grub

it opens an empty file, so i guess I am doing it wrong

Can you point me to how to edit grub? (Also, will this change survive upgrades?)

thanks...

---

### Post by MatMan on 2010-06-07
I just found that I don't need to change the grub.

I have a hp pavilion dv2000. Amongst other things, it has a Fn key, which changes the function of the keyboard. Sometimes, the number lock is on when the computer comes out of suspend. Pressing the Fn or Fn+scroll-lock unlocks the num-lock, returning the keyboard to its original state.

Don't know why num-lock is on though

---

### Post by ADani on 2010-06-10
I have the same problem with a Bangho Laptop with Kubuntu 10.04, but I doesn't happen every time it hybernates, maybe 1 in 6 times. Activating num-lock doesn't fix it.
In my case I think it happens when the laptop hybernates for long periods (+5 hours). So far, when woken up on those occasions where the keyboard dies, it fails to ask me for my password, it just goes straight to desktop.
Maybe I can try something on yakuake? I'm quite noob so if anyone has any suggestions I'm all ears.

---

### Post by levis lover on 2010-07-13
> **MatMan said:**
> 
i am interested in this fix that involves editing the grub, but can't seem to?

I typed gedit /etc/default/grub

it opens an empty file, so i guess I am doing it wrong

Can you point me to how to edit grub? (Also, will this change survive upgrades?)

thanks...

Same here .. did you find anything ?

---

### Post by bigtom71 on 2010-07-28
Type Sudo before gedit /etc/default/grub and then your password and you should be able to edit the grub. As for surviving upgrades, it probably won't survive from version to version. Hope this helps.

---

### Post by trackisimo on 2010-07-31
the solution of editing the grub file works for me also on a sony vaio VGN-CS290 laptop

Thanks.

---

### Post by wmalik on 2010-10-06
> **jmkhenka said:**
> Found a permanent solution!
 Edit /etc/default/grub
and change the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash atkbd.reset"
 and run update-grub, reboot and when you press E in grub you will se  the entry there.


This is with grub2 and on 10.04.

This solved my keyboard issue on a Sony Viao VGN-CS26G running Ubuntu 10.04

Thank you very much.

---

### Post by gmonster1st on 2011-02-12
> **jmkhenka said:**
> Found a permanent solution!
 Edit /etc/default/grub
and change the line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash atkbd.reset"
 and run update-grub, reboot and when you press E in grub you will se  the entry there.


This is with grub2 and on 10.04.


Is there a way to attach this to the default menu without having to use the cmdline?

---

