---
title: "Problems with Windows 7 dual boot w/ Ubuntu 10.10"
date: 2011-04-05
forum: General Help
---

### Post by ald3n3 on 2011-04-05
Hi Guys, after i install ubuntu 10.10 (dual boot) along side windows 7, windows 7 is not working well anymore.
 
Here are the problems:
1. **Everytime i start windows 7 it would show that black screen saying "one of the disk drive needs to be checked"** <--- i usually just got this message after improper shutdown.. and i always shut it down properly.
 
2. **Everytime i start windows 7 it also sometimes go to that window where it let me pick if i want to start on safe mode or normal mode** ...and again i usually just got this message after improper shutdown.. and i always shut it down properly.
 
3. **When i'm on windows 7 and i put the computer to sleep, after awhile my computer just shuts down by itself. And if i hibernate windows 7, the computer just goes straight to shutting down.**
 
4. **If i do a disk defragment it doesn't detect "drive C:" it has an option to defrag "recovery:"**
 
did i not install Ubuntu properly?
 
On the other hand the Ubuntu 10.10 side works perfectly.
 
I'm just worried that all these windows 7 issues will break my computer sooner.
 
Thank you a lot!

---

### Post by 3Miro on 2011-04-05
I have seen this happen if you read and write files to the main windows drive from within Ubuntu. While it is usually safe to read/write to a windows partition, it makes windows "nervous". That results in constant checks and so on.

Let windows run its diagnostics to make sure there are no problems, then try to not touch its files from within Ubuntu for awhile. Hopefully this will fix the issue.

---

### Post by oldfred on 2011-04-05
I agree with 3Miro.

You should set your windows install to read only in Ubuntu. Especially if you hibernate as writing into the drive while hibernated will cause damage to windows files. It may think it is in one place and now in Ubuntu you moved it so windows is lost.

If you have a lot of data you want to share create another NTFS partition just for data. I have all my Firefox & Thunderbird profiles & picasa photos still in my shared. I boot XP very little now but have not moved old common data into my Linux partitions.

---

### Post by ald3n3 on 2011-04-05
ok hopefull this will help =X

---

### Post by garvinrick4 on 2011-04-05
Can this happen from not defragging Windows a couple of times before installing side by side with another O.S.?

---

### Post by oldfred on 2011-04-05
Herman has tested a lot of installs and says that defragging is totally unnecessary. I still recommend it only because it speeds up the resize. 

I do not have link to where he said that.


One of Herman's install pages:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by garvinrick4 on 2011-04-05
> Herman has tested a lot of installs and says that defragging is totally  unnecessary. I still recommend it only because it speeds up the resize. 

I do not have link to where he said that. 
Have no reason to doubt you oldfred. 
##That is a nice link to pass on to New Ubuntu users for gparted, installation and more.
     I seem to have a lot of bookmarked 9.10 and below for some reason nice to have a
     more recent installation guide with the visual aids.

---

