---
title: "Evolution started hanging on MH folder"
date: 2010-06-20
forum: General Help
---

### Post by katiad on 2010-06-20
Just today, I came home, having left Evolution running all day, to find it frozen and unresponsive. I killed it, opened it back up... and same thing. It opens, checks through my folders (I have one imap account, and one MH folder that Evolution dumps my pop mail into.) and freezes.

In the status bar, when it freezes, this is what it's doing:

Opening folder mh:///home/katia/mail;command=ssh%20-C%20-l%20%25u%20%25h%20exec%20/usr/sbin/imapd#inbox(...)

And then it just hangs. 

Any idea what went wrong? If I disable my MH folder real quick, it doesn't hang and I can use my imap account fine. Re-enabling my MH folder quickly causes the hang again. 

I tried opening the MH folder in clawsmail, but it hung also. Mutt was able to open it fine.

How can I fix this???

---

### Post by dcstar on 2010-06-20
> **katiad said:**
> Just today, I came home, having left Evolution running all day, to find it frozen and unresponsive. I killed it, opened it back up... and same thing. It opens, checks through my folders (I have one imap account, and one MH folder that Evolution dumps my pop mail into.) and freezes.

In the status bar, when it freezes, this is what it's doing:

Opening folder mh:///home/katia/mail;command=ssh%20-C%20-l%20%25u%20%25h%20exec%20/usr/sbin/imapd#inbox(...)

And then it just hangs. 

Any idea what went wrong? If I disable my MH folder real quick, it doesn't hang and I can use my imap account fine. Re-enabling my MH folder quickly causes the hang again. 

I tried opening the MH folder in clawsmail, but it hung also. Mutt was able to open it fine.

How can I fix this???

[LIST=1]
[*]Are you using a 32-bit version?
[*]Is that folder now over 2GB in size?
[/LIST]

---

### Post by katiad on 2010-06-20
I am using the 64 bit version of Lucid, and I assume the evolution that comes with it is 64 bit. Also, the folder is not over 2gb in size, either. It was at 1.7 - I moved some folders out to test, and even at 280mb (just the inbox) it still hangs.

I tried renaming the .evolution folder. No luck, so I put it back...

---

### Post by katiad on 2010-06-20
I just noted that /usr/sbin/imapd doesn't exist. This might be a problem?

---

### Post by katiad on 2010-06-20
I fixed it. :) I found the folders.db file in the main mail folder and renamed it. That solved the problem. It was evidently corrupted somehow.

For anyone else in the future with this issue: there is more than one folders.db file. I tried deleting the one in the inbox itself, since that was where I thought the corruption was, but that wasn't the problem in my case. It was the main folders.db file in the top level mail folder.

---

