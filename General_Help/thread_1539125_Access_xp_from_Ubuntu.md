---
title: "Access xp from Ubuntu"
date: 2010-07-26
forum: General Help
---

### Post by SyAu on 2010-07-26
I'm dual booting xp and ubuntu. I mostly use Ubuntu for my daily Internet browsing, sometimes i need to access some software installed in xp, so i need to restart my laptop and then login to windows to access that particular application.

Is there anyway to access my already installed xp from ubuntu using virtual box or any similar software.

---

### Post by howefield on 2010-07-26
> **SyAu said:**
> Is there anyway to access my already installed xp from ubuntu using virtual box or any similar software.

No. Not for the purposes of running your xp installed software.

But you could install windows as a virtual machine inside Virtualbox or similar and run your programs from there, assuming your hardware is up to running a VM.

---

### Post by ronnielsen1 on 2010-07-26
What are you trying to run? Have you checked winehq for compatibility? It might run

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true)

---

### Post by John Bean on 2010-07-26
You can, but it's not without risks. See this somewhat out of date example of how to do it with VirtualBox: [http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883)

I don't really recommend this approach (yes, I have used it!) unless you want to risk losing the ability to boot XP natively for the convenience not having to always reboot. Better to use either a physical XP or a virtual one, but not both at the same time... 

Incidentally, converting your physical XP to a virtual one works fine, it's just the ability to use it in either mode that has lots of pitfalls providing new ways of breaking XP - as if it didn't have enough to start with.

---

### Post by SyAu on 2010-07-28
Thanks for the info guys .... I will play it safe and use xp separately.

---

### Post by dino99 on 2010-07-28
as told previously, all exe apps can run smootly (mostly) with wine (winehq), no need to be sticked with windoz

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

---

### Post by John Bean on 2010-07-28
> **dino99 said:**
> as told previously, all exe apps can run smootly (mostly) with wine (winehq), no need to be sticked with windoz

Not even close. *Some* will run ok, *some* will run with restrictions, *many* will not run at all. Saying that "all exe apps" will work in WINE - smoothly or otherwise - is simply wrong.

---

