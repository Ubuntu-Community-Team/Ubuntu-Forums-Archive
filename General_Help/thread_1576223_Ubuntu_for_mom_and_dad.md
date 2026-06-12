---
title: "Ubuntu for mom and dad"
date: 2010-09-16
forum: General Help
---

### Post by Lucas32 on 2010-09-16
My parents treat their computer well enough, but i know that my dad likes to check out some pron on the web every now and then which often nets them some nasty piece of malware.  As such, i was considering using wubi to install Ubuntu on their machine and see how they fare with it.  My concern is the passwords.  Can I configure Ubuntu to not require a password to log in and have separate accounts for the two of them?  Additionally, can I configure Ubuntu's update manager to run/download/install critical updates w/o needing any input?

thank you

PS:  if anyone knows of some guides on how to configure Ubuntu for a similar scenario please let me know.

---

### Post by 3Miro on 2010-09-16
You can tell Ubuntu to not require password on login, however, I am not sure it will be easy to disable the password for switching between them. If that use the computer at home only (i.e. not a laptop) they can just write the two passwords on sticky note next to the screen (just beware of guests).

I think Updates can be set up to go on automatically. If not form the gui, you can set up a cron job.

---

### Post by e79 on 2010-09-16
Though I would never recommend doing so, its better to set a password as '123456' than having none IMHO. For the updates, a simple windows pops-up from time-to-time (update manager - see attached .png) and all you have to do is click 'Install Updates'

I'm sure your parents could handle that easily  :p

---

### Post by jmszr on 2010-09-16
Lucas32,

To install security updates automatically: System > Administration > Software Sources > Updates > Click on "Install security updates without confirmation".

Just a thought, but couldn't your Dad do his surfin' with the Live CD - he might need to install "ubuntu-restricted-extras" every time to get flash, but that's not difficult or time consuming.

---

### Post by mike555 on 2010-09-17
Many have had trouble with wubi , I recommend a regular install to a separate partition .........also you might install Firefox with the add-on "WOT"  on their Windows and tell him about private mode.

---

### Post by sikander3786 on 2010-09-17
Yes I agree with mike555. I'll also like to see a regular install instead of Wubi.

For passwords, you can set one account, either your father's or mother's to login automatically, which one of them uses the PC more frequently. But then the other one will have to 1st logout and then login using his own account.

Updates can be automated as jmszr mentioned above.

> **jmszr said:**
> he might need to install "ubuntu-restricted-extras" every time to get flash

That will be not easy for a Linux Newbie. I won't recommend that.

---

### Post by Gunman1982 on 2010-09-17
He meant the case in which your dad uses only a Live CD.

---

### Post by s0563764 on 2010-09-17
Hey,

I just did that for my parents after I had to wipe one computer clean from XP and install Ubuntu, so I tried wubi for other computers.

I'm new to Ubuntu, but if you plan to use Wubi, then you should set the downloads etc to be saved in the Windows part, because the partition size is all 30 Gb at max, and mark shortcuts to those folders, so it can be accessed from ubuntu. Hope that helps

---

### Post by sikander3786 on 2010-09-17
> **Gunman1982 said:**
> He meant the case in which your dad uses only a Live CD.
Got it and edited my post accordingly. :-)

---

### Post by Lucas32 on 2010-09-17
I prefer a regular install to wubi too, but since this will be a trial than I'd rather go with wubi. 
once i install wubi/ubuntu, i plan on configuring/install everythng necessary: plug-ins, flash, video/audio codecs, etc...
i'm pretty sure that my parents won't want to share a single desktop/login.  they absolutely need their own accounts and they'll complain to no end if they have to enter a password each time.
again, i don't mean to be ungrateful or picky but a live cd won't really work for my folks.  my parents will moan and groan about the inconvenience of having to boot up a CD.  

i really think that Ubuntu would do the trick once it gets configured, but i'd like my two parents to have their own logins w/o passwords.   it'd keep them out of trouble from most of the nasty spyware and malware that's on the net/web.

---

### Post by s0563764 on 2010-09-18
Hey I just did the same thing for both my parents computer. You can disable a lot of the password stuff etc. I just did it for them for the same reasons, especially as my dad has not used a computer so far, so clicks on adverts without realising!

As for wubi, if you make the right shortcuts (to use the space in the rest of the drive) and configure it, it pretty much does what a normal installation does.

Good luck with getting your parents used it

---

