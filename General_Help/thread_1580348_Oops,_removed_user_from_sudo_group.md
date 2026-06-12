---
title: "Oops, removed user from sudo group"
date: 2010-09-23
forum: General Help
---

### Post by Lovegain on 2010-09-23
I made a mistake on my friend's Ubuntu system when trying to get hard drive permissions right. I wanted to add a user to a certain group with **usermod -G**, but without realising I should also use **-a**, with the result that the user is now not longer in the **sudo** group.

This is the only (regular) user on the system, which means I can not sudo usermod again to get it right. So what to do? The only solution I can think of is using a live disc to restore the group belongings, but I want to know if there's a quicker way.

Also, I don't know what more groups the user was in. Is there a history? Or else, what are the default groups?

---

### Post by WorMzy on 2010-09-23
Boot into recovery mode and drop to a root shell. You can re-add the user to the group there.

On my Lucid installation, my user is a member of the following groups:

[LIST]
[*]adm
[*]dialout
[*]cdrom
[*]plugdev
[*]lpadmin
[*]admin
[*]sambashare
[/LIST]

As well as it's own group, which has the same name as it's username. (e.g. my user is wormzy, so he is also in the wormzy group)

---

### Post by Lovegain on 2010-09-23
WorMzy, thanks, that makes sense.

Now, apparently I misinterpreted the error message, and the fault is not that the user is not in the sudo group, but that it's not in the "sudoers file". How do I handle that?

---

### Post by Rubi1200 on 2010-09-23
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
[http://ubuntuforums.org/showpost.php?p=7118727&postcount=1](http://ubuntuforums.org/showpost.php?p=7118727&postcount=1)
[http://www.gratisoft.us/sudo/sudoers.man.html](http://www.gratisoft.us/sudo/sudoers.man.html)

---

### Post by sisco311 on 2010-09-23
> **Lovegain said:**
> WorMzy, thanks, that makes sense.

Now, apparently I misinterpreted the error message, and the fault is not that the user is not in the sudo group, but that it's not in the "sudoers file". How do I handle that?


You have to add your user to the **admin** group, after that you will be able to use sudo(usermod/gpasswd) and/or policykit(Users and Groups) to add your user to default group(s). 

See:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

The /etc/gnome-system-tools/user-profiles.conf file contains the llist of default groups.

[noparse](In Maverick:)[/noparse]
Desktop user = cdrom,floppy,dialout,tape,dip,adm,plugdev,fax,fuse,video

Administrator = cdrom,floppy,dialout,tape,dip,adm,plugdev,fax,fuse,admin,sambashare,lpadmin,video

---

### Post by rgiles43 on 2010-09-23
Hello,

If I understand right you are trying to add an existing user to the sudoers file?

If so you can easily do this at the command line via command:

sudo adduser *username* admin

Hope this helps.

Thanks,

---

