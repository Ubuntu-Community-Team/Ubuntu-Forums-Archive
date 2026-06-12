---
title: "How do I get the latest official build of Firefox and Thunderbird?"
date: 2009-09-12
forum: General Help
---

### Post by papajonesy on 2009-09-12
Hey guys. I've been trying for a while to figure out how to get the latest official builds of Firefox and Thunderbird but can't quite figure it out. I tried, I believe it was called ubuntuzilla but it didn't work, it updated both Firefox and Thunderbird to the most recent version but wouldn't load any pages. Do I have to add new sources? Help would be much appreciated.

---

### Post by KyleRaynor on 2009-09-12
The devs are hard at work on 9.10 atm. You can download the tgz from the mozilla site, and unpack it to /opt like I did. Then move /usr/bin/firefox to /usr/bin/firefox.ubunu and ln -s /usr/bin/firefox /opt/firefox/firefox. Then all should be well.

---

### Post by papajonesy on 2009-09-12
thank you, worked like a charm. a while back i did the same thing except extracted the tarball to my home dir but after that i didn't know how to get the menu shortcuts to work, but you cleared that up for me with the /usr/bin dir. thank you.

---

### Post by papajonesy on 2009-09-12
were you able to get flashplayer to work? if so i could use a how to as well

---

### Post by KyleRaynor on 2009-09-12
No prob. /opt is where stuff like that should go, it will keep your home directory a little cleaner, but really you can unpack it where ever you want. IMHO That's whats so great about Linux. That and there's no registry to get cluttered up.
I even made an alias for when I compile my own stuff that adds "--prefix=/opt" to the end of ./configure. That combined with checkinstall makes life much easier for anything that's not in a repo yet.

---

### Post by KyleRaynor on 2009-09-12
It's been a while, if the flashplayer install doesn't work from synaptic, I probably installed it from the adobe website. But it works fine for me. Firefox 3.5.2 and flashplayer 10.0 r32
[edit]
flashplayer is installed in a plugins dir somewhere, which is separate from the ff install dir, I know that for sure, they should all share the same one.

---

### Post by papajonesy on 2009-09-12
I figured it out. I downloaded the tarball for flash player 10. you extract the lone libflashplayer.so file to /opt/firefox/plugins and presto, you have a working flash player. Thank you again, I appreciate the help. Now I have everything I need.

---

### Post by KyleRaynor on 2009-09-12
glad I could help. You haven't had any issues with compiz have you?
I need to turn it off, cause it doesn't play well with wine, but it screws up my screen. My post on it(it's not yet old enough for the right person to have seen it) has a screenshot of what I mean.

[http://ubuntuforums.org/showthread.php?t=1264957](http://ubuntuforums.org/showthread.php?t=1264957)

---

### Post by nanotube on 2009-09-12
> **papajonesy said:**
> Hey guys. I've been trying for a while to figure out how to get the latest official builds of Firefox and Thunderbird but can't quite figure it out. I tried, I believe it was called ubuntuzilla but it didn't work, it updated both Firefox and Thunderbird to the most recent version but wouldn't load any pages. Do I have to add new sources? Help would be much appreciated.

Hi
if you're using 64bit ubuntu, this is a known problem with the official mozilla build of firefox. to fix it, you have to set the network.dns.disableIPv6 setting to true, in about:config in firefox.

(this is described in the ubuntuzilla faq)

---

### Post by papajonesy on 2009-09-12
i'm guessing you are using avant window navigator. i had the same problems. try cairo dock, it works much better for me, i had no compiz problems. sorry, i love awn but it totally jacks my screen to oblivion within a few hours, especially as you said run wine or wine based apps, i couldn't run any of my games or apps i had installed with crossover without my screen turning to blocks.

---

### Post by KyleRaynor on 2009-09-14
sorry, haven't heard of avant, I've always used gnome (I for some reason can't stand the way kde looks). But I have found the reason, gnome-do using the docky theme requires compositing. I just have to turn off docky for the desktop, and compiz to use wine/gl games. I'm considering creating a new user specifically for running games. xfce wm cause it's light, and turn off any services/startups that aren't needed for the games to run.

---

