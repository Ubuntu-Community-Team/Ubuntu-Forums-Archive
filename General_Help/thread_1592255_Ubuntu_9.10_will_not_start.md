---
title: "Ubuntu 9.10 will not start"
date: 2010-10-10
forum: General Help
---

### Post by BBWin3 on 2010-10-10
Hello All, Just in case the thread **"Ubuntu won't load anymore"** is closed....
 
I am creating a new thread here."_Ubuntu 9.10 will not start_"
 
 
I am another nubie to Ubuntu 9.10. I had exactly the same problem as Teclas5.
I performed all of the same inputs suggested by Rubi1200. Including error fixes which 
got me back to the boot menu.THANK YOU for that!.
 
Now after starting machine then selecting the first (at the top, Unbuntu 9.10 kernel 
2.6.31-22) to boot from,
  my machine boots to blank screen. after a bit of time it then it echos back the 
following:
 
upsplash: using mode 1024 x 768
Mount: mounting /dev/disk/by-uuid/e760a<long i.d. number.....> a48beaf /on /root
Failed: invalid argument
Mount: Mounting /sys on /root/sys Failed No Such file or Directory.
Mount: Mounting /dev on /root dev Failed No Such file or Directory.
Mount: Mounting /sys on /root/sys Failed No Such file or Directory.
Mount: Mounting /proc on /root/sys Failed No Such file or Directory. 
 
Target file system doesnt have /sbin/init
No init found Try passing init = bootarg
 
BusyBox v. 1.13.3 (Ubuntu 1:1,13,3-1 ubuntu7) built-in shell (ash)
Enter 'help' for list of built-in commands
 
initramfs>
 
So I tried the following:
 
initramfs> init = bootarg
 
/bin/sh: init: not found
 
Any possible help would be most appreciated.
 
-Terri,
<BBWin3>

---

### Post by mörgæs on 2010-10-10
Hi, please post your question in the other thread. One does not know which advice you have already received, if you open a new thread.

---

### Post by BBWin3 on 2010-10-16
Yes. I did so. Unfortunately NO ONE has helped me.

---

### Post by mörgæs on 2010-10-16
I can see that Rubi is helping in the other thread, so you are in good hands!

---

### Post by BBWin3 on 2010-10-18
YES! Rubi is Very helpfull I am stopping this thread, Newbie mistake.
 
Thanks to all!!
 
-Terri

---

### Post by mörgæs on 2010-10-19
Good, then please mark this one 'solved'.

---

### Post by BBWin3 on 2010-10-24
I have not been able to find out how to mark this thread as solved.
Can someone advise.
-

---

### Post by mörgæs on 2010-10-24
It is in the 'thread tools' menu.

---

