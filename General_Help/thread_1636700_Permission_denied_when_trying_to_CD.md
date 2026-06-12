---
title: "Permission denied when trying to CD"
date: 2010-12-03
forum: General Help
---

### Post by JayUK20 on 2010-12-03
whenever I try and CD to a directoy I am being denied, how do i get round this?

---

### Post by plucky on 2010-12-03
> **JayUK20 said:**
> whenever I try and CD to a directoy I am being denied, how do i get round this?

For example?

Where are you trying to get to?

---

### Post by Paul41 on 2010-12-03
Try using sudo.  For example:

```
sudo cd /etc
```

---

### Post by galvatron408 on 2010-12-03
you probably don't have permission to access the directory.

type ll -d directoryName

see what it tells you.

Here is an example output for you:

ThinkPad-T61:~$ ll -d Music/
drwxr-xr-x 2 me me 4096 2010-11-10 12:49 Music//

As you can see, the Music directory is owned by "me" and I have rwx permission. If you do not understand ownership/permissions, do not attempt to change it. If you do, you might create bigger problems for yourself.

---

### Post by CharlesA on 2010-12-03
> **Paul41 said:**
> Try using sudo.  For example:

```
sudo cd /etc
```

You shouldn't need to use sudo to cd into any part of the file system. If you are trying to access an encrypted area, that's a totally different matter.

---

### Post by efflandt on 2010-12-03
Typically you need x permission for your user, group, or other for a directory in order to access it and r permission to read from it.  I was going to say you just need to use sudo.  However, for the following dir in /var/log:

```
drwxrwx--T 2 root              gdm        4096 2010-12-03 13:13 gdm
```This is strange, I cannot cd to it, but I can list it:

```
efflandt@xps8100:/var/log$ **ls gdm**
ls: cannot open directory gdm: Permission denied

efflandt@xps8100:/var/log$ **sudo cd gdm**
sudo: cd: command not found

efflandt@xps8100:/var/log$ **sudo ls -l gdm**
total 104
-rw-r--r-- 1 gdm  gdm   1292 2010-12-03 13:13 :0-greeter.log
-rw-r--r-- 1 gdm  gdm   1292 2010-12-03 13:01 :0-greeter.log.1
-rw-r--r-- 1 gdm  gdm   1181 2010-12-02 23:09 :0-greeter.log.2
-rw-r--r-- 1 gdm  gdm   2220 2010-12-02 23:08 :0-greeter.log.3
-rw-r--r-- 1 gdm  gdm   1292 2010-12-02 22:45 :0-greeter.log.4
-rw-r--r-- 1 root root 11710 2010-12-03 13:13 :0.log
-rw-r--r-- 1 root root 12331 2010-12-03 13:06 :0.log.1
-rw-r--r-- 1 root root 12008 2010-12-03 06:39 :0.log.2
-rw-r--r-- 1 root root 12008 2010-12-02 23:09 :0.log.3
-rw-r--r-- 1 root root 11939 2010-12-02 23:07 :0.log.4
-rw-r--r-- 1 root root   629 2010-12-03 13:13 :0-slave.log
-rw-r--r-- 1 root root   629 2010-12-03 13:01 :0-slave.log.1
-rw-r--r-- 1 root root   629 2010-12-02 23:09 :0-slave.log.2
-rw-r--r-- 1 root root  1183 2010-12-02 23:09 :0-slave.log.3
-rw-r--r-- 1 root root   711 2010-12-02 23:07 :0-slave.log.4
```

---

### Post by galvatron408 on 2010-12-03
If you read it carefully, you'll see that your sudo command output "command not found". 

> **efflandt said:**
> Typically you need x permission for your user, group, or other for a directory in order to access it and r permission to read from it.  I was going to say you just need to use sudo.  However, for the following dir in /var/log:

```
drwxrwx--T 2 root              gdm        4096 2010-12-03 13:13 gdm
```This is strange, I cannot cd to it, but I can list it:

```
efflandt@xps8100:/var/log$ **ls gdm**
ls: cannot open directory gdm: Permission denied

efflandt@xps8100:/var/log$ **sudo cd gdm**
sudo: cd: command not found

efflandt@xps8100:/var/log$ **sudo ls -l gdm**
total 104
-rw-r--r-- 1 gdm  gdm   1292 2010-12-03 13:13 :0-greeter.log
-rw-r--r-- 1 gdm  gdm   1292 2010-12-03 13:01 :0-greeter.log.1
-rw-r--r-- 1 gdm  gdm   1181 2010-12-02 23:09 :0-greeter.log.2
-rw-r--r-- 1 gdm  gdm   2220 2010-12-02 23:08 :0-greeter.log.3
-rw-r--r-- 1 gdm  gdm   1292 2010-12-02 22:45 :0-greeter.log.4
-rw-r--r-- 1 root root 11710 2010-12-03 13:13 :0.log
-rw-r--r-- 1 root root 12331 2010-12-03 13:06 :0.log.1
-rw-r--r-- 1 root root 12008 2010-12-03 06:39 :0.log.2
-rw-r--r-- 1 root root 12008 2010-12-02 23:09 :0.log.3
-rw-r--r-- 1 root root 11939 2010-12-02 23:07 :0.log.4
-rw-r--r-- 1 root root   629 2010-12-03 13:13 :0-slave.log
-rw-r--r-- 1 root root   629 2010-12-03 13:01 :0-slave.log.1
-rw-r--r-- 1 root root   629 2010-12-02 23:09 :0-slave.log.2
-rw-r--r-- 1 root root  1183 2010-12-02 23:09 :0-slave.log.3
-rw-r--r-- 1 root root   711 2010-12-02 23:07 :0-slave.log.4
```

---

