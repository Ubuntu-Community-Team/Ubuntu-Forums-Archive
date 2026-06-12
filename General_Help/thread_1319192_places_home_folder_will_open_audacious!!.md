---
title: "places home folder will open audacious!!"
date: 2009-11-08
forum: General Help
---

### Post by kostaben on 2009-11-08
Hi Forum,

I am on Kramic Koala 9.10. I have a very weird problem. When i go to the main menu > places > Home Folder or Desktop instead of opening these folders the system opens Audacious!! If i go through places > computer then Home Folder opens without problem.
The only thing i think to try is to see, by right clicking on home directory and choose properties, if there is open with tab. There is not such tab in properties.

Thank you for your help.

---

### Post by alinuxfan on 2009-11-08
I am having the opposite problem.  If I open from places, jpg files will not load.

---

### Post by Monotoko on 2009-11-08
Hmmm, have you tried removing audacious?

---

### Post by kostaben on 2009-11-08
mmmmm, i did not think about it :-\"
It worked, i reinstalled and same problem. I will use another player for a while.

Thank you

---

### Post by drs305 on 2009-11-08
Try opening Nautilus, right click on any folder, select "Open With" and then "File Browser" or something similar (I think it changed, File Browser is the Karmic version).

---

### Post by kostaben on 2009-11-08
Well, in this version of Ubuntu the Opens with tab has been removed! I was reading somewhere about it. i think there should be a way to do by commands. If someone knows how to, i would appreciate the help. I will try to look it up anyways and post back when i find it.

Thanks again, cheers

---

### Post by kostaben on 2009-11-10
Hi again,

So, there is Open With tab in 9.10 but not for folders. Given that the problem occurs only when i try to open the home directory from the main menu>places>home i think its a bug. Moreover when i uninstall Audacious i can access the home directory from the main menu without any problem, the system does not give a warning that the is not able to locate the application.

---

### Post by phatcartoon on 2010-11-06
I know this thread is old and probably dead, but I just wanted to post this since I just had this problem happen to me.  I'm using Ubuntu 10.10.   To fix the problem I right-clicked any random folder.  Instead of going down to properties and searching for an "open with" tab from the pop-up menu, I instead. . . 


right-clicked random folder. . .

right-click menu> Open With Other Application > File browser


Now when I go to home folder audacious no longer opens up all my music.  :D

---

### Post by pecuna on 2011-01-05
> **phatcartoon said:**
> I know this thread is old and probably dead, but I just wanted to post this since I just had this problem happen to me.  I'm using Ubuntu 10.10.   To fix the problem I right-clicked any random folder.  Instead of going down to properties and searching for an "open with" tab from the pop-up menu, I instead. . . 


right-clicked random folder. . .

right-click menu> Open With Other Application > File browser


Now when I go to home folder audacious no longer opens up all my music.  :D

Thanks man!!Thats did the trick :guitar:

---

### Post by MrPok on 2011-02-04
> **phatcartoon said:**
> I know this thread is old and probably dead, but I just wanted to post this since I just had this problem happen to me.  I'm using Ubuntu 10.10.   To fix the problem I right-clicked any random folder.  Instead of going down to properties and searching for an "open with" tab from the pop-up menu, I instead. . . 


right-clicked random folder. . .

right-click menu> Open With Other Application > File browser


Now when I go to home folder audacious no longer opens up all my music.  :D

I also ran into this problem today! *(and phatcartoon's advice worked)*

I'd installed Audacious for the first time ever yesterday, but I can't recall if I also rebooted afterwards any time yesterday. Today, from a cold boot it first showed this strange behaviour.
There doesn't seem to be any bug filed in [https://bugs.launchpad.net/ubuntu/+source/audacious](https://bugs.launchpad.net/ubuntu/+source/audacious)
I can't really tell if what we experienced is actually a bug though.
Maybe something related to dragging and dropping files in Audacious?

---

### Post by Vaphell on 2011-02-04
it's about choosing an alternative app for a given 'filetype' (folder in this case) and remembering the choice as the default. If you open dir with audacious - bam, you may have changed default app for folders if you haven't unclicked the checkbox below.
It's not a bug per se, more like poorly chosen defaults. It affects way too many people who don't notice the 'make it default' checkbox, which is as you may guess ticked on.

---

