---
title: "need a flash player"
date: 2010-03-17
forum: General Help
---

### Post by killing kittens on 2010-03-17
ive tryed adobe flash in a .tar.gz and every other format threw there site but nothing works plz help

---

### Post by _h_ on 2010-03-17
Need some more information.

What bit version of Ubuntu are you using, 32 or 64bit? Also, what browser are you using?

---

### Post by killing kittens on 2010-03-17
my browser is firefox im using hardy heron but not sure if its 32 or 64 i can find were this info is located

---

### Post by _h_ on 2010-03-17
Try this command via terminal and post the output:

file /sbin/init


It should tell you what kind of architecture your ubuntu is, something like this (which is my output):

/sbin/init: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.15, stripped

---

### Post by killing kittens on 2010-03-17
ok i hope you can help me i really need a flash player lol

/sbin/init: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped

---

### Post by rcayea on 2010-03-17
I think an easy way is to install Ubuntu-Tweak and then install Flash from there. Will that help? Or, maybe check synaptic.

---

### Post by _h_ on 2010-03-17
Ok, you got 64bit ubuntu. Adobe has an alpha version of 64bit flash in their labs, which you can download here:

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz)

Extract it to a folder something like /home/username/Downloads

Now open a terminal and run this command:

sudo mkdir ~/.mozilla/plugins

Which will create a plugins folder, and then run this command:

sudo cp /path/to/libflashplayer.so ~/.mozilla/plugins

Which will copy the libflashplayer.so from whatever directory you extracted it to your mozilla plugins folder which was created.

After that restart firefox and to see if you have a successful copy, goto Tools -> Addons -> Plugins and you should see a Shockwave Flash listed there as version 10.0 r32.

---

### Post by killing kittens on 2010-03-17
got it thank you sir ^_^

---

### Post by _h_ on 2010-03-17
> **killing kittens said:**
> got it thank you sir ^_^

Welcome. Now remember it's an alpha version of adobe flash player, so it may have bugs, but I am using it and haven't run into a problems with it yet. :)

---

