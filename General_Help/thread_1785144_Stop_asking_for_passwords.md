---
title: "Stop asking for passwords"
date: 2011-06-17
forum: General Help
---

### Post by mawil1013 on 2011-06-17
How do I stop all the,, enter password,, scenarios?

u10.04.2

---

### Post by AlphaLexman on 2011-06-17
Do you mean when you try to install new software?
Or try to make changes to the system configuration?

These are security measures, and are meant to keep non-authorized users from borking your system!

---

### Post by wolfgangmcq on 2011-06-17
[FONT=Courier New]man sudoers[/FONT] explains how to get rid of sudo passwords... *not* a good idea if you're not the only person who has access of any sort to your system.

---

### Post by idoitprone on 2011-06-17
stop trying to change your system. lol

---

### Post by deserthowler on 2011-06-17
> **mawil1013 said:**
> How do I stop all the,, enter password,, scenarios?

u10.04.2

Is it called Windows?  :confused:
Seriously, I have installed a right-click item in the menu that allows me to click a folder and open it as administrator so I can move, change, rename or delete items.  I can't recall the name of the program but I have it installed in 10.04 and 10.10.  I know it is somewhere in the repositories but that is the best I can do for you.  ](*,)

Earl

---

### Post by yetiman64 on 2011-06-18
@deserthowler,
I think nautilus-gksu is the package you may be referring to. You still require a password for its use.

@OP, the advice your're seeking, if given here would be very bad advice to post on this forum (others beside yourself use the forum as a research tool without asking questions), or could even in some cases go against forum rules as this forum openly supports Canonical's security model.

Some reading for your answers can been founnd in "man sudo" (already mentioned) or the [--Rootsudo Community Documentation--]("https://help.ubuntu.com/community/RootSudo")  [--Sudoers Community Documentation--]("https://help.ubuntu.com/community/Sudoers")   <--2 links

Removing password prompts is a very dangerous practice. It depends on how much you value your data --the prompts are a good reminder that what you are about to do next has the potential to mess you up badly ;).

---

### Post by garyweigh on 2011-06-18
You can find the best answer of your question by reading [http://www.howtogeek.com/howto/windows-vista/make-windows-vista-stop-asking-for-password-when-resuming-from-sleep/](http://www.howtogeek.com/howto/windows-vista/make-windows-vista-stop-asking-for-password-when-resuming-from-sleep/) .......

---

### Post by christopher.wortman on 2011-06-18
Well in my case, I use Kubuntu, and it has a handy little check box that says "remember for session" so I can install unlimited software titles by typing in the password once per login session. It remembers it in the local ram and if you log out or reboot it will ask for it again. Also when installing check the box that says "do not require password for login" and you notice this gets a lot less annoying.

---

### Post by wildmanne39 on 2011-06-18
Hi, the problem is if you stay at administrator level the whole time that you are on your system then you are open to security threats that you do not have if you are the user and just borrow the administrator powers for a short time.

---

### Post by Elfy on 2011-06-18
There's plenty of information on the web about this.Removing passwords is not supported. Closed.

---

