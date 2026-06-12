---
title: "Add Grip to CD's right-click Open With Menu"
date: 2009-11-13
forum: General Help
---

### Post by jamesisin on 2009-11-13
I have switched to using Grip (over SoundJuicer) and would like to make it a little easier to rip from a CD.  Currently I have to insert the disc and run Grip.  I would like to merely right-click on the disc (Desktop) and choose Grip from the context menu which appears.

Normally I could choose Properties from that context menu and add an application to the Open With tab.  However, the Properties dialog for the CD on my Desktop has no such Open With tab.

I am running 8.10.

What do I need to do to make this happen?

---

### Post by mc4man on 2009-11-13
I don't use 8.10 or grip but the principal should be the same 
To get a right click option on a dvd/cd icon the app needs to be a choice for autoplay (default app).

It doesn't need to be the default, just a choice.

Grip isn't registered upon install, there are several ways to do, this should suffice

Open up file management (in System -> Preferences if you've enabled in edit menus or go nautilus -> edit -> preferences or in terminal
```
nautilus-file-management-properties
```

Under the media tab -> cd audio in the drop down 'open with other application' enter grip

(there are several other ways if this doesn't work out 

Actually you may find it simpler to just insert an audio cd and hold down the shift button. In the pop up do the same as described above in the dropdown, though file management is an interesting place to look at

---

### Post by jamesisin on 2009-11-13
mc4man - Thanks.

Looks like the Shift trick doesn't work if you have Auto-Insert disabled (which I typically do).

I have to admit I was very dubious that your solution would actually work, but work it did.  Not very intuitive.

I will likely make a post to my blog about this one.

---

### Post by mc4man on 2009-11-13
This post, though a bit unorganized and mainly for hardy has a number of things still useful and alternate means, ect. ect. (sometimes the default launch command is unsuitable, then 'custom' launchers or scripts are needed

[http://ubuntuforums.org/showthread.php?t=895589](http://ubuntuforums.org/showthread.php?t=895589)  #7

---

### Post by jamesisin on 2009-11-15
Have you heard any good news about Grip?  It seems as though it has run out of development support.

---

