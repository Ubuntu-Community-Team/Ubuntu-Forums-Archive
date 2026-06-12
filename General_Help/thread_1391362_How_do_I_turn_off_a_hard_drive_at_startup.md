---
title: "How do I turn off a hard drive at startup?"
date: 2010-01-26
forum: General Help
---

### Post by jfeng on 2010-01-26
So i am a totally new to linux.

I have two hard drives and I want to shut down one of them when idle

I am using sudo hdparm -S60 /dev/sdb

Except I have to type it in every time i boot into ubuntu.

[U]How do i make it so that ubuntu automatically does that command on startup without typing it in every time?

[/U]I am using 9.10 64 bit.

---

### Post by sisco311 on 2010-01-26
Take a look at the /etc/hdparm.conf file.

You have to add something like:
```
/dev/sdb {
       spindown_time = 60
}

```
to the file.

---

### Post by steindor2 on 2010-01-26
1. create a new file
2. put the command for disconnecting the hard drive into the new file
3. right click on your file select allow running as executable
4. open up startup programs, select add new program and navigate to your file

you will now be asked to run this file when ubuntu starts up.

---

