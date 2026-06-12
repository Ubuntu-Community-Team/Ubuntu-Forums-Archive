---
title: "I Don't Have Permission To Write To My Seamonkey Profile"
date: 2009-08-03
forum: General Help
---

### Post by Mark76 on 2009-08-03
Which makes installing add ons like no script rather awkward.

How can I remedy this situation?

---

### Post by Brandon Williams on 2009-08-03
It sounds like there're files with the wrong owner in your .mozilla directory somewhere. Try this command in a terminal to change the owner of all files/directories under ~/.mozilla back to you:
```
find ~/.mozilla ! -user $USER -exec chown $USER {} \;
```

---

### Post by gtamplin on 2009-08-05
I have an identical problem. 

I am presently running UBUNTU 7.04 and trying to upgrade to version 8. 
Information on the website states that ALL FILES WILL BE LOST unless they are backed up to other media. 

When I try to copy my data and documents onto either my external drive, or to removable SD RAM, UBUNTU will not allow the copy. 

It displays a message saying either that I am not the "OWNER" of the disk, or that I "DO NOT HAVE PERMISSION" to write to the disk. 

How can I tell UBUNTU that I AM THE OWNER of all the drives? 

I tried the previous "solution" and it MADE NO DIFFERENCE. 

Do I have to destroy all my documents in order to upgrade to the next version?

---

### Post by spiderbatdad on 2009-08-05
You can launch seamonkey from your terminal as root:
```
sudo seamonkey
```Then install the add-ons or themes. Close seamonkey and reopen in the usual manner. Your add-ons will be applied.

---

### Post by michy99 on 2009-08-05
> **gtamplin said:**
> I have an identical problem. 

I am presently running UBUNTU 7.04 and trying to upgrade to version 8. 
Information on the website states that ALL FILES WILL BE LOST unless they are backed up to other media. 

When I try to copy my data and documents onto either my external drive, or to removable SD RAM, UBUNTU will not allow the copy. 

It displays a message saying either that I am not the "OWNER" of the disk, or that I "DO NOT HAVE PERMISSION" to write to the disk. 

How can I tell UBUNTU that I AM THE OWNER of all the drives? 

I tried the previous "solution" and it MADE NO DIFFERENCE. 

Do I have to destroy all my documents in order to upgrade to the next version?

If you open a session of nautilus as root, you should be able to copy anything you want. Open a terminal and enter:```
gksudo nautilus
```

---

### Post by mcduck on 2009-08-05
> **spiderbatdad said:**
> You can launch seamonkey from your terminal as root:
```
sudo seamonkey
```Then install the add-ons or themes. Close seamonkey and reopen in the usual manner. Your add-ons will be applied.

..and after that you can be sure your permissions are now overwritten by root.. ;)

Always run graphical applications with gksudo if you need to run them as root. "sudo" will not load root's environment correctly for graphical applications, which means that it will use your normal users configuration files but with root permissions. If you then save any settings the configuration file is overwritten with root permissions and your normal user won't be able to change any settings any more.

---

### Post by spiderbatdad on 2009-12-26
In certain versions of seamonkey I have seen that the user cannot make config changes in user files. sudo seamonkey should open user file as root, whereas gksu seamonkey will open root's seamonkey. Anyway I got the information on that trick here: [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

