---
title: "need some help with chmod command?"
date: 2010-01-06
forum: General Help
---

### Post by skool me on 2010-01-06
Hello, this is my first post.. 
I'm such a newbie when it comes to Ubuntu, or any Linux varient, period.. 
I was trying to install a driver for an HP All-in-One Printer and was trying all kinds of commands from different Google searches... still unsuccessful in the installation..
I downloaded the file to my desktop, but after using a Chmod command someone mentioned, i now have a folder on my desktop named: 

hplip-3.9.12 
i right-click
select
properties

Basic Tab
Type:folder (inode/directory 
Contents:unreadable 
Location:/home/mesk/Desktop

Permissions Tab
Owner:root
Group:root

"You are not the owner so you cannot change these permissions"


The folder's icon on my desktop has a red box with white circle on the middle right side and a lock symbol above that..

I'm the only user so I don't get why the permissions are protected from me, how do i undo this? please help!!!!


thanks in advance...

---

### Post by mikewhatever on 2010-01-06
I think the main problem is, you are trying it the way you would in Windows, but you aren't on Windows now. I bet the very same packages are available through the repositories. What is the model of your printer?
If you insist on installing files from HP, please post direct links. I'd be very surprised if you needed to use chmod at all.

---

### Post by garryknight on 2010-01-06
You can't change it because you don't own it. Root does. You need to become root in order to change it. If you open a console, you can do:
[code]
sudo chown mesk /home/mesk/Desktop/hplip-3.9.12
[code]
and enter your password when asked.

You might want to read up on the difference between the ordinary user and the root user. You might want to bookmark this site and maybe download the PDF version. It'll tell you much more than you ever wanted to know about Linux.

http://rute.2038bug.com/index.html.gz

---

### Post by garryknight on 2010-01-06
Come to think of it, mikewhatever is right. Your printer will either work with the hplip package from the Ubuntu repos or it won't work at all. I'm betting on the former, but not holding my breath...

---

### Post by manosx on 2010-01-06
Hello
Have you tried [https://help.ubuntu.com/community/HpAllInOne](https://help.ubuntu.com/community/HpAllInOne)  ?

In general, in order to change the ownership of a file or directory you open a terminal and type:

```
sudo chown -vR username:group dir
```

**chown** is the command that changes file owner and group
**-v** makes it verbose, it will inform you for the changes
**-R** will make it recursive, so it will change the ownership and group of all the contents of the directory.
**username** and **group** should be your user-name since a file or folder of a user belongs to the same-name group

---

### Post by skool me on 2010-01-06
thanks for the quick responses fellas...yes i got alot to learn. i will be dl'ing that pdf file...and bookmark this site for sure.... im going to try the directions and repost...thanks again

---

### Post by skool me on 2010-01-06
> **garryknight said:**
> You can't change it because you don't own it. Root does. You need to become root in order to change it. If you open a console, you can do:
[code]
sudo chown mesk /home/mesk/Desktop/hplip-3.9.12
[code]
and enter your password when asked.

You might want to read up on the difference between the ordinary user and the root user. You might want to bookmark this site and maybe download the PDF version. It'll tell you much more than you ever wanted to know about Linux.

http://rute.2038bug.com/index.html.gz



thanks my friend, the command worked like a charm!

and thanks for the PDF link....

thanks for all the replies....very much appreciated....

---

