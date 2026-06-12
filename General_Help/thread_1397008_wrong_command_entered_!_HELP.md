---
title: "wrong command entered ! HELP"
date: 2010-02-02
forum: General Help
---

### Post by konsta82 on 2010-02-02
I have Carmic on Dell inspiron.
I wanted to make link from tmp directory to desktop so I entered 
**[B]sudo chmod 666 /tmp**[/B]

Everything stopped working and I'm in recovery mode now.
On restart I got
THERE IS A PROBLEM WITH THE CONFIGURATION SERVER (/USR/LIB/LIBGCONF2-4/GCONF-SANITY-CHECK-2    EXITED WITH STATUS 256)

Can I undo chmod command somehow ?

---

### Post by konsta82 on 2010-02-02
Please give me some ideas , I don't want to reinstall ubuntu bcs of this

---

### Post by Iowan on 2010-02-02
On my Karmic machine, */tmp* is **drwxrwxrwt**(1777?) Will recovery mode let you **chmod** it back?

---

### Post by ankspo71 on 2010-02-02
Hi,
According to the stat command on my Ubuntu Lucid testing release
the /tmp directory is 1777  (read access, write access, executable, with sticky bit directory flag).

So try
```
sudo chmod 1777 /tmp
```For comparison purposes,  here is the output of my "stat /tmp" command
james@Lucid:~$ stat /tmp
  File: `/tmp'
  Size: 4096          Blocks: 8          IO Block: 4096   directory
Device: 801h/2049d    Inode: 1310722     Links: 11
Access: (1777/drwxrwxrwt)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2010-02-02 17:16:19.717362049 -0500
Modify: 2010-02-02 18:58:58.371617082 -0500
Change: 2010-02-02 18:58:58.371617082 -0500

---

### Post by konsta82 on 2010-02-02
YES

I entered chmod 1777 /tmp after login and everything is OK now

Thank you guys !!!

By the way,how to make link from /tmp to desktop without chmod ?
I need that for easy saving of youtube videos ?

---

