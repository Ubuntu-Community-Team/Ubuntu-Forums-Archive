---
title: "dual opening of 2 hard drives at once"
date: 2009-09-14
forum: General Help
---

### Post by john pilcher on 2009-09-14
My laptop/notebook has been split into 2 drives - "c" which had XP re-installed first (several months back) & "d" which had Ubuntu 9.04 installed 2 weeks ago. Everything went fine with both however, i now find the need to open both simultaneously. Can anyone give me a helping hand. Note : i am new to Ubuntu & don't know how to use the "command line" yet, or where it is.

thanks
John

---

### Post by P4man on 2009-09-14
Xp can't read ubuntu's filesystem, but the other way round is possible.
Usually, you don't need to do much if anything. Just go to Places, there look for the first harddisk (could be called something like "50GB filesystem") and click it to open it.

If that doesnt work, you'll need the dreaded command line :)
Go applications > accessories > terminal

and type in:

```
sudo fdisk -l
```

(last letter is a lowercase L)
copy paste the result here

---

### Post by john pilcher on 2009-09-18
Thanks for your help was able to view both drives via Places etc.

---

