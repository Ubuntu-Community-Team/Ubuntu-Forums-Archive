---
title: "What went wrong?"
date: 2009-08-26
forum: General Help
---

### Post by designateduser on 2009-08-26
so earlier this week I ran the command 
$ sudo apt-get install kubuntu-desktop
and installed Kubuntu to try it out, and after a while decided to get rid of it, so I entered 
$ sudo apt-get autoremove kubuntu-desktop
and after a restart I found that GRUB bootloader had a new entry called:
 {whatever kernal} TS (I forget exactly)
 and generic which is my current working one. I was surprised to find that all the Kdesktop programs were still in my applications folder though, so what did I do wrong?:-k

---

### Post by dmonkey on 2009-08-26
I don't know about the kernel issue (possible a new kernel was installed since you had last restarted?) but the problem with kubuntu-desktop is that removing it will not remove all of the programs that came with it, despite your use of autoremove.

You can try again with autoremove:

sudo apt-get autoremove

or you can look in the history of what was installed by looking at /var/log/dpkg.log:

cat /var/log/dpkg.log | grep "install "

and then remove the extra installed files manually (or parse the log file in a clever way :)

---

