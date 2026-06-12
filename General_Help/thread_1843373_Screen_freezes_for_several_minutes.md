---
title: "Screen freezes for several minutes"
date: 2011-09-13
forum: General Help
---

### Post by klereng on 2011-09-13
Hi. 
Have some problems when I open my laptop lid. When I open it the screen freezes of some kind, if the last program I used was e.g firefox I can klick on links and different tabs, but i cant press anything on desktop panel or toolbar, and suddenly everything works perfectly. This can last for 1 minute up-to several.

I have a hp compaq 6530b and uses ubuntu 11.04

Can anyone help me?

---

### Post by 2F4U on 2011-09-13
Do you get this problem only a resume from suspend or also on other occasions, e.g. after a fresh boot?

---

### Post by klereng on 2011-09-13
> **2F4U said:**
> Do you get this problem only a resume from suspend or also on other occasions, e.g. after a fresh boot?

Only when I resume from suspend, when I lift up the lid. After a fresh boot everything is perfect.

---

### Post by varunendra on 2011-09-14
> **klereng said:**
> Hi. 
Have some problems when I open my laptop lid. When I open it the screen freezes of some kind, if the last program I used was e.g firefox I can klick on links and different tabs, but i cant press anything on desktop panel or toolbar, and suddenly everything works perfectly. This can last for 1 minute up-to several.

I have a hp compaq 6530b and uses ubuntu 11.04

Can anyone help me?
I think it is happening due to swapping of system state to the drive and resuming from there. If it is not too annoying, I'll suggest to leave it as it is. Else you may try using s2ram command which allows to save the state to ram and resume from there resulting in a much quicker resume. You will need to install **uswsusp** package (it is in the repositories). But I haven't tried it myself so can't say how good it is or whether it is bug-free, maybe you can tell us once you try it :)

Here's an old tutorial: [http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html](http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html)
Man Page for the command: [http://manpages.ubuntu.com/manpages/natty/man8/s2ram.8.html](http://manpages.ubuntu.com/manpages/natty/man8/s2ram.8.html)

Alternatively, you may try this fix (also an old one): [http://penguinparens.blogspot.com/2008/11/fixing-your-ubuntu-suspendresume.html](http://penguinparens.blogspot.com/2008/11/fixing-your-ubuntu-suspendresume.html)


Please tell us if any of these works for you the way you wish.

---

### Post by klereng on 2011-09-15
> **varunendra said:**
> I think it is happening due to swapping of system state to the drive and resuming from there. If it is not too annoying, I'll suggest to leave it as it is. Else you may try using s2ram command which allows to save the state to ram and resume from there resulting in a much quicker resume. You will need to install **uswsusp** package (it is in the repositories). But I haven't tried it myself so can't say how good it is or whether it is bug-free, maybe you can tell us once you try it :)

Here's an old tutorial: [http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html](http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html)
Man Page for the command: [http://manpages.ubuntu.com/manpages/natty/man8/s2ram.8.html](http://manpages.ubuntu.com/manpages/natty/man8/s2ram.8.html)

Alternatively, you may try this fix (also an old one): [http://penguinparens.blogspot.com/2008/11/fixing-your-ubuntu-suspendresume.html](http://penguinparens.blogspot.com/2008/11/fixing-your-ubuntu-suspendresume.html)


Please tell us if any of these works for you the way you wish.

Hi. Thanks for respons. I don't know if this is the right solution, I tried it, but don't think I succeeded.
Still the same oroblem....

---

### Post by klereng on 2011-09-27
Hi again.
I've tried the guide previous mentioned, but it seems my ram is unknown for my system this is what i get when I type sudo s2ram

Machine is unknown.
This machine can be identified by:
    sys_vendor   = "Hewlett-Packard"
    sys_product  = "HP Compaq 6530b (GW688AV)"
    sys_version  = "F.13"
    bios_version = "68PDD Ver. F.13"
See [http://suspend.sf.net/s2ram-support.html](http://suspend.sf.net/s2ram-support.html) for details.

My problem has become more severe, now my system hangs even after a reboot, and suddenly after a minute and sometimes upto 5 its works perfectly again.
Is it possible that my RAM is broken in some kind of way?

---

