---
title: "!FIX! Conexant(compaq, dell, hp) speakers don't mute with headphones !FIX!"
date: 2010-09-01
forum: General Help
---

### Post by googeek on 2010-09-01
Hi there. Do you have a Conexant chip set for your audio?

Let's find out, shall we?

Type this into your terminal and check out the output
cat /proc/asound/card0/codec#* | grep Codec

If the line that appears contains the word Conexant, you've got a driver issue.
Most new comers to Ubuntu forget to seek out the drivers for their hardware. Since Ubuntu generally does such a great job of getting things just about right, most folks don't even know they're missing a driver until they try to do something fancy.
To use your audio card for things like recording, and to get the speakers to mute, all you need is the correct driver.


[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

This driver will work with most Conexant chipsets.
Download the deb, save it, install it. Restart your computer, and check out all the new channels in your mixer.
That's it!

Sometimes this install will cause you to need to restart your mixer. You can do this manually in the terminal very easily.
Also, from time to time certain ubuntu updates will revert your sound settings. Simply reinstall the deb and everything will go back to the way you had it.

---

