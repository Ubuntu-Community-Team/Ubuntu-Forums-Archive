---
title: "Update Manager STILL not telling me to update"
date: 2010-05-13
forum: General Help
---

### Post by Jerriy on 2010-05-13
There is something wrong with my Ubuntu Jaunty OS. The update manager has still not told me that there is a new Long term (LTS) ubuntu out there - I had my update manager configured so that it gives me that "update to the latest OS" button *only when a long term* release OS comes out, which is now the case (Lucid Lynx)

---

### Post by wojox on 2010-05-13
Doesn't really matter being you would have to upgrade to 9.10 first. How did you configure it so it only tells you when a LTS is out?

---

### Post by howefield on 2010-05-13
You wouldn't be able to directly upgrade to 10.04 from 9.04, you would need to upgrade to 9.10 first, then 10.04.

You can upgrade directly from LTS version to LTS version, eg, 8.04 to 10.04, otherwise you need to upgrade sequentially.

Or clean install.

---

### Post by ryan858 on 2010-05-13
> **wojox said:**
> How did you configure it so it only tells you when a LTS is out?

Software Sources > Updates tab > Release Upgrade > Long term support releases only

Though I'm pretty sure "Normal releases" option should also show LTS's.

---

### Post by Jerriy on 2010-05-13
> How did you configure it so it only tells you when a LTS is out?There is my setting (the LTS notifier is at the bottom of the update manager dialogue box)

---

### Post by wojox on 2010-05-13
That's right I forgot all about that option. Anyhow Jerriy why don't you do a fresh install so you can use Grub2 and ext4.

---

### Post by Jerriy on 2010-05-13
> You wouldn't be able to directly upgrade to 10.04 from 9.04, you would need to upgrade to 9.10 first, then 10.04.I didn't get a "upgrade to Koala" message either

---

### Post by Jerriy on 2010-05-13
> **wojox said:**
> That's right I forgot all about that option. Anyhow Jerriy why don't you do a fresh install so you can use Grub2 and ext4.What is Grub?

---

### Post by howefield on 2010-05-13
> **Jerriy said:**
> I didn't get a "upgrade to Koala" message either

Koala isn't an LTS.

You have set it to show only LTS versions.

I'd say you aren't getting the LTS version because a direct upgrade to 10.04 is not supported. Chicken and Egg :)

---

### Post by Jerriy on 2010-05-13
> **howefield said:**
> You wouldn't be able to directly upgrade to 10.04 from 9.04, you would need to upgrade to 9.10 first, then 10.04.

You can upgrade directly from LTS version to LTS version, eg, 8.04 to 10.04, otherwise you need to upgrade sequentially.

Or clean install.That last option is what I'm trying to avoid (since that requires me to go back to square one and re-install all the programs that I have on my ubuntu side.

---

### Post by bmuluu on 2010-05-13
> **Jerriy said:**
> I didn't get a "upgrade to Koala" message either

Koala was not an LTS version so your manager did not show it as you restricted it to 
LTS only. You have to upgrade to Koala first before you can get to Lucid unless you do a clean install.

---

### Post by Jerriy on 2010-05-13
> **howefield said:**
> Koala isn't an LTS.

You have set it to show only LTS versions.That's what I'm finding out so I'm about to change the settings and install the Koala - then when the "Lynx is available" button shows up, go to that next level upgrade immediately (**without bothering to see** if everything is OK inside the temporarily installed Koala to save time) - that's not a bad idea, is it?

---

### Post by howefield on 2010-05-13
> **Jerriy said:**
> that's not a bad idea, is it?

No it isn't a bad idea, it is your only (safe) option given you prefer not to clean install.

Not the one I'd choose, (and that matters not a jot :) ) but should work fine.

---

### Post by Jerriy on 2010-05-13
OK here we go...

But one more thing first: Do I get a single unified Firefox back? (If you guys remember during Jaunty some stuff happened with that version whereby a midway jaunty update created a split between the original (older) Firefox and the niewer version that came out and that was dubbed by Ubuntu as not Firefox but "Shiretokio")

---

### Post by wojox on 2010-05-13
Yes

```

||/ Name                   Version                Description
+++-======================-======================-============================================================
ii  firefox                3.6.3+nobinonly-0ubunt safe and easy web browser from Mozilla



```

---

### Post by wilee-nilee on 2010-05-13
> **Jerriy said:**
> That's what I'm finding out so I'm about to change the settings and install the Koala - then when the "Lynx is available" button shows up, go to that next level upgrade immediately (**without bothering to see** if everything is OK inside the temporarily installed Koala to save time) - that's not a bad idea, is it?

It is not a bad idea, but if anything gets borked in the process then you will be doing a fresh install if you can't fix it. Personally I would backup what you can't lose then do a fresh install, but back up no matter what.

You might use this as a method for learning and implanting in your memory your installs so that you can no matter what get your system back in case of some sort of failure, not even associated with the upgrade.

You will not get the advantage of a ext4 partition if you just upgrade. Although people do upgrade their partitions, but I haven't seen any instructions on this for at least a year on the forums, and it is not a job for a even medium level user.

Here is a link on how to backup whats installed to a list that can be run with a fresh install.
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

Now this list generated is going to need the repositories that contain them if they are even available. Some of your tweaking probably has involved 3rd party repos. So save the apt sources list by running in the terminal.
```
sudo gedit /etc/apt/sources.list
``` 

Then save the apt source list in gedit or even a document in open office. Be careful that when you have the apt source list open not to delete anything just copy and paste it onto another document to add to the new list, with the distro name changed. Now the only thing your missing is any keys that were part of a 3rd party repo being added.

So this apt list will have some of the same repos that are part of the standard install and some 3rd party so you will find the 3rd party repos usually at the bottom of the list.

This is probably the best method and what I would do if I didn't already know how to set my computer up after a fresh install, good luck. ;)

---

### Post by Jerriy on 2010-05-13
Wierd

I just upgraded it to Koala, everything went auto except that I had to input whether some formerly Canonical supported stuff has now been declared obsolete (so I chose the "replace or clean them" option

But once Koala installed I immediately noticed that the color of everything (including interface/window color scheme as well as one or two videos I opened in order to check sight and sound) is different: what was once red is now dark-brownish-grey-ish and people are blue-ish...etc (this is when playing one or two vid copies that are on my desktop, as opposed to youtube/online vids that seem to remain normal-colored)

What happened?? Where does this "Ubuntu Navi" bug I never seen nor heard of came from? 
 
Scared... but still intending to go to the next level (I see that "new ubuntu release available" button) hopefully by then everything won't deteriorate further and turn into black-and-white or something!

---

