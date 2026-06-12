---
title: "Problems with Youtube videos"
date: 2010-03-18
forum: General Help
---

### Post by SlashHeist on 2010-03-18
Im running Ubuntu 9.10 64bit on my Asus laptop, and when ever I watch a Youtube video, be it on the site or embedded on a different site I can click pause. The video just automatically starts and goes. A few other types of embedded videos do the same. 

Any ideas?

---

### Post by Megafag on 2010-03-18
> **SlashHeist said:**
> Im running Ubuntu 9.10 64bit on my Asus laptop, and when ever I watch a Youtube video, be it on the site or embedded on a different site I can click pause. The video just automatically starts and goes. A few other types of embedded videos do the same. 

Any ideas?

[This guide]("http://ubuntuforums.org/showthread.php?t=766683") gave me some pretty good results when my streaming was messed up.

---

### Post by SlashHeist on 2010-03-19
> **Megafag said:**
> [This guide]("http://ubuntuforums.org/showthread.php?t=766683") gave me some pretty good results when my streaming was messed up.

Hmm nothing changed it. I can watch all types of videos and they all play and work fine. Its just with youtube videos I cant pause them. The play/pause bottom and the native youtube video screen is there but when I click it to pause nothing happens. I can't change volume or video quality either. Its like all the button functions have been disabled or something.

---

### Post by darb_dabney on 2010-03-19
I've just had the experience in the past 48 hours-
On x86_64 9.10
browser: Chrome
what had been a perfectly fine viewing experience for many months will now not start downloading stream data from YouTube.

Flash is fine - Vimeo is happy, only YouTube shows this problem
YouTube site works ok on my Windows test environment, w/Chrome,
so it's not like it's a Comcast issue.

I'm perplexed - and it sounds a bit like this thread.

---

### Post by SlashHeist on 2010-03-19
> **darb_dabney said:**
> I've just had the experience in the past 48 hours-
On x86_64 9.10
browser: Chrome
what had been a perfectly fine viewing experience for many months will now not start downloading stream data from YouTube.

Flash is fine - Vimeo is happy, only YouTube shows this problem
YouTube site works ok on my Windows test environment, w/Chrome,
so it's not like it's a Comcast issue.

I'm perplexed - and it sounds a bit like this thread.

That is my problem exactly. Chrome won't work, although Im not sure if Firefox works with either... so I don't know what the deal is.

---

### Post by SlashHeist on 2010-03-20
Anyone have any ideas? I've tried uninstalling firefox and chrome and reinstalling updating, making sure I have flash plug ins and what not and nothing works. 

The video plays, but I can't use any of the video player controls. It seems to be only Youtube.

---

### Post by GSF1200S on 2010-03-21
I dont know how to fix the issue for chrome. The following is for firefox, but I know it must be possible for chrome as well.

I had issues with really crappy flash video performance upon installing Xubuntu as well. Ubuntu has not incorporated the alpha flash plugin that is available for Linux 64bit users, and instead incorporates nspluginwrapper. I can say from experience that the Adobe alpha plugin has been VERY stable for me, not resulting in even one crash on flash pages.

First uninstall any existing flash:
```
sudo apt-get remove nspluginwrapper
```
```
sudo apt-get remove flashplugin-installer
```
(I tried using the flashplugin-installer package to retrieve the latest flash, but it didnt work for me- I suppose you can try it if you want :) )

Then, go to the adobe page and download the flash plugin for 64bit browsers:

[http://labs.adobe.com/downloads/flashplayer10_64bit.html]("http://labs.adobe.com/downloads/flashplayer10_64bit.html")

Once the tarball is downloaded, extract the libflashplayer.so file with your archive manager. Go to the following location:
```
/home/user/.mozilla
```
and create a folder called:
```
plugins
```
inside the .mozilla folder.

Place the libflashplayer.so file in that folder, and restart firefox if you havent already. To double check you can go to youtube to see if it works, or type in the address bar:
```
about:plugins
```

You should see the flash listed on that page. In my experience, this flash option is far more stable and consumes far less resources. Hope it helps :)

---

