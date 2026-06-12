---
title: "New to Ubuntu, need alittle help. plz!"
date: 2009-10-11
forum: General Help
---

### Post by kswilson99 on 2009-10-11
Hello,
I've just recently switched from using Windows XP to Ubuntu 9.04, because Windows was giving me too many problems.  I love the OS and all that it has to offer, only problem is getting us to it.  I'm taking classes for college and need some certain programs to be able to do my assignments.  If I could get some help finding the sudo code for these programs it would be very much appreciated:

Eclipse w/ C++ and a working compiler
A good Virtual Machine program to run Windows XP on. (if there is a VM that can us a regular HD instead of a VHD I would love it.)
&  Unreal Tournament (The Original): I don't need that for school, I just miss playing it.

Any other suggestions and tips would be helpful.  Thank You!

Mr. Wilson:guitar:

---

### Post by mitchumpalooza on 2009-10-11
Hello. 

Is this what you are looking for:
[http://flurdy.com/docs/eclipse/install.html](http://flurdy.com/docs/eclipse/install.html)
^(you'll have to download the updated packages though. these are old ones)

You'll want to download the updated java package here:
[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

You can download the version of eclipse with C/C++ tools here:
[http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)

Hope this helps.

---

### Post by mitchumpalooza on 2009-10-11
Might I suggest in replacement of Unreal Tournament, Nexuiz?

You should be able to find that in synaptic package manager or:

sudo apt-get install nexuiz

I found it *very* similar to Unreal Tournament...

---

### Post by kestrel1 on 2009-10-11
For a Virtual Machine try VirtualBox. You can download the latest version from:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by myromance123 on 2009-10-11
To get Unreal Tournament to run on Ubuntu, I suggest that you first attempt to install the game using Wine 1.0.1 (which should be installed by default).
If it doesn't work, then maybe what you need is the development release of WINE. How to get it up and running is [here]("http://www.winehq.org/download/deb"). After thats installed just pop in your UT CD and run the .exe (Wine will handle it automatically). You should be able to install it as per normal~

Enjoy that cup of Ubuntu!
 P.S: The reason why you're game doesn't work isn't necessarily because Wine can't handle it, it may be because you don't have any graphic drivers installed!

---

### Post by hantechbl on 2009-10-11
Almost any windows app can run under Wine as long as it does not rely on internet/networking functions taht is when you will run into trouble.  For a vm try qemu or VMware player.

---

