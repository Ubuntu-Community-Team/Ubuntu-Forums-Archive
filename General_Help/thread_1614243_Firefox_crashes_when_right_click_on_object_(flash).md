---
title: "Firefox crashes when right click on object (flash)"
date: 2010-11-05
forum: General Help
---

### Post by thelastbean on 2010-11-05
I noticed this issue was brought up back in 2005, but because that thread was in the "archives" I couldn't reply to it.  Any time I right click on anything that has flash, my browser goes grey and is unresponsive.  I'm forced to force quit Firefox.  I'm still in the process of making sure this bug hasn't already been reported in 2010.

**OS**: Ubuntu 10.10 Maverick
Gnome 2.32.0

**Browser**: Firefox 3.6.12

**Flash**: File:  npwrapper.libflashplayer.soVersion:   Shockwave Flash 10.1 r102          Installed from restricted extras in repos

---

### Post by Zortrox on 2010-11-06
I have those exact same specs and it crashes for me as well.  I think it's with the new flash update.  It was working fine before I updated it.

---

### Post by wangsuda on 2010-11-07
My crash occurs whenever I right or center click on a link. Still trying to solve this one. I have reloaded FF twice, and nothing has improved.

---

### Post by benlyboy on 2010-11-07
I have the same issue with firefox and flash, but not in ubuntu but when I use firefox in wine.

I have ubuntu 10.10 and firefox and flash seems to work ok. I also have firefox installed in wine. I use it to work with a windows web editor that I like to use. 
This install does the same thing greying out if you open a page with flash content.

---

### Post by wangsuda on 2010-11-07
> **wangsuda said:**
> My crash occurs whenever I right or center click on a link. 
UPDATE - only seems to happen in G-Mail. Other things (like this and other forums) don't seem to be affected.

---

### Post by sampan74 on 2010-12-07
I am also experiencing this problem on some sites. It seems like right clicking works on some flash content but not on other. 

Here is an example that crashes flash/firefox on right click for me:
[http://www.aftonbladet.se/webbtv/nyheter/utrikes/article8233962.ab](http://www.aftonbladet.se/webbtv/nyheter/utrikes/article8233962.ab)

And here's one that does not:
[http://www.youtube.com/watch?v=y5fwvYICZvY](http://www.youtube.com/watch?v=y5fwvYICZvY)

BTW, I am using Ubuntu 10.04 64-bit and Adobe flash 10,1,102,65 on a HP Elitebook 8540w .

---

### Post by Skybinary on 2010-12-12
Same here, it is really really beginning to get my goat!
Am I not merciful, see no expletives.

---

### Post by outleradam on 2010-12-12
Yep. same problem here.  I'm uninstalling flash and installing Gnash right now to see if it is flash, firefox, or something about the firefox ubuntu extensions.   

Definately annoying...  I go on photobucket to deposit pictures, then when it gives me a like, I'm supposed to singe click it....  Thing is, I've been right clicking and then copy link location for years..  It's driving me nuts not being able to right click on Flash objects.

---

### Post by outleradam on 2010-12-12
I changed my active packages from Adobe Flash Plugin to Gnash SWF Viewer and Flashblock extension for Firefox.  Everything worked.  Now I'm going to go back and figure out the combination which is causing the problem.

---

### Post by outleradam on 2010-12-12
I've tried all the packages offered by the default package managers in Ubuntu, but I am getting nowhere.    Adobe is the only one which will view the video on this page.  [http://hackaday.com/2010/12/11/kids-type-with-their-eyes-robot-arm-prints-their-words/](http://hackaday.com/2010/12/11/kids-type-with-their-eyes-robot-arm-prints-their-words/)  But it also crashes every time you right click on anything flash related.

---

### Post by outleradam on 2010-12-12
Problem solved by installing Adobe Flash Player Square

Here's how:
```

sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper
sudo apt-get install ia32-libs nspluginwrapper
mkdir ~/flashplayer
cd ~flashplayer
```go here for the flash player if the following commands do not work [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)... unpack it into ~/flashplayer
```

wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz
tar zxvf flashplayer10_2_p3_64bit_linux_111710.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
cd ~
rm -Rf ~/flashplayer

```Now to link it all up manually
```

sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/xulrunner-addons/plugins/
```
For referenced I used this page: [http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html](http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html)   

Everything seems to work properly now for me.   Relatively easy  fix I'd say.

---

### Post by sampan74 on 2011-01-18
> **outleradam said:**
> ...
Everything seems to work properly now for me.   Relatively easy  fix I'd say.
I works like a charm for me! Thanks a bunch! This problem has been annoying me for months now.

---

### Post by wavesound on 2011-06-03
Hi All.
Just installed 10 10 lts
This happens a lot for me when I open flash full screen.
It goes grey and crashed ( I send the crash report for Flash)
Even cntl alt backspace wont work.
Eventually I get back to a page.
Also note that using the scroll wheel on my mouse seems to lock up Fire fox when the screen goes grey.

10.10 seem a bit ropey to me at the moment (64bit) and such a shame as I have recommended it to quite a few people.
Seem Ubuntu have dropped the ball here

Cheers
Bob

---

