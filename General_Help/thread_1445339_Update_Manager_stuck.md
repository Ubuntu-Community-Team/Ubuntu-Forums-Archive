---
title: "Update Manager stuck"
date: 2010-04-02
forum: General Help
---

### Post by EarlySight on 2010-04-02
Hi everyone!

I was wondering something about the repository; is it currently offline for maintenance? I'm asking because I've been unable to update the repository both in Update Manager and Synaptic, making it impossible for me to get the security updates. I haven't booted this laptop for two weeks so I'm pretty sure updates must be available.

What happens is when I click "Check" it gets stuck at the 44th item (out of 45). I'm running Ubuntu 9.10 Karmic Koala and updates always worked fine in the past.

Anyone else having this issue today?
Thanks in advance for any information.

---

### Post by crolanx on 2010-04-02
Hi,

could you try to use ```
sudo aptitude update
``` in a terminal? Then you can see which error occurs. In your case it seems that a packet list could not be downloaded (the 44th item).

Greetings

---

### Post by Naminator_X_ on 2010-04-02
Something is wrong with repositories for me too. I use bulgarian servers and i too stuck at 45th BUT after 2-3 minutes the checking continues. Can't really explain it >.>

---

### Post by EarlySight on 2010-04-02
Actually, this is the message I get within Update Manager:

> Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_US.bz2](http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_US.bz2)  
Failed to fetch [http://dl.google.com/linux/deb/dists/stable/Release](http://dl.google.com/linux/deb/dists/stable/Release)  
Some index files failed to download, they have been ignored, or old ones used instead.

I think you're right crolanx, these elements must make up the 44th item, and apparently they're not available for me at this time. I'll check again later and post a report. Thanks.

EDIT: Hello Naminator_X_. Do you receive the same message as the one I posted above?

---

### Post by EarlySight on 2010-04-04
Okay, I tried it again tonight and the repository update still gets stuck at the 44th item for some reason. Eventually, after maybe three minutes or so, it goes on and manages to complete the process. However, in doing so it tells me that the system is up-to-date, which is more likely not true, seeing as this laptop was turned off in a bag for weeks. Will keep on searching for a way to resolve this.

**[Here is a screenshot]("http://www.lunatikstudios.com/Misc/Screenshot_02.png")** so that you can see what I'm talking about.

---

### Post by NightwishFan on 2010-04-04
Check your system sources in System -> Administration -> Software Sources.

[LIST]
[*]Do you have all the boxes ticked under "Ubuntu Software"?
[*]In the second tab see if you have any third party repositories. If so, disable them until you review they are added correctly. This might be the kicker, I suggest you review your google sources.
[*]In the third tab are the top two boxes checked; Important security updates and Recommended Updates?
[/LIST]

---

### Post by EarlySight on 2010-04-04
Hey thanks, that worked! I disabled Google under the second tab (third party repositories) and was able to successfully get the security updates for the OS. Also, it no longer hangs while updating the repository list. I tested it and clicked "Check" a bunch of times and it gets refreshed in mere seconds, just like it did before.

The only downside is that Chrome won't be updated at this point, as it cannot be patched on its own; it works in conjunction with Ubuntu's updates.

But thanks again, that helped a lot!

---

