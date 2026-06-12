---
title: "Beep command does not work"
date: 2010-01-25
forum: General Help
---

### Post by DBQ on 2010-01-25
Hi everybody. My beep command stopped working -- it does not beep. I think this happened when I upgraded to Karmic (but could have been earlier). I use the beep command to notify me of important events. 

I tried looking in sound settings, and did not find anything suspicious. I also tried googling but most stuff just describes how to "disable the annoying beep".  Lastly, I tried different software channels and repositories to find an alternative program to the beep command, but nothing happened. Any ideas?  Thanks for the help.

---

### Post by t4thfavor on 2010-01-26
look in your /etc/modprobe.d/blacklist and make sure there is no entry for 

pcspkr

It may have been blacklisted since it's really annoying when your typing at night in an ssh window :)

---

### Post by blazemore on 2010-01-26
Check in your volume control for "PC Speaker"
it's most likely turned down.

You're welcome.

---

### Post by DBQ on 2010-01-26
I tried both suggestions.

My blacklist file is empty.

In the mixer, there does not appear to be a sound level control for pc speaker.

---

### Post by blazemore on 2010-01-26
Run the command "alsamixer"
Go along to the right, there should be a channel called "Beep" or "PC Speaker"
Hold Up to turn the level to full

---

### Post by DBQ on 2010-01-26
No such options in alsamixer

---

### Post by danastasio on 2010-01-26
perhaps the program got uninstalled?

> sudo apt-get install beep

---

### Post by DBQ on 2010-01-26
Its installed -- tried it. When I type beep it runs but makes no sound.

---

### Post by t4thfavor on 2010-01-26
My beep on my laptop didn't work either but mine was solved by unmuting Beep output on my alsamixer.

If you don't have one I wonder if the module didn't get loaded.

---

