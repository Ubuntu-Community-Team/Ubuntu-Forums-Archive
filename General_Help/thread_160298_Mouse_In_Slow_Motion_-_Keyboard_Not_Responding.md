---
title: "Mouse In Slow Motion - Keyboard Not Responding"
date: 2006-04-14
forum: General Help
---

### Post by OffHand on 2006-04-14
Randomly my mouse usb goes into some sort of slow motion mode (cannot click on anything but move it slow) and my ps2 keyboard stops responding. Reconnecting the mouse doesn't help. 
Anyone else experiencing something like this?

---

### Post by Silver Streak on 2006-04-14
This happens at times with me, too. It's only happened three times, and all of the incidents occured while running Firefox.

SS

---

### Post by FryerFox on 2006-04-17
ditto - my keyboard has stopped responding completely several times today (at first I thought it was my laptop hardware failing), and each time I have had Firefox running. I had to reboot to get the keyboard back.

This started this Saturday (about 3 days ago), but I don't recall getting an update to Firefox...

---

### Post by dmizer on 2006-04-18
my guess is that something is eating your resources.  memory or cpu.

run top and see if you find anything unusual.  for me, it was gaim that was causing the problem.  occasionally nautilus will act up.  firefox perportedly has a memory leak, the fix for that can be found here: [http://www.freerepublic.com/focus/f-bloggers/1327586/posts](http://www.freerepublic.com/focus/f-bloggers/1327586/posts)

but i don't know if that is true for the version that ships with ubuntu or not.  don't forget that in top, you can change how the fields are focused by hitting <shift>+f.

good luck.

---

### Post by FryerFox on 2006-04-18
Actually, I have System Monitor running in the panel, so I could see that it wasn't a memory or CPU problem in my case. I have learned to recognize when Beagle is about to freak out and switch to a terminal to kill it, but I don't think this was the same problem.

Even when the keyboard dies, you can still mouse around and click on other things which respond normally (i.e. movies don't skip frames, etc.)

On the other hand, you are probably right for subsonic_shadow's case - a slow mouse usually means the CPU is running full blast.

---

### Post by dmizer on 2006-04-18
[QUOTE=FryerFox]Actually, I have System Monitor running in the panel, so I could see that it wasn't a memory or CPU problem in my case. I have learned to recognize when Beagle is about to freak out and switch to a terminal to kill it, but I don't think this was the same problem.

Even when the keyboard dies, you can still mouse around and click on other things which respond normally (i.e. movies don't skip frames, etc.)

On the other hand, you are probably right for subsonic_shadow's case - a slow mouse usually means the CPU is running full blast.[/QUOTE]
indeed i was replying to subsonic_shadow ... it is his/her thread afterall ;)

in your case, you may have a hardware issue or a driver issue?  you have some kind of special keyboard (wireless etc)?  is it usb or ps2 ... bluetooth (you never know until you ask right ... lol)?

you might get more results if you started your own thread, because i'm sure that your issue and subsonic_shadow's are not similar.

---

### Post by FryerFox on 2006-04-18
Sorry, I probably should have started a new thread, but I just found that my issue is mysteriously related to Beagle.

---

