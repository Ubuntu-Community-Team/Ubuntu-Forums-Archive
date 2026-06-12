---
title: "Chrome Profile Backup"
date: 2010-03-09
forum: General Help
---

### Post by Toddus on 2010-03-09
Hi all,

did a quick search through the general help forum but didn't come across anything having to do with my problem (all results were something to do with chromium or FF). 

Anyway, I am trying to figure out how to backup my user profile for google chrome, and more importantly, figure out how to restore it. On my windows machine there is a simple program you can use, or swap a file out of the google chrome folder. However, I am making the switch to 9.10 for my lappy, and I don't know how to go about this on ubuntu, is there anyone that could help me out? 
Thanks.

---

### Post by arnab_das on 2010-03-09
if you want to backup your bookmarks then you can export it to an html file (from the Bookmark Manager). not sure if chrome offers a complete profile backup though.

---

### Post by lovinglinux on 2010-03-09
If you are using Chromium, backup the folder ~/.config/chromium. I don't know where Chrome store profile settings, but could be under ~/.config/Google.

To restore a profile, simply replace the folder with the backup.

---

### Post by Toddus on 2010-03-09
Well I am working with chrome, not chrommium...

Also, I am not just trying to backup my bookmarks, but my chrome user profile. This would include saved passwords etc... For some reason chrome doesn't offer and option to do this, unless you use some third party program, or manually find the profile file yourself. I just don't know how to browse to the file/folder in ubuntu.

---

### Post by lovinglinux on 2010-03-09
> **Toddus said:**
> Well I am working with chrome, not chrommium...

Also, I am not just trying to backup my bookmarks, but my chrome user profile. This would include saved passwords etc... For some reason chrome doesn't offer and option to do this, unless you use some third party program, or manually find the profile file yourself. I just don't know how to browse to the file/folder in ubuntu.

Have you looked into ~/.config/Google as I suggested?

All configuration folders are hidden, so you will need to hit CTRL+H in Nautilus to see them. The .config folder is under your user home directory.

---

### Post by Toddus on 2010-03-09
> **lovinglinux said:**
> Have you looked into ~/.config/Google as I suggested?

All configuration folders are hidden, so you will need to hit CTRL+H in Nautilus to see them. The .config folder is under your user home directory.

okay, thank you, I believe this took me to the folder I needed.

Now can I just copy the files from my windows machine to ubuntu?
I am looking in this directory in ubuntu:/home/todd/.config/google-chrome/Default

---

### Post by lovinglinux on 2010-03-09
> **Toddus said:**
> Now can I just copy the files from my windows machine to ubuntu?

Probably. I don't know how Google Chrome handles for example extensions that are OS specific. I would recommend using an on-line synchronizing extension if available, instead of copying profiles from one OS to another. You could also copy only the files you need, but I can't help you with that, since I'm a Firefox user.

---

### Post by fragos on 2010-03-09
On line syncing of bookmarks has worked well for some time. The files you want are in ~/.google-chrome.

---

