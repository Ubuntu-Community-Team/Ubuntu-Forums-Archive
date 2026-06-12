---
title: "Shame on me for upgrading from 10.04 LTS to 11.10. Can't boot up anymore."
date: 2011-11-02
forum: General Help
---

### Post by juicyoner on 2011-11-02
Shame on me for upgrading from 10.04 LTS to 11.10.

When I boot up, get to the grub menu and make a selection the machine will appear to be booting up. I will see the ubuntu icon for a moment then it goes black and spits out error messages. First one is something like..

"nxserver disabled... blah blah /etc/something.node.cfg"

Then it spits out some more seemingly random error messages and waits. At this point I have to click my laptop's *power button* and I'll get more errors to the display. Then it will wait again. I click my power button one more time and it shutsdown.

This happens no matter what kernel I choose from the grub menu **** INCLUDING MY PREVIOUSLY WORKING 10.04 LTS *****

HOWEVER - when I pick any of the recovery modes, I can log in and run "startx" however, I am completely unsure what to do. At this point I'd like to trash 11.10 and go back, but at the *very least* I'd just like to be able to run Ubuntu properly.

Anyone come across this? Any ideas?

---

### Post by rbishop on 2011-11-02
I am in total agreement!  Shame on me for upgrading to 11.10 from 10.04!

I am able to boot and use the system, but OMG I am so tired of having to look around to find the items that were right at my disposal in 10.04.  I am really thinking about wiping out my Ubuntu partition and reinstalling 10.04 from scratch to get back to a usable Ubuntu.

---

### Post by raja.genupula on 2011-11-02
hi man sometimes graphics driver also going to be a cause for this.what kind of graphic card you have ?

---

### Post by juicyoner on 2011-11-02
Hi Raja - 

When I run "lspci -v" I get this.


[FONT="Courier New"]00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
        Subsystem: Lenovo Device 3920
        Flags: bus master, fast devsel, latency 0, IRQ 30
        Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        I/O ports at 5050 [size=8]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915
[/FONT]

---

### Post by juicyoner on 2011-11-02
When I log into Windows 7, all I can tell is that I have a "Intel(R) HD Graphics" card.

---

