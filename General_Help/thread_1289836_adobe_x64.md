---
title: "adobe x64"
date: 2009-10-12
forum: General Help
---

### Post by haggus on 2009-10-12
HELP I can't get this working I have been at it for weeks with little or no success I have upgraded to 9.04 today I have tried the ndswrapper flashfree plugin and about 10 other ways that say the work and none of it does. All I get is 



Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.


I have the latest version the flashplayer10 from the adobe site put it in /usr/lib/mozilla/ plugins I've followed about five different threads that say it is working well I'm to the point now where I can't do anymore. 

Anyones help would be appreciated.

---

### Post by Giblet5 on 2009-10-12
Do you have the NoScript add-on for Firefox?

Are you using the Adblock add-on?

---

### Post by haggus on 2009-10-12
no add ons

---

### Post by Giblet5 on 2009-10-12
Try this:

Exit all instances of Firefox and Thunderbird.

```
cd ~
mv .mozilla .mozilla-backup
```

Now start Firefox and [go to TDS]("http://www.thedailyshow.com/").

Does the video play?

If so, Adobe Flash is working as well as it's going to.

If not:
```
cd ~
rm -fr .mozilla
mv .mozilla-backup .mozilla
sudo apt-get install flashplugin-nonfree
```

Then start Firefox and go to the TDS link above. All better?

---

### Post by haggus on 2009-10-12
No luck it's not telling me I don't have the plugin but it won't play video.
Any other ideas some program I am missing?

---

### Post by fluffman86 on 2009-10-12
Hope you didn't mess something up by getting it from the Adobe site.  All I did was
sudo apt-get install ubuntu-restricted-extras
and flash started working

---

### Post by haggus on 2009-10-12
ubuntu-restricted-extras is already the newest version

so says the terminal.

---

### Post by Giblet5 on 2009-10-12
If you were on 9.10 beta, I'd blame Firefox.

Flash doesn't work for me on this system (9.10) right now. If I restart Firefox, it might start working (it does, on and off) but I don't care. I installed Google Chrome and that works.

---

### Post by haggus on 2009-10-12
I have google chrome installed as well although I haven't tried it. Maybe I will see if flash works on it.

---

### Post by haggus on 2009-10-12
Well I don't know what else to do is there some way too get the log messages maybe there is something there otherwise I'm up a creek without a paddle.

---

### Post by 3rdalbum on 2009-10-12
Remove all instances of the 32-bit Flash plugin from your system, including flashplugin-installer (from Synaptic). Also remove nspluginwrapper. You might have put a copy of 32-bit Flash into ~/.mozilla/plugins previously, so if you did you must remove it from there too.

Put the 64-bit Flash Player alpha into /usr/lib/mozilla/plugins. Restart Firefox. Watch Youtube.

---

### Post by haggus on 2009-10-13
> **3rdalbum said:**
> Remove all instances of the 32-bit Flash plugin from your system, including flashplugin-installer (from Synaptic). Also remove nspluginwrapper. You might have put a copy of 32-bit Flash into ~/.mozilla/plugins previously, so if you did you must remove it from there too.

Put the 64-bit Flash Player alpha into /usr/lib/mozilla/plugins. Restart Firefox. Watch Youtube.

Yes I tried that and it still won't load youtube or flash sites in general. I installed opera put the libflashplayer.so in /usr/lib/opera/plugins and it works on most sites youtube works the daily show doesn't I'm confused as to why it works on some but not on others?

---

### Post by P4man on 2009-10-13
Did you do what giblet suggested?
```
sudo apt-get install flashplugin-nonfree
```

If it tells you its already installed, try removing it and install it again.

edit: oops, missed second page of this thread.

---

### Post by oldos2er on 2009-10-13
Have you tried this script: [http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938](http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938)

---

### Post by pricetech on 2009-10-13
Check out this thread:

[http://ubuntuforums.org/showthread.php?p=7954812](http://ubuntuforums.org/showthread.php?p=7954812)

---

### Post by haggus on 2009-10-17
ok so I have chromium kind of working with 64 bit flash but it still crashes all the time. I removed all files from the /usr/lib/mozilla /plugins folder and it has only libflashplayer.so so why is it crashing all the time.

---

### Post by agmcclard on 2009-10-17
Have you tried this

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

---

