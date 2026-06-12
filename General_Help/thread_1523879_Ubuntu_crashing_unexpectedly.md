---
title: "Ubuntu crashing unexpectedly"
date: 2010-07-04
forum: General Help
---

### Post by savvas.andreas on 2010-07-04
Hello,

I am a fairly new Ubuntu user and have been experiencing some odd problems.

Specifically, when I use Chrome to watch a flash video once in while my machine crashes in a completely unrecoverable ways. 
The screen either freezes up or starts bleeping and the keyboard is no longer usable so I can reboot my machine from the command line.
At other times, the machine will just decide to restart by itself(!) without any prior warning or indication.
So, the only way to restart the machine is to actually press the power button for a few seconds..
And on top of that, I can't immediately restart it because if I do it just starts beeping without booting up. I actually have to wait about 15' before I even attempt to boot the machine again..:-S 

Does anyone have an idea of how to go about troubleshooting a problem like that? I appreciate I could stop using Chrome but 1) I love this browser and 2) I've noticed the same problem happening in Firefox as well.

Does everybody agree that there should be a better error handling mechanism which would bring down only the crashed application and not the entire system?

Some tech specifications of my environment:
Release 10.04(lucid)
GNOME 2.30.0
RAM 2G
NVIDIA graphics card (with the up to date driver installed)
Four CPU's at 1.6GHz each

Kind Regards,
Savvas.

---

### Post by dino99 on 2010-07-04
you might find usefull errors logged into:
.xsession-errors (/home, unhide with ctrl+h)
system admin logviewer

check driver activation: system admin hardware driver

you need to activate canonical partner repo into synaptic

and use medibuntu for non-free codecs

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Mr Nemo on 2010-07-04
I have this same problem. Basically there is no sure fire way to fix this since flash is pretty unstable with Ubuntu. I've been searching for a while for a solution, but the truth is well just have to wait until adobe decides to fix this problem.

This is a link to one of my threads. The advice in it actually did reduce the frequency of my system crashes quite a bit. [http://ubuntuforums.org/showthread.php?t=1510936](http://ubuntuforums.org/showthread.php?t=1510936)

npviewer.bin seems to be the culprit for this problem. Setting the nice value lower for npviewer also seems to help a bit. (The only way I know how to change the nice value for a program is to run a flash video, go into system monitor, find npviewer, right click on it and go to set priority. Setting the nice value (priority value) to a lower number will make it a higher priority for the processor)

In the end there is no complete fix for this problem, or at least I haven't found one yet.

---

### Post by dino99 on 2010-07-04
there is no issue with flashplugin-installer on 32 bits system

---

### Post by happyhamster on 2010-07-04
> **savvas.andreas said:**
> 
Does everybody agree that there should be a better error handling mechanism which would bring down only the crashed application and not the entire system?

Firefox very recently implemented something like that:
[http://news.slashdot.org/story/10/06/23/0123243/Firefox-364-Released-With-Out-of-Process-Plugins](http://news.slashdot.org/story/10/06/23/0123243/Firefox-364-Released-With-Out-of-Process-Plugins)

Flash on linux is still a disaster though. 
> 
NVIDIA graphics card (with the up to date driver installed)

Do you mean the proprietary driver, or nouveau?

> 
Four CPU's at 1.6GHz each

Some systems are experiencing added trouble caused by the utility "irqbalance". Try testing with that package uninstalled.

Another suggestion: check your RAM. Run memtest for a few hours (available from the grub boot menu, or even better: run it from a live-cd).
 
Good luck.

---

### Post by lovinglinux on 2010-07-04
I would also recommend checking your RAM and CPU temps.

Although flash loves to crash the browser, the behavior your are experiencing suggest a memory issue.

---

