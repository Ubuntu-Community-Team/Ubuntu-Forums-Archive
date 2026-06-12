---
title: "Ubuntulite 8.04, Youtube videos choppy"
date: 2010-07-18
forum: General Help
---

### Post by Mortesins93 on 2010-07-18
Hello,
I have an old computer with Ubuntulite 8.04 installed on it, it works perfectly and brought this old piece of junk back to life. Anyways i managed to install Firefox and the adobe plugins but the videos on Youtube are choppy. Is it a problem of what I installed (btw i tried different plugins but nothing changed) or is it a problem of my computer (CPU or RAM not powerful enough)? 
Thank you in advance

---

### Post by RJARRRPCGP on 2010-07-18
> **Mortesins93 said:**
> 
 Anyways i managed to install Firefox and the adobe plugins but the videos on Youtube are choppy. 

You probably don't have the proper video drivers installed.

---

### Post by lovinglinux on 2010-07-19
Also see these:

[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)
[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)

---

### Post by Mortesins93 on 2010-07-23
Ok thanks, I will try looking at those tutorials when i find some time. 
A question for [RJARRRPCGP]("http://ubuntuforums.org/member.php?u=28754"): if i don't have the right drivers installed would i even see my videos choppy using gxine because if i try watching for example a  movie using gxine i don't have any problems?

---

### Post by lovinglinux on 2010-07-23
> **Mortesins93 said:**
> Ok thanks, I will try looking at those tutorials when i find some time. 
A question for [RJARRRPCGP]("http://ubuntuforums.org/member.php?u=28754"): if i don't have the right drivers installed would i even see my videos choppy using gxine because if i try watching for example a  movie using gxine i don't have any problems?

No. If gxine works well as a standalone player, then you would be able to see the embedded videos fine. Flash is problematic in regard to CPU usage, which can cause choppiness. 

You could use my [FlashVideoReplacer]("https://addons.mozilla.org/en-US/firefox/addon/161869") for YouTube, since it allows to replace flash with gxine and other plugins.

---

### Post by Mortesins93 on 2010-07-25
Ok I want to try and install your flashvideoreplacer. How do I do it? I managed to install it from your link but i can't find the gxine plugin for firefox, i tried installing it from Synaptic but it doesn't work. Where can i find the gxine plugin?

---

### Post by lovinglinux on 2010-07-25
> **Mortesins93 said:**
> Ok I want to try and install your flashvideoreplacer. How do I do it? I managed to install it from your link but i can't find the gxine plugin for firefox, i tried installing it from Synaptic but it doesn't work. Where can i find the gxine plugin?

Which version you got? I released version 1.0.3 yesterday, to fix an issue with YouTube, since they changed their video code.

Install [gecko-mediaplayer](apt:gecko-mediaplayer), is better in my opinion. Once you install it, just visit an YouTube video and it will load automatically. You can control which sites to load from the extension icon on the status bar or the toolbar.

---

### Post by Mortesins93 on 2010-07-27
I installed the new version of flash replacer and gecko mediaplayer but it doesn't work, I mean the two plugins work and it starts downloading but when i press play it says reading and I still get a blank screen. After reaching 5% it automatically says "Paused" even if the screen has been blank the whole time and continues to download. When it reaches 100% it says "Reading" but I still can't see a thing. What should I do? And what preferences should I put on the window that pops up when i press the extension icon on the right of the status bar?

---

### Post by lovinglinux on 2010-07-27
> **Mortesins93 said:**
> I installed the new version of flash replacer and gecko mediaplayer but it doesn't work, I mean the two plugins work and it starts downloading but when i press play it says reading and I still get a blank screen. After reaching 5% it automatically says "Paused" even if the screen has been blank the whole time and continues to download. When it reaches 100% it says "Reading" but I still can't see a thing. What should I do? And what preferences should I put on the window that pops up when i press the extension icon on the right of the status bar?

The Mime/Plugin Type preference doesn't matter for Linux, because the player is the same. In the other preferences, untick the site you don't want to see replaced.

Perhaps you have a codec issue. See [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by Mortesins93 on 2010-07-28
Ok thanks, I'll check that out when i have some time, I am not in a hurry because i don't use that computer to watch videos so much.
Thank you so much for your help.

---

