---
title: "Gsynaptics settings not saving"
date: 2010-05-04
forum: General Help
---

### Post by Jheric on 2010-05-04
I followed the instructions for installing Gsynaptics on 10.04 to configure my touchpad and it seems to be working... except, something seems to override my settings whenever I close Gsynaptics or after about 10-20 seconds has passed.

Mainly, all I'm trying to do with it is use it for a simple way for me to turn my touchpad on and off... since it's overly sensitive and causing problems.

Does anyone know why gsynaptic changes may not be sticking?

---

### Post by spayman on 2010-05-04
on GS , choose the packages u want install
then , make sure you click on the green mark on top(APPLY)
I think you didn't do that right :S

---

### Post by Jheric on 2010-05-04
No... it's successfully installed. That's not what I have a problem with. Gsynaptics just wasn't saving the changes it made. 

Anywho, I took another approach and I'm quite happy with it. A simple script saves the day for me... maybe other lucid users will want to do this:

```

#!/bin/bash
#
# create a desktop launcher to run this (better still, a toolbar icon so that single click does it)…
#
/usr/bin/synclient TouchpadOff=$(if [[ $(expr `synclient -l | grep TouchpadOff | cut -f2 -d =`) == 0 ]]; then echo 1; else echo 0; fi)

```

Just have to go to properties and tell it to execute as a program.

Then I just linked to it on my gnome panel and gave it a pretty button. Works like a charm!

---

### Post by dino99 on 2010-05-04
> **Jheric said:**
> No... it's successfully installed. That's not what I have a problem with. Gsynaptics just wasn't saving the changes it made. 

Anywho, I took another approach and I'm quite happy with it. A simple script saves the day for me... maybe other lucid users will want to do this:

```

#!/bin/bash
#
# create a desktop launcher to run this (better still, a toolbar icon so that single click does it)&#8230;
#
/usr/bin/synclient TouchpadOff=$(if [[ $(expr `synclient -l | grep TouchpadOff | cut -f2 -d =`) == 0 ]]; then echo 1; else echo 0; fi)

```

Just have to go to properties and tell it to execute as a program.

Then I just linked to it on my gnome panel and gave it a pretty button. Works like a charm!

from synaptic details:

With X.org 7.4, you might rather consider to use gpointing-device-
settings, which is modern replacement for gsynaptics.

anyway i wonder if you really need to install such package as kernel have built-in modules

---

