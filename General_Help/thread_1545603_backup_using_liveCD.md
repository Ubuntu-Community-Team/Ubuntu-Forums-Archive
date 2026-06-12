---
title: "backup using liveCD"
date: 2010-08-04
forum: General Help
---

### Post by Hajex on 2010-08-04
Hi everyone ..
 can I backup ex4 filesystem using 8.04 LiveCD  using commands??
Because I couldn't access using the current 10.04 liveCD

---

### Post by ajgreeny on 2010-08-04
What do you mean by backup?  If you simply want to backup some user files (docs, music, photos etc) you can do it easily as long as you have a disk attached to drop the files on to.

When you couldn't access using the live CD, what do you mean exactly?  You should be able to mount any partition using the live CD, and the only possible problem could be with file permissions not allowing you to copy them to another disk or partition.  If that is the problem, you can either use the terminal to copy, or simply start nautilus from the terminal with the command ```
gksudo nautilus
```  No password will be required in the live CD, but the window that opens will allow you to move things as root, and permissions will not be a problem.

---

### Post by Hajex on 2010-08-04
NO I can't copy it easily since I'm using ex4 filesystem which is not supported by ubuntu 8.04 LiveCD .
When I try to access home folder  it gives me msg that ex4 is not supported .

---

### Post by ajgreeny on 2010-08-04
Sorry, I didn't notice the 8.04 live CD reference.  I think you will need to download a live CD that does support ext4, and if you don't want to bother with the 690MB download of ubuntu, try puppy linux, which should do the job and is only about 100MB.

---

### Post by Hajex on 2010-08-04
Thanks ajgreeny , 
I tried 9.10 and 10.04 ubuntu liveCD but they didn't work as well . 

Let me try puppy linux .. Thanks so much sir

---

### Post by ajgreeny on 2010-08-04
I am very surprised that you can not do this with either a karmic or a lucid live CD, both of which have full ext4 support.  What exactly is the problem when you try to backup or copy files to your destination folder?  Can you show any error messages you see.

---

### Post by Hajex on 2010-08-05
it's a problem of " GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)" msg which prevent me from login to ubuntu 10.04 or using its LiveCD .

I tried to access home folder by " gksudo nautilus " and I found in home folder  2 files  one of them is read me " you don't have permission to access private data"  and the other is unknown file . 

So any way to backup ??

---

### Post by ajgreeny on 2010-08-05
> **Hajex said:**
> it's a problem of " GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)" msg which prevent me from login to ubuntu 10.04 or using its LiveCD .

I tried to access home folder by " gksudo nautilus " and I found in home folder  2 files  one of them is read me " you don't have permission to access private data"  and the other is unknown file . 

So any way to backup ??
I have no idea what this GLib-WARNING is all about, so can not help there.  Was that from puppy linux?  Perhaps users in puppy have a different uuid number than in ubuntu.

As for the contents of home; just 2 files, really?  Are you sure that was not the live CD's own home?  You need to mount your installed version partition and then look in /home/username to see what you are looking for.

If that is what you already have done, I am completely befuddled and don't know where else to go.

Two thoughts!
1.  I presume you home is not encrypted, as that could cause all sorts of problems when you try to read the files.
2.  Have you set a separate /root password in the ubuntu that you are trying to backup?

---

### Post by Hajex on 2010-08-05
yes I mounted to /home/hajar . What I found is that 2 files ..doing that by ubuntu 9.10 LiveCD . 

See what is displayed ..I have pw on root of ubuntu 
[IMG]http://i37.tinypic.com/ei2s80.png[/IMG]

---

### Post by rubylaser on 2010-08-05
Try this...
[http://www.linux-mag.com/id/7568/3/]("http://www.linux-mag.com/id/7568/3/")

Hope that helps.

---

### Post by Hajex on 2010-08-16
Thanks [U]rubylaser .. I could copy files but not all of them

Thnnks so much
[/U]

---

