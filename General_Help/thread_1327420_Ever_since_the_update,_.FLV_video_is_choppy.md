---
title: "Ever since the update, .FLV video is choppy"
date: 2009-11-15
forum: General Help
---

### Post by AgentWiggles on 2009-11-15
Pretty much self-explanatory. Ever since I updated from 9.04 to 9.10, streaming video from sites like YouTube and Break is really choppy and doesn't work well at all. Nothing else has changed since the update, so I'm guessing that the update has something to do with it. This is fairly irritating, so if anyone has a guess towards a solution, I'd appreciate it.

---

### Post by lovinglinux on 2009-11-15
See Flash Optimization section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). But don't expect miracles.

---

### Post by berman56 on 2009-11-15
Go to synaptic, uninstall flashplugin.

Head over to adobe, download the latest flash for linux (are you running 32 or 64 bit?)  If 64-bit choose:

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)

Open the archive and drop the libflashplayer.so into:

/home/.mozilla/plugins

and

usr/lib/mozilla/plugins

Restart firefox and see if that improves your situation.

---

### Post by Razmear on 2009-11-15
I also noticed a slow down in my streaming videos and general performance after upgrading to 9.10. 
I now run Xubuntu for the shell and things are much faster across the board. No need backup reinstall everything before converting, just follow the instructions here: 
[http://xubuntu.org/get](http://xubuntu.org/get)

```

Install Xubuntu from Ubuntu

If you have an existing Ubuntu, Kubuntu, or Edubuntu installation, 
it is possible to install Xubuntu and retain your current installation. 
To do so, just go into Synaptic (or Adept if you use Kubuntu) and 
install the xubuntu-desktop package. Next time you login, you can 
choose Xfce4 from the Session menu on the login screen.

```

If it doesn't help you can always just switch back by choosing Gnome when you log in again. 
I run an older 512mb ram PC and the speed difference switching to Xubuntu from Ubuntu 9.10 is comparable to what I saw when switching from XP to 8.10. 

eb

---

