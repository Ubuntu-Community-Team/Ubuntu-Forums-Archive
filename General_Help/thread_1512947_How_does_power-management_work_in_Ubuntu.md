---
title: "How does power-management work in Ubuntu?"
date: 2010-06-18
forum: General Help
---

### Post by morgonhed on 2010-06-18
Hi!

Can someone please explain to me how power-management works in Ubuntu Lucid and how it is configured (or point me to some documentation)?

Evidently some part is managed by the kernel itself, then there are some demons (with configuration under /etc) then there is the gnome-power-manager (via gconf-editor) and then there are the settings under System->Preferences->Power Management.

How does all of this fit together?

For example I cannot configure my laptop to do nothing on critical battery in the Power Managent preferences, but I can configure it via the gnome-power-manager, except that if I configure it there it does not work.

So the Power Managent preferences seem to be more than just a frontend gnome-power-manager and it restricts my ability to configure the power management the way I want it to be ... so please provide some insight.

Many thanks!

---

### Post by Digital Hick on 2010-06-19
> How does power management work in Ubuntu?

[SIZE="6"]It doesn't!
[/SIZE]Ubuntu does next to nothing in my opinion for power management.
  
You have to install the Nvidia driver to ramp back the GPU when it is not being used.  The Nouveau (sp?) driver does nothing.  I don't know about ATI cards and their performance.

You have to peg the processors to a lower level to save power with gnome applets.  One for each core at that.

The screen brightness has to be turned down by you to the lowest level.  Ubuntu simply does not take the screen brightness down as far as Windows will.
  
And then the fun begins... 
You have to slough through kernel settings to find other things to turn off.  Install laptop-mode-tools and create hooks for pm-utils to turn it on when you go to battery power.  

Powertop does nothing!  It never shuts anything off, it just pretends it does.  

Granola is worthless, it just sets their in the background eating cycles while your battery runs down.  

Hardware that is not being used does not turn it self off.  USB, CD/DVD drives, Wifi goes full bore all the time, killing your battery.  
This has got to be the most hacked-up mess in Ubuntu next to Ubuntu One.

With that said, 10.04 is actually a nice operating system as long as you do not get to far from a power socket.  So two problems, many other advantages to Ubuntu 10.04.

DH:confused::popcorn:

---

