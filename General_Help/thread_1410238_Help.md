---
title: "Help"
date: 2010-02-18
forum: General Help
---

### Post by Jinji on 2010-02-18
I have ubuntu 9.10 installed within my windows 7. I updated ubuntu and now have a little problem. When starting my laptop I'm asked to choose windows 7 or ubuntu. When i choose ubuntu it gives me 5 options:

Ubuntu 9.10.19
Ubuntu 9.10.19 recovery mode
Ubuntu 9.10.14
Ubuntu 9.10.14 recovery mode
Windows 7 loader(which brings me back to the previous screen)

How do i get rid of the 2  Ubuntu 9.10.14 options? Will it matter if I get rid of it?

---

### Post by nothingspecial on 2010-02-18
```
sudo apt-get update && sudo apt-get autoremove
```

14 is an older "version" of the linux kernel, it is useful to keep older ones around. Sometimes new versions, while fixing existing issues, in doing so create other problems. Soon you will get 18, then 19 etc.

If your system works on 17, it may not on 18 so having 17 available to boot is handy.........if you see what I mean, which you probably don`t because I have not explained it very well.

Also, and I`m not being rude, "Help" is not a good title for your problem. Maybe "How to remove options in boot list" or something like that.

---

### Post by Jinji on 2010-02-18
Ok i got what you were saying. Thanks for the help.

---

