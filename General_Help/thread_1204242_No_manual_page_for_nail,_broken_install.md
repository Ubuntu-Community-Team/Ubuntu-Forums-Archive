---
title: "No manual page for nail, broken install?"
date: 2009-07-04
forum: General Help
---

### Post by kanngard on 2009-07-04
In my Ubuntu Server Jaunty Jackalope 9.04 I installed nail, to be able to send to my SMTP host:
```
sudo apt-get nail install
```
which worked fine. But when I try:
```
man nail
```
I get:
```
man: warning: /usr/share/man/man1/nail.1.gz is a dangling symlink
No manual entry for nail
```

The nail command works though. Anyone knows what the problem is? If I do:
```
ls -la /usr/share/main/man/nail*
```
I get:
```
lrwxrwxrwx 1 root root 13 2009-07-04 18:35 nail.1.gz -> heirloom.1.gz
```
and heirloom.1.gz does not exist, the only heirloom is:
```
-rw-r--r-- 1 root root 41552 2008-08-05 02:49 heirloom-mailx.1.gz
```
Are these the same?

---

### Post by cmost on 2009-07-04
Uh oh...did you break a nail?

Seriously, here are a few posts I found that might help...

[http://www.linux.com/archive/feature/51767](http://www.linux.com/archive/feature/51767)

[http://www.linuxquestions.org/questions/linux-server-73/syntax-using-nail-mailx-for-smtp-without-postfix-or-sendmail-560929/](http://www.linuxquestions.org/questions/linux-server-73/syntax-using-nail-mailx-for-smtp-without-postfix-or-sendmail-560929/)

[http://ubuntuforums.org/showthread.php?t=711212](http://ubuntuforums.org/showthread.php?t=711212)

---

### Post by kanngard on 2009-07-04
Thanks for your reply, but my question was regarding the missing/broken man pages. How to use nail is easily found searching the net.

---

### Post by cmost on 2009-07-04
Ahh.  I assumed you were looking for the man pages to solve a problem with nail.  I didn't realize the primary problem you were having WAS the missing man pages.  Sorry.

---

### Post by kanngard on 2009-07-04
No problem :) I guess to fix my problem, I have to download the man pages separately?

---

### Post by kanngard on 2009-07-15
Found an answer to the fault at:
[https://lists.ubuntu.com/archives/universe-bugs/2008-December/029207.html](https://lists.ubuntu.com/archives/universe-bugs/2008-December/029207.html)
and:
[https://bugs.launchpad.net/ubuntu/+source/nail/+bug/306725](https://bugs.launchpad.net/ubuntu/+source/nail/+bug/306725)
And i can confirm that the fix described worked perfectly:
```
rm -f /usr/share/man/man1/nail.1.gz
ln -s /usr/share/man/man1/heirloom-mailx.1.gz /usr/share/man/man1/nail.1.gz

```
I wonder what the reason is for not fixing this?

---

