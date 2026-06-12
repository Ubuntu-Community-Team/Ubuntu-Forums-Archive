---
title: "automounting problems"
date: 2009-10-15
forum: General Help
---

### Post by ljungkvist on 2009-10-15
I can't seem to get thunar to automount CD roms! I use jaunty with dwm as a window manager, and run

```
thunar --daemon &
```

in my xsession startup script. I've set all the properties correctly with thunar-volman but it still doesn't recognize when I put a cd in the drive. I'm beginning to believe that that the problem lies deeper, and has something to do with dbus, hal, udev, or something like that. Putting in the cd and then running

```
dmesg | tail 
```

shows no trace of any event. What's strange is that USB drives are mounted automatically by the daemonized thunar.

What's also strange is that if I run nautilus with desktop management it sees the CD perfectly well and mounts it. Especially weird is that thunar then also sees it! Even if I eject the CD in between!

The cd drive works in windows so that should be okay. 

What could be the problem? 

If I any logs or outputs could be of any help I'm happy to supply them!

---

### Post by ljungkvist on 2009-10-15
No one knows what can be the problem?

Perhaps I posted this in the wrong section to get any answers. If someone with the power to do so would like to move it anywhere more appropriate I'd be happy.

---

### Post by ljungkvist on 2009-10-15
I managed to solve it. It turned out to be powertop which had disabled polling on the cdrom. Apparently it had not enabled when it quit.

---

