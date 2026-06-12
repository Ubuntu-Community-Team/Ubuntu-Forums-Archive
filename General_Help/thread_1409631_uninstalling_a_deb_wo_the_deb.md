---
title: "uninstalling a deb w/o the deb"
date: 2010-02-17
forum: General Help
---

### Post by Drone4four on 2010-02-17
How do I uninstall a deb if I no longer have the deb that I used to initially install it?  What's the command?

I ask because I want to upgrade to the latest version of Google Chrome using a deb I found in Launchpad but Package Installer says:

```

Error: Dependency is not satisfiable: chromium-browser (= 5.0.330.0~svn20100217r39184-0ubuntu2~ucd1) 

```

So I go to the official Google Chrome for Linux page and download the -current version of chrome and try to open the deb with Package Installer, this time the Status error says:

```

Error: A later version is already installed

```

So how do I uninstall the version of Chrome without the deb? 

I'm running 64bit Ubuntu.

---

### Post by dcstar on 2010-02-17
> **Drone4four said:**
> How do I uninstall a deb if I no longer have the deb that I used to initially install it?  What's the command?

I ask because I want to upgrade to the latest version of Google Chrome using a deb I found in Launchpad but Package Installer says:

```

Error: Dependency is not satisfiable: chromium-browser (= 5.0.330.0~svn20100217r39184-0ubuntu2~ucd1) 

```

So I go to the official Google Chrome for Linux page and download the -current version of chrome and try to open the deb with Package Installer, this time the Status error says:

```

Error: A later version is already installed

```

So how do I uninstall the version of Chrome without the deb? 

I'm running 64bit Ubuntu.

Use the GUI tools that you should be using for all packages - Synaptic.

---

### Post by darolu on 2010-02-17
Why don't you add the Chromium PPA to your sources? That way you'll get the latest version everyday.

Go to System - Admin - Software Sources and add: ppa:chromium-daily/ppa

If you don't use Karmic or want to do it manually, go to the launchpad chromium ppa: [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

---

### Post by jamesisin on 2010-02-17
First, I recommend using a repository for installing software so that Update Manager can be responsible for keeping track of version updates.  I found this article on adding a repo for Chrome:

[http://www.shivaranjan.com/2009/05/17/linux-how-to-install-chromium-google-chrome-web-browser-in-ubuntu-linux/](http://www.shivaranjan.com/2009/05/17/linux-how-to-install-chromium-google-chrome-web-browser-in-ubuntu-linux/)

Second, you should be able to uninstall a package without the original .deb file.  Just hop into Synaptic and look for that package (even .deb packages installed should *appear* in Synaptic).  Mark it for complete removal.  (Do this before you attempt to work with the repo linked above.)

System &#8212;> Administration &#8212;> Synaptic Package Manager

---

### Post by jamesisin on 2010-02-17
[deleted by me]

---

### Post by Drone4four on 2010-02-17
I usually use apt-get to install debs.  I was hoping for a CLI solution.  Perhaps if I asked my question using the CLI commands to install Google Chrome I would have got a CLI answer.  I usually just use Package Installer because it is so convenient because it opens once the download finishes in Firefox.  Oh well.  dcstar, synaptic worked perfectly.  Thanks.

---

### Post by jamesisin on 2010-02-17
Synaptic is really just a GUI for apt-get (and some others).  You are welcome to use commands for running the installation.  Regardless you will be better off adding a repository for this application.  Adding the repo, adding the associated key, and installing the application from the repo can all be done through the Terminal if you'd like.

As a matter of fact, there is only one step in the instructions I linked to above which are GUI instructions (adding the two repos to your sources list).  If you'd rather use a command for that step let us know and we'll craft the command.  The remainder of those instructions are all terminal commands.

---

