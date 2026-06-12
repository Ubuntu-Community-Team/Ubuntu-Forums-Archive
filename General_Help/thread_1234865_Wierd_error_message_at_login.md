---
title: "Wierd error message at login"
date: 2009-08-08
forum: General Help
---

### Post by ishmael2k on 2009-08-08
I am using 9.04 and am now getting the following message at login:


[I][FONT="Arial"]User's $HOME/.dmrc file is being ignored.
This prevents the default session and language from being saved.
File should be owned by user and have 644 permissions. 
User's $HOME directory must be owned by user and not writeable by other users.
[/FONT][/I]

I click ok and it finishes logging my in with no _apparent_ problems. 

Currently I am the only user on this machine, I did have another id but removed it. Did I leave something behind or???

---

### Post by raronson on 2009-08-08
Hi.  Try entering the following commands into the terminal, swapping out the real value for 'yourUserName'

```

sudo chown yourUserName /home/yourUserName
sudo chgrp yourUserName /home/yourUserName

```

> 
Currently I am the only user on this machine, I did have another id but removed it. Did I leave something behind or???


I'm guessing that you inherited the group setting from the other id.

---

### Post by harry2006 on 2009-08-08
did you look here, btw
[http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052)
and this:
[https://answers.launchpad.net/ubuntu/+question/7296](https://answers.launchpad.net/ubuntu/+question/7296)

---

### Post by ishmael2k on 2009-08-08
> **raronson said:**
> Hi.  Try entering the following commands into the terminal, swapping out the real value for 'yourUserName'

```

sudo chown yourUserName /home/yourUserName
sudo chgrp yourUserName /home/yourUserName

```



I'm guessing that you inherited the group setting from the other id.

Thanks! That took care of it. 

The other threads posted by harry2006 are very informative also. Thanks for those!

(I also added:  sudo chmod 644 /home/username/.dmrc)

---

### Post by raronson on 2009-08-08
Right on.  I didn't want to give you way too much info--but it's all out there.

Take it easy :)

---

