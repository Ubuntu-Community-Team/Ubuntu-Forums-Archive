---
title: "No GUI after restart in 10.10"
date: 2011-02-12
forum: General Help
---

### Post by Mikeyspike on 2011-02-12
Hey guys, I've got a problem with ubuntu 10.10.

I've recently dicided to install it. I then restarted my computer to allow the installation to complete and then ubuntu booted up fine.

I downloaded the updates it required and also a driver for my graphics adapter that ubuntu suggested. I then restart once again to finish off the installation, however, when it boots back up it just goes straight to terminal, asking me to login. I don't get a GUI like I did before.

I'm a bit of a newb when it comes to linux as I haven't had much experience and want to use it just as a seperate OS that I am going to use for work and such.

I did a quick google search and found that someone had the same problem, however this was after they restarted after the installation of the OS. It apeared to be that their graphics adapter didn't support Ubuntu/Linux.

Could anyone help me out?

---

### Post by runeh76 on 2011-02-12
Hi

Install ur desktop:

```
sudo apt-get install ubuntu-desktop
```

start GUI:

```
startx
```

---

