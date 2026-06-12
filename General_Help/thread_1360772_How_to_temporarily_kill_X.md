---
title: "How to temporarily kill X?"
date: 2009-12-21
forum: General Help
---

### Post by cdysthe on 2009-12-21
Hi,

I sometimes need to kill X and just be in a command shell. In previous versions of Ubuntu I did Ctrl+Alt+F2, logged in as root and did "killall gdm". That doesn't work in Ubuntu 9.10 for some reason. Also, there's no boot menu where I can choose to boot to a command shell. Can someone plese let me know how I can get to a command shell with no X running without more than a reboot needed to get back to the normal X login?

---

### Post by ratcheer on 2009-12-21
I thought it was Crtl-Alt-F1, but here are two ways to do it:

sudo service gdm stop

sudo /etc/init.d/gdm stop

Tim

---

### Post by junapp on 2009-12-21
after you stop the gdm, you'll want to start it back up again.

sudo /etc/init.d/gdm start

---

### Post by cdysthe on 2009-12-21
> **ratcheer said:**
> I thought it was Crtl-Alt-F1, but here are two ways to do it:

sudo service gdm stop

sudo /etc/init.d/gdm stop

Tim

Thanks! Worked!

---

### Post by junapp on 2009-12-21
might be worth a read to get the option for console only on startup:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
but I thought the option was there already (but mine skips the grub prompt unless there was a problem)

---

### Post by BbUiDgZ on 2009-12-21
ctrl+alt+backspace
EDIT: will only restart gdm - i read the full thread now- sorry

---

### Post by junapp on 2009-12-21
I don't think ctrl+alt+backspace is enabled by default any longer (since Jaunty).
[http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-enable-ctrl-alt-backspace-in-ubuntu-jaunty.html)

---

### Post by cdysthe on 2009-12-21
I found out how to do it in 9.10: 

I did Ctrl-Alt-F2. Then "sudo killall gdm-binary". The only difference from Ubuntu 9.04 is the addition of -binary to the last command.

---

### Post by ratcheer on 2009-12-22
> **junapp said:**
> might be worth a read to get the option for console only on startup:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
but I thought the option was there already (but mine skips the grub prompt unless there was a problem)

If you are using grub2, hold the Shift key just as grub is starting to get the grub menu.

Tim

---

