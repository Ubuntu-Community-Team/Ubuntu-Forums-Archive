---
title: "permissions"
date: 2010-05-03
forum: General Help
---

### Post by honnour on 2010-05-03
Hi

I'm a new Ubuntu user. I'm trying to move a file to opt folder. But I cant do it because I dont have the permission to do it. In folder preferences it says " you are not the owner"
How can I move a file to opt folder? or How can I change the folder permission settings?

Thank you

---

### Post by sunk8 on 2010-05-03
Take a look...
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by nothingspecial on 2010-05-03
Open a terminal and type ```
gksudo nautilus
```. 

You can copy it then.

Some old linux tutorials ask you to copy things to /opt when you don`t really need to.

What are you trying to achieve?

---

### Post by nitstorm on 2010-05-03
ubuntuforums.orgubuntuforums.org/showthread.php
looks like i was a lil slow while typing...
anyhoo... :P
If you want to move the things using file browser(nautilus), you should be able to do it using ```
gksudo nautilus
``` and put in the password and and you are golden. Beware though - be sure not to do something unless you are absolutely sure of it like deleting or moving a file or renaming unless you know you are not breaking anything that belongs to some other application or something

if u are using the terminal to copy then ```
sudo cp *pathtofile destinationpath*
```

---

### Post by honnour on 2010-05-03
i was trying to install xampp. The manuel that i'm following says this

"Extract the downloaded archive file to /opt: tar xvfz xampp-linux-1.7.3a.tar.gz -C /opt"


and my downloaded file is on my desktop, and i couldnt write the necesssary folder instead of /opt. So i decided to move to file to /opt.
Now i moved it thanks to you but still i get the same error


and that error is;


tar: xampp-linux-1.7.3a.tar.gz: open imposibble: No such file or directory
tar: Child returned status 2
tar: Exiting with failure status due to previous errors


how can i do this?


Thank you

---

### Post by nothingspecial on 2010-05-03
Can you post a link to the instructions you are following?

---

### Post by honnour on 2010-05-03
sure;

[http://www.apachefriends.org/en/xampp-linux.html#372](http://www.apachefriends.org/en/xampp-linux.html#372)

---

### Post by nothingspecial on 2010-05-03
I`ve been trying to test this for you, but unfortunately I have a 64bit machine and llamp only supports 32bit atm.

As far as I can tell, you didn`t need to copy it to /opt

But since you have .....

....btw - did you choose to open it with "archive manager" instead of saving it to disk? - if that is the case you will have a folder called lampp rather than a tar.gz.

If this is the case, and you have moved it to /opt, try

```
sudo chmod +x /opt/lampp/lampp

sudo /opt/lampp/lampp start
```

If it is still a tar.gz, extract it first, then try again.

Oh, and it looks like it has a shed load of dependencies, but maybe not.

---

### Post by WorMzy on 2010-05-03
Can you not just use tasksel (sudo tasksel) to install LAMP?

---

