---
title: "Compiz won't start - no rendering method"
date: 2010-10-14
forum: General Help
---

### Post by unsober on 2010-10-14
I'm on a *fresh, brand new* 10.04 Ubuntu install. All I've done so far is install the recommended ATI proprietary driver from the hardware manager. I have an [ATI] Radeon HD 2400

When I try to run compiz from CLI, I get this:
```
jim@jim-desktop:~$ sudo compiz
Blacklisted PCI ID 8086:2562 detected

Launching fallback window manager

```**Output of./compiz-check**
```
jim@jim-desktop:~$ ./compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc RV 610LE PCI [Radeon HD 2400]
 Driver in use:         fglrx
 Rendering method:      [COLOR=Red]None[/COLOR]

Checking if it's possible to run Compiz on your system... [COLOR=Red] [SKIP][/COLOR]

 Checking for hardware/setup problems...          [COLOR=Red] [SKIP][/COLOR]

At least one check had to be skipped:
[COLOR=Red] Error: [COLOR=Black]No rendering method in use (AIGLX, Xgl or Nvidia) [/COLOR][/COLOR]

```Can someone with more knowledge than I try to help? Why am I getting rendering errors?

_Additional information in attachments_

---

### Post by unsober on 2010-10-14
I google this and I get tons of hits, but not really any solutions..

---

### Post by unsober on 2010-10-14
I know I'm not the only one who has had this problem... :rolleyes:

There must be a solution out there somewhere

---

### Post by unsober on 2010-10-14
hmm okay. At this point I'm just giving up.
I've bumped this a few times and no responses at all. I guess I can't ever use compiz/emerald

I would of thought since it's a fresh 10.04 Ubuntu install it would be easy to work with.
There's no hope:|

---

