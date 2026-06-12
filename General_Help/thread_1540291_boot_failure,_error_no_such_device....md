---
title: "boot failure, error no such device:..."
date: 2010-07-27
forum: General Help
---

### Post by de Bacon on 2010-07-27
I installed from a live disc months ago.  It worked fine for a while, don't remember what caused the change. 
Now when I boot, I get this message:
> error: no such device: 199f276d-6872-41c5-91eb-144ec4c65c7c
grub rescue>
I have several hdds in this desktop box, one other has a OS on it, has the Hardy version.  But i disconnected that (it all used to work with both drives connected and I was able to use that boot menu to change from one OS to the other).  I can boot by getting to "boot menu" by pushing the "esc" key when the bios starts (just after the beep).  It gives the option to start from, with a list of possible devices to choose from.  I don't know where this menu is from, bios or other. I select hard drive, then select the correct hard drive and it starts right up. That is nonsense though.
I really no longer need version 8.04 but keep it as a backup in case my preferred OS/hdd fails. Ya never know! 
It would be nice to be able to start up normally again.  
Thanks

---

### Post by drs305 on 2010-07-27
Take a look at this solution by *meierfra*:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search")

If the solution doesn't work for you, run his 'boot info script' and post the results here. Place the contents between 'code' tags, which you can generate by pressing the # icon.

[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by de Bacon on 2010-07-27
I believe this may have the solution.  I will take it slowly as my knowledge of these things is limited.  I'll start by disconnecting all but the hdd with the OS on it. 
Thanks.  I'll let it be known what I find out.

---

### Post by de Bacon on 2010-07-27
I don't understand, one of those strange things.
I isolated the system down to the HDD with the OS on it.  Booted and thought to just see what happened without trying the boot menu, and it booted normal.  I shut it down, reconnected another HDD, booted again, all worked fine ... through the remaining HDDs, all works fine now.  It makes no sense to me.  

In the process of finding out from the recommendation of the sourceforge article, I did run the do the first command but didn't edit anything as to the thought of isolating the HDD to only the one with the OS on it.  I did note that the device string "device: 199f276d-6872-41c5-91eb-144ec4c65c7c" as listed above, did not show up on that list.  Though being unsure of which in the list having many HDDs, with partitions on each had the OS on it, it would be better to narrow down the possibilities before any real action, Then I wrote the reply before carrying on.  
But now it works, I am quite sure there is logic to it but I am too ignorant to see it.  
Thanks for what lead me to the cure (???) :)

---

