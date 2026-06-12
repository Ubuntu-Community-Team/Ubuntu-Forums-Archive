---
title: "Issues with 9.10 update manager"
date: 2010-02-06
forum: General Help
---

### Post by hito_kiri on 2010-02-06
I have been having some major issues with the update manager of ubuntu 9.10.  I have had 3 instances so far where the updater froze either in the middle of updating or right after, and every time resulted in a corrupted file system.  Two times it has happened to me which resulted in once having to completely reinstall and another was luckily saved by using Gparted on the live CD.  But now my friend who i installed Ubuntu for has had the same problem.  When it happened to me, I was forced to hold the power button to get the computer to turn off as it completely locked up the system.  My friend however, was able to use the shutdown menu.

Has this been an issue for anyone else?  I have no idea what is causing it, but it is a major major pain.

---

### Post by mac9416 on 2010-02-06
Hey, hito_kiri,

You should try updating the system with the command line instead of Update Manager. Then you will be able to study any error output.

Go to Applications > Accessories > Terminal and run...
```
$ sudo apt-get update
$ sudo apt-get upgrade
```

If you encounter any trouble then, you can post the output here or maybe diagnose it yourself.

Good luck!

---

### Post by warjowuch on 2010-02-28
Better is to study the output from update-manager itself. So I think you should start update-manager from the terminal.

sudo update-manager (or something like that)

---

