---
title: "GParted won't open"
date: 2010-11-09
forum: General Help
---

### Post by breNTx22 on 2010-11-09
I'm trying to open GParted to resize a partition so I can Dual boot with Windows 7.

I downloaded GParted through the software center, accessed it through "System > Administrator > ", type my password it, the GParted screen pops up and it's all grayed out except for the scanning feature, which is active. After about 5-10 seconds the program closes.

Any ideas?

---

### Post by TeoBigusGeekus on 2010-11-09
Open terminal, give
```
gksu gparted
```
and look for error messages after the program terminates.

---

### Post by breNTx22 on 2010-11-09
> **TeoBigusGeekus said:**
> Open terminal, give
```
gksu gparted
```and look for error messages after the program terminates.

I did that last night. I think all it said was "Aborted" but I didn't pay that close of attention. I'll do it again and post the results. I also tried that command from the root.

---

### Post by sohlinux on 2010-11-09
did you run it as sudo?

---

### Post by breNTx22 on 2010-11-09
> **sohlinux said:**
> did you run it as sudo?

I think so. That's what I meant when I mentioned 'root'.

What's the command to run it as sudo?

---

### Post by TeoBigusGeekus on 2010-11-09
Graphical applications should be run using [gksu and not sudo.]("http://www.psychocats.net/ubuntu/graphicalsudo")
Give 
```
gksu gparted
```
and post us any error messages.

---

### Post by sohlinux on 2010-11-09
normaly gksu for graphical apps but try run sudo gparted and see if you get any error messages pop up and paste them here, you may have a broken ownership/permissions in home from previous sudo graphical launch

---

### Post by garvinrick4 on 2010-11-09
Do you have any external USB drives connected that gparted cannot read? I do have a external that I have to disconnect before running gparted. Just an idea.

---

### Post by breNTx22 on 2010-11-09
> **garvinrick4 said:**
> Do you have any external USB drives connected that gparted cannot read? I do have a external that I have to disconnect before running gparted. Just an idea.

Nope.



When I type the command in I get:

"======================
libparted : 2.3
======================
"

---

### Post by TeoBigusGeekus on 2010-11-09
...and after it terminates?

---

### Post by breNTx22 on 2010-11-09
> **TeoBigusGeekus said:**
> ...and after it terminates?

Nothing or I would have posted it.

Thanks for the input thus far.

---

### Post by TeoBigusGeekus on 2010-11-09
Try with a live cd. Partitions have to be unmounted anyway for you to perform any operation on them.

---

### Post by WinRiddance on 2010-11-20
I downloaded Ubuntu Live CD and burned my image day before yesterday, on November 18th.
That's what I'm using at this very moment, to reply to this thread.
Well, guess what? The Gparted in the LiveCD has the same problem, at least on my system ...

Starting Gparted from the Gui shows an attempt which closes after a few seconds by itself.
Starting Gparted with sudo, directly from the terminal, terminates with this message:

> ======================
libparted : 2.3
======================

glibmm-ERROR **: 
unhandled exception (type std::exception) in signal handler:
what: basic_string::_S_create

aborting...
ubuntu@ubuntu:~$I need to work with one of my partitions for restoration & backup purposes. This really bites!

---

### Post by TeoBigusGeekus on 2010-11-20
See [this.]("https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/617885")

---

### Post by nunrgguy on 2010-11-20
I had exactly the same problem on one box but was able to do it from the live CD. If you look in synaptic there IS another partition utility (can't remeber what it's called but it comes up on search) that works good.

---

### Post by vhozard on 2010-11-24
It's fixed in the latest version of GParted.
Get the latest version here:
[http://packages.ubuntu.com/natty/gparted]("http://packages.ubuntu.com/natty/gparted")

---

