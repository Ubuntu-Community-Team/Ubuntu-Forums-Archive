---
title: "Is there any SOLUTION to the pw prompt logon loop?"
date: 2010-01-25
forum: General Help
---

### Post by NunyaB on 2010-01-25
Hello again,

I have been trying to resolve the same issue for awhile now.  I install Ubuntu 9.10,  it's great no issues, then I install packages I need, still fine no issues.  THEN it will start prompting me to enter my password to logon even though I installed with automatic logon option set.  Sometimes if you hit reset them machine will boot normally but then it will go to a loop cycle that you can NEVER get logged on.

I have posted twice before with this same issue but have not received a solution.  I have tried clean reinstalls and have gone so far as to clone the drive with 3 identical drives to see if it was an upgrade issue or what.  It gradually creeps back into each drive no matter what I try.

I have tried Linux Mint 8 and it does not seem to have this issue so far on the same machine which I am using right now to post this since ALL Ubuntu's have gone to pw loop.  Only Ubuntu has this.  **I like Ubuntu!**  **I want to use Ubuntu!** It seems a smoother in it's browser abilities and the interface is more intuitive. But if I can not rely on it to start when I need it well... 

Can some one PLEASE tell me if there is a solution for this or at least what the cause is?  

System:

Mini ITX VIA EPIA-PE
1 gig ram
integrated video & AC97 audio
160g internal storage hard drive no OS
80g OS hard drive ( removable and is swapped as needed )
LCD monitor connected thru KVM switch

This system is mini desktop used to test OS and software configs for Win XP / Linux versions, etc.  It is not a gamer but is used to clone hard drives, etc.  And it is a very reliable system with all tried except Ubuntu.  

Thank You in advance for your help!

---

### Post by pastalavista on 2010-01-25
> **NunyaB said:**
> Hello again,

I have been trying to resolve the same issue for awhile now.  I install Ubuntu 9.10,  it's great no issues, then I install packages I need, still fine no issues.  THEN it will start prompting me to enter my password to logon even though I installed with automatic logon option set.  Sometimes if you hit reset them machine will boot normally but then it will go to a loop cycle that you can NEVER get logged on.

I have posted twice before with this same issue but have not received a solution.  I have tried clean reinstalls and have gone so far as to clone the drive with 3 identical drives to see if it was an upgrade issue or what.  It gradually creeps back into each drive no matter what I try... [snip]

I'm not sure I understand the problem exactly. It sounds like you are trying to run full-time as root and that isn't possible. What programs did you install?

---

### Post by NunyaB on 2010-01-26
Hi pastalavista,  Thanks for responding

Run full time as root....  ???

I have installed Ubuntu all by itself on a hard drive for a system.  After a time it begins to ask me for my password when I try to power up.  It was set up to automatically login on power up.  If you enter your password or reset the system it goes right back into the prompt to enter your password.  Ubuntu will not start beyond start up splash.

---

### Post by pastalavista on 2010-01-26
You didn't say what programs you installed and what is set to run at start-up. You can't log on as administrator (root) without entering your password. If an auto-run program needs root permissions to work, bye-bye auto-login

edit: post the error messages you are getting...

---

### Post by NunyaB on 2010-01-26
I understand what you are saying.  But what ever is creating the issue in my case does not have to do with the software.  I have 3 hard drives, the 2 cloned from the first have aptoncd, DeVeDe, ISO Master, and Kbattleship added from the clean install.  ( Nothing serous added yet until I can get this resolved! )  One of these I allowed updates to be run the other not.  The Original hard drive I left clean, nothing added.  

They all have developed the same issue.

I have been browsing the new posts and there is a reference to "remove file $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml" fixing the issue for a few?  Not sure if this is my answer and will have to shut down Linux Mint on this machine to install one of the Ubuntu hard drives to try.

---

### Post by NunyaB on 2010-01-26
I checked out the display.xml file deletion.  No Change.  pastalavista your suggestion on software made me think harder about the issue since 3 hard drives different levels of software addition from clean install to several I didn't think that was it...  But looking closer it was an update that killed it.  I do not know which one.  But I went from 2-17 generic to 2-14 generic and problem is gone!  \\:D/

Now my question would be...  How do I know what to update since I do not know what created the issue?  I checked and my 2-14 update manager has 175 updates it wants to do.  My 2-17 that would not run 56, that does not narrow the field as far as knowing the killer update.  :confused:

---

### Post by pastalavista on 2010-01-26
All I can suggest is to have a look through System--> Administration--> Log File Viewer. I've had updates create problems before but never with authorizations. Just been lucky, I guess.

---

### Post by NunyaB on 2010-01-26
Thanks pastalavista I will try to see what I can find.  Wow, there's alot there.  guess I have a new hobby.  :-)  But it will be very interesting if I can find the creation of the problem.

---

