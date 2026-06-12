---
title: "Google Chrome Sharing Settings/Bookmarks/Tabs for Ubuntu/Win7 dual boot"
date: 2010-05-29
forum: General Help
---

### Post by LookUpSeeBlu on 2010-05-29
Hello,

I have a dual boot Windows 7 & Ubuntu 10.04 system.  I have a shared partition that I store data on so it is accessible to both systems.  Is there a way to point Google Chrome to a spot on this drive in both systems for settings, bookmarks, and previous/pinned tabs?  I keep a number of tabs open all the time that I use on a daily basis and I find myself booting into one over the other just because I used it last....  Is there a way to share this between both systems so the tabs I left open when using Windows 7 will be the ones opened up when I launch Google Chrome in Ubuntu?

Thanks for any advice!

Kevin

---

### Post by alem189 on 2010-05-29
You might want to use xMarks, which is an addon that can put your bookmarks/tabs on a server and sync them every time you use Chrome. I don't know about settings, though.

---

### Post by LookUpSeeBlu on 2010-05-30
Thanks!  I'll check that out.  The main thing I am hoping is for my last opened and pinned tabs.  I have about 15 sites open that I use constantly and if I have been working in one OS (Win7 a lot frequently unfortunately) I feel "unmotivated" to boot into the other one knowing I have to pull up the tabs (which change due to projects I am working on and what I am researching).

Thanks very much!

Kevin

---

### Post by lovinglinux on 2010-05-30
> **LookUpSeeBlu said:**
> Thanks!  I'll check that out.  The main thing I am hoping is for my last opened and pinned tabs.  I have about 15 sites open that I use constantly and if I have been working in one OS (Win7 a lot frequently unfortunately) I feel "unmotivated" to boot into the other one knowing I have to pull up the tabs (which change due to projects I am working on and what I am researching).

Thanks very much!

Kevin

Chrome has an option to sync bookmarks and tabs.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=158803&stc=1&d=1275239100[/IMG]

---

### Post by PGuk on 2011-03-25
Hi, 

I know this is an old thread, but I've used a slightly different method that might interest others. Basically I've used a separate partition to hold the default profile (which mounts automatically on start-up) and created a symbolic link to access it.  I've written down everything that I did and it seems to work perfectly - but obviously its attempted at your own risk.  There's no synchronisation server involved, and my bookmarks, tabs and history are all shared successfully and updated between Win7 and Ubuntu. 

You can read more [here]("http://www.paulgarside.co.uk/2011/03/shared-chrome-profile-for-win-7-and.html").

---

