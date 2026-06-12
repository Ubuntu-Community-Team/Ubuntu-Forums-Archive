---
title: "VLC has gone Evil"
date: 2010-12-26
forum: General Help
---

### Post by Dr Zin on 2010-12-26
Ok this so weird VLC has taken over My menu for places I click on  home it opens vlc. I removed vlc and my places worked. I re-installed it continues to happen. Then removed the plug in's one at time to if was one of them that was causing this to take place. It seem that does not work ether.

I go the menu places, then it displays home, blah, blah. I clink on home vlc opens finds videos to play in my home. It as well run very hot its using a lot of system resources as well like mad.

So I have set it for a complete removal.  Then reinstalled it continues to do the same thing. Well it seams to be a bug?

---

### Post by noah++ on 2010-12-26
That is weird. From Google, I am reading about two users who've experienced the same thing in Windows, but not Linux.

Are you just installing the latest VLC from Ubuntu's default repositories?

---

### Post by Vaphell on 2010-12-26
i think you got hit with this bug
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/603833](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/603833)

i think you need to right click any dir, choose 'open with program...' (or whatever it's called in english) and set nautilus as default for folders ('Remember this application for "folder" file')

---

### Post by Dr Zin on 2010-12-26
> **noah++ said:**
> That is weird. From Google, I am reading about two users who've experienced the same thing in Windows, but not Linux.

Are you just installing the latest VLC from Ubuntu's default repositories?

 Yes, I am pulling it form the Ubuntu's repository.

> **Vaphell said:**
> 
Re: VLC has gone Evil
i think you got hit with this bug
[https://bugs.launchpad.net/ubuntu/+s...us/+bug/603833](https://bugs.launchpad.net/ubuntu/+s...us/+bug/603833)

i think you need to right click any dir, choose 'open with program...' (or whatever it's called in english) and set nautilus as default for folders ('Remember this application for "folder" file') 

I just don't your get that post sorry man.

---

### Post by coffeecat on 2010-12-26
> **Vaphell said:**
> i think you need to right click any dir, choose 'open with program...' (or whatever it's called in english) and set nautilus as default for folders ('Remember this application for "folder" file')

> **Dr Zin said:**
> I just don't your get that post sorry man.

@Dr Zin, Vaphell has given you the correct solution, but let me put it another way. Right-click on the desktop and 'Create Folder'. It doesn't matter what you call it -  the default 'untitled folder' is fine. Now right-click on the new folder and choose 'Open with other Application'. Make sure the 'Remember this application...' box at the bottom is ticked, and find 'File Browser' in the list. Click on it and your problem is solved. You can now delete the desktop folder.

This is not really a bug - more a usability issue. You must have opened a media folder with VLC by right-clicking in the same way and the remember box was ticked. That's why VLC tried to open every folder thereafter.

---

