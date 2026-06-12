---
title: "&quot;The adobe flash plugin has crashed&quot; on video sites"
date: 2010-06-30
forum: General Help
---

### Post by modularModel on 2010-06-30
Hey guys,
I have been using Ubuntu for quite sometime and did have some problems getting it to work on my 64bit installation. I had it working fine since I fixed some issues I had when I first installed my current system (10.04 64 bit). 

I have updated through the Update Manager today, and after restarting I got into youtube and started seeing the above message in place of the youtube video, it happens in around 95% of videos.
The same issue is in vimeo but I didnt find a single video that worked there.

The update installed Firefox version 3.6.6 which has the new flash crash detection. I had flash crash on me when I first installed 10.04 but I used the Lahf fix here:[http://ubuntuforums.org/showthread.php?t=1263905](http://ubuntuforums.org/showthread.php?t=1263905)
It doesnt seem to crash on any non video sites that use flash like Facebook.

Any ideas or suggestion would be greatly appreciated!

---

### Post by tkrisz on 2010-06-30
Same issue, but i have a 32 bit Ubuntu.

---

### Post by lunalui on 2010-06-30
Hi everyone. I've got the same problem, too.
when I opened firefox after updating this morning, I had this message appear on a "horizontal tab" on top of the page. I clicked on the "learn more link" which led me to this site [http://support.mozilla.com/1/firefox/3.6.6/Linux/en-US/plugin-crashed](http://support.mozilla.com/1/firefox/3.6.6/Linux/en-US/plugin-crashed) and from there to [http://www.mozilla.com/en-US/plugincheck/](http://www.mozilla.com/en-US/plugincheck/)
which seems to suggest that my [Shockwave Flash]("http://www.adobe.com/go/getflashplayer") needs to be updated, so I tried that, but nothing changed (not even the status of the shockwave Flash, which remains outdated!)
any help will be greatly appreciated!

---

### Post by tkrisz on 2010-06-30
I did the same, installed version 10, but about:Plugins still say i have version 9. I suppose somehow i have to completely remove version 9 first. The ways i tried did not work. I will look at it tomorrow, i don't have more time today for an intensive googling.

---

### Post by jmszr on 2010-06-30
modularModel, et al,

After updating to Firefox 3.6.6 I ran the Firefox addon FLASH-AID: [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) . It "Removes conflicting flash plugins from Ubuntu Linux systems and installs the appropriate version according to system architecture." 

It did exactly that and YouTube is running well. Highly recommend that you try it.

---

### Post by tkrisz on 2010-06-30
Thx, jmszr it works!!!

---

### Post by lunalui on 2010-06-30
thanks for the suggestion, jmszr I'll keep that in mind for the next time, since I'd already managed to fix the problem...
for some reason the Gdebi had not installed the flashplugin properly: after I installed it by hand and moved  libflashplayer.so to the .mozilla/plugins directory, everything was back to normal.

---

### Post by dgermann on 2010-06-30
Thanks to jmszr it was easy to fix. I seem to recall that this gets put in the wrong place.

My system is 8.04.

What I did was to rename /home/doug/.mozilla/plugins/libflashplayer.so to a backup name, then copied /usr/lib/adobe-flashplugin/libflashplayer.so over the top of /home/doug/.mozilla/plugins/libflashplayer.so

All is working correctly now, with just this small fix. No need to go to an outside website for a fix.

Thanks, jmszr! :guitar:

---

### Post by Buntu Bunny on 2010-06-30
jmszr Thank you!  Thank you! Thank you!

I was having the same issue and spent all afternoon searching for help. Neither adobe nor firefox websites had any answers.  I knew if I came here I'd find help.  What a relief.

---

### Post by karash on 2010-06-30
Awesome!

This works for 32 bit installations as well. It broke half-way through my install, but I ran sudo apt-get clean, apt-get update, and the broken package was in Synaptic and it was the correct one.

All is well now!

Thanks jmszr!

---

### Post by Royle Lindsey on 2010-07-01
Hi..Flash Player 9 Update is available now..It works perfectly..Try this..

---

### Post by scohar70 on 2010-07-05
Thx, jmszr it works!! Great plugin!

---

### Post by philinux on 2010-07-05
If anyone gets the problem of the flash menu button not working correctly or full screen poor frame rate then this is the fix.

[http://ubuntuforums.org/showpost.php?p=9468193&postcount=4](http://ubuntuforums.org/showpost.php?p=9468193&postcount=4)

---

### Post by ftp1234 on 2010-07-12
Thanks a lot for the solution

---

### Post by nutsy.ben on 2010-07-13
GREAT SOLUTION !!! 

Since the time I struggle with flash for each update of Firefox or Ubuntu IT IS SUPER WELCOME!!!

---

### Post by JimGvo on 2010-09-23
> **jmszr said:**
> modularModel, et al,

After updating to Firefox 3.6.6 I ran the Firefox addon FLASH-AID: [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/) . It "Removes conflicting flash plugins from Ubuntu Linux systems and installs the appropriate version according to system architecture." 

It did exactly that and YouTube is running well. Highly recommend that you try it.

Didn't work for me, running 32 bit Ubuntu 10.04 and Firefox 3.6.10.  

Jim.

---

### Post by chuck-dtol on 2011-04-02
Wow - After so much torture and tinkering, I found this thread.  After months of trying this and that, and having little success, tried Flash-Aid and it worked.  I only had to manually disable Shockwave Flash 10.0.r42 after I ran Flash-Aid and the new version worked great.

Running Mint Isadora (Ubuntu Lynx) with Firefox 4 (Still had same Adobe Plash Plugin crash as on FF 3.6) on x64 architecture.  Tried everything.

---

### Post by ricardisimo on 2012-09-16
> **philinux said:**
> If anyone gets the problem of the flash menu button not working correctly or full screen poor frame rate then this is the fix.

[http://ubuntuforums.org/showpost.php?p=9468193&postcount=4](http://ubuntuforums.org/showpost.php?p=9468193&postcount=4)

I'm still having problems, and so far as I can tell there no longer is any such config file as npviewer anywhere on 12.04, as the link you posted says.

Now, I supposed that I can install nspluginwrapper, but my guess is that it isn't installed because it is no longer integral. Reading the [description of nspluginwrapper]("http://en.wikipedia.org/wiki/Nspluginwrapper") leads me to believe that this is an odd workaround at best.

---

