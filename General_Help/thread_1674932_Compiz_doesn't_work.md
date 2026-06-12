---
title: "Compiz doesn't work"
date: 2011-01-24
forum: General Help
---

### Post by John Lucsoft on 2011-01-24
Hi, I hope I'm posting in the right place. I'm relatively new to ubuntu... here goes:

Compiz is not working. I have compiz installed, together with the CompizConfig settings manager, and the simple ccsm. When I change the settings in either of those things (or in System->Administration->Appearance->visual effects), no changes actually occur. I tried uninstalling and reinstalling compiz, and I tried a host of other things I could find advised for my situation. I'm at my wits end about this. 

When I type 'compiz' into the terminal, the screen, and all the windows, flash like crazy for a few seconds, and then the terminal returns:


> Xlib:  extension "GLX" missing on display ":0.0".
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

and just hangs there indefinitely.

Any advice? Thank you very much. I appreciate it.

---

### Post by davidmohammed on 2011-01-24
please type in a terminal

lspci | grep VGA

copy and paste the output here in a reply.

---

### Post by John Lucsoft on 2011-01-24
> 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

Thank you. I should note that it was working before, and then suddenly stopped, I'm not sure what I did to tick it off :D

---

### Post by clhsharky on 2011-01-24
John Lucsoft

This may be of some help

The Great Desktop Effects FAQ of 2010
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)


Sharky

---

### Post by John Lucsoft on 2011-01-24
Thanks. I looked through that thread, but I didn't find much assistance there, most of it I already knew or didn't address my problem. I did run the compiz check linked there ([here]("http://forlong.blogage.de/entries/pages/Compiz-Check")), and this is what I got: 
> Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 


What does that mean?

---

### Post by John Lucsoft on 2011-01-24
Also, if it's related at all: when I open the additional drivers window (jockey-gtk), I get no proprietary drivers in use on this system'. I'm not sure if there's a driver issue or not. 

Thanks for the assistance.

---

### Post by davidmohammed on 2011-01-24
do you have dual graphics cards?  e.g. both an intel and either an nvidia/ati?  

Did you try to install the proprietary drivers such as nvidia or ati?

---

### Post by John Lucsoft on 2011-01-24
I don't think I have a dual graphics card, but I don't really know. I know that > 00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
 is all I get when I enter 'lspci | grep VGA'.

I know I have a bunch of different nvidia stuff installed, but I might be missing something, so I'm going to try to install the nvidia drivers fresh.

---

### Post by John Lucsoft on 2011-01-24
I'm going to mark this as solved, even though I never did find a solution. 

Lots of things were acting up, I don't know what went wrong, so I just put a fresh installation of Ubuntu 10.10 on my machine. I had my home folder in a separate partition, and my files on a partition that's shared between Windows and Linux (NTFS), so all I need to do is install the programs I need. All is well... for now.

Thanks for your help.

---

### Post by John Lucsoft on 2011-01-24
I'm going to mark this as solved, even though I never did find a solution. 

Lots of things were acting up, I don't know what went wrong, so I just put a fresh installation of Ubuntu 10.10 on my machine. I had my home folder in a separate partition, and my files on a partition that's shared between Windows and Linux (NTFS), so all I need to do is install the programs I need. All is well... for now.

Thanks for your help.

---

### Post by davidmohammed on 2011-01-25
... actually the reason why was in your last reply - you should not install nvidia drivers since you dont have a nvidia graphics card.

the solution would have been something like

sudo apt-get remove nvidia-*

or something like that.

---

