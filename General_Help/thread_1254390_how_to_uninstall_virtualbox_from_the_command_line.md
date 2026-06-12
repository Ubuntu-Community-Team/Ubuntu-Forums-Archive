---
title: "how to uninstall virtualbox from the command line"
date: 2009-08-31
forum: General Help
---

### Post by colinireland on 2009-08-31
Hello,

I have recently run into a problem when I start virtualbox 3. The gui starts fine but I can't start XP on it. I just get some error messages. I think this started to happen when i installed a new kernel 2.6.28-15-generic. 

I figure that if I uninstall and then reinstall virtualbox 3.0.6 (i think) things should work a little better. However I didnt install virtualbox from the add/remove of synaptic package manager and I don't know how to go about uninstalling it.

Any suggestions would be greatly appreciated.

Colin

---

### Post by howefield on 2009-08-31
> **colinireland said:**
> I have recently run into a problem when I start virtualbox 3.

I figure that if I uninstall and then reinstall virtualbox 3.0.6 (i think) things should work a little better. However I didnt install virtualbox from the add/remove of synaptic package manager and I don't know how to go about uninstalling it.

You'll probably find that you don't need to reinstall Virtualbox to sort the issue out, (the errors are most likely related to you upgrading the kernel).

However, it is sometimes simpler and quicker to do just that, I'd guess that you will find Virtualbox in synaptic and be able to remove it from there, even though you did not use synaptic to install it in the first place.

Have you looked ?

---

### Post by colinireland on 2009-08-31
Ya I have check in symaptic but there are no checked boxes there. I don't know anything about kernels to give fixing it that way a go so I think I'll just stick with trying to uninstall virtualbox.

any ideas?
Thanks

---

### Post by TheExplorer on 2009-08-31
Well, what I do is:
1) Use Virtualbox from the official website: [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
Just download the .deb file and execute:
```
 sudo dpkg -i virtualbox*
```

2) And when upgrading the kernel I just execute the following (to recompile vbox module for the new kernel):
```
 sudo /etc/init.d/vboxdrv setup
```

3) to uninstall virtualbox from the command line (as you are asking here) execute this:
```
sudo apt-get purge virtualbox
```

(use Tab to complete package names)

That's all.

---

### Post by colinireland on 2009-08-31
Hey thanks for you help. Everything is running smoothly now.
Colin

---

