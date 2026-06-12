---
title: "Sudo User"
date: 2011-01-02
forum: General Help
---

### Post by cbarnett2486 on 2011-01-02
I am new to Linux and I keep running into the problem of having to authenticate every time I do anything! I have googled about adding a user to sudo so I be in root or whatever, but it doesn't work! Somebody tell me what I'm doing wrong??

---

### Post by ibe2fly4chu on 2011-01-02
sudo is a form of admin command in linux. There are many uses. For example if you are typing in terminal...to execute a command as Root (admin) the command "sudo" must be typed first. First however what are you trying to do? If you are trying to open gnome as a admin to swap files or are you trying to run terminal as admin?

---

### Post by cbarnett2486 on 2011-01-02
Initially I was just trying to copy some background images into the directory so they would show up in the box where you select them.  It would be nice to be able to do what I want to do, but I just can't get the admin thing to work...  Thought I would add, I have been able to run terminal in root mode(?) as admin...  I am just not able to add my user name as a sudo.

---

### Post by aysiu on 2011-01-02
> **cbarnett2486 said:**
> I am new to Linux and I keep running into the problem of having to authenticate every time I do anything! I have googled about adding a user to sudo so I be in root or whatever, but it doesn't work! Somebody tell me what I'm doing wrong??
If you're prompted for a password any time you do anything, your installation isn't working correctly.

Ubuntu should prompt you for a password only every time you launch an administrative app or issue a *sudo* command... and then only once every 15 minutes.

If you're issuing several *sudo* commands in succession, you can save time by typing ```
sudo -i
``` and then issuing the rest of the commands without *sudo* and then typing ```
exit
``` to go back to a regular user prompt.

---

### Post by aysiu on 2011-01-02
> **cbarnett2486 said:**
> Initially I was just trying to copy some background images into the directory so they would show up in the box where you select them.  It would be nice to be able to do what I want to do, but I just can't get the admin thing to work...  Thought I would add, I have been able to run terminal in root mode(?) as admin...  I am just not able to add my user name as a sudo.
Creative a launcher or keyboard shortcut for the command ```
gksudo nautilus
``` and you can copy and paste to system directories to your heart's content.

---

### Post by cbarnett2486 on 2011-01-02
Thanks!! Believed it worked...  I really appreciate it!

---

### Post by uRock on 2011-01-02
An even easier way to move pictures to the background folder is by right-clicking the desktop and selecting Change Desktop Background. Then use the Add button to add a picture.

---

