---
title: "Need help removing shortcut on Applications menu of a Wine installed program"
date: 2009-07-12
forum: General Help
---

### Post by sois on 2009-07-12
I'm a pretty new user and I installed Wine.  I've found a replacement for all of my Windows programs except a media player named Media Monkey.

I installed Wine via the Ubuntu add/remove programs tool.  I then installed MediaMonkey.  I didn't like the performance so I removed Wine.  However, in my Applications menu, there is a category called Other and it has links to MediaMonkey options, as you would see in a Windows Start Menu list.  

How can I remove this?  Also, how do I remove the left over files?  I know they are still there and are taking up hard drive space.

Thanks Ubuntu users!

---

### Post by DeMus on 2009-07-13
> **sois said:**
> I'm a pretty new user and I installed Wine.  I've found a replacement for all of my Windows programs except a media player named Media Monkey.

I installed Wine via the Ubuntu add/remove programs tool.  I then installed MediaMonkey.  I didn't like the performance so I removed Wine.  However, in my Applications menu, there is a category called Other and it has links to MediaMonkey options, as you would see in a Windows Start Menu list.  

How can I remove this?  Also, how do I remove the left over files?  I know they are still there and are taking up hard drive space.

Thanks Ubuntu users!

Right click on the word Applications (top left) and choose edit menu.
Then in the new window on the left select the menu and on the right deselect the box in front of the program name. Don't delete it the whole entry, just deselect the box. It's enough to not show up again.

---

### Post by sois on 2009-07-13
That's great!

Is there anything I can do about removing the legacy files?  I still see Wine and MediaMonkey files.  I am not familiar with the Linux file system yet.  Thanks for the fast response!

---

### Post by sois on 2009-07-13
bump

---

### Post by pedro_orange on 2009-07-13
> **sois said:**
> That's great!

Is there anything I can do about removing the legacy files?  I still see Wine and MediaMonkey files.  I am not familiar with the Linux file system yet.  Thanks for the fast response!

Open up nautilus, and go to your home directory. Hit Ctrl + H, this will show you all the hidden files & folders. You should have a folder there called .wine (Yes there is a full stop there) - This is where Wine installs everything to. Feel free to delete it if you have indeed removed wine.

---

### Post by sois on 2009-07-13
Thanks guys, this works well.  So far so good on Ubuntu!

---

