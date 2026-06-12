---
title: "why my ubuntu or firefox cannot watch youtube??"
date: 2009-09-23
forum: General Help
---

### Post by miao miao on 2009-09-23
hi recently i've switched to ubuntu. i've fully updated everything via update manager.and i've installed all the files that firefox asked me to install n i still cannot watch youtube .. pls help me...

---

### Post by 3rdalbum on 2009-09-23
Install Flash Player.

On 32-bit, install the "flashplugin-nonfree" package from Synaptic Package Manager.

On 64-bit, download the 64-bit alpha Flash Player from Adobe Labs, and put the "libflashplayer.so" file into /usr/lib/mozilla/plugins. You need to open a file browser as root in order to write this file to this location:

```
gksudo nautilus
```

---

### Post by miao miao on 2009-09-23
I've installed but still cannot..

---

### Post by 3L33T on 2009-09-23
> **miao miao said:**
> still cannot

Are you behind a firewall?  Does youtube work in a windoze machine that is in the same network as your Ubuntu machine?

---

### Post by invitingdopeman on 2009-09-23
just guessing but what kind of pc you got i have an old gateway that i found its a gp6-400c and i cant watch vids on youtube cuse my prossecer isnt fast enough hopefully it helped INVITINGDOPEMAN:guitar:

---

### Post by miao miao on 2009-09-23
I'm using acer aspire one with 8 G SSD. Previously I was with kubuntu and the youtube played just nice. but when i switched to ubuntu... It becomes like these: the volume cannot be adjust n movie cannot control( which means I cannot control which part I want to play) n sometime the video shows & sometime it just shows a triangle with grey background. in addition on that i can hear to sound while it plays

---

### Post by bedhead75 on 2009-09-23
Which release of Ubuntu are you using and is it 32 or 64 bit?  I installed flash through ubuntu-restricted-extras in synaptic and it just worked in Firefox and any other browser.  I'm running 32-bit flash on 64-bit Jaunty because 64-bit flashed crashed Firefox on some sites like Hulu.com.  Also to troubleshoot, try installing another browser like Epiphany, Midori, Seamonkey, Opera, or Galeon just to see if flash works there.

---

### Post by 3rdalbum on 2009-09-23
> **miao miao said:**
> I'm using acer aspire one with 8 G SSD. Previously I was with kubuntu and the youtube played just nice. but when i switched to ubuntu... It becomes like these: the volume cannot be adjust n movie cannot control( which means I cannot control which part I want to play) n sometime the video shows & sometime it just shows a triangle with grey background. in addition on that i can hear to sound while it plays

There's a Firefox plugin (Is it NoScript?) that stops Flash movies from playing. Either you can block them directly, where they'll never appear, or they will only start to load when you click on the triangle.

---

### Post by miao miao on 2009-09-23
on firrefox bars>tools>Add ons> it only shows these:
1.default plugin
2.demo print plugin for unix/linux
3. DivX(R)web player
4.quicktime plug-in 7.2.0
5. shockwave flash
6.VLC multimedia plugin (compatible Totem 2.26.2)
7. windows media player plug-in 10 ( compatible; Totem)

---

### Post by bedhead75 on 2009-09-23
First see if the problem is specific to Firefox or specific to your installation of flash.  If flash works on another browser, than Firefox is the problem.  It's not unheard of for some Firefox add-ons to be problematic.  We need to find a starting point first.

---

### Post by peterthinking on 2009-09-24
grey circle with the play arrow on it? right click and select "autoplay" and "remember last"

if that won't fix it do this..
-----------------snip----------------------------
Flash not working? all choppy and pixeled?
Get rid of the old one....

In terminal type...

sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin

Now enable Canonical partner download, navigate here...

System> Administration> Software Sources> Third Party Software and then check on the Canonical partner boxes.

Now get the new one...Type in terminal...

sudo apt-get install adobe-flashplugin


Done
---------------snip----------------------
Peter

---

### Post by miao miao on 2009-09-24
when i type on sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin.
it said :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package swfdec-mozilla-plugin-gnash


should i continue the following step?

---

### Post by 3rdalbum on 2009-09-24
> **miao miao said:**
> when i type on sudo apt-get remove --purge swfdec-mozilla mozilla-plugin-gnash flashplugin-nonfree adobe-flashplugin.
it said :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package swfdec-mozilla-plugin-gnash


should i continue the following step?

Copy and paste the command into your terminal. You typed it wrong.

---

### Post by sunshine1 on 2009-09-24
this problem happened to me  i went here _[http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)_

then i choosed the version (which was ubuntu 8.04 +) i pressed agree and instal now i installed the dep package and all now is fine

---

### Post by miao miao on 2009-09-24
thank you peter . it works!! i can watch youtube video now!! 
so what actually happened to my computer peter?? i don't know anything about ubuntu. i was exwindow user.

---

### Post by peterthinking on 2009-09-24
> **miao miao said:**
> thank you peter . it works!! i can watch youtube video now!! 
so what actually happened to my computer peter?? i don't know anything about ubuntu. i was exwindow user.

not sure, may be something new in the new package that the old one didn't have. Anyway replacing it is an easy fix so save the fix on a file and carry on with your life. If you ever re-install you may want to run it again.

Find the Firefox extension "Download Helper" If you really like a U tube video you can keep it...very easy to use. when the little red/green/blue ball symbol on your menu bar starts spinning you have a video on that page you can download.

Later

peterthinking

---

### Post by doron387 on 2009-09-24
check out this post - it made my computer to work great.
i didn't read your thread but the following post will also solve you all the future problems regarding multimedia.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

enjoy and welcome to ubuntu and the community
doron387

---

### Post by miao miao on 2009-09-24
once I use my "computer janitor" to clean up a system. the youtube video stop working n the only  way to solve this problem again is to do the same as peter said.   so meaning i cannot use my computer janitor anymore...:(

---

### Post by Lars Noodén on 2009-09-24
> **miao miao said:**
> hi recently i've switched to ubuntu. i've fully updated everything via update manager.and i've installed all the files that firefox asked me to install n i still cannot watch youtube .. pls help me...

What you can do in the longer run to prevent that problem is vote with your feet and patronize sites that make use of standards that any system can run.  

	[http://thevideobay.org/](http://thevideobay.org/)
	[http://commons.wikimedia.org/](http://commons.wikimedia.org/)
	[http://dailymotion.com/](http://dailymotion.com/)

[Youtube's product is your attention]("http://www.helium.com/items/702342-a-look-at-youtubes-business-model") and the money comes from advertising.  The real customers are the advertisers.  Not all the decisions appear to be business decisions.  Youtube is marketing closed formats and that locks out a growing segment of the market.

---

