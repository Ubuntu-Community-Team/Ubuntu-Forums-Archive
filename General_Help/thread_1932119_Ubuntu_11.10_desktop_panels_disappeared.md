---
title: "Ubuntu 11.10 desktop panels disappeared"
date: 2012-02-26
forum: General Help
---

### Post by sirriffsalot on 2012-02-26
Hello!

Just upgraded to 11.10, and the only thing I can see on my desktop are the files that were there prior to update... Is this a common bug? How would I go about fixing this? I can always use Ubuntu Classic, but I'd love to know how to sort this out if it is possible.

Also, 11.10 has somehow messed up my opera window configuration, because, as I ran opera in terminal, I got this message:

(operapluginwrapper:2400): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

and I suppose it has something to do with the fact that the "brown-grayish" framing of opera has disappeared and I have no means of moving the window around. Thanks a lot for any help! :-)

--> Leo

---

### Post by Frogs Hair on 2012-02-26
If the terminal works try the following . ```
sudo apt-get install gnome-session-fallback
```
Restart and see if you can login to _Classic Gnome_ using the gear icon on the right side of the greeter.If you can then install the following ```
sudo apt-get install gnome-tweak-tool
```
Open up the tweak tool > desktop and turn your desktop icons on properly . They should not be there at all.This is something residual from the upgrade.

Run the following to find out if you can run Unity.
```
/usr/lib/nux/unity_support_test -p
``` 

If the test says yes logout and try to login to Unity 2D if everything appears to work install the CCSM from software. Install a proprietary driver if needed . I write if needed because I can login to Ubuntu with out it.

Finally try to login to Ubuntu.

---

### Post by sirriffsalot on 2012-02-27
Thanks for taking time out to help:)

E: Unable to locate package gnome-session-fallback

This was what I got from doing "sudo apt-get install gnome-session-fallback"

... :D

Edit:

There can be many different reasons for this, one being as simple as the Unity panel having disappeared, in which case you just have to mouse over the left side of the screen until it appears, or more complicated solutions like running "unity --reset" in a terminal or checking your compizconfic (sudo apt-get install compizconfig-settings-manager) to temporarily disable the Unity tick to see if that is at all affecting the situation or not. If it does, then things are working fairly alright, and you should search around for solutions, if not, I suggest reinstalling Ubuntu. Also, check the "window decorations" option and reboot; if nothing has changed, try "unity --reset" again. Hope this helped!!

--> Leo

---

