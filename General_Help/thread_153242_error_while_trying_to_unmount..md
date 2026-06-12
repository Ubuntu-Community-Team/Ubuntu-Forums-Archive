---
title: "error while trying to unmount."
date: 2006-03-31
forum: General Help
---

### Post by Felix21685 on 2006-03-31
hey guys 2 days ago or so i tried chapter 5 windows partitions of the ubuntu guide.

i followed the steps to a T.

it didn't work..dont know if it was because my drive is a sata..

i made sure to mount my sata which is /dev/sda

now when i try to unmount it so i can try the following guide:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

i get this:
```
felix@ubuntu:~$ sudo unmount /media/windows/
sudo: unmount: command not found

```

any help on this is as always appreciated :D

---

### Post by ispmarin on 2006-03-31
just little typo... is umount, not unmount... :mrgreen:

---

### Post by Felix21685 on 2006-03-31
hey thanks ivan.. still have to get used to the linux lingo.

maybe u can help me with this now lol
i dont get why i cant mount or unmount my windows sata drive```
felix@ubuntu:~$ sudo umount /media/windows/
umount: /media/windows/: not mounted
felix@ubuntu:~$ sudo mount /dev/sda /media/windows
mount: you must specify the filesystem type
felix@ubuntu:~$ sudo mount /dev/sda /media/windows/ -t ntfs -o umask=0222
mount: /dev/sda already mounted or /media/windows/ busy
felix@ubuntu:~$

```

---

### Post by ispmarin on 2006-03-31
err.. I think that again is just another typo... you have to pick a partition on /dev/sda. like /dev/sda1, or /dev/sda2 etc...this should work.

---

### Post by Felix21685 on 2006-04-01
well ill be darned :)
your right..

didnt know it had to be sda1.
thanks again for the help!

---

### Post by ispmarin on 2006-04-01
You are welcome!

---

