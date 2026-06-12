---
title: "Log in Question..."
date: 2009-11-14
forum: General Help
---

### Post by Jukki14 on 2009-11-14
Well the thing is i've been using ubuntu for some weeks and today (like 30 min ago) i restarted my pc just to discover that the login didn't work anymore, only the console stays and even if i log in with the console it stays on the console, how can i fix this problem???

BTW im new here, so i'd appreciate any help

---

### Post by tommynz1975 on 2009-11-14
so after login you are left with something like.

user@places:~$

if so try typing startx and see what happens.

---

### Post by Jukki14 on 2009-11-14
It says a lot of things, and the last ones say xinit: No such file or directory (errno 2) and something about a "/var/log/Xorg.0.log"

---

### Post by Wim Sturkenboom on 2009-11-14
So check that file (for lines with WW and EE) and see what goes wrong.

And what did you do before it stopped working (e.g. install updates or upgrade from 9.04 to 9.10) ?

---

### Post by Jukki14 on 2009-11-14
How do i know what is wrong? and the only yhing i did was install some siscontrol or somthing like that because my pc won't recognize my graphic card

---

### Post by CoryThompson on 2009-11-14
Hello,

Looks like you have installed the wrong drivers. I would try typing in:

sudo dpkg-reconfigure -phigh xserver-xorg
Hope this helps ;)

---

### Post by Wim Sturkenboom on 2009-11-15
> **Jukki14 said:**
> **How do i know what is wrong?** and the only yhing i did was install some siscontrol or somthing like that because my pc won't recognize my graphic cardSorry if I sounded a bit hard, that was not really the intention. But if something tells you to check something it's the first thing to do. You might understand it and solve the issue. Or you might not understand it and ask the questions.

And the information that you installed something related to the video is very crucial and should have been mentioned in the first post. I think that that would even have been a pointer for you.

---

### Post by Jukki14 on 2009-11-15
> **CoryThompson said:**
> Hello,

Looks like you have installed the wrong drivers. I would try typing in:

sudo dpkg-reconfigure -phigh xserver-xorg
Hope this helps ;)

I tried this and it stays the same

And sorry i didn't mention the video stuff on the first post... so any other suggestion in what to do?

Like i said im new with ubuntu, at least with the console

---

### Post by ctult on 2009-11-15
It sometimes happens if Ubuntu does not load fast enough.  Just try restarting your computer.

---

### Post by Jukki14 on 2009-11-15
> **ctult said:**
> It sometimes happens if Ubuntu does not load fast enough.  Just try restarting your computer.

I've restarted it one time for each post on here plus like 5 times when i noticed it

Thanx anyway

---

