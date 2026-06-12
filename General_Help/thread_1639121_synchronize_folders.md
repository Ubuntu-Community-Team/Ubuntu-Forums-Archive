---
title: "synchronize folders"
date: 2010-12-06
forum: General Help
---

### Post by DrScum on 2010-12-06
I have done some research regarding possible options to synchronize folders between laptop and desktop.

Here is what I want to do: at the end of the day synchronize the work I'd done during the day on my laptop with a mirror folder on the desktop in order to keep the work safe.

I've tried rsync, unison-gtk, keep, Grsync, back in time and what not but I keep having trouble with permissions and connections. 


Isn't there a solution out there which the terminal unexperienced user can manage?

---

### Post by gandaran on 2010-12-06
I would use ubuntu one for that and forget all the backup applications, but you will need a fast internet and probably an unlimited internet connection.

---

### Post by oldfred on 2010-12-06
I did this with my portable only when we traveled. Between Windows updates and Ubuntu updates and only traveling occasionally, I had issues getting Samba to work. I had Ubuntu on Desktop and WinXP on portable. I decided I did not need XP and just converted to Ubuntu on portable and changed to NFS. I installed both server & client on both machines.

I just have to add some settings to /etc/exports and  run a couple of scripts, one to mount my data folders and the other to rsync.  I have to use scripts as I have reinstalled Ubuntu every 6 months and do not travel that much that any settings are preserved.

HOWTO: NFS Server/Client if no windows 
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by Matt West on 2010-12-06
I use DirSyncPro to sync my files between external drives, my desktop, laptop, memory stick and pretty much everything tbh. It's got a GUI which makes things a lot easier than having to run commands from terminal all the time.
You can get it here:
[http://www.dirsyncpro.org/]("http://www.dirsyncpro.org/")

---

### Post by Matt West on 2010-12-06
One thing I would add if you use DirSyncPro is when you set up a sync job remember to write timestamps back to the synchronized files (the options under the advanced tab in set-up) otherwise problems can occur when you do an 2 way sync.

---

### Post by mlentink on 2010-12-06
> **gandaran said:**
> I would use ubuntu one for that and forget all the backup applications, but you will need a fast internet and probably an unlimited internet connection.

+1

Either Ubuntu One or, if you absolutely must use Windows-machines, Dropbox, which runs on both, pretty seamlessly.

---

### Post by jbeiter on 2010-12-06
ubuntu one isn't ready yet. I've tried to implement it twice and it's flaky as hell. At best, doesn't deliver.

---

### Post by gandaran on 2010-12-06
> **jbeiter said:**
> ubuntu one isn't ready yet. I've tried to implement it twice and it's flaky as hell. At best, doesn't deliver.
I do agree ubuntu one still does have some problems, I have yet to get firefox bookmarks backup to work but the rest is working very well including any folder synchronization between desktop and my netbook, my only problem is the 2GB internet monthly plan, so most of the time ubuntu one is disabled here.

---

### Post by buddyd16 on 2010-12-06
Set up a samba share on both computers then just use the copy command in the terminal with the update and recursive option after you have mounted the shared folder on either the desktop or laptop.
 
From laptop to desktop:```
 cp -r -u laptop directory desktop directory
```
From desktop to laptop:```
 cp -r -u desktop directory laptop directory
```

the recursive option will go through any sub folders in the specified directory and grab any updated files. If you don't have any sub folders you can leave out the "-r" in the above.

---

### Post by lrgmmc on 2010-12-06
what errors were you having with rsync?
i have always used rsync over ssh woks like a charm.

---

### Post by Benchrest on 2011-01-01
I have been using Unison for about 8-9 months and am happy with it. It is not automatic as I must run it each time but that is the way I want it. I sync between my laptop and desktop. Both are dual boot. I keep all my own data, don't have it sitting on someone else's server. About once a month I back up to DVD's. 
I use a number of profiles with Unison.  The main profile is for Our Documents folder which has most of my stuff including financial in it. This I synchronize daily or multiple times.
I also have a profiles for pictures, music, email, bookmarks etc. that are synced less frequently as changes occur.
It also works to synchronize between my dual boot windows systems.  I edit my web pages from Ubuntu but use Unison to move to windows to publish with frontpage. (no, there is no other option to a server with frontpage extensions)

---

