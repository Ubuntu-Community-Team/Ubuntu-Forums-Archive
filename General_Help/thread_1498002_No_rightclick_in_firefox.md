---
title: "No rightclick in firefox"
date: 2010-05-31
forum: General Help
---

### Post by AlexDudko on 2010-05-31
No rightclick in Firefox. Ubuntu 10.04 fresh install, recent updates.

---

### Post by lovinglinux on 2010-05-31
Is your Firefox profile also new?

---

### Post by AlexDudko on 2010-05-31
Yes, this is a fresh install on a new computer, no add-ons installed.
It's strange, another computer with Ubuntu-10.04 (upgraded from 9.10) works flawlessly.
I tried to reinstall the OS, but the bug still exists...

Just found a similar thread, where updates fixed the bug... [http://ubuntuforums.org/showthread.php?t=1450341&highlight=firefox+rightclick](http://ubuntuforums.org/showthread.php?t=1450341&highlight=firefox+rightclick)

---

### Post by lovinglinux on 2010-05-31
> **AlexDudko said:**
> Yes, this is a fresh install on a new computer, no add-ons installed.
It's strange, another computer with Ubuntu-10.04 (upgraded from 9.10) works flawlessly.
I tried to reinstall the OS, but the bug still exists...

Just found a similar thread, where updates fixed the bug... [http://ubuntuforums.org/showthread.php?t=1450341&highlight=firefox+rightclick](http://ubuntuforums.org/showthread.php?t=1450341&highlight=firefox+rightclick)

Try to disable Ubuntu Firefox Modifications extension to see if the problem persists.

I'm not sure, but I guess it also could be Compiz affecting Firefox. Try to disable visual effects.

---

### Post by AlexDudko on 2010-05-31
Nothing helps. Though I rebooted once and right clicking was working. Rebooted again several times and it doesn't. A hardware issue? (Not a mouse, because it is only firefox specific and everything's working in any other application).

P. S. Compiz is disabled.

---

### Post by yeats on 2010-05-31
Have you started firefox in safe mode?  From the terminal:

```
firefox --safe-mode
```

starting from the command line will also give you verbal feedback on  any errors.

---

### Post by lovinglinux on 2010-05-31
> **chrissharp123 said:**
> Have you started firefox in safe mode?  From the terminal:

```
firefox --safe-mode
```

Probably won't help, because the OP doesn't have any add-ons installed. It doesn't hurt to try tho.

---

### Post by AlexDudko on 2010-06-01
Strange but good news - after several reboots I cannot reproduce the bug.

---

### Post by ironscf on 2010-06-27
I have the same problem now. I have closed and restarted Firefox with no change . I hope it disappears on reboot. My firefox menu bar is also dead; no response to clicking on File, Edit, View nor Bookmarks . The bookmarks backup files are there and the content looks OK in gedit.:confused:

---

### Post by ironscf on 2010-06-28
So the reboot made no change . Still no right click and menu bar dead.

Then I tried the safe mode as suggested and disabled add-ons and reset preferences; just kept the bookmarks .  That worked fine and all looks OK now . Thanks to Forum advisors .:popcorn:

---

### Post by ironscf on 2010-06-30
It gets stranger . Today I did the software update that was notified (about 37Mb and a lot of it Firefox) . Then restarted Firefox as required .
Result: the same problems recurred . So I restarted firefox with safemode command again and the problems go away.  :confused:

---

### Post by lovinglinux on 2010-06-30
> **ironscf said:**
> It gets stranger . Today I did the software update that was notified (about 37Mb and a lot of it Firefox) . Then restarted Firefox as required .
Result: the same problems recurred . So I restarted firefox with safemode command again and the problems go away.  :confused:

Try to create a new profile. Looks like something in your current profile is corrupted. See [http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

### Post by Szise on 2010-06-30
I disabled "Ubuntu Firefox Modifications" (Firefox add-on) and is working for the moment.

---

### Post by Szise on 2010-07-03
> **Szise said:**
> I disabled &quot;Ubuntu Firefox Modifications&quot; (Firefox add-on) and is working for the moment.

 Stopped working again after restarting the PC few times, we need a fix for this.

---

### Post by barrydirk on 2010-07-20
I had the same problem after updating, started firefox in safe mode from terminal edit, preferences, manage add-ons, disable "ubuntu firefox modifications". Problem gone hopes this helps.

---

