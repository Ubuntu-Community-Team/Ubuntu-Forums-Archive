---
title: "Missing menu.lst in /boot/grub!!"
date: 2009-11-03
forum: General Help
---

### Post by Geraba on 2009-11-03
I tried to follow the guide **[https://help.ubuntu.com/9.10/switching/dualboot-custom.html](https://help.ubuntu.com/9.10/switching/dualboot-custom.html)**, so I could change the default OS, but when I try to open menu.lst there's none!!! I tried to explore the folder, but there's no menu.lst file...
The only mention to timeout and the OS's is in the grub.cfg, in the same folder.
Please help!

---

### Post by NoXiS on 2009-11-03
Grub2 uses the grub.cfg for it's configuration now, and there is no menu.lst, so that is completely normal.

If you want an easy GUI to change the default OS, you can get it here:
```

sudo apt-get install startupmanager
```
You will now see a "Startup-Manager" option in the System->Administration menu.


P.S. Be careful tinkering with this though, because I went a bit crazy ramping all the resolutions up and stuff, and it screwed up the booting. So I would advise you just to dip in, change your default OS, and get out again. I don't think this is an official Gnome app, but it's the only one I could find in the repositories.

---

### Post by Geraba on 2009-11-04
Thanks for the quick response, NoXiS!
It worked like a charm! I tought my installation was corrupt...

---

