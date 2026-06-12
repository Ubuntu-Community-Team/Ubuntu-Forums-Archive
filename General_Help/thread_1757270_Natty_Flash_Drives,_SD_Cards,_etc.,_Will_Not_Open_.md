---
title: "Natty: Flash Drives, SD Cards, etc., Will Not Open Automatically"
date: 2011-05-13
forum: General Help
---

### Post by coljohnhannibalsmith on 2011-05-13
Hello,

**Flash Drives, SD Cards, etc., Will Not Open Automatically:**

For the last several distros, when inserting any type of flash media, including mp3 players, the first time I insert this type of media, I am presented with a window which offers me to perform any number of actions automatically for this type of media, including ***opening*** the media.  However, historically, I have always chosen the do-nothing option; because, I am usually performing another task and just want to get the window ***out of the way.***  Unfortunately, I have discovered to my discomfit; that I am never offered this option again.  In fact, I am forever more presented with the same window, grayed-out, displaying the following message:

***No applications found. ***(See attachment)

When I attempt to resolve this situation manually by right-clicking on the media icon and selecting properties, there is no ***'Open With'*** tab to allow me to select an application to open the media device with; such as nautilus. (See attachment)

I can always double-click on the media icon to open the device; ***but this is annoying.***  There should be a way to fix this behavior.  *Also, this appears to be a [COLOR=Red]'BUG'[/COLOR] that needs to be fixed.*

***I suspect I can work-around this issue by editing the mime-types; but I'm uncertain about which file, and which entry(s) to edit.***


What are my options:confused:




Thanks Hannibal

---

### Post by pqwoerituytrueiwoq on 2011-05-13
places -> home
edit -> preferences
media tab
change settings to your liking

---

### Post by coljohnhannibalsmith on 2011-05-13
> **pqwoerituytrueiwoq said:**
> places -> home
edit -> preferences
media tab
change settings to your liking

It's all ***'greyed-out.'***

I don't think this is good... (See attachment).

---

### Post by salterlee on 2011-05-16
Confirm this is a really bad bug!! I've been trying to ask for help, but have not had a single response. My DVD drives won't get read and no USB storage devices are recognised, and even when I force them I can't use them properly. Strange cos my notebook version works fine!

---

### Post by coljohnhannibalsmith on 2011-05-16
I suspect this is more of a [COLOR=Blue]***Linux***[/COLOR] kernel issue than an [COLOR=Red]***Ubuntu***[/COLOR] distro issue; either that, or it has to do with specific pacakages that come from a variety of sources. Either way it needs to be fixed; and in the meantime I need a workaround...  

BTW, I wonder who maintains the actual Linux kernel.  There must be some specific group that does this... [COLOR=Red]***It also seems to me that Ubuntu distros go through cycles of having ACPI problems. ***[/COLOR] I suspect this is 'also' a [COLOR=Blue]***Linux***[/COLOR] kernel issue; and has to do with small bits of legacy code finding their way back into the main kernel, ***after*** the issue was resolved in the previous kernel. ** This is a versioning control problem.**

[COLOR=Blue]***It's my understanding that the most powerful versioning control system available is GIT; and I'll bet the Linux kernel development team isn't even using it...***[/COLOR] [COLOR=Blue][B][I]Or, they're using it and [COLOR=Black]'still[/COLOR]' having problems!!!
[/I] [/B][/COLOR]

**[COLOR=Black]Comments???[/COLOR]**

[IMG]http://lh6.ggpht.com/_Mz0tuQtsZl4/SrLdQCCrgsI/AAAAAAAAAhY/imVa_s-XZFQ/StillFrustrated%255B7%255D.png[/IMG]




[COLOR=Blue]***Hannibal***[/COLOR]

---

### Post by salterlee on 2011-05-18
Just in case anyone has the same problem (and like me you get bugger all  help here! Sorry, but grrr), it came down to an error in the Partition  Tables (which tell Ubuntu which drives are which), presumably caused  simply by upgrading to Natty 11) which in turn seems to have prevented  Ubuntu reading any drives properly (esp USB storage and DVDs). In the  end I had to do a fresh install (and have lost 250gigs somewhere!!!) -  there was no alternative - it's all a bit too much of a reminder of  Windows really, but I'll try to stick with it for a bit.

---

### Post by coljohnhannibalsmith on 2011-05-19
> **salterlee said:**
> Confirm this is a really bad bug!! I've been trying to ask for help, but have not had a single response. My DVD drives won't get read and no USB storage devices are recognised, and even when I force them I can't use them properly. Strange cos my notebook version works fine!

I haven't figured this out yet.  But if your thread doesn't get a response, then wait 24 hours and add a reply with just the word ***BUMP***.  This will send the thread to the top of the list where someone else will get a chance to see it...  You can do this repeatedly until you get a response; however the forum rules are that you have to wait 24 hours between bumps.

And BTW, I'll give that partition-table idea a little bit of thought...





**Thanks Hannibal**

---

### Post by coljohnhannibalsmith on 2011-05-22
bump

---

### Post by linuxinstalledfromhdd on 2011-05-22
I just checked on 10.10, and it works great here.

---

