---
title: "Wiimote cannot emulate keyboard"
date: 2009-07-09
forum: General Help
---

### Post by Labmonkey on 2009-07-09
Hello,

I am trying to use my Wii remote as a key board to play some games. I used CWiiD and wminput. I have done this on two ubuntu installations before, and everything has worked fine. This time I have a strange problem that while I can emulate mouse clicks and movement with my wii remote, I cannot get the wiimote to emulate keyboard presses.

The only thing different between this installation and the other ones that I can think of is that this is xubuntu, and the others were default ubuntu.

I am kind of a linux noob, but I think the problem might lie with the UInput module as when I loaded it it give this warning:
```

WARNING: All config files need .conf: /etc/modprobe.d/oss-compat, it will be ignored in a future release.

```

If anyone can help that would be really appreciated!

---

### Post by synapsys on 2009-07-09
That warning just means you need to change 

/etc/modprobe.d/oss-compat
to
/etc/modprobe.d/oss-compat.conf

By default, xubuntu comes with a lot less packages installed, as it is meant to be installed on older machines. Make sure you have all the right packages and libraries to do what you want to do.

---

