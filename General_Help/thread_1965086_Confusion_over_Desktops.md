---
title: "Confusion over Desktops"
date: 2012-04-25
forum: General Help
---

### Post by Quarkrad on 2012-04-25
I'm running 10.10 and about to migrate to 12.04 - I look after a number of family machines, some who don't mind Unity, some who want to keep their gnome 2 environment.  I have installed Mate over 12.04/Unity in virtualbox and I think it is very good but I'm a little confused over the Desktop options re Ubuntu.  There is Unity, classic, KDE, XFCE, Mate, Cinnamon, to name a few.  To install Mate for example, does it matter whether you start off with a basic 12.04/Unity install and then install Mate on top (or is it along side?) or 12.04/XUbutu (XFCE) basic install and then install Mate on top?  My confusion is (I think) I understand, for example, things like installing **sudo apt-get install kubuntu-desktop** and **sudo apt-get install mate-core** (along with all the the install dependencies) to get a new/different Desktop environment but does it matter what you have installed in the first place?  How independent are these various Desktops from the core OS underneath them?

---

### Post by zombifier25 on 2012-04-25
Nope, doesn't matter :D
The DEs are merely the shell on top of the OS. They're pretty much independent. Deep down, Ubuntu, Kubuntu, Xubuntu, Lubuntu, etc. are the same OS, just different set of packages by default.

---

### Post by deckoff on 2012-04-25
Very much like the previous post said it:
- Ubuntu is the body.
- the desktops are more or less different clothing to select from. You just select what is appropriate for the case.
Be warned ( for old PCs):
- newer kernels does not support non-pae CPU - new version possible with upgrade only (my thinkpad x40 fires an error for 12.04 betas)
- Go with Ubuntu if you have to choose between it or flavours - Ubuntu comes packed with packages that might be omitted in flavours . This might save some time fixing things, working properly in Ubuntu.
- Do consider the upgrade - newer versions come packed with newer versions of software and drivers that might break performance of older hardware  :)

---

### Post by Quarkrad on 2012-04-25
Thank you for your replies.  I've just remembered I converted a friend to Ubuntu some time ago (I started in 8.04 days) who has an old'ish laptop - I've mailed him to ask his make/model.  Re non-pae CPUs - to my understanding Ubuntu 10.04 has another years life in it - what do we do re Ubuntu for older machines?  Does this mean we have to move to another distro?

---

### Post by forrestcupp on 2012-04-25
Unity is based on Gnome3, and Mate is a fork of Gnome2. People run them side by side with no problems, but I did hear about someone having trouble when they tried to uninstall Mate and things weren't set back to how they were.

You might want to check out Mint. Their main version is based on Mate now.

---

### Post by zombifier25 on 2012-04-25
> **forrestcupp said:**
> Unity is based on Gnome3, and Mate is a fork of Gnome2. People run them side by side with no problems, but I did hear about someone having trouble when they tried to uninstall Mate and things weren't set back to how they were.

You might want to check out Mint. Their main version is based on Mate now.
Or GNOME Classic if you don't want to jump to another OS.

---

