---
title: "Unable to access previous usr"
date: 2012-02-23
forum: General Help
---

### Post by Hobomank on 2012-02-23
I hate that my first post has to be a help request but I'm having a simple problem with ubuntu. 

I installed 11.04 on a very simple, old machine in order to revive and repurpose it.

Heres my situation:

While fiddling with with settings in ubuntu 11.04 i ended up selecting an incompatable video driver. giving me blackscreen. rather than fix the issue i put my computer to the side for another day.

I picked it back up to work on it and found a new release for ubuntu so i figured i would install the update without changing any of my previous usr settings to fix the issue. I have a new root account on 11.10 but i can't access any of my files from my old account because i can't remember the original password. it comes up as. any help would be appreciated. :)

Edit: apparently im not the root usr, as it seems that i cannot view the root folder, i do not have the proper permissions.

---

### Post by wildmanne39 on 2012-02-23
Hi, try looking at the files with this command please:
```
gksudo nautilus
```
then enter your password.

The root account is locked so it is your user account you need with the gksudo command for graphical or sudo for the terminal.

Here is a link to help.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Thanks

---

### Post by Hobomank on 2012-02-24
thank you so much, while i didnt do that exactly , it pointed me in the right direction

---

### Post by wildmanne39 on 2012-02-25
Hi, glad to be of any help at all, please post your solution for others and use thread tools to mark as solved.
Thakns

---

### Post by Hobomank on 2012-02-25
This code allowed me to use a different password in order to access my encrypted files
```
gksudo nautilus
```

But that wasn't my problem, i was able save my files on  flash drive with this, but my problem was thatcomputer was filled with corrupted partitions. Mainly from so many distributions of linux.

To solve that problem i used the 'gparted' program that came [puppy linux]("http://ubuntuforums.org/puppylinux.org/") (which can be booted from a live cd if you cannot boot you computer without issue) to view/delete corrupt partitions so i could do a fresh install of Ubuntu. 

Note:I would recommend this option if linux is the only OS on your computer and you have all your files backed up . as this will delete your windows partition along with any linux files.

---

