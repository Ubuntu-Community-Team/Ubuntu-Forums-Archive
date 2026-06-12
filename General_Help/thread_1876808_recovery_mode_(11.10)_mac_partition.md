---
title: "recovery mode (11.10) mac partition"
date: 2011-11-06
forum: General Help
---

### Post by recezone on 2011-11-06
Hey all,
    I'm new to the forum and Linux in general.  I have learned a lot in the past month or so, running Ubuntu 11.10 on a MacBook pro 3,1.  Anyway,  i was Trying to install a /home partition after the original install and managed to change root user permissions. So I could no longer use "sudo" command in the terminal. I found out how to fix this in recovery mode,  however this is were my problem began (and it should be so simple!!!!).  I log into recovery mode and get the Options:  Resume, fsck, root etc.  To my dismay i can't for the life of me figure out how to scroll down the options.  Of course I first tried the arrows,  then 'j' and 'k' like in the vim editor.  Then I tried just running both hands across the keyboard to see if the cursor would move down or up or anywhere..  I got nothing. Even 'enter' doesn't work so i can't even select the highlighted option selected by default.  is there something I'm missing.  Or is the macbook keyboard not recognized in recovery mode?  this should be really simple..i just want to log into recovery mode and I can't..it's weird!!!!  By the way,  my keyboard works fine in normal mode.  Arrows, keys, esc, enter etc.  So it's an issue only when booting in recovery.

---

### Post by tombean on 2011-12-24
Hi recezone,

The same problem occured to me today, after I screwed up my xorg.conf file I wanted to boot into recovery mode and fix it. But the problem was the same like yours: The keys on my MacbookPro5,5 didn't react. 

I solved the problem by disconnecting any USB-devices I had plugged in and attached an old external USB-keyboard. After that I could choose the options, but also then it really looked weird (picture).

Hope that could help and that I'm not too late!

tombean.

---

