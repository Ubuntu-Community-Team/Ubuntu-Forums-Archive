---
title: "IceAuthority file."
date: 2010-04-12
forum: General Help
---

### Post by SidZ on 2010-04-12
Hello, everytime I boot up, I get this error about my ICEauthority file thing not working. Any answers or solutions?

---

### Post by SidZ on 2010-04-13
Bump

---

### Post by philinux on 2010-04-13
Hi. This might help.

[http://ubuntuforums.org/showpost.php?p=6433832&postcount=2](http://ubuntuforums.org/showpost.php?p=6433832&postcount=2)

Please try to use the forum search.

As mentioned in that post you must substitute user for your username also note that the command is case sensitive.

Write them down carefully or print them off first.

---

### Post by Kobalt on 2010-04-14
Did you set up an encrypted home directory during your install ? Did you change your login password after that ?

---

### Post by mjcritchie on 2010-04-20
I have had the same problem twice, both times after updating (currently running 64bit Karmic).

Tried various solutions on the net, but this is the only one that worked for me:

Open a terminal and run:

> sudo chown -R user:user /home/user/.*

Where user is your user_name. This should change ownership of all the hidden files and directories in your home directory to: user:user, as they should be.

This comes courtesy of tommcd over at [this]("http://www.linuxquestions.org/questions/ubuntu-63/karmic-9-10-with-separate-home-partition-caused-could-not-update-iceauthority-798084/") post on LinuxQuestions.org

---

