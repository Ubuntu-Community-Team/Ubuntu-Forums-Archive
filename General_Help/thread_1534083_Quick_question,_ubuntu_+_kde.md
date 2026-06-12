---
title: "Quick question, ubuntu + kde"
date: 2010-07-19
forum: General Help
---

### Post by Deicider on 2010-07-19
The question being, if i install ubuntu and run it with kde will there be performance problems compared the standard buntu with kde (kubuntu).
Or do you recommend kubuntu instead of ubuntu + kde.Am saying this cause i already installed ubuntu and am thinking of dling kde instead of installing kubuntu.
Am talking bout 10.04

---

### Post by darolu on 2010-07-19
Just install the Kubuntu desktop and that's it:

```
sudo apt-get install kubuntu-desktop
```

This will install KDE, apps and configurations (like themes) that come with Kubuntu, you can choose wich one you want to use when you log in.

Performance should be the same.

---

### Post by Mike_IronFist on 2010-07-19
> **Deicider said:**
> The question being, if i install ubuntu and run it with kde will there be performance problems compared the standard buntu with kde (kubuntu).
Or do you recommend kubuntu instead of ubuntu + kde.Am saying this cause i already installed ubuntu and am thinking of dling kde instead of installing kubuntu.
Am talking bout 10.04

Hey, You can install KDE on top of Ubuntu, and you shouldn't expect a performance loss. As darolu showed you above, you can install all the packages that come with Kubuntu. However, installing kubuntu-desktop on top of Ubuntu means you'll have a ton of programs, since there will be both Kubuntu's default apps and whatever apps are currently in your Ubuntu installation.

---

### Post by Deicider on 2010-07-19
thanks,i appreciate your replies,i will install kde on top of ubuntu as you said.
Another problem came up,i was careless and forgot to you my old Home username(cause i separated home from root )and used a new home/user ,any of you know how to make my old home/user be default user?
Also,my old home/user is seen as a separated partition instead being inside my current Home folder,bit off topic but if you know the answer hit me.

---

### Post by Mike_IronFist on 2010-07-19
> **Deicider said:**
> thanks,i appreciate your replies,i will install kde on top of ubuntu as you said.
Another problem came up,i was careless and forgot to you my old Home username(cause i separated home from root )and used a new home/user ,any of you know how to make my old home/user be default user?
Also,my old home/user is seen as a separated partition instead being inside my current Home folder,bit off topic but if you know the answer hit me.
When you install Ubuntu, if you set up the partitions manually, you have to specify in the installer that you want that partition mounted as **[FONT="Courier New"]/home[/FONT]** , otherwise it will just ignore the partition and assume it's not meant to be treated as your home folder.

Then, as long as your username (not full name) is the same as the name of your old home folder, you'll have all your old files and settings accessible.

---

### Post by Deicider on 2010-07-19
so is there a way to rename my current home username to my old,so the old is used instead the new one.

---

