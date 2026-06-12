---
title: "compiz extra plugins"
date: 2010-10-15
forum: General Help
---

### Post by scottykal12 on 2010-10-15
I up graded to 10.10 the other day and everything was working when I ran the update manager today and restarted my computer I notice that most of my compiz stuff wasn't working. I checked the synaptic package manager and notice that compiz-fusion-plugin-extra was not installed, tried to install is and got this message:

>  scott@scott-laptop:~$ sudo apt-get install compiz-fusion-plugins-extra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 compiz-fusion-plugins-extra : Depends: compiz-core-abiversion-20091102
E: Broken packagesI want emerald themes to work so if I could get some help I would appreciate it.

thank you in advance
-Scott

---

### Post by Quackers on 2010-10-15
Compiz fusion plugins extras and emerald are available in System > Admin > Synaptic Package Manager. Enjoy :-)

---

### Post by scottykal12 on 2010-10-15
I knew where it was it just wasn't letting me install it.

I figured it out though:

I had to purge the compiz ppa then it let me install the package and now everything is back to normal.

(i accidently  updated the compiz ppa using tweak and it wasn't going to work with 10.10)

Scott

---

