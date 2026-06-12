---
title: "I have upgraded to 10.4"
date: 2010-05-14
forum: General Help
---

### Post by Mdhall7477 on 2010-05-14
And now it is slow as a ten year itch I dont understand what has happened nor how to fix the problem.. It is choppy  slow and hard to load things. even writing this it is taking forever to type it properly I used the upgrade feature and everything said it was fine what have I done wrong... is there a way to run a system diagnostic or something.

---

### Post by ubunterooster on 2010-05-14
system>administration>system monitor. 

Go to the tab titled "resources"  How much Ram is used? CPU?

---

### Post by Mdhall7477 on 2010-05-14
CPU say 13.3% used

---

### Post by ubunterooster on 2010-05-14
Ram?

---

### Post by kevinatkins on 2010-05-14
You're going to need to post full hardware specs for peeps to help you.. what you describe really doesn't sound right, at all...

---

### Post by Mdhall7477 on 2010-05-14
I dont seeRAM I see 24.1% of MiB if that is what your needing... Sorry this thing is slow as crap to load anything

---

### Post by Mdhall7477 on 2010-05-14
> **kevinatkins said:**
> You're going to need to post full hardware specs for peeps to help you.. what you describe really doesn't sound right, at all...


Tell me all that you all need and where to find it and I will recover it for you..  but it is not loading nothing really fast.  even trying to post replys takes what seems minutes

---

### Post by ubunterooster on 2010-05-14
How much RAM (memory) you have, The processor(CPU), and the graphics card (GPU).
Speaking of GPU go to System>administration>hardware drivers. If there are any, install them.

Attached is a screenshot of my system monitor

[quote=kevin]peeps[/quote] that's a first

---

### Post by pastalavista on 2010-05-14
If you aren't having any trouble connecting to the internet, try this

Reboot in recovery mode and open a networked console. Enter these commands```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```
Then boot up normally and see if there's any improvement.

---

