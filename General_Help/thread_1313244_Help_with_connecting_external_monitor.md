---
title: "Help with connecting external monitor"
date: 2009-11-03
forum: General Help
---

### Post by dbyjazz on 2009-11-03
I need some help connecting my HP Pavilion to my tv. I have a nvidia graphics card and I've been reading up a lot on X Screens? Is this what I need to be doing? If so how do I use it correctly? To be clear I just want to mirror my desktop and be able to close my laptop without the power going off. Thanks.

---

### Post by radu.ro on 2009-11-03
Open the Nvidia Settings as root: sudo nvidia-settings. From there you can set up your multiple display configuration really easy.

For the laptop lid thing, go to *System - Preferences - Power Management* and select what your laptop should do when you close the lid.

Good luck!

---

### Post by dbyjazz on 2009-11-03
thank you for the response, although I don't know which settings to choose, there are many.

---

### Post by dbyjazz on 2009-11-03
any ideas?

---

### Post by radu.ro on 2009-11-03
Yes... Sorry. There was a power outage here. Maybe this screenshot will help you:
[IMG]http://s3.amazonaws.com/twitpic/photos/full/40619646.png?AWSAccessKeyId=0ZRYP5X5F6FSMBCCSE82&Expires=1257294416&Signature=zANUGcXCwSw4J0yrjWiMBVI0xm4%3D[/IMG]
1. Separate X means that you will have another screen like the one you will have on your laptop monitor, but it will not be a clone.
2. Twinview lets you extend your screen so that it will be extended across two monitors.
Either way, you should be able to use you TV as a second display.

---

### Post by dbyjazz on 2009-11-03
I hit apply and it doesn't do anything.

---

### Post by radu.ro on 2009-11-03
If it says in the parantheses that the X needs to be restarted then you should log out and log back in. But not before you save your settings to the xorg.conf file. In my screenshot I was running a separate X display already so that's why I wasn't asked to restart the X.

The settings where you aren't advised to restart the X server can be applied immediately using the Apply button.

---

