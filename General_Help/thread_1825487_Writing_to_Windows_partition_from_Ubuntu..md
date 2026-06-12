---
title: "Writing to Windows partition from Ubuntu."
date: 2011-08-15
forum: General Help
---

### Post by Abrer on 2011-08-15
Does this cause any problems? I never really thought about it until I loaded up windows last night to run some other software and it loaded up rather strangely. Mouse and Keyboard didn't do anything until after a few restarts, network icon never says connected, despite having internet access, anti-virus is in an "inconsistent" state and just some other weirdness. The app I wanted to run doesn't even completely execute. Shows up in the process list but never makes it to the GUI.

So I was just wondering if my writing to the Windows partition from Ubuntu may have caused any problems. These writes were 99% wallpapers to a folder on my C:\ drive.

Any ideas? If not, it's cool. Gonna nuke both my Windows and Ubuntu at a later date. May just do it earlier is all.

-Thanks.

---

### Post by Primefalcon on 2011-08-15
Never has in my experience and I have been using Linux for over 5 years now, on my own system and as a recovery tool on other peoples

---

### Post by Abrer on 2011-08-15
Ah ok, good to know that's likely not the problem. I have other suspicions. Thanks.

---

### Post by Primefalcon on 2011-08-15
that is unless of course you inadvertently deleted something windows/the program  needs

---

### Post by Abrer on 2011-08-15
No changes to anything other than the directory where I store some images on C:\. Just a sudden problem.

---

### Post by Duncan Williams on 2011-08-15
run a few malware scanners over your windows.
malwarebytes, panda online scanner, etc...

---

### Post by oldfred on 2011-08-15
If you were hibernated in Windows and then write into the Windows partition it can cause huge problems. Also Ubuntu shows all files & folders or you can see and accidentally modify system files in windows that windows normally protects you from. 

Often best to set the C: drive as read only unless you have to make repairs from Linux and create a D: drive for any data you want to share in both systems. I have my Firefox & Thunderbird profiles in my shared and never have had an issue that I can identify to sharing a partition.

---

