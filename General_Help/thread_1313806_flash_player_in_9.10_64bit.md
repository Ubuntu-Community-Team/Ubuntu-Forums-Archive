---
title: "flash player in 9.10 64bit"
date: 2009-11-04
forum: General Help
---

### Post by niite on 2009-11-04
Looking for some guidance.

I've upgraded to 9.10 from 9.04.  All is well with the exception of the flash player.  The 32 bit version is really bad.  Flash will load, but it's pretty much crap on the page.  

So I've been trying to get the alpha 64 bit version from adobe going.  I've tried a number of methods, with the same results.   Running the script being circulated to install it (see [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8236653#post8236653](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=8236653#post8236653) ).  As well as just uninstalling the 32 bit plugin and loader, then copying the 64bit player into usr/lib/mozilla/plugins    Anyway i've tried, once it's installed, firefox still crashes when i try to load a page that has flash on it.  I've verified the plugin is installed by going to about:plugins, so I don't see any problems there.  Firefox just crashes and closes  when it encounters flash.  

So I'm kinda stuck..  32bit player kinda functions, but on some sites I really need the controls, it doesn't work.  And no joy at all with 64.  I need to be able to get work done so i've been using my windows install - but this is really not the way I'd like to go.

Any help or suggestions would be much appreciated.

-j

---

### Post by JamesUser on 2009-11-04
I don't have a 64-bit processor. But from what I hear from others, the 32-bit flash player with nsplugin works just fine.

---

### Post by JoePits on 2009-11-04
32 bit flash was crap so i found this thread

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1259102](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1259102)


uninstalled 32 bit flash in synaptics

ran that script to install 64 bit


was crashing hulu at first
until i rebooted.  now everything is fine, and playback is better than the default 32 bit plugin.

---

### Post by 00ber n00b on 2009-11-04
Did you purge all of the 32 bit plugins from your system?  Is this a laptop?

---

### Post by niite on 2009-11-04
> **00ber n00b said:**
> Did you purge all of the 32 bit plugins from your system?  Is this a laptop?

yeah it's a laptop.  i dumped all the 32 bit plugins for flash.

---

### Post by niite on 2009-11-04
> **JoePits said:**
> 32 bit flash was crap so i found this thread

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1259102](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1259102)


uninstalled 32 bit flash in synaptics

ran that script to install 64 bit


was crashing hulu at first
until i rebooted.  now everything is fine, and playback is better than the default 32 bit plugin.

well i did everything but reboot, i'll run the script again and then reboot.

---

### Post by cenzorrll on 2009-11-04
if your issue with the 32bit version of flash, all you need to do is turn off Compiz.

go to System--Preferences--Appearance, click on the visual effects tab and select no effects.

on my system, I installed the flashplugin-nonfree package (probably not the real name) from synaptic and it worked fine from there so long as compiz was off.

so hopefully you're not married to your desktop effects.  i was looking forward to all the fun stuff in compiz, but i rather like being able to use a fully functioning browser.

i am using 64bit 9.10 with few issues

---

### Post by bigbroantonio on 2009-11-04
First of all the script you referred to should be corrected to:

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# more very minor updates by damien[at]groovey[dot]com
# and one more update by Antonio Cassano bigbroantonio[at]yahoo[dot]it
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and installing Getlibs for required libraries"
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"
```

I'm really not sure about installing in the nspluginwrapper under 64bit.

Also, have a look at this thread: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1311649](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1311649)

There you'll find two other solutions

1.  the recommended move libflashplayer.so to /usr/lib/mozilla/plugins/
2.  yet another script.

Good luck!

---

### Post by niite on 2009-11-04
> **niite said:**
> well i did everything but reboot, i'll run the script again and then reboot.

i followed this one and rebooted..  works great now.  Many thanks!!!

---

### Post by kipper_t on 2009-11-04
> **bigbroantonio said:**
> First of all the script you referred to should be corrected to:

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba romeo.cioaba@spotonearth.com
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# more very minor updates by damien[at]groovey[dot]com
# and one more update by Antonio Cassano bigbroantonio[at]yahoo[dot]it
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and installing Getlibs for required libraries"
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
tar zxvf libflashplayer-10.0.32.18.linux-x86_64.so.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"
```I'm really not sure about installing in the nspluginwrapper under 64bit.

Also, have a look at this thread: [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1311649](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1311649)

There you'll find two other solutions

1.  the recommended move libflashplayer.so to /usr/lib/mozilla/plugins/
2.  yet another script.

Good luck!

Tried this, copied the code into a .sh script, ran it, restarted firefox, seemed to work, then I had youtube and googlemail open and it segment faulted. 
Did a system restart with alot of errors so i just cut the power and turned back on again and *touch wood* seems to be going good so far.
Anyone any ideas about what was causing the segment fault, my terminal output just had a load of
(firefox:2295): Gdk-WARNING **: XID collision, trouble ahead
maybe from the restarting of firefox into the old session or something.
but yay i have youtube now.
thanks for all this info :)

---

### Post by ladgrove on 2009-11-09
Hey all, just thought I'd report in, Flash Adobe plugin fully working on Firefox 3.5.3 with Compiz enabled Karmic 9.10, the work-around is the right-click, then left click off the menu whilst still holding right click to make your selection. 

Not ideal, but I think a better "solution" than disabling Compiz, which I didn't really think was much of a solution in the first place, given that a lot of new users are drawn to Ubuntu for Desktop Effects, gimmicky though some may be... One of the reasons I keep coming back to Ubuntu is the brilliant Desktop Cube & other Compiz goodies which speeds up my workflow.

Anyway, that's my 2-cents worth.

Cheers.:p

---

### Post by pippi89 on 2010-01-02
I used the script and rebooted, then the flash plugin worked fine on any page but the facebook's Restaurant City game. when I go to that page, my browser freezes and I get "unable to establish a connection to Restaurant City" error. when I use flash plugin with wrapper by installing ubuntu-restricted-extras, I can play this game but I can't control the flash player in youtube. Anyone please help me!!!




p.s. Sorry for my bad english >.<

---

### Post by HappyFeet on 2010-01-02
Some websites will not work properly with linux's version of 64bit flash. However, most do. I think you will have to choose which flash does the most for you. For me, 64bit flash wins.

---

### Post by Astrals on 2010-01-17
> **HappyFeet said:**
> Some websites will not work properly with linux's version of 64bit flash. However, most do. I think you will have to choose which flash does the most for you. For me, 64bit flash wins.


Have to agree.

All I do to install it is:
Download the 64bit tar.gz from adobe, extract it.
Create "plugins" folder under my home /home/xxxx/.mozilla
terminal "sudo cp libflashplayer.so" to the plugins folder.
Done flash working great with no sound issues.

Now that is easy as can be.

I hope this helps.

---

