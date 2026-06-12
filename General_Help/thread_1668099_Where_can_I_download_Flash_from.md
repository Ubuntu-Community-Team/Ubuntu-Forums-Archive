---
title: "Where can I download Flash from?"
date: 2011-01-15
forum: General Help
---

### Post by Maheriano on 2011-01-15
This is embarrassing, for some reason my Flash doesn't work anymore and it's not the easy process I remember it to be. I went on vacation for a month and left my machine on, then did all the updates once I got back. The machine had to restart so I did, now I notice that Flash videos don't play in Chrome, it tells me I'm missing the plugin. When I go to the Adobe website to download it, the 64 bit link gives me options for 32 bit downloads. And when I click the 10.2 beta link, there's no download for it. Very weird.

I tried Firefox but for some reason that won't even open, it keeps crashing. Isn't Chrome supposed to have Flash built in? What's up?

Oh and I'm pretty good with Ubuntu, I just need to know where to download the file and then where to put it on my machine. I've already switched to HTML5 so I can view Youtube fine, just Flash don't work.

---

### Post by oldos2er on 2011-01-15
Click the FlashAid link in my sig.

---

### Post by Maheriano on 2011-01-15
Downloaded that and ran it 2 days ago, did nothing. I mean nothing, I double clicked it and it sounded like it was trying to do something but nothing happened.
I'm all updated, newest install.

---

### Post by darkstaar on 2011-01-15
I did manage to locate a 64-bit version for you [here]("http://www.419baiter.com/errata_data/flashplayer_square_p2_64bit_linux_092710.tar.gz"). Not sure why Adobe isn't offering it on their site at the moment but I asked for (and was granted) permission to link to this file by the site's owner.

Simply dump the libflashplayer.so file within this archive into your /.mozilla/plugins directory. It will also work in Chrome from this location.

This version is a couple of months old but it works perfectly on my system so I recommend that you replace it with the update from Adobe as soon as they make a newer version available.

---

### Post by akand074 on 2011-01-15
I've downloaded it from the adobe website several times without a problem. But recently Ubuntu installs it automatically now if you check the box for it to during the installation. Pretty great.

---

### Post by efflandt on 2011-01-16
This is where you can find the most recent 64-bit version from adobe [http://labs.adobe.com/technologies/flashplayer10/square/](http://labs.adobe.com/technologies/flashplayer10/square/)

After extracting it, I typically put it in /usr/lib/mozilla/plugins (which you have to do using sudo or gksu).  The only thing that does not find it there automatically is 64-bit Hulu Desktop, so ~/.huludesktop needs to be edited to find it.

As far as I know the flashplugin-installer Ubuntu package still uses 32-bit flash with a wrapper for 64-bit systems.  On my newest system that gives me log errors for crashes I do not even notice, but real 64-bit flash works fine.

---

### Post by oldos2er on 2011-01-16
> **Maheriano said:**
> Downloaded that and ran it 2 days ago, did nothing. I mean nothing, I double clicked it and it sounded like it was trying to do something but nothing happened.

I don't understand. You installed the Flashaid extension in Firefox, then double-clicked on what exactly?

---

### Post by Maheriano on 2011-01-16
> **efflandt said:**
> This is where you can find the most recent 64-bit version from adobe [http://labs.adobe.com/technologies/flashplayer10/square/](http://labs.adobe.com/technologies/flashplayer10/square/)

After extracting it, I typically put it in /usr/lib/mozilla/plugins (which you have to do using sudo or gksu).  The only thing that does not find it there automatically is 64-bit Hulu Desktop, so ~/.huludesktop needs to be edited to find it.

As far as I know the flashplugin-installer Ubuntu package still uses 32-bit flash with a wrapper for 64-bit systems.  On my newest system that gives me log errors for crashes I do not even notice, but real 64-bit flash works fine.

I go to that website and click the link on the right side which reads 'Download the latest release versions of Flash Player.' I click that and it brings me to another page where I go to the bottom and change the dropdown box to '.deb for Ubuntu 8.04+' and it gives me a link to click. I click the link, download the file and when I run it it tells me, 'Wrong architecture 'i386'.'

---

### Post by oldos2er on 2011-01-17
Here's a direct link: [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz)

---

### Post by Maheriano on 2011-02-17
After the latest update I have this problem again. I don't even have a mozilla folder until /var/lib so I'm not sure where to put this libflashplayer.so file. How do I watch James Rolfe again?

---

