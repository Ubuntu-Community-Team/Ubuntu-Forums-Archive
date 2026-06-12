---
title: "Ubuntu 11.10 left click not working."
date: 2011-10-24
forum: General Help
---

### Post by C.P.T. on 2011-10-24
Hey everyone.

My specs:

- Toshiba Satellite 5200
- 1GB RAM
- 1.9GHz P4 M Processor
- 32MB NVidia GeForce4 460 Go

Let me start from the beginning:

I've been a windows user all my life. I decided to switch to Xubuntu because I liked the look of it, and I fancied a change. Upon trying the Xubuntu 'try without installing' option, however, I found that I could not left click, try as I might.

I assumed (perhaps foolishly) that this problem was specific to Xubuntu, and that it would be worth giving Ubuntu a try (as I preferred the GUI anyway). I tried the 'try without installing' option, and, to my delight, found that the left click was working well. I played around with Ubuntu for a while and quickly found I really liked using it, so proceeded to do a complete install, erasing XP.

This turns out to have been a very, very stupid thing to do.

I rebooted, and guess what.

No.

Left. 

Click.

Oh, the horror.

Basically, I'm now trapped in the Ubuntu 'try without installing' setting, guffawing across the internet, looking for a solution to my problem.

Here's what I've tried based on the advice I've been given thus far:

I found that in the 'try without installing' mode I can move my mouse via my USB mouse, and via my laptop trackpad, however can only click using the mouse, whereas in actual install mode, I can move both, but only right click with the USB mouse. This lead me to try disabling the trackpad totally. I found the FN laptop shortcut for disabling doesn't work at all, and that on this laptop it is impossible to enter the bios. (It can apparently only be done via an application in Windows. Great.).

Beyond that I have absolutely no idea what I'm doing.

I have no alternative to this laptop (I'm using it as a last resort due to my desktop breaking), so it's imperative to me that I have it functional again.

Thanks kindly,

-*C.P.T.*

---

### Post by C.P.T. on 2011-10-25
Anyone?

---

### Post by C.P.T. on 2011-10-25
Surely someone has some idea of the problem?

---

### Post by C.P.T. on 2011-10-25
I really need this fixed by tomorrow...

---

### Post by jean noel on 2011-10-25
I may be wrong, but you do not need windows to have access to the bios. You may need to press a key during boot, may be esc or del. Anyway, why do you connect the mouse?
Btw i use 10.04.
Regards
Jean Noel

---

### Post by bala1987 on 2011-10-25
> **C.P.T. said:**
> I really need this fixed by tomorrow...

I had similar problem , and I use a external mouse apart from my touchpad.. 

I just left-clicked my touchpad mouse once.. 

Now everything seems okay... both touchpad left click and external mouse left click works. 

Let me know if this fixes your problem

---

### Post by Rafterman414 on 2012-02-12
So I am going to revive this thread because I am having the exact same issue on my Sony VAIO VGN-CS215J running Ubuntu 11.10 64 bit, up to date on updates. I tried the fix listed here at [http://pessetto.com/question2answer/index.php?qa=52&qa_1=ubuntu-11-10-clickpad-not-working-right-click-not-working](http://pessetto.com/question2answer/index.php?qa=52&qa_1=ubuntu-11-10-clickpad-not-working-right-click-not-working)
I installed the patch and did the reboot with no luck at all. For me not even pressing the left click on the touchpad works, nor does left clicking the mouse, or tapping on the touchpad for a click. I have also tried to remove the mouse and plug it back in with no luck in that department either. It seems so far the only fix is to restart the machine.

Is anyone aware of any solutions for this issue? I have tried to search but so far I am coming up with plenty of reports about the problem with no solutions. I appreciate any support and assistance that you can provide. Thanks.

---

### Post by sdmiller on 2012-03-06
I want to second that this is indeed an issue. Since upgrading from 10.04 to 11.10, I've seen this issue on both my Lenovo Thinkpad and Zeareason Verix laptops. Mouse clicks completely stop registering, whether from the touchpad, USB mouse, or even keyboard proxys (via the Universal Access->Pointing and Clicking->Mouse Keys option). A reboot appears to be the only option.

This happens ~ once every 2 days. Including right now, in fact. It is an extremely annoying problem, and I can't imagine the 3 who have posted here are the only ones who have experienced it.

SPECS:
Laptop 1
---
Model: Lenovo Thinkpad W700 
OS: Ubuntu 11.10 64 bit
Graphics Card: Nvidia QuadroFX 3700M
Xsessions: Observed in Unity and Gnome Classic

Laptop 2
-----
Model: Zareason Verix
OS: Ubuntu 11.10 64-bit
Graphics Card: Nvidia GTX 570M
Xsessions: Observed in Gnome Classic


EDIT: If you are trying to cope with this, I'd recommend looking into using XMonad ([http://xmonad.org](http://xmonad.org)) for window tiling and Pentadactyl ([http://dactyl.sourceforge.net/pentadactyl/](http://dactyl.sourceforge.net/pentadactyl/)) for web browsing. This bug becomes significantly less crippling with mouseless navigation options.

---

### Post by spedax on 2012-03-07
> **sdmiller said:**
> I want to second that this is indeed an issue. Since upgrading from 10.04 to 11.10, I've seen this issue on both my Lenovo Thinkpad and Zeareason Verix laptops. Mouse clicks completely stop registering, whether from the touchpad, USB mouse, or even keyboard proxys (via the Universal Access->Pointing and Clicking->Mouse Keys option). A reboot appears to be the only option.

This happens ~ once every 2 days. Including right now, in fact. It is an extremely annoying problem, and I can't imagine the 3 who have posted here are the only ones who have experienced it.

SPECS:
Laptop 1
---
Model: Lenovo Thinkpad W700 
OS: Ubuntu 11.10 64 bit
Graphics Card: Nvidia QuadroFX 3700M
Xsessions: Observed in Unity and Gnome Classic

Laptop 2
-----
Model: Zareason Verix
OS: Ubuntu 11.10 64-bit
Graphics Card: Nvidia GTX 570M
Xsessions: Observed in Gnome Classic


EDIT: If you are trying to cope with this, I'd recommend looking into using XMonad ([http://xmonad.org](http://xmonad.org)) for window tiling and Pentadactyl ([http://dactyl.sourceforge.net/pentadactyl/](http://dactyl.sourceforge.net/pentadactyl/)) for web browsing. This bug becomes significantly less crippling with mouseless navigation options.

I have the same problem on thinkpad T420. Left mouse click just stops working every couple days. Very annoying. Anyone found a fix yet ?

---

