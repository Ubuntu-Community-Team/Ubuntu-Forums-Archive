---
title: "Accessing files in XP from Ubuntu"
date: 2009-11-02
forum: General Help
---

### Post by Haedrian on 2009-11-02
I installed Ubuntu 9.10 on a machine which already has windows XP on it.

They now exist seperately together - but I want to access the "My Documents" folder (from XP) from Ubuntu.

How can I do that?

Thanks

Added: I'm very very new to this whole thing - so please don't make any assumptions

---

### Post by iMisspell on 2009-11-02
**WinXP-Hard-Drive**/Documents and Settings/**WinXP-UserName**/My Documents

your xp desktop would be:
**WinXP-Hard-Drive**/Documents and Settings/**WinXP-UserName**/Desktop

Is that what your looking for ?


[edit]
Not sure if Ubuntu 9.10 is the same as Ubuntu 9.04, but in 9.04...
From your "tool-bar":
Places > **WinXP-Hard-Drive-Name**
Then the path...
Documents and Settings/**WinXP-UserName**/My Documents
Documents and Settings/**WinXP-UserName**/Desktop
_

---

### Post by Haedrian on 2009-11-02
Yes that's the folder I want, unfortunatly since the Ubuntu installation and the XP installation are on the same disk - I can't access C:\ - when I click "Home" I start from the space I reserved for the ubuntu installation - and I'm not able to access the rest of the hard disk.

---

### Post by iMisspell on 2009-11-02
I edited my first post (sorry)...

Does this help ?

[edit]
Not sure if Ubuntu 9.10 is the same as Ubuntu 9.04, but in 9.04...
From your "tool-bar":
Places > WinXP-Hard-Drive-Name
Then the path...
Documents and Settings/WinXP-UserName/My Documents
Documents and Settings/WinXP-UserName/Desktop

---

### Post by Haedrian on 2009-11-03
No, there isn't the option to do that.

Maybe I didn't make myself clear enough - I installed Ubuntu 'inside' XP (from the installation CD). Its not on a different partition (or if it is, XP isn't recognising there is a different partition) and in C:\ (from XP) I have a folder called "Ubuntu" which I suppose holds all the stuff inside it. I suppose C:\ is outside the scope of it.

From "Places" the closest I can get is [hard disk symbol] which contains the same files as the Ubuntu folder in XP.

I can't get to C:\ from the Places browser - is there another way?

---

### Post by jmore9 on 2009-11-03
When i was dual booting linux and xp pro all i did was ( in linux ), goto places, then scroll down to my computer and mount the ntfs partition i wanted.

I was able to read and write from the ntfd partition with no loss of data.

You also have to install some ntfs stuff from the repos so it will all work proplerly.

Here is a page on one way to accomplish that:

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Hope this helps a littlebit

Oh yea i also did a chkdsk on the drives i used in linux using the windows checker upon the next use of windows

---

### Post by coffeecat on 2009-11-03
> **Haedrian said:**
> Maybe I didn't make myself clear enough - I installed Ubuntu 'inside' XP (from the installation CD).

That sounds as though you installed with Wubi, which is an entirely different matter. iMisspell was assuming (as I would have done) that you did a conventional dual-boot install.

Anyway - Have a look at this link:

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

Scroll down to "[SIZE=2]Can I access my Windows files from a Wubi installation?[/SIZE]", It says:

> Yes, the Windows partitions will be available within the directories /host and /media.To get to those directories, go to Places and click on 'Computer' and double-click on Filesystem. You should see both /host and /media among those folders. Try navigating to your 'My Documents' from there. Once you get to where you want to be, if you add a bookmark in the file browser (Nautilus) from the Bookmarks menu, the bookmark will appear as a selection in the main Places menu. Which is handy. :)

---

### Post by Haedrian on 2009-11-03
/host worked

Thank you for all your help :)

---

