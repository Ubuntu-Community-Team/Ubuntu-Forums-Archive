---
title: "Greek letters in a vfat partition"
date: 2006-03-01
forum: General Help
---

### Post by Zalbor on 2006-03-01
I have a vfat partition where windows 98 is installed, and several of the directories have greek names. The problem is in choosing a charset to see them correctly.
If I write **iocharset=utf8** in fstab, they appear correctly. But the system warns me at startup that "utf8 isn't a good charset for vfat, as the filesystem becomes case-sensitive". And I've noticed that if I create a directory or file with all capital letters, it disappears from nautilus and reappears with lower-case name if I reload.
I tried **iocharset=iso8859-7** (which I know to be a greek encoding) but it doesn't work, the letters appear as question marks.
I tried **iocharset=iso8859-7,codepage=737** (737 is the codepage win98 uses for the letters) but not only they still appear as question marks, they have the words "invalid encoding" below them.
I tried just **codepage=737** but it's question marks again.

Does anyone have an idea what the correct way to mount it is? Thank you.

---

### Post by lha on 2006-03-01
Have you tried utf8? I don't mean iocharset=utf8, but just utf8. I don't have greek characters in filenames, but umlauts, and they work fine.

---

### Post by Zalbor on 2006-03-01
Yes -this works correctly, thank you! :D
I didn't think it would make a difference, really. I thought it was the same, just in a more "proper" way of setting it.

---

