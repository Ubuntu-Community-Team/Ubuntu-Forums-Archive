---
title: "Can't select an update"
date: 2011-02-01
forum: General Help
---

### Post by fruityloops on 2011-02-01
Hello, 

I recently installed Ubuntu 10.10 and tried updating the software after the installation. All of the updates seemed to have installed properly, except one - Event based init daemon. It remains in the update window and I am unable to select it to update it. I have tried refreshing the update window and even restarting my computer, but neither worked. I have tried updating it in the synaptic package manager but it gives me an error message stating that it would break libc6 if I chose to update event based init daemon. 

How can I fix this problem?

Edit: I just noticed that there are a few other threads dedicated to this same problem. I'll just keep an eye on the other threads. Please feel free to delete this thread if you want.

---

### Post by t3rrian_tr00pa on 2011-02-01
Hey there,

I'm having the same problem right now.
Can't check event-based init daemon for "update"
I've tried upgrade via terminal and update thru update manager w/o any luck.

Terminal says "1 not upgraded"

Thxz

P.S.
fruityloops, do u mind PMing or posting here to me with da links to other threads, I can't seem to find em.
That'd be great!

---

### Post by residualbit on 2011-02-01
I am having the same issue. I think this update became available about 2 days ago. All other updates install just fine....

---

### Post by michaelcole on 2011-02-01
> **nkirk1 said:**
> I am having the same issue. I think this update became available about 2 days ago. All other updates install just fine....

Me too, on both my computers:

quickstart@qs09:~$ uname -a
Linux qs09 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux

michael@mc-desktop:~$ uname -a
Linux mc-desktop 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

---

### Post by Rowan_ on 2011-02-01
Me too; both my desktop and netbook.
Also; netbook is now experiencing random freezes - related or coincidence?

---

### Post by FZR_Rider on 2011-02-02
I'm having the exact same problems.  When I click to check for updates in the Update Manager it doesn't appear that it is downloading anything.  It says that it is download 0B of 1B.  

I've even typed 'apt-get distr-upgrade' and it still says that the update has been held back.....

---

### Post by usatrooper on 2011-02-02
Having the same prob myself. Update Manager comes up with it in the box as recommended, but won't let me d/l it.

---

### Post by piquat on 2011-02-02
> **fruityloops said:**
> How can I fix this problem?

By waiting.  Give it a day or two.  They'll sort it out.

---

### Post by MorrisseyJ on 2011-02-02
Same problem here and, like Rowan_, i am also experiencing random freezes on an Asus Arp6 Notebook - none for months and now 4 times this morning.

fruityloops: Could you please post the links to those other threads you mentioned.

Edit - crashing/freezing had to do with the kernel upgrade. Current kernel seems to work fine, i was set back to -22 kernel which meant i went back to -23 with this upgrade. That kernel has always given me problems. Don't know why i didn't spot this.

---

### Post by cocoa117 on 2011-02-02
same issue here.

---

### Post by opvolger on 2011-02-02
Same here, With Ubuntu 10.10. I'm not able to select the update, so i can't install it.

[edit]
it is fixed! 13H after the problem and it is already fixed! :)
[/edit]

---

### Post by nighttrap on 2011-02-02
I am not an ubuntu geek, but I installed the update incidentally. I had "Ubuntu Tweak" installed in my netbook. First, I tried to update with the update utility of this program, no chance. The I check the "disable the third party PPA sources", and voila. 

May be, it could work for you too

):P

---

### Post by Rowan_ on 2011-02-02
> **MorrisseyJ said:**
> Same problem here and, like Rowan_, i am also experiencing random freezes on an Asus Arp6 Notebook - none for months and now 4 times this morning.

fruityloops: Could you please post the links to those other threads you mentioned.

Edit - crashing/freezing had to do with the kernel upgrade. Current kernel seems to work fine, i was set back to -22 kernel which meant i went back to -23 with this upgrade. That kernel has always given me problems. Don't know why i didn't spot this.

It seems that my random freezes are related to the wireless.  If i turn it off, no more freezes.  My temp workaround is to plug in an Ethernet cable.  
Still cant update 'event-based init daemon'.

---

### Post by W3N4 on 2011-02-02
As for me, I had the same issue with the particular update but it is fixed now.
As for the random freezes, I experienced them several times too, I hope they are gone (haven't had them for a day at least).

---

### Post by FZR_Rider on 2011-02-02
I just ran the update manager again and the issue seemed to have resolved itself.  I hope it works for everyone else here.

---

### Post by t3rrian_tr00pa on 2011-02-02
Yes, I can also confirm the update is now available and installs without problems.

Cheers!

---

### Post by PenM@X on 2011-02-03
Ubuntu 10.10: keep getting uninstallable 'event-based init daemon' update!

How long can it take to resolve this? Smacks of amateurism somewhere ...

:lolflag:

---

### Post by PenM@X on 2011-02-03
It got sorted! Was it something I said?

:p

---

