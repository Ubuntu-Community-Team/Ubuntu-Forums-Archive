---
title: "Empathy and AIM"
date: 2010-02-18
forum: General Help
---

### Post by ElSlunko on 2010-02-18
Hey all,

Haven't been able to connect to AIM since yesterday morning. Not sure what changed. I'm using the telepathy ppa and have tried removing ppa, uninstalling everything telepathy related that I could, cleared cache, & reinstalled yet still no luck.

Perhaps there is a list of AIM servers that I could try connecting to because the default keeps returning a Network Error. I'm back to the telepathy ppa.

Any help / response would be appreciated.

Thanks,

---

### Post by belgarth on 2010-02-19
I'm running into the same problem with empathy 2.29.90. I just tried adding the ppa, but it seems to be at the same version as the standard repositories. What's odd is pidgin can log in fine and the advanced settings show that pidgin is connecting to the same aim server url as empathy is failing on.

---

### Post by ElSlunko on 2010-02-19
> **belgarth said:**
> I'm running into the same problem with empathy 2.29.90. I just tried adding the ppa, but it seems to be at the same version as the standard repositories. What's odd is pidgin can log in fine and the advanced settings show that pidgin is connecting to the same aim server url as empathy is failing on.

You have progress on me on that one since Pidgin doesn't work for me either. Just using meebo for the time being.

---

### Post by akakingess on 2010-02-19
For some reason I remember something like this happening last year, and it turned out to be AOLs doing somehow, may want to search forum archives and see if it's related.

---

### Post by ElSlunko on 2010-02-19
I'll keep digging around. I know the AIM client went under some big changes recently adding facebook. Don't see how that would affect things but it may have.

---

### Post by mynimal on 2010-02-20
Same problem here. Was connected for a long while, relogged a while ago and now AIM can't connect.

---

### Post by howefield on 2010-02-20
> **ElSlunko said:**
> Haven't been able to connect to AIM since yesterday morning. Not sure what changed.

Problem here with ICQ and AIM.

Seems to happen occasionally, usually fixed within a couple of days.

---

### Post by saturnblackhole on 2010-02-20
> **ElSlunko said:**
> You have progress on me on that one since Pidgin doesn't work for me either. Just using meebo for the time being.

yeah i had this problem with pidgin the solution is to go to accounts-->manage account---> click on the aol account --->modify and go to the advance panel.once your in the advance panel unclick the "use ssl" box. 

unfortunately this option isn't available in empathy

---

### Post by ElSlunko on 2010-02-20
> **saturnblackhole said:**
> yeah i had this problem with pidgin the solution is to go to accounts-->manage account---> click on the aol account --->modify and go to the advance panel.once your in the advance panel unclick the "use ssl" box. 

unfortunately this option isn't available in empathy

Yeah. Guess it's back to pidgin. Oh well, time to customize my pidgin icons now :P

---

### Post by mynimal on 2010-02-23
The plot thickens?

AIM was working fine on my laptop before I upgraded to the latest Lucid dev, and after the upgrade it has the same problem.

---

### Post by ElSlunko on 2010-02-23
There was an update to telepathy via the ppa this morning, but no luck yet on AIM :(.

---

### Post by mynimal on 2010-02-25
Just did a dist-upgrade, which had some new Empathy stuff. Now AIM connects. Yay.

---

### Post by ElSlunko on 2010-02-25
> **mynimal said:**
> Just did a dist-upgrade, which had some new Empathy stuff. Now AIM connects. Yay.

Are you on 10.04?

---

### Post by ElSlunko on 2010-02-25
Got bored today and did the risky upgrade from 9.10 to 10.04 alpha 3 & Empathy + AIM works now. I wouldn't suggest changing to the alpha just for Empathy though, but somewhere down the line there is a fix. Wish I knew more so I could figure out how to resolve the issue for others.

---

### Post by Jackelope King on 2010-02-25
Speaking of Empathy and AIM, while I'm not having problems logging on, I have never been able to successfully join a group chat for AIM on Empathy (whether accepting an invite from another user or by joining manually). Does anyone else have this problem?

***EDIT:** Never mind. I spoke to one of the devs on the Empathy IRC channel, and apparently the problem is that while AIM's normal one-on-one chat works, their group chat doesn't work with telepathy-haze.*

---

### Post by BOFslime on 2010-03-09
Both Pidgin and Empathy have this issue, however you can disable ssl within pidgin allowing you to connect.  Empathy on the other hand does not have such an option available.  I'm guessing that AOL made a change to their servers to cause this, as these are default settings.

---

### Post by belgarth on 2010-03-18
I started looking into this again and found
[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/526146](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/526146)
and 
[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/524221](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/524221)
which seem to be the issue, but the bugs are filled against empathy and then end up being fixed in pidgin, which has me very confused. Hoping someone else on this thread might be able to figure out what is going on.

---

