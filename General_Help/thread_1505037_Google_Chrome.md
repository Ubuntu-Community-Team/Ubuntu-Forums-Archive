---
title: "Google Chrome"
date: 2010-06-08
forum: General Help
---

### Post by yo2lux on 2010-06-08
I would like to install Google Chrome for linux.
Which is the best way?

Applications menu -> Ubuntu Software Center -> **Chromium** ; or
[http://www.google.com/chrome](http://www.google.com/chrome) -> **Chrome**

Is there a difference between the Chrome release (found on Google website) and Chromium (Ubuntu) ?

---

### Post by cbrunhaver on 2010-06-08
Chrome is the stable version of Chromium.  Chromium (for their beta, dev, or daily PPA) is potentially unstable, though I have had no issues with the 6.xx beta builds versus the stable version and the newer version are a hair faster with java script and such.

I believe that the EULA under Chrome is a bit scarier than for Chromium and so that alone may be reason enough to use chromium.

---

### Post by yo2lux on 2010-06-08
The only way to install Chrome is to download the .deb from Google website?

---

### Post by scouser73 on 2010-06-08
Go to [http://www.google.com/chrome](http://www.google.com/chrome) and click on **Download Google Chrome**

Select 32 bit if you're on a 32 bit system, or 64 bit if you're on a 64 bit system.

Then click **Accept And Install**

---

### Post by Dennis N on 2010-06-08
One difference: Chrome includes support for the H.264 video format. I don't believe that Chromium does. 

Also, the Chrome Linux download adds a PPA automatically when you install, so that it will keep updated.

---

### Post by yo2lux on 2010-06-08
OK, I downloaded and installed the .deb file! It works.
One more question. Is there a way to uninstall the browser?

Thanks!

---

### Post by Don1500 on 2010-06-08
I'm running Fadora 13 in a small partition on my Linux drive (Ubuntu is in the large partition.) But I use this to test out programs before moving them into my main system. I just installed Chrome in this setup and it is working very well, feels faster, but I've only had it up for about 5 minutes.

---

### Post by cbrunhaver on 2010-06-08
I forgot to mention that Chrome is closed source while chromium is open source.
 
As far as h.264 support, are you referring to in an HTML5 type container or just some general h.264 libraries?

-Chris

---

### Post by Timmer1240 on 2010-06-08
To uninstall google crome go to synaptic click on installed and scroll down to google chrome and mark for complete removal.I use chrome and luving it faster than a bullet!Karmic + chrome =speedmachine!

---

### Post by _khAttAm_ on 2010-06-08
You should use Chromium as it gets upgrades from the update manager directly.. And no there is no difference after you install chromium-codecs-ffmpeg-extra...

and about stability, I'm using chromium daily build (the most unstable one available via repos) and no it has never crashed or behaved differently... However, daily builds may have problems and are for testing only, I use it as my default browser.

You can settle for chromium-browser without any problems regarding stability.

---

### Post by Helios747 on 2010-06-08
Chromium is just an unbranded Chrome, no?

---

### Post by Queue29 on 2010-06-09
> **Helios747 said:**
> Chromium is just an unbranded Chrome, no?

Not quite, as stated before, chromium receives updates on a daily basis and is not considered stable. 

Chrome on the other hand is stable, in that Google releases updates when they feel it's ready to be updated and won't cause problems. 

Also the icons are different.

---

### Post by _khAttAm_ on 2010-06-09
> **Queue29 said:**
> Not quite, as stated before, chromium receives updates on a daily basis and is not considered stable. 


Not true..

I receive updates daily coz I use the "daily" PPA and am using version 6 of Chromium...

There is a stable channel for Chromium:
[https://launchpad.net/~chromium-daily/+archive/stable](https://launchpad.net/~chromium-daily/+archive/stable)

which is not required in Lucid and Maverick BTW, since the same stable version is already available in standard repo...

---

### Post by yo2lux on 2010-06-09
> **Timmer1240 said:**
> To uninstall google crome go to synaptic click on installed and scroll down to google chrome and mark for complete removal.I use chrome and luving it faster than a bullet!Karmic + chrome =speedmachine!

Thanks, mate!
Is the synaptic "google-chrome" version the same as [http://www.google.com/chrome](http://www.google.com/chrome) ?

---

### Post by _khAttAm_ on 2010-06-10
> **yo2lux said:**
> Thanks, mate!
Is the synaptic "google-chrome" version the same as [http://www.google.com/chrome](http://www.google.com/chrome) ?

Seems like you've added repo for it.. Having done that, you can install either way and the result is the same.. i.e. even if you choose to download and install the deb from website, you will be able to receive updates if they are available in the repos..

---

