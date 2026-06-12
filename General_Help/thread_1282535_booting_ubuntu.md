---
title: "booting ubuntu"
date: 2009-10-04
forum: General Help
---

### Post by darman12 on 2009-10-04
I've just downloaded ubuntu 9.04 and I think I've successfully created a bootable disk useing InfraRecorder suggested by this sight.

A few weeks ago someone gave me a working computer from his work but he didn't give me a password to log in. He also wants me to wipe the hard drive by installing a new operating system.

Is there a way to install ubuntu on my computer without logging in?

---

### Post by ermeyers on 2009-10-04
Assuming you have Ubuntu CD, setup to boot from CDROM first.  Boot from CD, and select to Install Ubuntu.

---

### Post by darman12 on 2009-10-04
Where do I do this?

---

### Post by Bartender on 2009-10-04
Unless of course BIOS is also password-protected...

---

### Post by darman12 on 2009-10-04
I am not very smart in this type of thing...as you may have already noticed.

---

### Post by darman12 on 2009-10-04
> **Bartender said:**
> Unless of course BIOS is also password-protected...
What is BIOS?

---

### Post by darman12 on 2009-10-04
Also, when I was goofing with the login a program called Pointsec opened also requiring a password...I havn't been able to close it.

---

### Post by darman12 on 2009-10-04
> **ermeyers said:**
> Assuming you have Ubuntu CD, setup to boot from CDROM first.  Boot from CD, and select to Install Ubuntu.

what does it mean to "setup to boot CDROM" ?

---

### Post by wojox on 2009-10-04
What happens when you put the cd in the tray and reboot the computer?

---

### Post by Bartender on 2009-10-04
Your computer boots into BIOS (Basic Input Output System) before it goes to find an operating system.  You access BIOS by tapping on a key repeatedly right after turning the PC on.  Typical keys are Esc or F2; there are a few others.  So you have to find out which key gets you into the BIOS on your buddy's PC.

Just google the PC model and add "BIOS" to the search.  You should get a hit that tells you which key to use.

Once you're inside BIOS, navigate (mouse won't work, you'll need to use a combination of "Enter" and arrow keys) to the "Boot" section and find the menu that lets you change the boot priority.  The optical drive must be nudged to the top.  This can be a little confusing - some BIOS'es use a goofy combination of space bar, arrow keys, etc.  

Once you get the optical drive to the #1 spot, you then have to "save" the changes.  Usually a combination of F10 and Enter key, maybe Y key too.

Restart the PC and slip the CD in real quick, or if you miss it just get the CD in the tray and restart again.

Once you've got Ubuntu installed, you can go back into BIOS and set the HDD as #1 in boot priority.  Or not.  If you leave the optical drive as #1 the PC will take a quick look at the optical device when starting up and move on if it doesn't see a bootable disc.

---

### Post by darman12 on 2009-10-04
disregard

---

### Post by darman12 on 2009-10-04
Thanks...i will post in a little while to give you an update and ask questions if needed.

---

### Post by darman12 on 2009-10-04
how do you restart without logging on

---

### Post by wojox on 2009-10-04
Try Ctrl+Alt+Delete

---

### Post by ermeyers on 2009-10-04
> **darman12 said:**
> Where do I do this?

At boot, press F2 or other for "Setup"  find Boot Sequence, and put CDROM to boot first.

---

