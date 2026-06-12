---
title: "What is this?"
date: 2010-03-01
forum: General Help
---

### Post by Silvertones on 2010-03-01
When I double click on "filesystem" this file is in there. It's unknown but owned by ROOT.

---

### Post by 3rdalbum on 2010-03-01
Type the first word into the terminal, put a space with the spacebar, and then drag the file onto the terminal and run the result as a command. Then type the second word, etc:

file
less

The first will tell you what type of file it is, if possible. The second command will allow you to look at the file.

If it's a binary file (non-human-readable), then it might be there as the result of part of your filesystem going wrong. Look up a HOWTO about how to "fsck" your hard disk and do it, this should repair whatever damage (if any).

I don't think this file is worth *worrying* about. If it was malicious, then it wouldn't be in such an obvious place and it wouldn't look so odd.

---

### Post by Silvertones on 2010-03-01
BTW my install is WUBI.
I tried both things and it's unreadable.
I ran ```
sudo fsck
``` and it went through some things and asked me to answer "Y" to some things which I did. The file is still there. I would like it gone.

---

### Post by Silvertones on 2010-03-01
Can't someone help me with this?
Thanks

---

### Post by megamania on 2010-03-01
If all you want is to delete it, open the terminal and type
```
gksudo nautilus
```
navigate to the file, select it, hit the DEL key.

---

### Post by Silvertones on 2010-03-01
Thanks much>

---

