---
title: "Random beginner questions."
date: 2010-01-02
forum: General Help
---

### Post by Cityscape on 2010-01-02
Hi I'm a beginner and I have a few random questions.

1. How do I add a shortcut for a document or folder to the desktop or top panel?
2. I have multiple hard drives/partitions, when I delete a file from them it tells me "Cannot move file to trash, do you want do delete it immediately? The file [file name] cannot be moved to trash". Why cant they be deleted to trash? How do i make it so they can?
3. How do I add a delete button to the top bar (where the back, up & reload buttons are) of nautilus?
4. are there any decent On-demand virus scanners (meaning a scanner that just scans a file when I ask it to, and doesn't always run in the background) that i can use on ubuntu. It would be nice if it could scan for both Windows and Linux viruses.

---

### Post by xtjacob on 2010-01-02
1. Just drag it up to the top.
2. I think it might have to do with permissions. Is it windows or linux partitions?
4. Avast, or clam-AV

---

### Post by Cityscape on 2010-01-03
> **xtjacob said:**
> 
1. Just drag it up to the top.
2. I think it might have to do with permissions. Is it windows or linux partitions?
4. Avast, or clam-AV

1. What about for the desktop?
2. One is a Windows partition and the other is a documents drive. both have them same problem.
3. ???
4. Thanks ^_^

---

### Post by xtjacob on 2010-01-03
1. You can make a link of it and copy it to your desktop.
2. If they are formatted as NTFS then Ubuntu mounts it as read only. You can try this: [http://ubuntuforums.org/showthread.php?t=615166](http://ubuntuforums.org/showthread.php?t=615166)
3. You can follow [this]("http://ubuntuforums.org/showthread.php?t=659294") guide on how to add copy, cut, paste, and delete to the toolbar. If you want to edit it you basically have to edit nautilus-navigation-window-ui.xml. Run this command to edit it. ```
sudo gedit /usr/share/nautilus/ui/nautilus-navigation-window-ui.xml
```

---

### Post by chewearn on 2010-01-03
When you edit "nautilus-navigation-window-ui.xml" you don't have to restart gnome to effect the changes.  Just open a terminal and run:
```

killall nautilus

```

and Nautilus will restart with the changes.

---

### Post by Cityscape on 2010-01-04
> **xtjacob said:**
> 2. If they are formatted as NTFS then Ubuntu mounts it as read only. You can try this: [http://ubuntuforums.org/showthread.php?t=615166](http://ubuntuforums.org/showthread.php?t=615166)

1. complete, thanks
3. complete, thanks
4. complete, thanks

The link was quite old. The person having the problem was using Ubuntu 6.xx version.
[Wikipedia states]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_7.10_.28Gutsy_Gibbon.29"): [QUOTE=]Ubuntu 7.10 included several new features, among them...full NTFS support (read/write) via NTFS-3G[/QUOTE]
They solved it by installing NTFS-3G. My Ubuntu 9.04 already has NTFS-3G on it. 

So I'm still confused as to the problem!

---

### Post by Strongman332 on 2010-01-04
2. install 'ntfsprogs'

---

