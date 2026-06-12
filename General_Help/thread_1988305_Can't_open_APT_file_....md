---
title: "Can't open APT file ..."
date: 2012-05-27
forum: General Help
---

### Post by Bucky Ball on 2012-05-27
Hi all,

I have recently done a 10.04 minimal install on our old desktop. Running great. Trying to install flash from this site:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

... and selecting the 'APT for Ubuntu 10.04' option, but all I get is apturl or gdebi.desktop to open the file (neither of which does) or the option to choose a different app. I've done some research as to what that other might be to no avail. 

Anyone have any clue what I might be missing?

---

### Post by maverickaddicted on 2012-05-29
Sorry, but I am little confused about this-
Is it not getting installed or you want the installation files?

---

### Post by Bucky Ball on 2012-05-29
> **maverickaddicted said:**
> Sorry, but I am little confused about this-
Is it not getting installed or you want the installation files?

[QUOTE=Bucky Ball]http://get.adobe.com/flashplayer/

... and selecting the 'APT for Ubuntu 10.04' option, but all I get is apturl or gdebi.desktop to open the file (neither of which does) or the option to choose a different app.[/QUOTE]

Kinda says it all. When I hit 'Download' a window pops up on my local machine with a choice of two applications to open the file. Neither work. I don't know what piece of software I need to open this file automatically.

---

### Post by anonymous5 on 2012-05-29
> **Bucky Ball said:**
> Hi all,

I have recently done a 10.04 minimal install on our old desktop. Running great. Trying to install flash from this site:

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

... and selecting the 'APT for Ubuntu 10.04' option, but all I get is apturl or gdebi.desktop to open the file (neither of which does) or the option to choose a different app. I've done some research as to what that other might be to no avail. 

Anyone have any clue what I might be missing?

Try this instead :

sudo apt-get install flashplugin-installer

---

### Post by Orion8 on 2012-05-29
I agree with the poster above me.  Don't try to install from Adobe's website but use the package manager.  You can search for "flash" in the Ubuntu Software Manager or Synaptic package manager depending on your preference.

[http://www.liberiangeek.net/2010/05/how-to-install-flash-player-in-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/05/how-to-install-flash-player-in-ubuntu-10-04-lucid-lynx/)

---

### Post by maverickaddicted on 2012-05-30
> **Bucky Ball said:**
> Kinda says it all. When I hit 'Download' a window pops up on my local machine with a choice of two applications to open the file. Neither work. I don't know what piece of software I need to open this file automatically.

You can directly install it from Ubuntu Software Center.

---

### Post by vasa1 on 2012-05-30
OP has done a **minimal install**. Programs we take for granted may not be present.

---

### Post by maverickaddicted on 2012-05-30
> **vasa1 said:**
> OP has done a **minimal install**. Programs we take for granted may not be present.

Sorry forgotten that. Have you tried anonymous5 solution.

You can also try this - 

```
sudo apt-get install ubuntu-restricted-extras
```

Or Download it from here - [http://packages.ubuntu.com/lucid/ubuntu-restricted-extras](http://packages.ubuntu.com/lucid/ubuntu-restricted-extras)

---

### Post by Bucky Ball on 2012-05-31
Okay. Thanks for all your suggestions. I am actually asking why the 'APT for Ubuntu' is not being opened automatically (as it is on my other machines).

I have flash installed (11.2 r202) but it hasn't fixed the reason I wanted to install it. For those of you in Australia, I am attempting to access this site:

[http://www.abc.net.au/iview/](http://www.abc.net.au/iview/)

Works fine on other machines. On this one I just get a black screen when I hit that address. I have posted about this issue separately (to almost zero response) here:

[http://ubuntuforums.org/showthread.php?t=1985135](http://ubuntuforums.org/showthread.php?t=1985135)

I have a feeling I am missing something in my minimal install. Yes, I have ubuntu-restricted-extras installed.

---

