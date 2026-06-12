---
title: "Does EVERY Program Installed Through Ubuntu Software Center ALWAYS Updated?"
date: 2012-04-21
forum: General Help
---

### Post by montecarlo87 on 2012-04-21
Question:
 
Does EVERY program/program package installed through Ubuntu Software Center ALWAYS updated?
 
Is "every and all" installed applications/programs onced installed through Ubuntu Software Center are monitored and routinely updated through the Ubuntu (specifically, the Ubuntu Update Manager) on a Linux Ubuntu v.11.10 64-bit operating system? Or are there "a few exceptions" to this where there may be the case where a some circumstances of applications/programs installed through Ubuntu Software Center may NOT be updated thru Ubuntu (specifically, the Ubuntu Update Manager)?
 
Please explain.
 
Thank you!

---

### Post by Metul Burr on 2012-04-21
Wouldn't updating/upgrading after install make this moot?

---

### Post by montecarlo87 on 2012-04-21
@ Metul Burr:
 
Hello. Nice to meet you.
 
I'm sorry, I must of confused you from my comment.
 
Typically, for the programs that I have installed though Ubuntu Software Center, Ubuntu Update Manager will find an update or upgrade and install it automatically when the time arrives when there is a program update or upgrade from the program author. 
 
Now is this true for ALL programs that are installed though the Ubuntu Software Center -- does the Ubuntu Update Manager ALWAYS automatically upgrade or update EVERYONE of those installed programs when the time arrives when there is a program update or upgrade from the program author or not?       
 
 
 
 
 
I think you making it sound like 'two separate' events -- where I install the upgrade or upgrade for the particular program myself and then later I expect Ubuntu Update Manager to follow through -- NO! I am NOT doing any of the updating or upgrading here. It is all up to the Ubuntu Update Manager. Just want to know if the Ubuntu Update Manager takes care of "ALL" program updates or upgrades once I install it though the Ubuntu Software Center... ...or the Update Manager isn't 100% effective with ALL updates or upgrades for programs installed through Ubuntu Software Center? 
 
Understand?
 
Please reply.
 
Thank you!

---

### Post by cottfcfan on 2012-04-21
Brief answer is no.
Firefox & Thunderbird usually get updated to the latest.
As for the rest they usually just get bug & security updates.
There is the odd exception, but if you want the latest software, you need to add ppa's to your software sources.
Although beware that doing so may occasionally cause problems.

---

### Post by Paqman on 2012-04-21
> **cottfcfan said:**
> Brief answer is no.


Well, more like yes and no.

**Short answer:** yes, the system *can* update all of the packages you install through Ubuntu Software Centre. Same goes for installing through apt-get on the command line, Hardware Drivers, or PPAs. It's all the same thing.

**Long answer:** that doesn't necessarily mean you *will* always have the latest version of everything. You system can only update you to whatever the latest version is in the repositories. On an old release that could be quite an old version of the software, as after release it's generally only security updates and major bugfixes that make the updates. So something like your kernel that is important for security is likely to get a lot of updates, but most of your applications won't. That's why a lot of people like PPAs, as it allows them to get updated versions of packages through Update Manager.

---

### Post by montecarlo87 on 2012-04-21
@ cottcfan & anyone:
 
Hello. Nice to meet you.
 
Thank you for your comment.
 
So you are saying that installing programs though the Ubuntu Software Center does NOT guarantees you will always have Ubuntu automatically provide you updates or upgrades for that particular program when made available? 
 
I had a friend state that: "All programs installed by the Ubuntu Software Center, Synaptic Package Manager, the line command sudo apt-get or aptitude are perfectly consistent and are interfaces to the same dpkg utility working on the same repositories, defined in Software Sources." ...implying that ALL programs installed through anyone of the given installing components of Ubuntu, namely the Ubuntu Software Center I am addressing, that the particular program will "ALWAYS" have updates or upgrades when they are made avaiable. 
 
I see the truth to be -- "MOST" of the time it IS consistent, BUT "NOT ALWAYS" will an installed program from the Ubuntu Software Center get an update (or upgrade) from the Update Manager or the Software Sources. Am I correct?
 
Please reply.
 
Thank you!

---

### Post by CatKiller on 2012-04-21
They will all get updates if they are available. Updates that are not security updates are not made available. Those will be included in the next Ubuntu version.

---

### Post by cottfcfan on 2012-04-21
Sorry I see what you're saying now.
Whether you install from the Software Centre, Synaptic or the Terminal, all the updates will be consistent & the same, but that does not mean that you will necessarily get the latest version of the program.

---

### Post by Paqman on 2012-04-21
> **montecarlo87 said:**
> 
So you are saying that installing programs though the Ubuntu Software Center does NOT guarantees you will always have Ubuntu automatically provide you updates or upgrades for that particular program when made available? 


If an updated version of the software hits the repos, your system will get the update.

---

