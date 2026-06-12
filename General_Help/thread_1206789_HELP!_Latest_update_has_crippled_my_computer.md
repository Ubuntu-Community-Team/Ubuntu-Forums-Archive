---
title: "HELP! Latest update has crippled my computer"
date: 2009-07-07
forum: General Help
---

### Post by shelbyvision on 2009-07-07
I installed the latest updates this morning (there were 12 or 14 of them, I think). I used the computer for a while after that, and it said that I needed to restart it for the updates to take effect. I had to leave for a while, so I turned it off, and then turned it back on when I came back an hour or two later. It shows the same login as usual, and everything looks OK, until it goes to what's supposed to be the Ubuntu desktop, and then it looks completely different (see attachment), and it's unbelievably slow. just changing workspaces take 20-30 seconds. It also changed my mouse settings. How can I fix this?
I have an HP omnibook 4400 laptop, 2GH P4, 512 MB RAM, with Ubuntu Hardy 8.04.

---

### Post by shelbyvision on 2009-07-07
No suggestions? I sure would like to have my Ubuntu back.

---

### Post by Sef on 2009-07-07
Upon start up, go into GRUB and use an older kernel to check if the problem is still there.

---

### Post by shelbyvision on 2009-07-07
Thanks for the suggestion...I already tried that and unfortunately it made no difference.

---

### Post by LoneWolfJack on 2009-07-07
quite possible you have to reinstall the restricted drivers for your graphics card. check if they are still enabled.

---

### Post by shelbyvision on 2009-07-07
> **LoneWolfJack said:**
> quite possible you have to reinstall the restricted drivers for your graphics card. check if they are still enabled.

How do I do that?

---

### Post by shelbyvision on 2009-07-07
I just went to synaptic and found the updates that were installed this morning in the history. I was able to copy it and here it is, FWIW:

Upgraded the following packages:
base-files (4.0.1ubuntu5.8.04.4) to 4.0.1ubuntu5.8.04.7
libnm-glib0 (0.6.6-0ubuntu5.8.04.1) to 0.6.6-0ubuntu5.8.04.2
libnm-util0 (0.6.6-0ubuntu5.8.04.1) to 0.6.6-0ubuntu5.8.04.2
libpurple0 (1:2.4.1-1ubuntu2.4) to 1:2.4.1-1ubuntu2.5
libtiff4 (3.8.2-7ubuntu3.1) to 3.8.2-7ubuntu3.2
libvlc0 (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.3
linux-headers-2.6.24-24 (2.6.24-24.53) to 2.6.24-24.55
linux-headers-2.6.24-24-generic (2.6.24-24.53) to 2.6.24-24.55
linux-image-2.6.24-24-generic (2.6.24-24.53) to 2.6.24-24.55
linux-libc-dev (2.6.24-24.53) to 2.6.24-24.55
linux-restricted-modules-2.6.24-24-generic (2.6.24.17-24.1) to 2.6.24.18-24.1
linux-restricted-modules-common (2.6.24.17-24.1) to 2.6.24.18-24.1
network-manager (0.6.6-0ubuntu5.8.04.1) to 0.6.6-0ubuntu5.8.04.2
pidgin (1:2.4.1-1ubuntu2.4) to 1:2.4.1-1ubuntu2.5
pidgin-data (1:2.4.1-1ubuntu2.4) to 1:2.4.1-1ubuntu2.5
vlc (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.3
vlc-nox (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.3
vlc-plugin-pulse (0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.2) to 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.3

---

### Post by shelbyvision on 2009-07-08
I still need help. I'm clueless.
Maybe I should explain better what the symptoms are. The whole look is different; it doesn't look like Ubuntu any more. Most of the icons are different, the color scheme is different, and the windows do not have navigation buttons at the top and most have only partial captions. My touchpad has been set to the tap mode, which is so sensitive that it constantly selects things by accident. When I go to the mouse setup, there is no mention of tap, so I can't change it. When I try to change the appearance, nothing gets changed. The most annoying things is how slow some things are. If I click a menu item, nothing happens at all for several seconds, and changing workspaces is excruciatingly slow.

---

### Post by shelbyvision on 2009-07-09
I'm not giving up; someone out there has to have an answer.

---

