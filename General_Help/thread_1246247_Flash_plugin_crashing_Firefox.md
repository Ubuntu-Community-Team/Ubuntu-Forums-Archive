---
title: "Flash plugin crashing Firefox"
date: 2009-08-21
forum: General Help
---

### Post by TomX19 on 2009-08-21
Have had a slight problem with the flash plugin in Jaunty 64-bit lately.  Say for example I use iPlayer to stream something and then surf in another window or tab.  Occasionally when a web page loads something which contains flash (adverts or content), it will cause the existing iPlayer window's flash plugin to crash, as in the portion of the display that would have been displaying the flash goes grey and has to be reloaded.

I've re-installed flash non-free but that hasn't helped.

Has anyone else had this issue?  It's only started happening in the last couple of weeks so there must have been something in one of the updates which caused it.

Cheers

Tom

---

### Post by aldimond on 2009-08-21
I have a similar problem occasionally... what can one say, Flash is kind of sucky?

---

### Post by bobince on 2009-08-21
Yeah, I concur with the Kind Of Sucky hypothesis. Used to crash for me a fair bit on Windows too.

Flashblock is great. You can limit Flash just to sites you trust to use it without crashing the machine, pegging the CPU with animations, making annoying noises and sneaking Flash-cookies in.

---

### Post by TomX19 on 2009-08-23
Gonna do a cheeky bump of this.  This forum is so busy that your posts soon sink a few pages.

---

### Post by scouser73 on 2009-08-23
You could try **Right Click** on the video, select **Settings** and uncheck the box named **Enable Hardware Acceleration**.

---

### Post by mbuehl on 2009-08-23
I was having infinite issues with my flash plugin, if it did work it didn't work well... then! I did the following.

sudo apt-get remove swfdec-mozilla
sudo apt-get remove mozilla-plugin-gnash
sudo apt-get remove adobe-flashplugin
sudo apt-get remove flashplugin-nonfree
sudo apt-get install flashplugin-nonefree

Essentially removes all flash from your system, then reinstalls v10. Worked for me, give it a go?

---

### Post by TomX19 on 2009-08-25
> You could try Right Click on the video, select Settings and uncheck the box named Enable Hardware Acceleration. 

Didn't work for me, but thanks for the reply.


> removes all flash from your system, then reinstalls v10. Worked for me, give it a go? 

This seems to be working so far...  I guess time will tell.  Thanks very much. :)

---

