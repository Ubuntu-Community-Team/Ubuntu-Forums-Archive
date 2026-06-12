---
title: "Lost graphical boot"
date: 2009-08-25
forum: General Help
---

### Post by mazz0 on 2009-08-25
So, my computer's started booting in text mode rather than graphical.  Any ideas?  Is there some config I should check to see if it says to boot graphically?  If it's set to yes, is there a log I can check to see why it's not loading?

---

### Post by uylug on 2009-08-25
> **mazz0 said:**
> So, my computer's started booting in text mode rather than graphical.  Any ideas?  Is there some config I should check to see if it says to boot graphically?  If it's set to yes, is there a log I can check to see why it's not loading?

Have you checked the messages log?

```
dmesg
```

What happens if you login in console mode and run this command:

```
sudo /etc/init.d/gdm restart
```

---

### Post by mazz0 on 2009-08-26
Oooh, sorry, I didn't explain very well.  Gnome runs fine when it gets that far, it's just that I'm seeing text instead of a progress bar while the computer starts up.

---

### Post by mazz0 on 2009-08-26
Oh - installing GRUB2 fixed it :)

---

