---
title: "Ubuntu r Kubuntu?"
date: 2009-11-27
forum: General Help
---

### Post by karumudi7 on 2009-11-27
Hi Frnds, I am in a Dilemma of Ubuntu or Kubuntu?
I love Kubuntu Desktop, but what abt softwares support or anything?
I want a complete description between both of these.
Which one you Prefer?

Thanks!

---

### Post by MelDJ on 2009-11-27
see: [http://www.psychocats.net/ubuntu/kdegnome](http://www.psychocats.net/ubuntu/kdegnome)

---

### Post by karumudi7 on 2009-11-27
what abt Softwares compatability?
Both can support same softwares?

---

### Post by MelDJ on 2009-11-27
yes.
if you use gnome and what to install a kde application, you will just have to install some kde libraries and vice versa

---

### Post by karumudi7 on 2009-11-27
I am Using KDE Kubuntu Karmic, I would like to have a support of Gnome . Can u plz tell me the libraries to instal, where can i get them?
I am a beginner tooo!

---

### Post by MelDJ on 2009-11-27
you could install both in your ubuntu. if you have kde, just install the gnome package from synaptic and it will install gnome and all its libraries.

if you only need a certain software, just install the program and the needed libs will be installed

---

### Post by nerdopolis on 2009-11-27
If you install an GNOME application (such as firefox) with kpackagekit or apt-get (or a package manager like that), it pulls in the required libraries automatically.

---

### Post by karumudi7 on 2009-11-27
You mean all it is automatic?
what abt the softwares that are not in respiratory, If i dwld a software of GNOME from a website, then the libraries required will install automatic?

---

### Post by audiomick on 2009-11-27
For anything that you install via synaptic package manager, the dependencies are automatically fulfilled, or you get a message saying it couldn't be installed and why.

If you download a .deb package, and install it with gdebi, which is on Ubuntu as standard, that will take care of dependencies.

If you build something yourself from scratch, you have to worry about dependencies yourself. If you are new to the Linux world, stick to the stuff in the repositories, i.e. the stuff that is supported by Ubuntu. The really is a program in there for practically anything you could think of.

As to your first question, kbuntu or ubuntu: it comes down to which desktop you prefer, and since you can add either desktop to the other version, it doesn't matter in the end all that much.

---

