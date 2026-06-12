---
title: "from terminal to menu"
date: 2011-01-02
forum: General Help
---

### Post by shafagh on 2011-01-02
Hi
I want to start a program which starts from terminal window and needs sudo permission.
How can I start it from Application menu without need of any permission?
thanks in advance.
shafagh

---

### Post by cyb3r_sn4k3 on 2011-01-02
Try adding sudo to the command by editing the menu. 
Or change the permissions of the file (not recommended)
This might help if u want to change the permission 
[http://ubuntuforums.org/showthread.php?t=269330](http://ubuntuforums.org/showthread.php?t=269330)
Good Luck :)

---

### Post by MooPi on 2011-01-02
You will need to edit your /etc/sudoers
```
sudo visudo
```will open the file in question.

This is the last segment of my sudoers
> # Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
[COLOR="Blue"]%demo ALL=(ALL)NOPASSWD:/sbin/shutdown[/COLOR]
Notice the part in blue is the added extra so I can use the shutdown without permission.
Be careful editing , because if you mess it up you'll be booting to a live CD to correct.

---

