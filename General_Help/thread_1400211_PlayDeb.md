---
title: "PlayDeb"
date: 2010-02-06
forum: General Help
---

### Post by tlillies on 2010-02-06
I am not sure if this is the right place to put this thread but i am having trouble with the PlayDeb Repositories. I am trying to install Sandbox Game maker for my computer. To access the PlayDeb repository I added the software source "deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb apps" and then entered "wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -" command to add the GPG key. Then i go to PlayDeb.net and try to install Sandbox and it says can not find package 'sandboxgamemaker'. I am an ubuntu noob and i am not sure what i am doing wrong.

---

### Post by howefield on 2010-02-07
If you have successfully added the repository, load up Synaptic Package Manager. You'll find it in the System > Administration menu.

Do a search for sandbox and you'll see the various options, check the box beside the package you want to install and mark for installation.

Then press the apply button, and apply again.

---

### Post by marshmallow1304 on 2010-02-07
You need to do a
```
sudo apt-get update
```
first.

This can also be accomplished via the "Reload" button in Synaptic.


After that, you should be able to install via the PlayDeb website or using Synaptic as howefield describes above.

---

### Post by tlillies on 2010-02-08
Wow i really messed up badly! I added the GetDeb repository instead of the PlayDeb one. Sorry guys! Thaks

---

