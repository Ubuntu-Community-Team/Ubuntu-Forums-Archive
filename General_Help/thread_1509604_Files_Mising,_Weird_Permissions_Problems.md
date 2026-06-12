---
title: "Files Mising, Weird Permissions Problems"
date: 2010-06-14
forum: General Help
---

### Post by zjmichen on 2010-06-14
Ok, here's the problem.  I logged on today  to find that all the folders in my home folder are empty when I look at them in nautilus.  When I try to cd into them via the terminal, I get a message that says I don't have permission.  When I cd as root, however, all my files are there.

Yesterday I was messing around with Apache authentication, and it appeared from Firefox that the contents of one of my directories was empty.

I checked, and I am an Administrator, etc.  I'm on Ubuntu 10.04.  Wtf happened?

---

### Post by squaregoldfish on 2010-06-14
Check the ownership of the files in your directory - has it been changed to another user (e.g. apache)? If so, you can use chown (as root) to reset the ownership.

Steve.

---

### Post by zjmichen on 2010-06-14
Nope, I own everything. :/

---

### Post by zjmichen on 2010-06-14
Well, I restored from a Back in Time backup, and that seems to have fixed it, but I still don't know what went wrong.

---

