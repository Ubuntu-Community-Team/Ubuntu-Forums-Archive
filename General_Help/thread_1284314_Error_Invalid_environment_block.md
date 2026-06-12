---
title: "Error: Invalid environment block"
date: 2009-10-06
forum: General Help
---

### Post by ChaosChris2009 on 2009-10-06
Ubuntu 9.10 Karmic Koala BETA, GNome 
 
Downloded it fresh off of Ubuntu's main site
 
Have done a fresh install three times, Ubuntu's the primary OS
 
Upon boot-up GRUB makes a sad attempt to load, but fails in turn and gives me this message
 
Error: Invalid environment block
 
This has happened 3 times already!
 
Help, and thanks to anyone who helps

---

### Post by ChaosChris2009 on 2009-10-06
Anyone?

---

### Post by drfox on 2009-10-06
When your GRUB2 menu is up
Press e to edit grub
Remove the line save_env recordfail
Press TAB
Press CTRL+X to boot

HTH

Larry

---

### Post by Akita on 2009-10-06
Same thing just happened to me on a normal boot an hour after a normal shutdown.

The grub menu fix won't work because it's grub giving the error BEFORE there's a menu. Hitting any key just gets a repeat of the error. G2 borked itself. 

Does anybody know recovery procedures for grub2?

---

### Post by dcstar on 2009-10-06
> **Akita said:**
> Same thing just happened to me on a normal boot an hour after a normal shutdown.

The grub menu fix won't work because it's grub giving the error BEFORE there's a menu. Hitting any key just gets a repeat of the error. G2 borked itself. 

Does anybody know recovery procedures for grub2?

Boot off the install CD and mount the drive so you can edit the file.

---

### Post by drfox on 2009-10-06
Karmic developers have made a real mistake by not making a visible grub menu the default. You need to get to a command prompt and edit this file:
/etc/default/grub
with vi - since you won't have a GUI, you won't be able to use gedit or kate
Find this line:
GRUB_HIDDEN_TIMEOUT=0 
and edit it to look like this
#GRUB_HIDDEN_TIMEOUT=0 
and save the file.
The you need to run: 
update-grub
to get the grub2 menu to come up.
If you can't do that with your current configuration, you'll have to use a live CD and chroot to update your grub. 

HTH  Larry

---

### Post by Peter09 on 2009-10-07
Post 3 just worked for me.

---

### Post by Tim_Olaguna on 2009-10-07
> **drfox said:**
> Karmic developers have made a real mistake by not making a visible grub menu the default. You need to get to a command prompt and edit this file:
/etc/default/grub
with vi - since you won't have a GUI, you won't be able to use gedit or kate
Find this line:
GRUB_HIDDEN_TIMEOUT=0 
and edit it to look like this
#GRUB_HIDDEN_TIMEOUT=0 
and save the file.
The you need to run: 
update-grub
to get the grub2 menu to come up.
If you can't do that with your current configuration, you'll have to use a live CD and chroot to update your grub. 

HTH  Larry

This is a real disappointment which provides no usable option for me, apparently.  I was trying to test 9.10 beta via VirtualBox when it starting throwing up this error upon every attempt to boot.  Since VirtualBox drives are not "real" drives but *.vdi files I can figure no way to access and edit any files on the "test drive"; much less grub files.  What a pain.  :mad:

Update:  I ended up deleting the whole installation and reinstalling.  It seems to be coming up fine now whenever I boot up.  BUT: The one thing I have not done so far is run "Search For Updates".  Choosing that option now at best offers only a partial update.  I believe it was doing only a partial update after my previous installation that brought on the boot failures described in notes above.  I'll wait a few days before trying to another update.  And then only do so if it provides a complete, rather than only partial, update of files.

Update 2:  I waited a couple of days then tried a fresh boot of my VirtualBox install.  It would not boot at all.  Went back to the bad behavior described by others above.  Remember, since this is an install on a virtual drive (a *.vdi file) instead of a real hard drive I can find NO WAY to get in and edit any grub files as suggested by some.  Thus there is no way to remove the line "save_env recordfail".  

My conclusion:  the Beta is crap.  Designed poorly to fail.  Too bad.  The earlier alphas at least enabled you to boot consistently when testing virtual installs.  No way am I installing this on a hard drive or upgrading my existing hard-drive-based 9.04 Ubuntu system to 9.10 until this really bad bug is fixed.  If it doesn't test well on a virtual install it doesn't get installed permanently on a hard drive.

---

### Post by abgalphabet on 2009-10-11
I encountered the same problem. It boot successfully again to my desktop environment after removing the line "save_env recordfail".

But what's happened to this problem?! or can i add the line back afterwards?

---

### Post by abgalphabet on 2009-10-11
The "save_env..." line is added back after i execute update-grub2 and it boot normally afterwards.

---

### Post by jhenager on 2010-08-11
> **drfox said:**
> When your GRUB2 menu is up
Press e to edit grub
Remove the line save_env recordfail
Press TAB
Press CTRL+X to boot

HTH

Larry

YOU da man.

---

### Post by irpsit on 2011-12-31
I upgraded Ubuntu 10.10 to 11.10 and since the update there is the "error invalid environment block" everytime I boot, this shows two times, before GRUB menu appears, and after it appears. I must press any key to continue. It is annoying. 

ps. There is no "save_env..." line in GRUB, and it would not matter, because the error also appears before GRUB.

---

### Post by Penalva on 2012-01-06
iam getting the same in 11.04.

This was after a series of incomplete turn-offs with windows xp.

also got some file systems errors in the usual drive check process.

More horrifying is the system shuting-down from nothing, sometimes but not always, this being right after the boot. Strange that this come to happens together with this error. I dont think it's cause hardware malfunction .

Suggestions ?

Thank you in advance.

---

