---
title: "evince"
date: 2010-06-18
forum: General Help
---

### Post by wbrb on 2010-06-18
upon rebooting my computer has hung. I ssh'd into it and see:

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
25361 u0324     20   0 59920  14m  11m D   51  1.4  68:31.91 evince
25367 u0324     20   0 60308  14m  11m D   51  1.5  68:12.96 evince                                                          25359 u0324     20   0 19928 6600 5344 R   49  0.6  69:47.92 evince-thumbnai
25344 u0324     20   0 59956  14m  11m D   48  1.4  70:54.23 evince

It took me a while to get that far because if I run ps, the bash session hangs. If I run apt, I'm told that:

u0324@bra-wbrown3:~$ sudo apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I can't kill -9 or killall the evince (even after a sudo su ) and I'm not exactly clear as to why. Prior to rebooting I had a few issues where PDF's were hanging and I had to force quit evince. I also tried to update my system. I assume that something here has to do with that.

Any ideas anybody?:confused:

---

### Post by wbrb on 2010-06-18
After a couple reboots /var/lib/dpkg/lock no longer gave an error and ps started working.

Instead apt-get upgrade gave me:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

After followed directions and rebooting again the system appears working.

---

### Post by pastalavista on 2010-06-18
That's the great thing about Ubuntu. It's a very smart OS. dpkg was stuck in an upgrade or installation (evince was upgraded recently)

---

