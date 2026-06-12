---
title: "Flash Makes Ubuntu Slow for me."
date: 2009-10-10
forum: General Help
---

### Post by TheNerdAL on 2009-10-10
Okay, so I upgraded to the 9.10 Beta and Whenever I go to like a Myspace Music page with a lot of flash, it goes slows and lags and maybe freezes, how do I stop this?

---

### Post by TheNerdAL on 2009-10-10
Anyone?

---

### Post by delcypher on 2009-10-10
It could a number of things.

1. Incorrectly configured video drivers

Find out the make of your card
```
lspci | grep VGA
```

and see if there are any reported problems with that card, or recommended configurations.

2. Incorrect choice of flash-plugin

Look at my post here [http://ubuntuforums.org/showthread.php?t=1287012#9]("http://ubuntuforums.org/showthread.php?t=1287012#9")

and this post about improving flash performance (see flash tweaks)

[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

3. You're using a Beta, it's likely things aren't quite sorted yet.

---

### Post by TheNerdAL on 2009-10-10
But I think this also happened on 9.04, and this is what I got: "01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"

---

### Post by TheNerdAL on 2009-10-10
Anyone?!?!?!

---

### Post by TheNerdAL on 2009-10-10
Help me! D:<<<<<<<<<<

---

### Post by TheNerdAL on 2009-10-10
D:

---

### Post by TheNerdAL on 2009-10-10
Still no help....

---

### Post by Vaphell on 2009-10-10
it's looks like a crappy gpu and flash taxes CPU heavily, not much to be done. You can try installing adblock and noscript to get rid of every flash animation and every unneeded javascript that is not crucial for the webpage experience (ads, banners, traffic monitors, data mining stuff)
Probably in windows you'd get better performance, it's not like flash under linux is the top priority for adobe.

---

### Post by RichardLinx on 2009-10-10
Yeah. Flash sucks on Linux big time. I find Opera handles a lot of flash content noticably better - but it's still not fantastic. Like Vaphell mentioned above, disabling flash would fix this priblem but then you won't be able to view flash content on the page at all (If you actually want to).

You could also install Adblock Plus in firefox and manually block different flash objects.

---

### Post by TheNerdAL on 2009-10-10
> **RichardLinx said:**
> Yeah. Flash sucks on Linux big time. I find Opera handles a lot of flash content noticably better - but it's still not fantastic. Like Vaphell mentioned above, disabling flash would fix this priblem but then you won't be able to view flash content on the page at all (If you actually want to).

You could also install Adblock Plus in firefox and manually block different flash objects.

Okay, where do I get Adblock Plus?

---

### Post by RichardLinx on 2009-10-10
> **TheNerdAL said:**
> Okay, where do I get Adblock Plus?

[https://addons.mozilla.org/en-US/firefox/addon/1865](https://addons.mozilla.org/en-US/firefox/addon/1865)

I found that by googling "Adblock Plus". It's a firefox add-on. :)

---

### Post by Johnny B on 2009-10-11
i had the same problems, this worked for me
install flash from this guide:
[http://ubuntuforums.org/showthread.php?t=1233235]("http://ubuntuforums.org/showthread.php?t=1233235")

---

### Post by Johnny B on 2009-10-11
sorry thats for 64 bit. but it will work for 32 bit if you change the libflashplayer.so file
which you can get from [here]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.tar.gz%29")

and heres the script
```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Edited by Jordan Loehr jordan.loehr@gmail.com

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox

echo "Removing any other flash plugin previously installed:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


echo "Installing Flash Player 10"
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

cd /etc/
mkdir adobe
sudo touch /etc/adobe/mms.cfg
sudo echo "OverrideGPUValidation=true" > /etc/adobe/mms.cfg
exit
```

---

### Post by emada on 2009-11-06
@Johnny B 

tyvm, your solution worked great!

---

