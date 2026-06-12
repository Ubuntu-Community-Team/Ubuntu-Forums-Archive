---
title: "Ubuntu wont load past screen before log in"
date: 2009-12-16
forum: General Help
---

### Post by Sjorge3442 on 2009-12-16
I was playing around with my ubuntu box tonight trying to get my linksys wireless card to work and I happened to get it to work. Then I went to restart my computer because I had installed firestarter so that I could bridge my network connections, but the OS never loaded back up.

What happens is, it goes through the entire loading process (shows the bar loading) and then it gets to the screen right before the login screen. the screen is black and only has the busy mouse icon there. I can move it around, but nothing else works. 

Any suggestions? I believe i am on 8.40

oh and could you guys go easy on me. I am a real noob when it comes to ubuntu. thanks

---

### Post by Chesamo on 2009-12-16
8.04, I think you mean. My question is, why are you three releases behind?

*slaps self* Back OT. Do you have SSH enabled? If you do, then you can SSH into the system (in terminal, type```
ssh username@IPAddress
```which will enable you to log in remotely to the Ubuntu Terminal. From here, you can purge Firestarter and retry the installation.

---

### Post by Sjorge3442 on 2009-12-17
I am kinda confused as what you mean by this. Once I get in, what am I supposed to do? Like I said, I am kinda of a noob with this.

I am three released behind because this box hasnt been turned on in quite some time.

---

### Post by Sin@Sin-Sacrifice on 2009-12-17
I have a better idea. When you see the OS start to load press F12 and let us know what the output is. Hopefully you'll get a login prompt and you can log in the terminal. From the terminal you can diagnose what's going on by trying a few things. Post back either when you get a text prompt or you see where it's stopping.

---

### Post by Sjorge3442 on 2009-12-17
Pushing F12 did nothing for me.....

---

### Post by Sin@Sin-Sacrifice on 2009-12-17
Hrm... always works for me. Have you tried to boot from recovery mode? If you can do that then you should be able to get a root prompt.

---

### Post by Sjorge3442 on 2009-12-17
Yeah I get into the recovery mode, but I have no idea what to do from there. Is there a command that I can call that will load the cd? I have absoulutly nothing on the hard drive other than the OS, so I am just trying to install the newest OS now.

---

### Post by Sjorge3442 on 2009-12-17
I put my 8.04 disc in and it wont boot from that. I dont know why. I am going to try to make an iso of 9.10 and try that. Does anyone know the call command for the root to load the cd?

---

### Post by Sjorge3442 on 2009-12-17
does anyone have any suggestions?

---

