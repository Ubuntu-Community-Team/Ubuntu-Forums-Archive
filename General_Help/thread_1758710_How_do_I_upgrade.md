---
title: "How do I upgrade ?"
date: 2011-05-15
forum: General Help
---

### Post by Gordonisnz on 2011-05-15
Release 10.04 (lucid)
Kernel Linux 2.6.32-31-generic
GNOME 2.30.2


Hello.

I'm interested in upgrading my Linx (i have NO CD.)

- I've done all the updates so far (but not upgrade) - I do get an "eee" error - which occurs at each update, i can't get rid of - But all updates seem to be completed.


How / what screen do i go to to "upgrade". I can't see any upgrade option in my system, admin areas of my system.

Thank you

---

### Post by Hedgehog1 on 2011-05-15
If your system does not have a CD drive, you can upgrade using a LiveUSB. If you were thinking of upgrading to Natty/11.04:

Download the Natty/11.04 ISO, and then use the 'startup disk creator' to turn a USB stick into a LiveUSB of Natty.

If you have your data in a separate '/home' partition you can install 11.04 over your 10.04 '/' partition and be sure to not format the '/home' partition:

First, define your '/' (root) partition:

[IMG]http://img31.imageshack.us/img31/7520/04allocdrivespace2.png[/IMG]

[IMG]http://img130.imageshack.us/img130/9673/05allocdrivespace3.png[/IMG]

Then define your '/home' partition:

**[SIZE="4"]IF YOU ARE DOING AN UPGRADE, DO NOT FORMAT THIS PARTITION![/SIZE]**

[IMG]http://img202.imageshack.us/img202/6828/07allocdrivespace5.png[/IMG]

This separates your documents and 'stuff' from the system files and 'stuff' in the '/' partition.

***The Hedge***

:KS

p.s. To learn how to move your '/home' into it's own partition: **_[SeparateHomePartition]("http://www.psychocats.net/ubuntu/separatehome")_**

---

### Post by mikewhatever on 2011-05-15
Since you have Ubuntu 10.04 installed, you can only upgrade to Ubuntu 10.10. Here is a step by step howto:
[https://help.ubuntu.com/community/MaverickUpgrades#Upgrade%20from%2010.04%20LTS%20to%2010.10](https://help.ubuntu.com/community/MaverickUpgrades#Upgrade%20from%2010.04%20LTS%20to%2010.10)

While the choice is entirely yours, I'd discourage an upgrade just for the sake of upgrading. Lucid is pretty stable now, and will allow you to upgrade directly to the next LTS in April 2012.

---

### Post by Hedgehog1 on 2011-05-15
> **mikewhatever said:**
> While the choice is entirely yours, I'd discourage an upgrade just for the sake of upgrading. Lucid is pretty stable now, will allow you to upgrade directly to the next LTS in April 2012.

+1 on staying with 10.04.02.  Even if you want to go to Natty, you might want to wait till it 'settles down'

***The Hedge***

:KS

---

### Post by PaulW2U on 2011-05-15
> **mikewhatever said:**
> While the choice is entirely yours, I'd discourage an upgrade just for the sake of upgrading. Lucid is pretty stable now, and will allow you to upgrade directly to the next LTS in April 2012.

Exactly my thoughts although I have moved to **K**ubuntu 11.04 and re-installed the existing LTS 10.04 which I am only using some of the time. Unity is incomplete and buggy, just look around these forums to see the problems people are having. :sad:

---

### Post by Topsiho on 2011-05-15
I think/fear that there might be some confusion here.

You can "upgrade" to a newer Ubuntu version in two distinct ways:

1. You could do a fresh install, which is described above as an upgrade. You download a LiveCD for your hardware, depending on processor and 32/64 bits, or if that doesn't work an alternate CD. As you don't have a CD player you should make a LiveUSB, as described above.

2. You could also do what is called an (direct) upgrade. This is only possible, as described, in a step by step fashion, from one version to the next, or from one LTS version to the next LTS version. This happens in an automatized way, and is in fact no different from the usual updates, only the number of updates is far and far greater, taking very much downloading (easily far more than one GB),and time for the actual updating (depending on your system this can take hours).
It is usually started pressing a button when doing a normal update (Update Manager), visible when a new version is available.

My experience so far is that a fresh install is preferable, though the second, upgrade process, in theory is the simplest one. But sometimes goes haywire, and then you are in trouble. And you have to do a fresh install anyway :(

Topsiho

---

### Post by mikewhatever on 2011-05-15
> **PaulW2U said:**
> Exactly my thoughts although I have moved to **K**ubuntu 11.04 and re-installed the existing LTS 10.04 which I am only using some of the time. Unity is incomplete and buggy, just look around these forums to see the problems people are having. :sad:

Every Ubuntu release is followed by a storm of negative comments similar to yours with a remarkable persistence. "Incomplete, buggy, pointless, nightmare, worst release ever", etc (I can pm the link if you want them). However, after a time, it blows over, those who come to badmouth get tired, those severely affected switch, bugs get fixed, people get used to the changes, and by the time of the next release, everybody loves the previous one and is ready to hate the next.

Anyway, all that is irrelevant, because the OP can only upgrade to Maverick.

---

### Post by PaulW2U on 2011-05-15
> **mikewhatever said:**
> Every Ubuntu release is followed by a storm of negative comments similar to yours with a remarkable persistence. "Incomplete, buggy, pointless, nightmare, worst release ever", etc (I can pm the link if you want them). However, after a time, it blows over, those who come to badmouth get tired, those severely affected switch, bugs get fixed, people get used to the changes, and by the time of the next release, everybody loves the previous one and is ready to hate the next.

If you checked back through my previous posts you would see that I have never bad-mouthed Unity, I helped alpha/beta test it for several months and actually support its introduction. However, at the time of 11.04's release it was left incomplete and I stopped using it due to several very annoying bugs that not yet been fixed. Yes, they will be fixed in time, it will be improved but until that happens people will continue to have problems such as missing panels or a missing launcher when they first install it. I have every intention of following its progress throughout the 11.10 development cycle and will adopt it for sure when 12.04 is released but for now I'm not using it. That's all I was trying to say. Unfortunately some people are too quick to criticise anyone who dares criticise Unity, constructively or otherwise.

---

### Post by mikewhatever on 2011-05-15
@PaulW2U
I've never said or implied that you had badmouthed Unity. Where did that come from? For all I care, you are free to criticize it as much as you want and the way you want.
I was going to pm you this and refrain from derailing the thread even further, but you don't allow pms.

---

