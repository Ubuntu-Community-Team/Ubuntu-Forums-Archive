---
title: "This has never happened to you before! Unexplained!"
date: 2010-11-16
forum: General Help
---

### Post by yperionas on 2010-11-16
I have a Dell laptop at which I have installed Ubuntu linux. Everything was going well for some weeks until this morning where I discovered that the text on the screen is highlighted on its own. I write in the browser and the system gets crazy. Text is highlighted, clicks (like pressing enter) occur without me doing anything or spaces between letters.
It is not a problem neither of the keyboard or mouse. I have disconnected them both and still the same thing happens. The desktop gets crazy!
 
Any ideas why this is happening out of the blue?
 
Thank you in advance!

---

### Post by CharlesA on 2010-11-16
Vnc?

---

### Post by yperionas on 2010-11-16
What is Vnc?

---

### Post by yperionas on 2010-11-16
Are you refering to virtual network computing? No I am not suing Vnc. All these events that take place are totally random and have no specific purpose. Random text is highlighted, random clicks happen automatically, enter/or double click is pressed at random moments etc...
 
I thought there was a mouse, keyboard problem but eventhough I have disconnected them the problem persists. Even at the login screen to this phenomenon occurs.

---

### Post by yperionas on 2010-11-16
Have found a similar post here: [http://ubuntuforums.org/showthread.php?t=1119474](http://ubuntuforums.org/showthread.php?t=1119474)
 
But with no solution. Any ideas?

---

### Post by CharlesA on 2010-11-16
Have you made any changes to yer system since?

Does the same thing happen if you boot off a livecd?

---

### Post by yperionas on 2010-11-16
I have installed recently the qemu to run another linux dist virtually and im currently wondering if the real OS and the virtual are somehow influneced. But this is just an idea. I haven't made any other changes to the system except this installation.
 
There is also a another similar post here: [http://www.webdeveloper.com/forum/showthread.php?t=196388](http://www.webdeveloper.com/forum/showthread.php?t=196388)
 
But still with no evident solution.
 
I haven't tried booting a live cd. Does booting from a live cd helps us understand what is going on at the real system? You think i should give it a shot?
 
Currently im posting and trying to look for a solution with windows. Was impossible to do that with ubuntu installation.

---

### Post by CharlesA on 2010-11-16
Booting from a livecd would rule out a problem with the install itself. If it happens on the livecd, it'd a hardware problem more then likely.

If it's not happening on Windows now, it's probably qemu that is causing the problem. *shrug*

---

### Post by yperionas on 2010-11-16
Hmmm so I should remove qemu and cross my fingers right?

By removing qemu do I still need to update the system to avoid any incosistency that may remain with the drivers or whatever or the removal process does that automatically?

Btw thanks very much for your time and effort helping here. I really appreciate it.

---

### Post by CharlesA on 2010-11-16
Everything should be removed automagically.

---

### Post by yperionas on 2010-11-16
It is very strange but the problem has disappeared (so far) by just removing the qemu from the panel? 

I had enabled the icon of qemu to appear at the desktop panel at system's start up (only the icon not starting up the emulator itself). I am not sure if this somehow influences the system by starting some processes in the background. Nevertheless, I have not done anything else other than removing the icon from the panel. The problem has disappeared.... Everything runs smoothly again.

I will still though search around a bit for any possible reasons that this happened. Thanks for all the help.

---

### Post by CharlesA on 2010-11-16
Could be that is was conflicting, don't know.

---

