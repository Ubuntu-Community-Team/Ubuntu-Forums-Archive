---
title: "My Ubuntu crashes with Screensaver"
date: 2006-05-18
forum: General Help
---

### Post by ROUBOS on 2006-05-18
Hi,
I left my PC for a few minutes and my screensaver came up (3D with date and time) must be the ubuntu default screensaver, and it froze.
So I rebooted the PC and got into the screensaver options to switch the screensaver off, and it froze again....

My system crashes with the screensavers...any help??? Please....

---

### Post by Ramses de Norre on 2006-05-18
Try reinstalling your video drivers, it seems openGL is crashing.

---

### Post by ROUBOS on 2006-05-18
How do I do that?
I just installed Ubuntu and it's with whatever it has auto-detected...

---

### Post by DaBigEd on 2006-05-22
Yea I'm Having similar problems too.

Any ideas?

---

### Post by dmizer on 2006-05-22
heh ... just turn the screen saver off.  it doesn't really do anything anyway.  i had the same problem when i first installed, i just switched my to blank the screen.  maybe it's boring, but it's easier on the hardware.

---

### Post by corytoneill on 2006-05-22
I have the same problem and when i try to disable screensaver it freezes again

---

### Post by confused57 on 2006-05-22
I had it happen for the first time today using Dapper.
Pressed Ctrl+Alt+F1 to get to a command prompt.
Then:
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

to get back to the GUI.

---

### Post by SFAOK on 2006-05-22
My housemate has this problem. His graphics card was quite old and the card/drivers were not up to the job of the 3D screensavers. I disabled the opengl modules being loaded by editing the /etc/X11/xorg.conf file and adding a hash at the start of the lines under the Module section with Load "GLcore" and Load "glx"

At least, that's off the top of my head, so back the file up i case somethign goes wrong. This also assumes that the 2D (i.e. non opengl) screensavers work ok.

---

### Post by Cirrocco on 2006-05-23
this started doing it to me too about 3 days ago.

you CAN'T disable the screensaver because when you open the screensaver option menu, x crashes.

the damn stupid part is that I did nothing to provoke this. it just started doing it.

I've got a Geforce mx440,  can someone post a link to the nvidia driver how to?  or better yet, the line I have to edit in my xorg.conf file to make this work?

---

### Post by Tristan9669 on 2006-05-24
[QUOTE=ROUBOS]Hi,
I left my PC for a few minutes and my screensaver came up (3D with date and time) must be the ubuntu default screensaver, and it froze.
So I rebooted the PC and got into the screensaver options to switch the screensaver off, and it froze again....

My system crashes with the screensavers...any help??? Please....[/QUOTE]
I'm having the same problem...I have an ati 9000 and using the drivers what ever ubuntu comes with on a fresh install

**edit: I found this fix **[http://ubuntuforums.org/showthread.php?p=1049597#post1049597]("http://ubuntuforums.org/showthread.php?p=1049597#post1049597")

---

