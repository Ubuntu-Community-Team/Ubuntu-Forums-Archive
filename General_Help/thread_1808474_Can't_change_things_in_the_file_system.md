---
title: "Can't change things in the file system"
date: 2011-07-20
forum: General Help
---

### Post by lakshmen on 2011-07-20
I would like to change some files in the file system section.How do i gain access to change the file system?

---

### Post by jramshu on 2011-07-20
Open nautilus as root.

---

### Post by AlphaLexman on 2011-07-20
You probably don't have the correct permission(s).

What do you want / need to change??

---

### Post by lakshmen on 2011-07-20
sorry i dun understand

---

### Post by lakshmen on 2011-07-20
I would like to change a file in ROS distribution which i downloaded from ROS website..

---

### Post by WorMzy on 2011-07-20
What is "ROS distribution"?

---

### Post by lakshmen on 2011-07-20
some files from ROS..

---

### Post by WorMzy on 2011-07-20
Okay, and what is "ROS"?

---

### Post by AlphaLexman on 2011-07-20
See [http://www.ros.org/wiki/Support]("http://www.ros.org/wiki/Support")

---

### Post by lakshmen on 2011-07-20
how do u gain access to change a file in the file system?

---

### Post by haqking on 2011-07-20
so you have downloaded some files and you want to make some changes to them ?

you are attempting to make changes and are getting permission denied ?

If so then it is a permission issue.

are the files in your own home directory ?

right click on the file or files and see who the owner of the files are, you may need to make some permission changes if the files do belong to you of course ;-)

it is possible to do using the sudo command however this isnt necessarily a good idea if you yourself own the files even if you have sudo permission

---

### Post by WorMzy on 2011-07-20
Okay, so it's some software. Have you installed it, [following the guide]("http://www.ros.org/wiki/diamondback/Installation/Ubuntu")? Or have you downloaded the source code?

If you've installed it, what file(s) are you trying to edit? Is it a text file?

If so, run
```
gksudo gedit /path/to/text/file
```

---

### Post by lakshmen on 2011-07-20
basically, i downloaded the file from the website a long time ago. I would like to add a similar txt file in on one of the file folders. but i am not able to do so...

---

### Post by WorMzy on 2011-07-20
Why not? Do you get an error? Where *exactly* are you trying to move the txt file to?

---

### Post by lakshmen on 2011-07-21
i donot get any error. I cant change any file. I dun have the option to either create a folder or document. whereas in my user folder i can do it... how do i gain access to be the root user?

---

### Post by haqking on 2011-07-21
> **lakshmen said:**
> i donot get any error. I cant change any file. I dun have the option to either create a folder or document. whereas in my user folder i can do it... how do i gain access to be the root user?

use sudo for all admin tasks.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

the root user is disabled by default in ubuntu and should remain so, however you can use sudo to gain eleveated permission to carry out admin tasks as long as your account is specified in the sudoers file.

it should be as long as you are the admin for your machine

---

### Post by lakshmen on 2011-07-21
thanks.. so if i want to change someting in the file system for example, i can type sudo nautilus. Am i right? then i will gain access to the file system?

---

### Post by WorMzy on 2011-07-21
No. You should use "gksudo nautilus". Never use "sudo" for graphical applications.

---

### Post by lakshmen on 2011-07-21
what is the difference between gksudo and sudo? i am a newbie to all this... sorry

---

### Post by WorMzy on 2011-07-21
sudo is for terminal commands, gksudo (or gksu) is for graphical commands. It's all explained on the link haqking posted.

---

