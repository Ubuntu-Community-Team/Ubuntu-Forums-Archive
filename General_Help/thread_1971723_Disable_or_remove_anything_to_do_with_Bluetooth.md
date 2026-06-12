---
title: "Disable or remove anything to do with Bluetooth"
date: 2012-05-02
forum: General Help
---

### Post by cryptotheslow on 2012-05-02
Hi,

I've been running 12.04 Desktop since early beta and am plagued by crash reports popping up about:

"Sorry, Ubuntu 12.04 has experienced an internal error."

ExecutableName
/usr/bin/blueman-applet

Package
blueman 1.23-0ubuntu2

ProblemType
Crash

Title
blueman-applet crashed with KeyError in card_cb():'bluez.path'

etc.

KnownReport
[https://bugs.launchpad.net/bugs/962469](https://bugs.launchpad.net/bugs/962469)


The laptop this is running on has no bluetooth capability. So how do I kill any bluetooth daemon and remove this clearly overripe applet that keeps falling over drunk on its own fumes?

The most recent things I can find with goggles and duck seem to suggest the bluetooth daemon is compiled into the kernel. :confused:  Surely that can't be right :confused:

So yeh - any ideas welcome :)

Thanks
crypto

---

### Post by cryptotheslow on 2012-05-03
bump - anyone any ideas?

---

### Post by pqwoerituytrueiwoq on 2012-05-03
you cant remove it unless you don't care about the network manager
you should be able to turn it off in startup applications
there is a app called startup manage that may help

---

### Post by cryptotheslow on 2012-05-06
Thanks, I did as you suggested and removed the applet from startup applications.

---

