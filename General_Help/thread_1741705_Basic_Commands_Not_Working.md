---
title: "Basic Commands Not Working"
date: 2011-04-28
forum: General Help
---

### Post by Robert_61 on 2011-04-28
Hello.

This is very strange. I opened a terminal and entered the command:

ace@Front-Office:~$ sudo cd /home/ace/

and got this message:

sudo: cd: command not found

I don't understand this.

Also, I was trying to change directories and got this.

ace@Front-Office:/home$ cd /home/ace/desktop/work/
bash: cd:  /home/ace/desktop/work/: No such file or directory

I know that this folder exists on the desktop

Any help would be appreciated.

---

### Post by pAsM on 2011-04-28
Hello,
[INDENT]There seems to be a few issues with your commands, please try
```

sudo su
cd /home/ace/

```
rather then
```

sudo cd /home/ace

```
 
(Do you really need to do this as root however???, you are logged in as "ace" afterall)
 
 
[/INDENT]

---

### Post by ELD on 2011-04-28
As said before don't use sudo to change directories.
 
Also "desktop" will be "Desktop" it has a capital ;)

---

### Post by WorMzy on 2011-04-28
cd is a in-built shell command; it doesn't have an actual executable like most commands, so it can't be used with sudo. If you need to cd to a folder that you don't have read permissions to, use a root shell:

```
sudo -i
```

---

### Post by Robert_61 on 2011-04-29
Got it, thanks.

I didn't think that case mattered in Ubuntu.

---

### Post by WorMzy on 2011-04-29
Nah, you're thinking of Windows. Unix has always* been case-sensitive.


*AFAIK

---

