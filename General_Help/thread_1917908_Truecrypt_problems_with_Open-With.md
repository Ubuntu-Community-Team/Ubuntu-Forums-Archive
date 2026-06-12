---
title: "Truecrypt problems with Open-With"
date: 2012-01-30
forum: General Help
---

### Post by yeh on 2012-01-30
I'm trying to set up my main truecrypt encrypted file to automatically be opened by Truecrypt when I double-click it.

However, when I right-click the file and go to the Open With tab, truecrypt does not show up as an available application to open with.

I thought maybe this was a problem with the way truecrypt is installed. Maybe it was an executable file? Truecrypt didn't install traditionally with synaptic or ubuntu software center though.

I can't find any other way to install it though. No repository to add to sources. No .deb file to install. There's a tar.gz file that can be extracted from the individual file, but I don't see how it's helpful at all.

---

### Post by yeh on 2012-01-31
If I try to uninstall with the software center, I can't find it installed. If I try to find the package with Synaptic, I can't find any mention of Truecrypt.

If I try to uninstall with sudo apt-get remove truecrypt, I get the message that truecrypt is a virtual package and so can't be removed. 

The command I found to get rid of truecrypt is truecrypt-uninstall.sh

Hope someone sees in this some reason why Truecrypt doesn't show up in the "open with" tab of files.

---

