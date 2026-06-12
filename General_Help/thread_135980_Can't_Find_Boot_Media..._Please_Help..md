---
title: "Can't Find Boot Media... Please Help."
date: 2006-02-25
forum: General Help
---

### Post by ephman on 2006-02-25
hi,

i just finished setting up a brand new computer and kaboowie.  what i tried to do was reinstall my winxp (yuck i know but i have the space).  after i rebooted grub was gone and only had microsoft's loader only giving me the winxp option.  i can't figure out how to get to my linux install?  any help would be appreciated.

thanks,
ephman

---

### Post by Xian on 2006-02-25
[How-To Restore Grub](http://www.ubuntuforums.org/showthread.php?t=24113)

---

### Post by Trab on 2006-02-25
while that might be helpful, heres a quick rundown...
go find ur ubuntu installer disc, pop it in, boot the machine...
when it brings up the menu asing u for boot options, type 
```

rescue 
```
then, once its loaded, mount ur filesystem however u like, doesnt really matter....

and execute ```
 grub-install /dev/hda1 
```
should fix it fine.... u might need to retweak ur grub menu enteries, but thats it!

gl mate

---

