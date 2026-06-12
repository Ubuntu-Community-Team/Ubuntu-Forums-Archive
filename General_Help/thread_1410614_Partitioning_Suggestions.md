---
title: "Partitioning Suggestions"
date: 2010-02-18
forum: General Help
---

### Post by Zzarkc-20 on 2010-02-18
Hi, I just built a brand new computer not long ago, and I'm looking to get it working as a triple boot system. Now, what I'd like is to have Ubuntu, Windows XP, and Windows 7. The Windows 7 is an upgrade version, so I'll need to have XP installed twice. 

I'll be using a 1 TB hard drive, and so I'm a little curious on how I should partition things. I want enough space to boot each version, and I want to have the rest be NTFS formatted, allowing me to access those files from all my OS's. I tried a test set up with an old hard drive without Windows 7, and found out that with all the updates and such, 10GB was not nearly enough for my Windows XP partition.

Hence, how much should I allow for each of my partitions, and in which order should I have them partitioned. I'm thinking:

1GB Swap
15GB Ubuntu /
30GB Windows XP
40GB Windows 7

Rest goes to NTFS.

Questions:
1)Are each of those partitions well sized? Remember, I'll need space for programs like Adobe CS4 Designer, Autodesk, and Microsoft Office in both XP and 7. (Please offer amount of space. It's 1TB, so I'm not worried about having TOO much in each OS. I'm tempted to just throw 50GB in each boot partition)

2)Should the order be changed in any way for efficiency? I'll probably use 7 more than XP.

3)Tips for order of installation, and I'm not sure if it matters too much, (for example, both XP partitions, then upgrade one to 7, then install Ubuntu, or XP>7, then new XP, then Ubuntu)

Thanks! I appreciate the suggestions!

---

### Post by zbirdman777 on 2010-02-19
I have my laptop setup in a similar way but with just Windows 7 and Ubuntu and a storage partition. My suggestion is don't be stingy with the installation partitions, especially Windows 7. I used 100 for each on mine.

I have 78 gB used on Windows 7 and I DON'T store any files on the same partition where 7 is installed and I hardly use Windows 7 for anything but Visual Studio and it has some basic programs.

33.8 gB used on Ubuntu for me and I use it heavily so you could get away with 50 minimum for Ubuntu I'd say.

XP would probably need a little more than Ubuntu. 70 minimum I think.

In short I suggest:

Windows 7: 100-120 gB
Windows XP: 70-100 gB
Ubuntu: 50-100 gB

Just curious btw, why would you want to install Windows XP if you have 7 and Ubuntu? 7 has compatibility mode for XP anyway.

Good luck with your endeavors!

---

### Post by Zzarkc-20 on 2010-02-19
Thanks for the tips. As I haven't run Windows 7 yet, I like hearing the different suggestions.

I'm planning on running both 7 and XP because even with the compatibility mode, I've heard of different programs having different problems. Also, since I'll be having 1TB, I don't mind sacrificing that little storage for the ability to add another OS. I'm used to running off of around 100 GB, so 1TB is like a mansion.

Also, is 1GB swap good? I remember hearing you should have half as much swap as memory, but I've got 6GB of memory. I also heard that swap rule was made when they didn't have more than 1GB. Never found something conclusive about that. Thanks!

---

### Post by argos3016 on 2010-02-19
1Gb  of swap is good.
The RAM its only important for the /dev , /proc and few other linux dirs , that the kernel creates at boot ( the ramfs), when detects new devices or run programs like init.

---

