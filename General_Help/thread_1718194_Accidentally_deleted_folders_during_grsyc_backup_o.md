---
title: "Accidentally deleted folders during grsyc backup on the destination hd."
date: 2011-03-31
forum: General Help
---

### Post by philnice on 2011-03-31
Well, i took a back up using grsync and stupid me, the "delete on destination" was enabled.
So, i lost some folders and files that i used to keep only on the receiver hd to keep my host clean.
Any chance i could retreive those data? Thanks.

---

### Post by cain071546 on 2011-03-31
probably not

but thats just my opinion

---

### Post by philnice on 2011-03-31
Well, i hope to receive some better news, although i understand this could be nearly impossible. Thanks for the reply.

---

### Post by wolfen69 on 2011-03-31
> **cain071546 said:**
> probably not

but thats just my opinion

Anything can be done with the right tools. I once had to restore a few 1000 jpegs. I used Macic Rescue to do this. It is in the repos. I'll post back in a few with an example of how to use this cli app.

Here you go: [Data Recovery]("https://help.ubuntu.com/community/DataRecovery")

For example, if you had jpegs to recover, you would run something like this:
```
$ magicrescue -r jpeg-jfif -r jpeg-exif -d ~/output /dev/hdb1
```

[Magic Rescue Manual]("http://www.irongeek.com/i.php?page=backtrack-3-man/magicrescue")

---

### Post by philnice on 2011-03-31
Never heard of that tool before, installed already. :) I will post back as soon as i have something since, i need to read the manual first. wolfen69, thanks a lot!

---

### Post by philnice on 2011-03-31
Wow that was really easy at last! After some more digging around the forum, i installed testdisk from the repositories, run it from terminal, found my usb hd on which the deleted files were, listed them, and then just copied one by one to my home folder... Wow... Thanks a lot guys!

---

