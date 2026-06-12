---
title: "sl-modem-daemon"
date: 2006-05-04
forum: General Help
---

### Post by jsmidt on 2006-05-04
I am trying to follow the wiki for setting up a modem.  It says I need to run apt-get install sl-modem-daemon.  When I do I get this error:

Unpacking sl-modem-daemon (from .../sl-modem-daemon_2.9.10+2.9.9d-6ubuntu1_i386.deb) ...
Setting up sl-modem-daemon (2.9.10+2.9.9d-6ubuntu1) ...
FATAL: Module slamr not found.
SmartLink modem driver not available for this Kernel. Please read README.Debian
or try to install the package sl-modem-modules-2.6.15-20-686. Exiting...
invoke-rc.d: initscript sl-modem-daemon, action "start" failed.


The is no sl-modem-modules-2.6.15-20-686 or sl-modem-modules-* .  What can I do?

---

### Post by Sutekh on 2006-05-04
But there is [Ubuntu Pacakges - sl-modem-source](http://packages.ubuntu.com/breezy/misc/sl-modem-source), which you need to compile.  This creates a module which you can insert/'modprobe' into the kernel.

I assume this is the link you are following [Ubuntu Wiki - Dialup Modem HOWTO](https://wiki.ubuntu.com/DialupModemHowto)

---

### Post by Bunkai on 2006-05-08
jsmidt,

Did you get your modem working? I'm having a similar problem (same fatal error msg.)

If you figured it out it would be a great help to me to know what you did. You can see my post [here]("http://ubuntuforums.org/showthread.php?p=995910#post995910").

If not, keep your eyes glued to that post and maybe we can get this thing, eh?

Bunkai

---

### Post by jsmidt on 2006-05-08
[QUOTE=Bunkai]jsmidt,

If not, keep your eyes glued to that post and maybe we can get this thing, eh?

Bunkai[/QUOTE]

    I will be working on this all week.  Hopefully I can get the modem working.  It is really hard to enjoy Ubuntu(or any OS) when you can't get the internet.  I'll keep you informed on my progress.

---

### Post by Bunkai on 2006-05-10
Thanks, will let you know if I have a breakthrough.

---

