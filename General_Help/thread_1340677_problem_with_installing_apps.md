---
title: "problem with installing apps"
date: 2009-11-28
forum: General Help
---

### Post by Skyturnred on 2009-11-28
Well before you ask, yes I am brand new to Ubuntu. And yes I researched this (to the best of my ability) on google. But I just can't figure it out, it's so different from Windows. Anyways I'll get to it. 

I just installed Ubuntu yesterday and I am trying to get evolution setup with my hotmail acount. I found this

[http://ubuntuforums.org/showthread.php?t=200408](http://ubuntuforums.org/showthread.php?t=200408)

which seems like a great tutorial. Only the problem is, when I get to the point where I type "sudo apt-get install inetutils-inetd", the terminal doesn't install anything. Instead it returns:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package inetutils-inetd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

I know that you can just tell me what to do and help me fix my problem but that is not what I am looking for. I want to *learn* ubuntu. I hope I don't sound too demanding. Anyways, this happens about 99% of the time where I have to install something using the terminal. My guess is there is some kind of package I am supposed to download? Thanks for the help.

---

### Post by fluffman86 on 2009-11-28
Ah, the package inetutils-inetd is not available directly from canonical, but is available through other Ubuntu developers.  What you need to do is expand the places that apt-get, synaptic, etc, all look for available packages.  

Go to System > Administration > Software Sources, and check the first 4 boxes on the main tab.  Close the window, reload your list of available apps, then run your command again, or install it with synaptic (System > Administration > Synaptic).

---

### Post by Skyturnred on 2009-11-28
Thanks for the help, that explains a bit. I got it installed through Synaptic. But I still have a problem. When I went into Software Sources, the first 4 options were already installed, and the install code for inet still didn't work... also, I got the Ubuntu distribution directly from this site. Should that be?

---

