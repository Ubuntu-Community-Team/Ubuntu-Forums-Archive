---
title: "Open folder in Firefox error"
date: 2011-10-23
forum: General Help
---

### Post by Feilin on 2011-10-23
I've encountered an interesting problem that has emerged gradually. It consist of when I right click and choose "Open folder" for downloaded files in Firefox (from that little download window), they're always opened in VLC. By gradually I mean that this only happened for certain file types at first, but now it seems to do this with all file types.

Since VLC can't handle anything but audio and video files, I only get a VLC window and the error window which tells me it can't play the files. What has gone wrong (could this be a virus?), and more importantly, how do I fix this so I open the folder in the file browser instead?

---

### Post by mc4man on 2011-10-23
If you post the contents of this file will fix up for you or you can fix yourself
```
gedit ~/.local/share/applications/mimeapps.list
```
Look for inode/directory= lines, change nautilus-folder-handler.desktop to 
nautilus-home.desktop

The file can also just  be deleted & it will be re-created, if you aren't using any 'custom commands' then that's a decent way
```
nautilus ~/.local/share/applications/
```
delete mimeapps.list

---

### Post by Feilin on 2011-10-23
Worked like a charm, thanks!

Bonus question: why did Nautilus suddenly decide it thought I wanted to open stuff in VLC (especially since I'd had it for a while and it was as such not caused by me changing default applications)?

---

### Post by mc4man on 2011-10-24
> **Feilin said:**
> Worked like a charm, thanks!

Bonus question: why did Nautilus suddenly decide it thought I wanted to open stuff in VLC (especially since I'd had it for a while and it was as such not caused by me changing default applications)?

That would of depended on the contents of mimeapps.list & whether you did an upgrade to 11.10 or fresh install. 

When opening a folder from the r. click contest menu an entry to the inode/directory line is added to the front for that app if it's not already there in the [Added Associations] section

In 11.10 the is no inode/directory line in the [Default Applications] section.(not needed on a fresh install) If you had done an upgrade from 11.04 to 11.10 then you'd have already had a line in place there pointing to a .desktop that doesn't exist. In that scenario then the 1st listed on the line in the [Added ...] section would be used  by Firefox instead of nautilus
There are a few other scenarios same basic idea. 

You can also usually fix this by just deleting mimeapps.list & letting a new one be created.

bug on
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876788](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/876788)

---

