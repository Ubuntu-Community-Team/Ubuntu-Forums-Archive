---
title: "GMT Time"
date: 2006-02-24
forum: General Help
---

### Post by jenkins_t on 2006-02-24
I installed Ubuntu as a 3rd OS on my laptop. When it asked about time, either local or GMT, I chose GMT. Now my other 2 OS's are off by 5 hours and change every boot, even after correction. How can I change Ubuntu back to local?

---

### Post by andrewsawyer on 2006-02-24
Try right clicking on the clock on the gnome-panel, and choosing preferences.  See if UTC is checked.  You might also try checking what the time settings in your bios are.  Not sure whether Ubuntu changes the bios clock or not, however as you say that your other os's are off, this might be an explanation.

---

### Post by jenkins_t on 2006-02-27
I found a solution, well more of a hack. I tried UTC and many other time/date stuff with no avail. Always seemed to write GMT to CMOS. So I did this:

```

$ sudo su
password:
root@ubuntu# nautilus
```

From file manager as root I went to /etc/rc6.d/ and created a folder called no_longer_used and cut K25hwclock.sh and pasted in new folder /etc/rc6.d/no_longer_used/

Now it don't run during reboot and time stays same, and I still have script in case I need it.

---

