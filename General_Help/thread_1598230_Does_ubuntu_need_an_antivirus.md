---
title: "Does ubuntu need an antivirus ?"
date: 2010-10-16
forum: General Help
---

### Post by kanishkdudeja on 2010-10-16
im new to ubuntu and loving the experience..however i need to ask tht shud i install an antivirus software on ubuntu ? is ubuntu susceptible to viruses ?

---

### Post by WorMzy on 2010-10-16
You don't need an antivirus, but you can install one if you want to.

[https://help.ubuntu.com/community/Antivirus]("https://help.ubuntu.com/community/Antivirus")

---

### Post by sp0nge on 2010-10-16
Need is relative. It's not a necessity, even on windows if you pay attention and know what you're doing. Anti-virus is definitely a good tool, another layer to the onion of security, but not a "silver bullet"- meaning you're still at risk with or without AV. 

Sadly, there are many attacks out there that will allow hackers to completely bypass the AV, confuse or dupe the AV into thinking all is well, or in some cases, attackers have even used the AV as an attack surface. 

If you're behind a router/firewall and you surf safely (ie no clicking on the dancing gnomes or the links in emails about the free iPad you just won), you're at less risk.

While Linux viruses DO exist, here is a little article about why they live [a hard knock life]("http://bit.ly/c8rfif").

---

### Post by kanishkdudeja on 2010-10-16
:)

---

### Post by a-user on 2010-10-16
like any linux: no

---

### Post by Chrison999 on 2010-10-16
Okay, somewhere I saw there was a gui interface for clamscan but now I can't find it.  Does anyone know the name of the package, is it in the repos, and is it any good?

Thanks!

Regards,

Chris

---

### Post by Brian88 on 2010-10-16
It is not a must, but you might need it for scanning your Windows share, deinfecting flash drives and Windows folders. I'd better install one.

By the way, Windows antiviruses will sometimes work under Wine, but it will lose its real-time protection ability. It doesn't matter though, as Linux is resistant to Windows' viruses.

---

### Post by Brian88 on 2010-10-16
> **Chrison999 said:**
> Okay, somewhere I saw there was a gui interface for clamscan but now I can't find it.  Does anyone know the name of the package, is it in the repos, and is it any good?

Thanks!

Regards,

Chris

It is clamtk.

---

### Post by gandaran on 2010-10-16
clamtk
and yes its in the repos
but I wouldn't recommend this clam-antivirus, you get to many false positives with it.

---

### Post by Chrison999 on 2010-10-16
> **gandaran said:**
> clamtk
and yes its in the repos
but I wouldn't recommend this clam-antivirus, you get to many false positives with it.

Thanks for the pointer.  I knew it was something like that, but was thinking clam-gtk instead.

So, if you don't recommend clamav, what would you recommend?

Thanks!

Regards,

Chris

---

### Post by WorMzy on 2010-10-16
I recommend clamav, even if Gandaran doesn't. It does find a few false-positives, but it doesn't do anything with them by default. If it *does* find false-positives, leave them alone, if they're not false-positives, delete them/move them to your ext4 filesystem.

---

### Post by hawthornso23 on 2010-10-16
You don't need a virus checker in ubuntu.

Clamav on linux is a tool designed to help protect windows machines running on your network. The viruses that clamav scans for are windows viruses.

You don't need a virus checker in ubuntu.

Lots of windows refugees feel naked if they are not running an antivirus, a troijan checker etc etc etc. Those things really don't make them any safer, but give a sense of security in a dangerous windows world. 

You don't need a virus checker in ubuntu.

Linux is a whole different frame of mind. You don't need to install any so called extra `security applications. It comes fully secure. But people in a windows frame of mind find that hard to believe so you have to tell them like half a dozen times.

You don't need a virus checker in ubuntu. 

While ubuntu is perfectly safe without a virus checker, that doesn't mean security isn't important. But security on linux is all about not doing stupid things that might make your system vulnerable. Don't run services you don't need. Don't change security settings unless you know what you are doing. It isn't about running virus checkers and the like.

You don't need a virus checker in ubuntu.

Are we there yet? Lets see ... 1 2 3 4 5 ... one more ought to do it.

You don't need a virus checker in ubuntu.

---

### Post by kanishkdudeja on 2010-10-17
thanks for the information guys..:)

---

