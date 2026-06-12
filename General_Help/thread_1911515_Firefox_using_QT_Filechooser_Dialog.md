---
title: "Firefox using QT Filechooser Dialog"
date: 2012-01-19
forum: General Help
---

### Post by SadaraX on 2012-01-19
I am having a Firefox issue. I want to know, how do I enable the QT file chooser (saving a file, or opening a file) for Firefox? I was not even aware it could be done until it happened accidentally to me. Below is an image of what my Firefox with the QT file chooser looks like.

[[IMG]http://img5.imagetwist.com/th/00887/hxtp68djbf0n.jpg[/IMG]](http://imagetwist.com/hxtp68djbf0n/firefox_running_qt_file_chooser.png.html)

I think it is related to some Ubuntu package I have installed but I don't know what.

I have two computers, each running Kubuntu 11.04, On both I am running the latest stable version of Firefox (version 9.0.1), which I downloaded from the Ubuntu Mozilla Security PPA ([https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa)).

However on one computer, when I save or open anything, the dialog is a QT style window. On the other computer, it is in GTK. I want to know, how do I enable the QT file chooser for both?

I have tried this with blank profiles, and the results are still different between each computer. It is not a Firefox profile configuration issue (at least something I have done).

I am guessing maybe it is some library or extra package I have installed but I don't know what.

---

### Post by lovinglinux on 2012-01-20
Install *firefox-kde-support* package.

---

### Post by SadaraX on 2012-01-20
> **lovinglinux said:**
> Install *firefox-kde-support* package.

That worked PERFECTLY. Thank you!

---

### Post by lovinglinux on 2012-01-20
You are welcome.

---

