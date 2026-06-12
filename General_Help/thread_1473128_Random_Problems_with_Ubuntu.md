---
title: "Random Problems with Ubuntu"
date: 2010-05-04
forum: General Help
---

### Post by Joseph Schwenker on 2010-05-04
I am using Ubuntu 10.04 and am having numerous problems.  First of all, and most importantly, I am unable to use my printer.  I turn on my computer, try to print something, and it gives me an error.  I look in the printing preferences, and no printers show up.  I try restarting my printer, plugging it in again, but nothing works.  Even restarting my computer does not work now.  This is AN EXTREMELY BIG ISSUE.  Second, I have Gnome-Do set to not show the window at start, and it DOES IT ALL THE TIME.  After I unlock the keyring and make the window go away, I try and press super+space to open Gnome Do, but nothing happens.  All of a sudden my theme's controls and icons change to another random theme, and cannot be changed back.  Another issue is repositories.  In Ubuntu 9.10, I could just add a source to the Software Sources, and it would automatically download the key.  Now, it always says that it cannot authenticate it.  Is there a problem with the key server?  Thanks in advance.

---

### Post by cariboo on 2010-05-04
Have you installed the printer by going to System->Administration->Printing?

---

### Post by Joseph Schwenker on 2010-05-05
I have been able to print on this machine before.   I do not think I need to install it.  The printer just randomly disappears sometimes, rendering me unable to print.  Because of this issue, I was unable to complete an assignment for a class.

---

### Post by themusicalduck on 2010-05-05
Which printer do you have?

and how are you adding sources? I usually add using the add-apt-repository command and that downloads the keys automatically. I don't know if it does the same when you add it with the GUI.

---

### Post by Joseph Schwenker on 2010-05-05
> **themusicalduck said:**
> Which printer do you have?

and how are you adding sources? I usually add using the add-apt-repository command and that downloads the keys automatically. I don't know if it does the same when you add it with the GUI.

I have the HP Photosmart C4180 All-in-One.  It has been compatible with previous versions of Ubuntu.  It is not a problem with the printer.  It is a problem with Ubuntu.  Also, I said in my first post that I used Software Sources to add the sources.

---

### Post by Joseph Schwenker on 2010-05-05
Restarting and replugging the printer does not work.  Only a restart solves the problem.  Could this be the fault of a specific application, possible a printer managing one?

---

### Post by Joseph Schwenker on 2010-05-06
This is an URGENT ISSUE.  This is more important than any other post, as this affects my productivity.  If I can't print an assignment, then I'm up until 10 trying to get it to print for school the next day.  This NEEDS TO BE SOLVED.  What can I run from the terminal for outputs?

---

### Post by Twitch6000 on 2010-05-06
> **Joseph Schwenker said:**
> This is an URGENT ISSUE.  This is more important than any other post, as this affects my productivity.  If I can't print an assignment, then I'm up until 10 trying to get it to print for school the next day.  This NEEDS TO BE SOLVED.  What can I run from the terminal for outputs?

First off you post is just as important as anyones,no more or less. Do not act like you are better.

The problem seems to be something killing the process. 

Do you remember doing anything before it just disappears?

---

### Post by brandon1004 on 2010-05-06
Wow. Was it a fresh install? Did all of this happen after you did something? Was it ever working on this install? Oh, and good luck.

---

### Post by Twitch6000 on 2010-05-06
Oh and as for your gnome-do problem. Go to start up applications and remove it from there.

---

### Post by Joseph Schwenker on 2010-05-06
> **Twitch6000 said:**
> Oh and as for your gnome-do problem. Go to start up applications and remove it from there.

The problem is not that I don't want it to start, it is that it is supposed to be using "Quiet Mode", so that the window does not appear on startup, but the application loads.  It worked on this install before, but randomly does not now.  Though it does appear that there are two Gnome Dos in my startup applications list.  I removed the second one.  Hopefully that solves this problem.

---

### Post by Joseph Schwenker on 2010-05-06
> **Twitch6000 said:**
> First off you post is just as important as anyones,no more or less. Do not act like you are better.

The problem seems to be something killing the process. 

Do you remember doing anything before it just disappears?

I meant to type "This is more important than any of my other posts", as I am having some other issues with 10.04.  My theory is that when you shut down Ubuntu, it kills any process open.  I ALWAYS have Empathy, Evolution, Gwibber, Gnome Do, and Docky open when I turn off my computer.  Those start with my computer, and are taken care of by the system when I turn my computer off.  Anyway, when Ubuntu kills those processes, there may have been another one, possible a printer daemon running that wasn't responding.  When the system killed it, it might have corrupted.  Any packages I can reinstall to fix it?

---

### Post by Joseph Schwenker on 2010-05-06
> **brandon1004 said:**
> Wow. Was it a fresh install? Did all of this happen after you did something? Was it ever working on this install? Oh, and good luck.

Yes, this is a fresh install.  I never noticed anything that I did, though I am a bit suspicious about the unauthenticated repositories.  The first time I went to print a document, it was a PDF file about DRM for the Day Against DRM (Tuesday).  I opened it, did a File, Print, and Print to File was the only option available.

---

### Post by Joseph Schwenker on 2010-05-06
The update manager on my computer opened, and I installed the updates.  Because I removed the second entry of Gnome Do, Gnome Do works flawlessly now.  I am waiting for the other problems to kick in.  So far, I am not seeing any printing problems.  Until I know for sure that these problems are solved, I will not mark this thread as solved.  I'll have to check back on the unauthenticated repositories, though.

---

### Post by Joseph Schwenker on 2010-05-14
The latest Ubuntu updates seemed to fix my problems.

---

