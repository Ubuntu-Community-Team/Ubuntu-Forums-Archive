---
title: "Maverick: suspend fails"
date: 2010-10-12
forum: General Help
---

### Post by vanhecke on 2010-10-12
I upgraded from 10.04 to 10.10
Worked fined, but suspend doesn't work anymore.
When I click suspend, a tty1 terminal screen appears, exactly as you would hit ctrl+alt+F1, with the exception that no input is possible. 

I'm a newbie and an Ubuntu fan but I absolutely have no idea how to solve this...

My specs:
HP 8540w, Kernel: 2.6.35-22, Nvidea Quadro FX 880M

---

### Post by djscurippio on 2010-10-13
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install)

> When the XHCI module is loaded for USB 3.0 operation the system cannot suspend. Manually unloading XHCI will allow suspend to complete normally. To avoid future suspend problems, the workaround is to add SUSPEND_MODULES="xhci-hcd" to /etc/pm/config.d/unload_module then the system can suspend normally.

Already tested, proposed solution works!

---

### Post by vanhecke on 2010-10-13
Thanks djscurippio,

You put me at the right track! your workaround is close, but does no longer work. Nevertheless, I found the official filed bug (Bug #522998 ), and the solution can be found at comment #30 by creeson:

This post caught my eye:
d3mia7 wrote on 2010-05-05: #11
Note that the module has been renamed "xhci_hcd" in the latest mainline kernel (2.6.34-rc6).

There is a typo in this post. The module has been renamed to "xhci-hcd", not "xhci_hcd".

This workaround fixes the problem for me:
create files : /etc/pm/config.d/00sleep_module and /etc/pm/config.d/unload_module
add line to files : SUSPEND_MODULES="xhci-hcd"

----------

This works fine for my Maverick :-)

---

### Post by mercmobily on 2010-10-31
Hi,

this worked for me... Suspending is really important to me, thank you for helping out!

Merc.


> **vanhecke said:**
> Thanks djscurippio,

You put me at the right track! your workaround is close, but does no longer work. Nevertheless, I found the official filed bug (Bug #522998 ), and the solution can be found at comment #30 by creeson:

This post caught my eye:
d3mia7 wrote on 2010-05-05: #11
Note that the module has been renamed "xhci_hcd" in the latest mainline kernel (2.6.34-rc6).

There is a typo in this post. The module has been renamed to "xhci-hcd", not "xhci_hcd".

This workaround fixes the problem for me:
create files : /etc/pm/config.d/00sleep_module and /etc/pm/config.d/unload_module
add line to files : SUSPEND_MODULES="xhci-hcd"

----------

This works fine for my Maverick :-)

---

### Post by dt_ on 2010-11-07
Thank you, this helps my computer finally sleep! (Sort of) :) ..
The catch is:

- When it's asleep, the mouse is still turned on (i.e. it's an optical mouse, and the red optical sensor is still on all the time), though I'm not sure if this is fine/intentional or not, 
- I can't wake up the computer with the keyboard like i can in Windows... only by pressing the power button

and, (and this is the kicker):

- **The computer won't resume properly**.

When I wake it up from sleep by pressing the power button, the screen turns on, but it just shows a blank (black) display. No flashing cursor, and nothing responds to key press. I have to hard reboot the computer to get anything to work. :(

Has anyone else had this problem, or does anyone have any suggestions for remedying it?

Thanks! :)

dt



> **vanhecke said:**
> Thanks djscurippio,

You put me at the right track! your workaround is close, but does no longer work. Nevertheless, I found the official filed bug (Bug #522998 ), and the solution can be found at comment #30 by creeson:

This post caught my eye:
d3mia7 wrote on 2010-05-05: #11
Note that the module has been renamed "xhci_hcd" in the latest mainline kernel (2.6.34-rc6).

There is a typo in this post. The module has been renamed to "xhci-hcd", not "xhci_hcd".

This workaround fixes the problem for me:
create files : /etc/pm/config.d/00sleep_module and /etc/pm/config.d/unload_module
add line to files : SUSPEND_MODULES="xhci-hcd"

----------

This works fine for my Maverick :-)

---

### Post by kostmo on 2010-12-06
> **dt_ said:**
> 
- **The computer won't resume properly**.

When I wake it up from sleep by pressing the power button, the screen turns on, but it just shows a blank (black) display. No flashing cursor, and nothing responds to key press. I have to hard reboot the computer to get anything to work. :(


This is exactly what happens to me.

---

