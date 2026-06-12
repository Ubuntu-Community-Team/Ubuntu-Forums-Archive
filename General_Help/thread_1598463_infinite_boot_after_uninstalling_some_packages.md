---
title: "infinite boot after uninstalling some packages"
date: 2010-10-16
forum: General Help
---

### Post by bukzor on 2010-10-16
I was possibly overzealous in uninstalling packages using deborphan. I uninstalled various libraries and progams that I don't use (ppp, gimp, etc.), but I must have touched something useful, since the machine will no longer boot.

I thought this might cause a few problems, but expected to be able to recover, at least using the Recovery Mode. This isn't the case, sadly.

The main symptom is an infinite boot process, even using the recovery-mode boot. Things proceed as normal (grub screen, few lines of startup messages), but then a ton of text starts pouring onto the screen. It scrolls much too fast to read, and the Pause/Break key won't stop it. I do notice that there is a lot of talk about devices and udev, but can't make out more than that. The text doesn't obviously repeat, so I tried just waiting it out, but gave up after a couple hours.

For starters, how can I get a good look at these messages?

Thanks,
--Buck

---

### Post by bukzor on 2010-10-16
The lines scrolling past are all prefixed by 'udevd-work' or 'udevd'. 


Once, it slowed down and I could read this:

```
[udevd-work] seq 951 done with 0
[udevd] seq 951 processed with 0
```



Other words I can pick out...

```
seq RUN /devices/pc device compare LINK
GET CONFIGURATION 
(stdout)
(stderr)
monitor
devpath
preserve
<there are lots of UUID's in the output>
created 
(connection refused)

```

---

### Post by bukzor on 2010-10-16
I was finally able to get the system to boot normally. It still spent a good five minutes printing udev messages.

This is a link to the boot.log:

[https://docs.google.com/leaf?id=0B75uxIcyEbdgOTk1YTkyNjEtZTI5MC00YjBlLTkwOTYtZjRkNTRiMmY1NmZj&hl=en&authkey=CMDVx-gK](https://docs.google.com/leaf?id=0B75uxIcyEbdgOTk1YTkyNjEtZTI5MC00YjBlLTkwOTYtZjRkNTRiMmY1NmZj&hl=en&authkey=CMDVx-gK)

---

### Post by bukzor on 2010-10-16
So the machine seems to boot reliably now, albeit slowly. Is there any way for me to change the title of this thread?

A secondary symptom is that X fails to run when using the newest kernel. Fortunately the slightly older kernel is still installed, which seems to work fine.

Attached are the Xorg, syslog, and boot logs when trying to boot to the newest kernel.

---

