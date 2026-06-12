---
title: "Wrong Flash version"
date: 2009-12-13
forum: General Help
---

### Post by OldGrantonian on 2009-12-13
When I use the BBC site, I see messages "Cannot play media.You do not have the correct version of the flash player. Download the correct version"

However, when I go to Applications > Ubuntu Software Centre, I get the message, "Adobe Flash Player is installed on this computer. It is used by 1 piece of installed software"

I would be grateful for any advice.

BTW: If I try to use the Firefox add-ins feature, I'm directed to the Adobe page. Is it safe to use this feature rather than, for example, Synaptic Package Manager?
.

---

### Post by Greenwidth on 2009-12-13
Check that Gnash and Swfdec are not installed (alternate flash plugins) they might be interfering.

---

### Post by scouser73 on 2009-12-13
[COLOR="Red"]**Installing Flash Player via the Adobe website**[/COLOR]

**1** - Go to [[COLOR="Red"]**Adobe Flash**[/COLOR]]("http://get.adobe.com/flashplayer/?promoid=BUIGP")

**2** - Select **.deb for Ubuntu 8.04+** from the drop down menu

**3** - Click **Agree & Install Now**

**4** - Select **Open With** **GDebi Package Installer** in firefox or save the file and install the **.deb** file that way

**Current Version - Adobe Flash Player version 10.0.42.34**

---

### Post by OldGrantonian on 2009-12-14
Many thanks to Greenwidth and scouser73 for the responses :)

I haven't replied because I've been testing my disaster recovery plan.

It looks as if re-installation has restored my Flash :)

> **Greenwidth said:**
> Check that Gnash and Swfdec are not installed (alternate flash plugins) they might be interfering.

Although my Flash is working, I followed your suggestion for my own interest. Gnash or Swfdec are not installed :)
.

---

### Post by fancypiper on 2009-12-14
Is your cpu 32 bit or 64 bit?

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com

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
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
tar zxvf libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

echo "Linking the libraries so Firefox and apps depending on XULRunner (vuze, liferea, rsswol) can find it."
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins/

# now doing some cleaning up:
sudo rm -rf libflashplayer.so 
sudo rm -rf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

---

### Post by OldGrantonian on 2009-12-14
That looks like a very useful script :)

I have a 32-bit cpu. Do I need to so some edits?


> **fancypiper said:**
> Is your cpu 32 bit or 64 bit?

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com

echo "Stopping any Firefox that might be running"
sudo killall -9 firefox
...
...
sudo rm -rf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
```

---

### Post by fancypiper on 2009-12-14
No, for 32 bit I would use:

apt-get install flashplugin-nonfree

---

### Post by OldGrantonian on 2009-12-14
> **fancypiper said:**
> No, for 32 bit I would use:

apt-get install flashplugin-nonfree

I can see from Synaptic Package Manager that "flashplugin-nonfree" is already installed. So it must have been screwed up during all my experiments, and then restored after today's re-installation (which was for a different reason).

Thanks for your help :)

---

