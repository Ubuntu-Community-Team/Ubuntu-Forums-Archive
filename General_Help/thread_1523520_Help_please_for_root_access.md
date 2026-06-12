---
title: "Help please for root access"
date: 2010-07-03
forum: General Help
---

### Post by ozstar on 2010-07-03
HI,

I am new to Linux and have 10.4.

I am so tired of having to do sudo evey time I want to do something.

There is only me on the machine, no one else so I  do not need to seek root permission everytime as i set things up.

Is there a way I cam set it for me to access everything all the time, so that when I initiate gedit, or file browser or anything I am in and able to to what I need.

Loving the challenge from an old Dos dude but this part is driving me nuts!!

Thanks,

oz :-)

---

### Post by nautica17 on 2010-07-03
You could try this: 
sudo -i 

This log you in as root. Be very carful though as it is not recommended to be in root constantly. You basically at that point can potentially delete something crucial. I'd just stick with sudo. ;)


Edit: To the mods, if my post is breaking rules, I apologize. I don't see my command under harmful command lines in the thread about that stuff..

---

### Post by jwbrase on 2010-07-03
It's actually against forum rules to give that information out, as it's a rather bad idea security-wise to stay logged in as root on a networked computer.

DOS machines usually weren't connected to the Internet. Linux and modern Windows machines usually are, and so need to take security precautions that weren't needed in the DOS era.

---

### Post by Yuri sss on 2010-07-03
Logging in as root is an excessively stupid idea. Don't do it! [-X

If you need to run individual applications as root, right-click the desktop, select "Run command" and enter "kdesudo <*appname*>".
e.g. for a root terminal, you would use:

kdesudo konsole

For Gnome, replace "kdesudo" with "gksu".

---

### Post by yetiman64 on 2010-07-03
To all, Please check this post from philinux (forums staff) and carefully follow and read the links he posts, about linux security and forum policy. [http://ubuntuforums.org/showpost.php?p=9537525&postcount=5](http://ubuntuforums.org/showpost.php?p=9537525&postcount=5)

To the OP, link #4 in my sig is the documentation referred to in the forum policy post on this issue from bodhi.zazen (forums admin) [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

[RootSudo link here as well.]("https://help.ubuntu.com/community/RootSudo") Yetiman64

---

### Post by Rubi1200 on 2010-07-03
This explains what root and sudo is all about on Ubuntu:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

