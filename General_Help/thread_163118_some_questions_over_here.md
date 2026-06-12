---
title: "some questions over here"
date: 2006-04-20
forum: General Help
---

### Post by canci on 2006-04-20
](*,)   I am a bit desperate. Whenever I install Ubuntu, I set a hostname, but in /etc/hostname the name "localhost" prevails. When doing sudo command, it says  "cannot look up host by name" (not the exact way it's said, but like this). I fixed it by stopping X, logging in as root and editting /etc/hostname. !HOWEVER! my other username is not in the sudoers list! So here are my q's:

1. Since it's very complicated, PLS just tell me briefly, how to add eg. "canci" as a sudoer.

2. Was that hostname confusion the problem? If yes, any1 else encountered this? Or am I the only one? Could you fix that if it's a widespread phenomenon?

3. Since I have a very old PC, is it recommendable to use the latest kernel w/it? I had no hardware problems except some failed autodetection which I fixed. Would an earlier version be faster/slower? I managed to compile a kernel on my own on my other old RedHat 6 Linux, and I have the HOWTO for Ubuntu.

TNX in advance ;D

---

### Post by sYs^ on 2006-04-20
1: add user "canci" to group "admin", I think it'll help.

---

### Post by m.musashi on 2006-04-20
Localhost refers to your network, specifically a loopback (I believe), and not a system user. When you set up your first user (canci for example) that user has admin rights via sudo.

If I missed the point, please let me know.

---

### Post by Al3xanR0 on 2006-04-20
[QUOTE=canci]](*,)   I am a bit desperate. Whenever I install Ubuntu, I set a hostname, but in /etc/hostname the name "localhost" prevails. When doing sudo command, it says  "cannot look up host by name" (not the exact way it's said, but like this). I fixed it by stopping X, logging in as root and editting /etc/hostname. !HOWEVER! my other username is not in the sudoers list! So here are my q's:

1. Since it's very complicated, PLS just tell me briefly, how to add eg. "canci" as a sudoer.

2. Was that hostname confusion the problem? If yes, any1 else encountered this? Or am I the only one? Could you fix that if it's a widespread phenomenon?

3. Since I have a very old PC, is it recommendable to use the latest kernel w/it? I had no hardware problems except some failed autodetection which I fixed. Would an earlier version be faster/slower? I managed to compile a kernel on my own on my other old RedHat 6 Linux, and I have the HOWTO for Ubuntu.

TNX in advance ;D[/QUOTE]

open console (as root) or run visudo command added the following line :

canci    ALL=(ALL) ALL

F3 edit  file name to /etc/sudoers

enter-> y (to overwrite)

ctrl + x to exit

hope this helps

---

