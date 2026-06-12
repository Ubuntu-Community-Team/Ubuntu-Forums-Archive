---
title: "File Permissions"
date: 2010-09-11
forum: General Help
---

### Post by -Derek- on 2010-09-11
Hey everyone,

Today i made the leap from windows to Ubuntu and I'm having a bit of trouble fully understanding how the permissions work. I ran rkhunter and went to check the log file but i didn't have permission to open it. I am the administrator of the system so i found it a little strange.

After searching for answers i didn't find much, so any help will be appreciated.


Thanks in advance, Derek.

---

### Post by lloyd_b on 2010-09-11
> **-Derek- said:**
> Hey everyone,

Today i made the leap from windows to Ubuntu and I'm having a bit of trouble fully understanding how the permissions work. I ran rkhunter and went to check the log file but i didn't have permission to open it. I am the administrator of the system so i found it a little strange.

After searching for answers i didn't find much, so any help will be appreciated.


Thanks in advance, Derek.

Not strange at all.  Ubuntu, by default, has the root account disabled.  This means you can't be logged in as administrator, even if you want to.

For commands that require extra privileges, you can preface them with the "sudo" or "gksudo" command.  Putting this command in front of another command will run the command as root.

Lloyd B.

---

### Post by 3Miro on 2010-09-11
In Ubuntu you are the "Administrator", however, in order to view/edit system files, you have to explicitly give yourself permission.

If you are running a terminal program (i.e. a script or some other commands), you have to type "sudo" before the command (super user do). If you know exactly where the file is, you can type in the terminal:
```
sudo less /path/to/file
```
and this will show the file.

If you want to run a graphical application, from the terminal you can put "gksudo". For example:
```
gksudo nautilus
```
will open file manager and you will be able to access all files.

Be very careful with those command, they can really damage your system if you don't know what you are doing.

Also, on a related note, log files are usually readable by anyone. If you cannot read the log file, the issue might be something else.

---

### Post by -Derek- on 2010-09-11
Thanks! I used the "gksudo nautilus" command and it worked.

---

### Post by bodhi.zazen on 2010-09-11
While that works, IMO you should do some reading when you have time.

The "admin account" in LInux is root. What an admin account means is that you have access to root, in ubuntu via sudo (other distros use su)

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

Linux permissions are odd at first, but they are an essential part of security :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

HTH

---

