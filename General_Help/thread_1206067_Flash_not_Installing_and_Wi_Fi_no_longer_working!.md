---
title: "Flash not Installing and Wi Fi no longer working!?"
date: 2009-07-06
forum: General Help
---

### Post by KeithCostin on 2009-07-06
Hi all,

I've fiddled with Ubuntu before, but I'm not super-knowledgeable about Linux, so please bear with me.

I installed Ubuntu Netbook Remix on a partition of my Acer Aspire One today and, at first, everything worked great. However, I've encountered two big problems that I don't know how to solve.

Firstly, I've tried installing Adobe Flash 10 in a few different different ways (installing .deb file off adobe's website and then using the command line's apt-get function), but things still aren't working right. For example, whenever I go to Tweetdeck.com it still tells me that Flash needs to be upgraded. And even worse, when I try to use youtube, none of the buttons are clickable and the video does not play past the first second (although, strangely enough, when I scroll up and down it seems to refresh the video one frame forward at a time.) Has anybody else had this problem? Is there a way that I can uninstall Flash and give it a do-over?

Also, after pulling a few restarts trying to get Flash to work properly, it seems like my Wi Fi card stopped working completely! I've tried flipping the wifi switch on the front of the computer over and over but I get no response from either the system or even the LED indicator light. To add insult to injury, it's not working on my Windows XP partition either! Anybody know how I can fix this issue? I'd really appreciate any input. Thanks!

---

### Post by Tclarkie on 2009-08-04
*try reinstalling [http://ubuntuforums.org/showthread.php?t=1230177](http://ubuntuforums.org/showthread.php?t=1230177) 			*

---

### Post by nothingspecial on 2009-08-04
Did you do your updates? It seems a recent kernel update has broken atheros wifi.

The easiest solution to this is to boot into the previous kernel. Reboot your netbook and hold down the escape button.

When the grub boot menu appears you will be presented with a few options.

Choose Ubuntu 9.04, kernel 2.6.28-13-generic

instead of Ubuntu 9.04, kernel 2.6.28-14-generic

This is not perfect or even a solution really but it should work (i hope)

---

