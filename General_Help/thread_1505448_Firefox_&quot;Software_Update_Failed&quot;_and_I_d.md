---
title: "Firefox: &quot;Software Update Failed&quot; and I don't know why!!"
date: 2010-06-09
forum: General Help
---

### Post by t0p on 2010-06-09
I'm running Firefox 3.6 on my Hardy machine.  I still have the 3.0 version installed because, as I remember, community docs recommended keeping it (can't remember why though).  I've got an icon/launcher to launch Firefox 3.6, and have successfully used it as my default browser for some time now.

Anyway: since a recent software update, I get the following message every time I launch Firefox 3.6:

> 
Software Update Failed

The update could not be installed.  Please make sure there are no other copies of Firefox running on your computer, and then restart Firefox to try again.
I click OK, and lo-and-behold, 3.6 then launches without any more problems.

What could be cauing this strange behaviour?  And how can I stop it?  (Note: please don't suggest upgrading to Lucid.  I will get round to doing so in my own sweet time.  In the meantime:  Hardy is *supposed* to work, as is Firefox 3.6.  So why oh why is this happening?

**EDIT:** I downloaded the ubuntu-10.04-desktop-i386.iso using the **wget -c** command, as my internet connection is very unreliable and drops and stuff.  Could that be the problem?  Doesn't the Lucid .iso play nice with wget -c?  (I don't know why that would be a problem though, I've used wget -c to get hold of Ubuntu .iso images many times in the past...).

---

### Post by lovinglinux on 2010-06-09
How did you install Firefox 3.6? There are several methods of installing Firefox, so would be nice to know which one you used.

I suspect you have downloaded Firefox 3.6 from Mozilla and installed it manually into the /opt directory. You probably have the option to check for Firefox updates in the Advanced Firefox preferences enabled. What is happening is that Firefox 3.6 is trying to download updates from Mozilla, but doesn't have permission to save the updates in the /opt folder. To "fix" this you can disable the automatic update in Firefox 3.6 or start it with gksudo, get the updates and then restart as normal user (NEVER USE SUDO). 

Keep in mind Firefox 3.6 will be coming to Hardy soon. See [this thread](http://ubuntuforums.org/showthread.php?t=1500861) for more info.

---

