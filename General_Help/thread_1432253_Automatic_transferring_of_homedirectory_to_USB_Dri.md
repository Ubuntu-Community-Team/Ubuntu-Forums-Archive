---
title: "Automatic transferring of /home/directory to USB Drive"
date: 2010-03-17
forum: General Help
---

### Post by DarkGreen16 on 2010-03-17
I was hoping someone on the forum might be able to recommend a method of automatic backup from my hard drive to a usb drive when plugged in.

Basically I'll be constantly putting files in /home/downloads and I want it so when I plug in a NTFS usb drive it will automatically Cut(not copy) all the contents of that folder including other folders to my usb drive. Is there any well known programs that can do this?

I would prefer something that is in the repositories that is easily configurable via command line rather than some complicated script.

Any recommendations?

Thanks in advance

---

### Post by blackmail on 2010-03-17
This is a rather extravagant idea, but it is nonetheless a cool one :)
Sadly I can only think of bash to do this, nothing else, or you can also do this with python. But look at it this way, rather that having a program run in the background and use up memory, could you not do a simple copy-paste action instead?

---

### Post by DarkGreen16 on 2010-03-17
The task will be repeated on a daily basis and will never change. Thus an automated process makes the most sense.

---

### Post by blackmail on 2010-03-21
Then getting an external backup drive, and running a batch script at start-up is the best idea, a hint on how to make the script should be, since you have movies, they must be stored in a folder, you write a script to check what files/folders are not present on the backup drive regarding the folder you store your files/folders in and copy them to the backup drive, there is no other thing i can suggest you :)

---

### Post by rnerwein on 2010-03-21
hi
nice idea.
think about "rsync" and another hint is: apt-get install inotify-tools.
( i'am using inotifywait combined with ~/.bash_logout and last not least if i fall in sleep cron - all combined with rsync )
ciao

---

