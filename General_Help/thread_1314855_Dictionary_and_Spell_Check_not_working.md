---
title: "Dictionary and Spell Check not working"
date: 2009-11-04
forum: General Help
---

### Post by tyhee88 on 2009-11-04
My Gnome-dictionary doesn't do anything-except freeze when I type in a word.  In what may or may not be a connected problem, in OO Writer spell checking won't reveal any problems, even if all words in a document are misspelled.

When I try to find a word using the dictionary it freezes and I end up using the kill application utility (which I installed as Force a misbehaving application to quit on the top panel when I started having this problem) to make it quit.

I'm Karmic, installed on Sunday as a fresh install, dual-booting with XP Home.  When first installing it, at the stage where it was installing language files there was something to click on to skip, which, undoubtedly stupidly, I did.  

When the problem came up and I couldn't fix it, I did a fresh install from the same CD, but without reformatting the home partition.

In the preferences menu for the dictionary the source shows as the default dictionary server.  

Any ideas?  I'd be happy to install dictionaries to my hard drive rather than use the online dictionary just in able to get something to work.  I don't personally need the dictionary and don't use a spell checker-but my wife does and she will end up booting into XP to work if I can't get this fixed.  I was hoping never to have this computer boot into XP again.

If there is reason to think it will work, I can reinstall and format the /home partition as well this time.

For the purpose of helping those kind souls who might try to help, while I sometimes like to kid myself into thinking I've advanced all the way to low intermediate, it's probably more accurate to say I'm a perpetual novice when it comes to Linux.


Thanks.



                                                                                  Bob C.

---

### Post by Arup on 2009-11-04
What language have you selected for default use? Usually US or GB English works out fine.

---

### Post by tyhee88 on 2009-11-04
> **Arup said:**
> What language have you selected for default use? Usually US or GB English works out fine.

My default was English (Canada).  Changing to English (United States) didn't help, nor did a change to English (United Kingdom) in System-Admin-Language Support.  After each change I shut down and booted up again.



                                                                                 Bob

---

### Post by Arup on 2009-11-04
As a work around for now you can install Stardict which is in the repos along with choice of dictionaries on their site, works out far better than the built in one. If you wish to use a offline dictionary with the built in one here is how to do it.

[http://blog.chewearn.com/2008/11/13/offline-dictionaries-in-ubuntu/](http://blog.chewearn.com/2008/11/13/offline-dictionaries-in-ubuntu/)

---

### Post by Barriehie on 2009-11-04
I got tired of waiting for the seemingly never online dictionary so I installed one locally.  See this [post](http://ubuntuforums.org/showthread.php?t=982326&highlight=offline+dictionary).  It's very easy to do.

Barrie

---

### Post by tyhee88 on 2009-11-04
Thanks folks.  I added dictd and dict-gcide, changed the default and the dictionary works fine-and faster than I remember it working using the online dictionary in other versions of Ubuntu.

Now it's time to go on to my OO spell check problem, which is obviously different and if I can't work that one out will be the subject of a visit to the OO forums.  :))

---

