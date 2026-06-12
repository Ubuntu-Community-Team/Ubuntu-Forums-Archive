---
title: "Ownership of folder"
date: 2011-09-01
forum: General Help
---

### Post by Lighthorse01 on 2011-09-01
Well I have tried to search for this but cant find it, I hope someone can help.
Using ubuntu 11.04
I am trying to put a folder with my background pix and xml file into usr/share/backgrounds , it keeps telling me I am not the owner. :shock: 
I am the only one that uses this laptop. 
I have checked all of the groups 
I am set as admin 
I set all permissions 
and still I cant add a folder to the usr directory.
This is nuts , there must be something that sets permission to do this.
It is bad enough that ubuntu does not see the webcam and mic that is built
in but it seems that access is way to restricted to admin. 
 
and how the .... do you tell it to stop asking for the .... password every 
time you want to do something.
 
anyway please Help..

---

### Post by saltmarshlamb on 2011-09-01
You can open a file browser as root to move the folder.

Run this from a terminal

```
gksudo nautilus
```

Be careful that you don't do something you shouldn't though :)

> and how the .... do you tell it to stop asking for the .... password every
time you want to do somethingYou don't. It'll only require a password when you need to do something to thing's that aren't owned by you. 

You own the things in your home. 

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by ajgreeny on 2011-09-01
Is there a good reason why you needed to put that background picture into the /usr/share/backgrounds folder other than perhaps some neatness requirement of yours, of course.

Don't forget you can use any picture, anywhere on the computer, as your desktop background.  There is no need to move it.

---

### Post by Lighthorse01 on 2011-09-01
I wanted to use the xml for slideshow, I assumed the folder and pix had to be there.
I finally figured that out, so now the sideshow is working, I think. 
As far as moving the folder to backgrounds I gave up everyone said to change stuff through the terminal or counsel.
Ummm I cant find either one of those.
 
 
Thanks

---

### Post by miasmablk on 2011-09-01
ctrl + alt + t

will bring up your console/terminal. however i must caution you placing these files in  usr/share/backgrounds is inadvisable the file system directory is root permissions only and for good reason. it would be be safer to place these files in your home directory in the pictures folder.

---

### Post by blueridgedog on 2011-09-01
There is nothing by definition wrong with placing items in /usr/share/backgrounds.  If you take a big view of the system and see yourself as the administrator of a multi-user computer system and you want to make files available to all users of the system, then it is the logical and correct place to put them.

It does require super user permissions to place your files there, but that is nothing more complicated than:

sudo cp /path/to/my/image.png /usr/share/backgrounds/

The reason for the reluctance you are encountering and the encouragement not to place the items there is that once you take on that level of management of the system, you more or less have to be willing and able to deal with the consequences.  With great power comes great responsibility...sudo carefully.

Since you were not certain how to get the images into the directory, it means that you are still learning about file and directory permissions and how things work.  As such you may not be ready to take over how the base system is setup.  I also think people learn by doing, so learning how to place system wide resources in system wide locations is part of learning to be a good system admin, even if it is only your own desktop.

---

### Post by miasmablk on 2011-09-01
> **blueridgedog said:**
> 
Since you were not certain how to get the images into the directory, it means that you are still learning about file and directory permissions and how things work.  As such you may not be ready to take over how the base system is setup.  I also think people learn by doing, so learning how to place system wide resources in system wide locations is part of learning to be a good system admin, even if it is only your own desktop.

exactly ;D

---

### Post by Lighthorse01 on 2011-09-01
Thanks guys I left it in the Home directory

---

### Post by The Llama on 2011-09-01
```
gksu nautilus
```

---

