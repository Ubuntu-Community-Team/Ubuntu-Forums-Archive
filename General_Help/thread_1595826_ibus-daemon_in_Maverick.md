---
title: "ibus-daemon in Maverick"
date: 2010-10-13
forum: General Help
---

### Post by Rypervenche on 2010-10-13
I use iBus to type in Chinese (chewing for traditional characters), as well as anthy for Japanese. Ever since I upgraded to Maverick, I've been having a few problems with the ibus-daemon (or maybe it's just iBus in general).

Basically after a while of using it, it no longer changes pictures when I turn it on, and I can't see what I'm typing, although it does still produce what I want if I type blindly. Also, I cannot restart it or close it from the top panel. I thought it was maybe Compiz that was doing it, but I have since turned it off and I still get the same results. It doesn't happen right away, but after maybe 10 minutes or so of using my laptop, it does it again.

I'm on an Eee PC 1201PN.

Please help. I hate having to have to restart my computer to be able to type in another language.

---

### Post by stryderjzw on 2010-10-13
I have something similar.

I have chewing to type Chinese as well. On Maverick, whenever chewing tries to come up, the window flickers a couple dozen times and the ibus-daemon dies. I believe it's trying to bring up the Chewing Settings menu.

I've turned off Compiz and it's okay. I'm using the ATI fglrx drivers on Maverick.

Not sure if it's the same problem, but looking for solutions as well.

---

### Post by thomasyen on 2010-10-13
I have the same prolem, namely that whenever I start an application, a box with "Settings" in Chinese in the title keeps flickering on and off, and IBus becomes unresponsive. I tried switching the window manager from Compiz to Metacity, but the problem persisted. After killing the IBus daemon, I restarted it from the command line, but IBus only printed the following error: ```
(ibus-daemon:2673): IBUS-CRITICAL **: _context_request_engine_cb: assertion `bus_input_context_has_focus (context)' failed
```

I googled around but didn't see anything helpful. I'm going to try using a previous kernel.

Update: I tried using the older, pre-upgrade 2.6.32 kernel. Everything works fine (namely, IBus-daemon responds to every command such as "display about box", changes input method on command normally, etc.). Sigh.

---

### Post by stryderjzw on 2010-10-13
Thanks thomasyen. 

Yeah, that's my problem. At least we narrowed it down. I wonder if we should file a report somewhere.

---

### Post by Rypervenche on 2010-10-15
I have found that the one causing the problem is /usr/share/ibus/ui/gtk/main.py . When I turn this off, it stops. When I load Ubuntu without ibus, I have no problems. I even often have main.py which freezes and hogs 100% of my CPU until I force kill it.

I suppose I'll try adding this as a bug under ibus, I don't know if it will do any good though.

---

### Post by alexfish on 2010-10-15
> **Rypervenche said:**
> I have found that the one causing the problem is /usr/share/ibus/ui/gtk/main.py . When I turn this off, it stops. When I load Ubuntu without ibus, I have no problems. I even often have main.py which freezes and hogs 100% of my CPU until I force kill it.

I suppose I'll try adding this as a bug under ibus, I don't know if it will do any good though.

Needs to be posted  : ref Python ibus

also look look at 

**[B]Sticky:**[/B] [Known Maverick Meerkat issues/bugs with workarounds]("http://ubuntuforums.org/showthread.php?t=1588889")

alexfish

---

### Post by thomasyen on 2010-10-28
It appears that the Ibus developers have solved this problem in version 1.3.8. You can install this version from Peng Huang's Ibus PPA.

---

### Post by Rypervenche on 2010-10-28
Oh yeah thanks for reminding me. I had found the ppa on the ubuntu-tw. For those who still have this problem, "sudo add-apt-repository ppa:ossug-hychen/ibus" then "sudo apt-get update && sudo apt-get upgrade" and you're all set. Log out and you will have no more problems.

---

### Post by Ian Clark on 2011-02-05
Looks like the problem is back, only this time in relation to IM. Using Empathy or web-based IM through FF causes flashing and skips in the ability to input Chinese.

---

