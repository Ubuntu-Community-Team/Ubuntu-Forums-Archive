---
title: "Temporary GUI for server?"
date: 2012-05-17
forum: General Help
---

### Post by Daktyl198 on 2012-05-17
I am about to install Ubuntu Server onto my home server. While I have been using Ubuntu for at least 2 years and LOVE to use the terminal, I always forget commands. Therefore I need a GUI.
Plus, I don't want to edit network config files and such without an editor...

Anyway, I only need the GUI for the setup purposes, as after that I can just FTP files to and from it.
I really don't want the GUI hogging my system resources after all the setup so I was wondering if there was a solution to only temporarily enable a GUI (say... until next reboot) so that I can setup the server comfortably but not worry about resources later.

---

### Post by rai4shu2 on 2012-05-17
You could do:

```
sudo apt-get openbox
```

And that would give you a pretty minimal GUI.

ArchWiki has a pretty good guide for getting that working.

[https://wiki.archlinux.org/index.php/Openbox#Openbox_as_a_stand-alone_WM](https://wiki.archlinux.org/index.php/Openbox#Openbox_as_a_stand-alone_WM)

When you're done, you can just delete ~/.xinitrc, and you should be back in server mode at the next restart.

---

