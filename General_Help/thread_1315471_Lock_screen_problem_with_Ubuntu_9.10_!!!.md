---
title: "Lock screen problem with Ubuntu 9.10 !!!"
date: 2009-11-05
forum: General Help
---

### Post by alihmohd on 2009-11-05
I'm having problem with my Ubuntu 9.10 karmic (Gnome), sometimes when I enter (Screen Saver) or when I lock the Screen, I can't wake up from the machine !! 
unless I shutdown by holding the power button !!

Plz any advises ?

Regards,

---

### Post by balteo on 2009-11-14
same problem for me...

---

### Post by Wolfhere on 2009-11-14
MMMM......for me, I cannot lock the screen at all. There is a bug report on this issue. I can still suspend, but no lock at all.

---

### Post by SteveFoerster on 2009-11-17
My problem is similar, if my screensaver is running, and someone else logs in in the meantime, then they can log out, but the screen stays blank.  I can Cntl+Alt+Del and shutdown, with the rest of the screen staying blank, but nothing else.  It's very irritating.

So I disabled the screensaver, or so I thought, but even though Preferences->Screensaver shows that I've turned mine off, the behavior remains.

---

### Post by bobpcman on 2009-11-20
Same problem here.
I activated the screensaver and to automatically require a password to unlock.
When typing the password, the windows status is "checking" and it does not unlock, until times out.
I pressed CTRL+ALT+F3 to login and kill x, but even there I can not login... Lots of erros messsages and I can not login.
Thanks.

---

### Post by bobpcman on 2009-11-20
Hey,

I tried the fix shown on the bottom of this thread and it works.

[http://ubuntuforums.org/showthread.php?t=945350](http://ubuntuforums.org/showthread.php?t=945350)

[INDENT][I][COLOR="Red"]From a different thread - here is what worked for me and kind of makes sense - the /etc/shadow file needs the right permissions to allow the /sbin/unix_chkpwd to read it.

[http://ubuntuforums.org/archive/index.php/t-804647.html](http://ubuntuforums.org/archive/index.php/t-804647.html)

I quote:
Rogerborg
September 15th, 2009, 04:57 AM

Yup, this bug is still extant in 9.04. The stock install was fine, but somewhere along the way, my /etc/shadow has become root:root and 0400.

I'm not sure what's causing it. Running useradd sets the permissions to 0440, but doesn't touch the permissions.

sudo chown root:shadow /etc/shadow
sudo chmod 440 /etc/shadow

fixes the screen unlock problem for me in 9.04.[/COLOR][/I][/INDENT]

Cheers!

---

### Post by illusion88 on 2009-12-02
I have been having issues with this and just found that simply running gnome-screensaver from a terminal enabled me to lock my screen again (once the problem has occurred) which suggests this is just crashing for some reason.

---

### Post by gglaser on 2009-12-07
I am having the same problem as alihmohd: whenever my screensaver starts, I am not able to wakeup the machine.  Moving the mouse, typing on the keyboard, etc doesn't have any effect.  This is different from the "checking" message problem when you try to enter the password that others mentioned.  Does anyone have a solution to the screensaver problem?
 
Thank you,
Gina

---

### Post by vuul on 2010-02-03
I was having this problem too on my desktop system using GNOME until I changed the following setting. 
1. Go to: System -> Preferences -> Power Management
2. On the "On AC Power" tab change the "Put display to sleep when inactive for:" setting to Never.

---

### Post by anthony.cros on 2010-06-28
Hi everyone,

I have the exact same problem as alihmohd, balteo and gglaser and none of the solutions proposed work. 

Most of the time I can unlock it but every now and then, if I lock it overnight I can't unlock it anymore in the morning (can't make the login window appear again by touching mouse or keyboard). I noticed that it seems to happen when I leave a swing application running overnight or an ssh session open, although I'm not 100% sure.

Has anyone tried to ssh to their machines and run "gnome-screensaver-command --poke" to see if it helps? I intend to do so next time it happens anyway (will post result). I doubt it'll work but well... :?

Otherwise, any alternative means of locking access to the computer? maybe just locking keyboard/mouse for instance (i don't care about the screen itself).

Cheers!
Anthony

---

