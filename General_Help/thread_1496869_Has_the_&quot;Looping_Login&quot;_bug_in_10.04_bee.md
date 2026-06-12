---
title: "Has the &quot;Looping Login&quot; bug in 10.04 been reported yet?"
date: 2010-05-29
forum: General Help
---

### Post by lightnb on 2010-05-29
The scenario is:

Computer boots up.
You choose your user name
You enter your password
you hit enter
the system accepts your password (not an authentication problem)
the screen goes black
the login screen reappears

A (temporary) workaround:
login screen appears
hit ctrl+alt+F1
login with your name and password.
type "sudo service gdm stop" (you must have sudo permissions)
type startx

I've seen this problem mentioned in a couple threads here, but I couldn't find a bug report on Launchpad.

Has it been reported?

Also, what "package" would/should this be filed under?


Thanks,

---

### Post by Spr0k3t on 2010-05-29
What graphics card do you have.  I've seen these same steps used for some of the older Intel based integrated graphics chips.  Check through the sticky posted at the top.  I believe it's already been reported, but double check.

---

### Post by nerdopolis on 2010-05-29
Is your drive full? I once had a problem like that a while back, and it turned out it was because my drive was full.

---

### Post by lightnb on 2010-05-29
@nerdopolis: No, I've got 5 GB free. Initially after installation, login worked fine. The problem started after running an update/upgrade.

@Spr0k3t: It's an onboard graphics adapter with an nVidia/nForce chipset. I'm running the restricted nVidia drivers, but the problem occurs with and without the proprietary drivers installed.

UPDATE: I could not find this issue in the "known issues" thread. Can someone confirm if it's on launchpad? I don't mind starting a bug, but what package should it report against?

---

### Post by mrosenfe on 2011-03-21
I have this exact same issue with 10.04.  It started happening after a security update.  I do have a fairly full hard drive but there is still adequate space.  I have an older ATI graphics on an older Compaq laptop.   This laptop has run the LTS releases for sometime with no problems.   I have tried changing the password by booting into recovery mode, but that does not seem to help.   I will try the fix noted in the post.   Has it worked for anyone else?

---

### Post by pqwoerituytrueiwoq on 2011-03-21
install nvidia's run file from there site it fixed it on my xubuntu desktop
be sure the default driver (no something) is disabled or you cant install it
[http://ubuntuforums.org/showthread.php?t=1682799](http://ubuntuforums.org/showthread.php?t=1682799)

---

