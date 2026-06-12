---
title: "file permission"
date: 2009-08-22
forum: General Help
---

### Post by AmerNewbieInDE on 2009-08-22
when i boot my pc, i get an error for permission..

it says..
users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permission. User's $HOME directory must be owned by user and not writable by other users.

I have changed permission on the file, tried <sudo chmod 644 /home/william/.dmrc> but i still get the error.. what am i doing wrong..

---

### Post by michy99 on 2009-08-22
Also, make sure that you are the owner.```
sudo chown william:william /home/william/.dmrc
```

---

### Post by drs305 on 2009-08-22
Here is a guide I wrote a while back for solving .dmrc issues:
[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?p=6161267")

Just follow it step by step. Near the end is a quick summary if you don't want to read through the entire post.

---

