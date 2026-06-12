---
title: "New Video Card"
date: 2006-04-27
forum: General Help
---

### Post by Kintwa on 2006-04-27
I just installed my new video card! :D Only problem is, I'm not sure how to get it working with Ubuntu without a fresh install. My old video card was an ATI 9800. I've switched to Nvidia, Geforce.

As expected, X doesnt want to start, as I have it configured to use ATI drivers.  I can login, and use the shell just fine. This is where I'm stuck. I'm not sure what to do next. Are there nvidia drivers I need to download / install? Or do I just have to edit my Xorg config file? I'm new to nVidia on Linux.

Any help is appreciated. :)


Edit: Wow! How did I manage to post this here? Can this be moved to the Breezy hardware forums?

---

### Post by helpme on 2006-04-27
[QUOTE=Kintwa]I just installed my new video card! :D Only problem is, I'm not sure how to get it working with Ubuntu without a fresh install. My old video card was an ATI 9800. I've switched to Nvidia, Geforce.

As expected, X doesnt want to start, as I have it configured to use ATI drivers.  I can login, and use the shell just fine. This is where I'm stuck. I'm not sure what to do next. Are there nvidia drivers I need to download / install? Or do I just have to edit my Xorg config file? I'm new to nVidia on Linux.

Any help is appreciated. :)


Edit: Wow! How did I manage to post this here? Can this be moved to the Breezy hardware forums?[/QUOTE]
I think the best way would be to install the nvidia-drivers (sudo apt-get install nvidia-glx should take care of that) and then either edit xorg.conf by hand, or rund sudo dpkg-reconfigure xserver-xorg.

Hope this helps.

---

### Post by justleen on 2006-04-27
i did the same, and its acutally quite easy

theirs a great guide on the Nvidia drivers on this forum [here]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia+drivers")

Dont let the amount of tekst scare you off :)
If you download the linux drivers of the nvidia site, i recommend skipping to install method 2 in that thread.

The 3th reply in the post offers a very easy way to install them as well.

if you follow the link in my sig for the Ati driver, you can use the first part to get rid of the ati drivers (this is NOT neccesary for it to work, but why have them lingering around..)

Edit: as a quick way to get X working again, boot your machine, switch to a terminal with CTRl-ALT-F1, login there and run *sudo dpkg-reconfigure xserver-xorg*.
dont autodetect, and select the NV driver. 
Go back to X with CTRL-F7, and press CTRL-ALT-BKSPC to restart X..
This will use the "default" nvidia driver. Note that this is NOT the same driver as the one from Nvidia so the 3d performance is awfull

---

