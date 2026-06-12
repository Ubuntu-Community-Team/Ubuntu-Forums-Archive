---
title: "Question Bombardment"
date: 2010-12-06
forum: General Help
---

### Post by 0949er on 2010-12-06
haha anyway, quite a few questions, figured people could answer a few of the ones they might know. Here we go:

How do I:

1) make openssl startup on boot without my default user having to actually log on first

2) open a process on a specfic display. for example, 
```
remote_connection@me:~/: rhythmbox > tty7 (does not work)
```3) is it possible to have one "master" sudo password that all users use (in the sudoers group) so that even though a user has permission to use "sudo", they still need to know the UNIQUE password (and not their actual user password)?

4) **BONUS QUESTION**: What is the coolest thing you can do with the command line (and no x display)? For example, remote reboot.

Thanks guys. Pick and choose if you want :)

---

### Post by 0949er on 2010-12-07
bump please, its been almost 12 hours :)

---

### Post by Frogs Hair on 2010-12-07
1-3. From Administration > Users and Groups you could set up an  account for all users  with sudo permissions.  From  Administration > Login screen , set the account to log in automatically . This will require you to make one password . Be sure you trust the users with sudo permissions prior to doing this.

2. I don't understand the question ( have not used remote desktop settings) . You can open applications in another work space with the workspace switcher. (See preferences  > remote desktop)

4. The coolest thing you can do is limited by your imagination , script writing knowledge , and the operating system.  :p

---

