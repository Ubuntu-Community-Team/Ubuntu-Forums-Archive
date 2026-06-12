---
title: "How to: Keep Chromium Bookmarks if &quot;Export&quot; is not accessible"
date: 2011-03-26
forum: General Help
---

### Post by hakermania on 2011-03-26
OK, I know that it is quite simple, and many of you may already have found it, but, I had a similar problem lately, when a friend of mine had a kernel problem and wanted to reinstall from scratch ubuntu, keeping his chromium bookmarks.
The only access to the PC, was through terminal, using Alt+Ctrl+F1, so assuming that you, at least, have access to the PC through a terminal, either the way described above, or by a live CD, both would work.

Please, do not follow this guide if you have access to chromium, because by default it has an option for exporting/importing bookmarks.

**Ctrl+Alt+F1 way: **(means that you have access to the PC, but not to your Desktop)
After pressing these keys, you'll be asked your login and passwd. Give both.
insert a USB, it will be mounted manually to /media/ folder. So, then, type
```
cp ~/.config/chromium/Default/Bookmarks /media/NAME
```**Live CD way: **(means that you don't have any access to the PC by default)
Mount the partition, open a terminal and give
```
cd /media/Disk_NAME(usually something like a hash)/home/user/
```then type
```
cp .config/chromium/Default/Bookmarks ~/Desktop
```This will copy the neeeded file to LIve CD's Desktop. Copy it to a USB.

**Both:**
After this, in your new installtion, just replace the same file  (~/.config/chromium/Default/Bookmarks) with the one you back-uped to your USB.
Restart chromium and the Bookmarks will be there.
This worked both for 10.10and 11.04 beta.

Hope this will help somebody...

---

