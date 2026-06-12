---
title: "GRUB2 timeout problem"
date: 2009-12-20
forum: General Help
---

### Post by tombaugh on 2009-12-20
I configured my GRUB2 menu to have a 5 second timeout, but the menu is either skipped (with USB keyboard attached) or it doesn't time out (without keyboard attached). This machine is woken on lan and is supposed to boot without the keyboard attached.

Any thoughts?

---

### Post by Leppie on 2009-12-20
comment out the 2 lines concerning hiding the menu in /etc/default/grub:
```
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true

```

---

### Post by tombaugh on 2009-12-20
Works fine now, thanks Leppie!

---

### Post by Leppie on 2009-12-20
you're welcome.

glad all is working fine ;)

---

### Post by tombaugh on 2009-12-20
Looks like I cheered too soon. Now it doesn't work without the monitor attached...

---

### Post by Leppie on 2009-12-20
are you sure that this is a grub issue?
i've never heard that grub depends on a monitor being present.

is there an error or message displayed when attaching the monitor?

---

### Post by tombaugh on 2009-12-20
I think this is the situation now:

- monitor present and keyboard present: no problem, 5 s timeout
- monitor present, no keyboard present: no problem, 5 s timeout
- no monitor present, keyboard present: grub menu shown after attaching monitor, no timeout
- no monitor present, no keyboard present: black screen after attaching monitor, says no video after switching off and on

Just for information: booting by wakeonlan, shutting down by sudo halt over ssh.

---

### Post by Leppie on 2009-12-20
did you change anything to the graphical mode?

---

### Post by tombaugh on 2009-12-20
> **Leppie said:**
> did you change anything to the graphical mode?

No, I didn't...

edit: to make it even more complicated: I just booted using the on button, without monitor but with keyboard attached, and that gave me an empty screen as well.

---

### Post by sque on 2009-12-26
I am having the same or very similar problem. I have a fresh single installation 9.10 64-bit server edition. When I boot pc with k/b and monitor connected it boots with hidden menu. If I disconnect then the grub shows the menu and waits for a selection FOR EVER, connecting keyboard back and pressing "enter" boots grub.

**FIXED**
Here [https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29](https://wiki.ubuntu.com/Grub2#grub%20%28/etc/default/grub%29) at the paragraph *GRUB_HIDDEN_TIMEOU* explains how it works and also at [https://lists.ubuntu.com/archives/karmic-changes/2009-September/007874.html](https://lists.ubuntu.com/archives/karmic-changes/2009-September/007874.html) it says:
```

 If other operating systems are installed, then automatically unhide
        the menu.
      - Otherwise, if GRUB_HIDDEN_TIMEOUT is 0, then use keystatus if
        available to check whether Shift is pressed. If it is, show the
        menu, otherwise boot immediately. If keystatus is not available,
        then fall back to a short delay interruptible with Escape.


```
Probably in our m/b when you don't have a k/b connected, grub querying SHIFT status responds to true and stops.
**Setting GRUB_HIDDEN_TIMEOUT to any value bigger than 0 it works in all cases**

---

### Post by apostolos1975 on 2010-07-01
My 2cents on this topic. 

Fresh installation of 9.10. Cold boots and reboots without any problem if the screen is connected (the keyboard doesn't seem to affect grub2). Detach the screen and the boot process stops. Having the screen attached but off does not affect the boot process. Having only the screen cable attached stops the boot process. Is there signal in the cable when the screen is off?

Any ideas on how to resolve this?

---

### Post by sivadgiarc on 2010-08-12
I can't even get the timer to run when a keyboard and monitor ARE attached.

New ubuntu install, no timer.
Updated packages, including grub-pc, no timer.

Checked config files, its set for 10 seconds but it doesn't matter. No timer on the grub boot screen.

---

