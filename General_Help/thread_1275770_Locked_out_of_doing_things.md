---
title: "Locked out of doing things"
date: 2009-09-26
forum: General Help
---

### Post by swedski on 2009-09-26
Hello,
Having been using ubuntu 8 for about a while and liked it.  Redid my computer and thought ok I'll go up to 9.  I'm here it is generally working until I want to do anything like partition a disk or copy things to a usb disk.
I hooked up a usb drive (an old wd160 ) and was going to back up something from my network drive (which by the way must be connect to every time and that connection time takes at least 5 minutes, that the next post)and it tells me I don't have permission to do this.  I try adding administrative rights to my user and it still gives me grief.  This is silly.  I am the only one who uses this machine in my house and yet there is no why for me to log in to the gui as root so I can do as I please.  Isn't that the point of a home PC

---

### Post by scouser73 on 2009-09-26
**1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your new drive, **Right Click**, select the **Permissions** tab 

**3** - Change the **Owner** drop-down menu to your name, then change **Folder Access** to **Create & Delete Files**, then **File Access** to **Read & Write**, then **Group** to your name, **Folder Access** to **Create & Delete Files**, **File Access** to **Read & Write** then click **Apply Permissions To Enclosed Files**.

You will now have full access to your drive.

---

### Post by 3rdalbum on 2009-09-26
I should clarify this:

> **scouser73 said:**
> **1** - Go to **Terminal**, copy & paste this command: **gksudo nautilus** that will open Terminal as root

**2** - Navigate to your new drive's folder in /media, **Right Click** the folder icon, select the **Permissions** tab 

I must say I've never had to do this with an external drive, so I'm not sure why you're getting Permission Denied. Usually it gets mounted read/write for you automatically.

---

### Post by swedski on 2009-09-26
Thanks that worked

---

