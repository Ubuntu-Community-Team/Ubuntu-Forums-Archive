---
title: "Help!"
date: 2009-08-18
forum: General Help
---

### Post by natekrell on 2009-08-18
My fiancee has Ubuntu installed on her computer, and it usually loads first. She went away for a while and I tried to select to boot a windows system she had installed too (on that first options screen, I selected the last option of boot to windows, instead of whatever the default option is.) 

That brought me to the "Compaq System Restore" thing, which would only try and load a page saying I should try the Windows XP recovery features too (!). I can get to the Boot Menu, along with the Startup options from the Compaq boot screen. I can't get the computer to load the Ubuntu system, and when I put the Ubuntu CD in, it won't reinstall the system. The screen just goes black. 

How can I just get back to turning the computer on, and having Ubuntu be the default system? Please help. Starting to get worried.

---

### Post by approaching on 2009-08-18
You should still be able to pop in the live disk and boot off of it. I know that there should be a way to re-install grub and everything, but i have always been a fan of just nuking the system when something like this happens. My way would be to boot the live disk, then grab all the files off into an external drive or something, then use the live disk to nuke the system, but it isn't exactly the most graceful of methods. If the live disk won't boot, your issue might not be software related.

---

### Post by Locutus_of_Borg on 2009-08-18
there is no reason to "nuke" the system

firstly, ensure that in the BIOS that boot from optical media is the first (or at least before HDD) option
secondly, boot with linux cd in the drive (if the one you are using is not working, download and burn another one)
thirdly, restore grub by following one of the methods described here: [http://www.google.com/search?q=restore+grub&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=restore+grub&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by natekrell on 2009-08-19
That sounds like the sort of thing I was looking for. I'll try it and let you know. Thanks!

---

