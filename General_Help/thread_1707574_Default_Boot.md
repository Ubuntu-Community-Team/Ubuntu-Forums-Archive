---
title: "Default Boot?"
date: 2011-03-15
forum: General Help
---

### Post by khoraski on 2011-03-15
This may be a dumb question, but how could I set a defualt boot? Like, instead of asking which OS to boot in from at startup, it just loads into a default one. And if you want to use the other one, you have to go back and change the default boot.
I tried boot settings, but it only lets me choose from a network, USB, DVD/CD, or normal. Which is just the grub list of OS's to choose from.

---

### Post by ianc1 on 2011-03-15
You could reduce the time in the grub2 config file so that the choices at boot time in the grub menu hang around for less time and the system boots into the default.  Mine moves on to the default after 10s and the default is Ubuntu.  If you reduce the time you obviously have to catch it on the way if you want to boot into the non-default OS.

If this is what you want let me know as I've done this before so I'm sure I can easily dig out the method.

---

### Post by Script Warlock on 2011-03-15
im not sure but burg also let you choose OS well yeah adjusting your boot time to 0 might do the trick. just be careful in modifying your grub.

---

### Post by khoraski on 2011-03-15
> **Script Warlock said:**
> im not sure but burg also let you choose OS well yeah adjusting your boot time to 0 might do the trick. just be careful in modifying your grub.

I've been Googling it but I can't find out how.

---

### Post by oboedad55 on 2011-03-15
You can install "startup-manager". From there you can set the default OS and how long the delay is, as well as screen resolution, etc.

---

### Post by Script Warlock on 2011-03-15
i'd rather recommend startup manager if you still want to try burg take a look at here and read carefully.. [http://www.omgubuntu.co.uk/tag/burg/](http://www.omgubuntu.co.uk/tag/burg/) and here [https://help.ubuntu.com/community/Burg](https://help.ubuntu.com/community/Burg)

---

### Post by drs305 on 2011-03-15
You can also install Grub Customiser, which was designed for Grub 2. Here is a link explaining how to use it:
[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

You can also take a look at the "Tasks" link in my signature line. That guide discusses how to set the default OS and timeout (although you may be more comfortable with Grub Customizer's GUI rather than the command line).

---

### Post by Script Warlock on 2011-03-15
> **drs305 said:**
> You can also install Grub Customiser, which was designed for Grub 2. Here is a link explaining how to use it:
[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

You can also take a look at the "Tasks" link in my signature line. That guide discusses how to set the default OS and timeout (although you may be more comfortable with Grub Customizer's GUI rather than the command line).

wow nice :)

---

### Post by khoraski on 2011-03-15
Thanks for your help, peeps. I found Startup-Manager, installed it, and now I can use it to change my boot time. THANKS. :D

---

