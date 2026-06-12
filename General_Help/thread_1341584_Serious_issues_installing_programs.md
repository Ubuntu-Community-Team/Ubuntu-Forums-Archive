---
title: "Serious issues installing programs"
date: 2009-11-29
forum: General Help
---

### Post by Rasenganfan2 on 2009-11-29
[FONT=Comic Sans MS]Hello, I'm new to Ubuntu 9.10. I used to use 8.10 Intreped Ibex, but uninstalled it after some serious mess ups. I installed Ubuntu 9.10 as a fail-safe to Windows. However, since then, some things have been seriously messed up. Not in Windows, but in Ubuntu. 

My problems are:

1.) I can't install programs using the command line
2.) I can't install programs using the Software Center
3.) I can't install programs using a .deb package it says "This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."
4.) When I open Synaptic Package Manager, it says "E: Malformed line 1 in source list /etc/apt/sources.list.d/pidgin-ppa.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report." which, not really knowing what that means, I know it's bad.

Help would be greatly appreciated.
[/FONT]

---

### Post by john newbuntu on 2009-11-29
[B]Open this page and go to the section titled: "Manually add repositories" and try it out.
[/B]

 **[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)**

---

### Post by bwang on 2009-11-29
It means something is wrong with your sources.list
Can you post the contents of /etc/apt/sources.list.

---

### Post by snova on 2009-11-30
> **Rasenganfan2 said:**
> 4.) When I open Synaptic Package Manager, it says "E: Malformed line 1 in source list /etc/apt/sources.list.d/pidgin-ppa.list (dist parse)

That file (/etc/apt/sources.list.d/pidgin-ppa.list) is probably the source of the problem.

It appears to be a familiar problem as well. Try the instructions [here]("http://ubuntuforums.org/showthread.php?p=7264681"), but replacing "jaunty" with "karmic", and then re-update.

---

### Post by Rasenganfan2 on 2009-11-30
Thank you very much. Now I just need to figure out what to do to install Pidgin and then I will be fine...

I also discovered the problem with Software Manager... when I go to a program, such as Flash Plug-in for Mozilla browsers, it says "Not available for your hardware architecture". Does that mean that my hardware doesn't meet the minimum requirements? Do I need to have a Nvidia graphics card or something?

If you need my computer's tech specs, here they are:

Gateway M-1625 laptop
2GB RAM
ATI Radeon X1270
AMD TUrion 64x2 (32-bit CPU)

So any more help would be appreciated.

---

### Post by aviedw on 2009-11-30
To install Pidgin, first open up the command line. 

Then type sudo apt-get install pidgin. That should do it.

---

### Post by Rasenganfan2 on 2009-12-05
OK, I did that, but that actually doesn't resolve anything... it just messes up my terminal. I'm unable to install ANYTHING. Not Flash, not Java, not Flock, not anything.

---

