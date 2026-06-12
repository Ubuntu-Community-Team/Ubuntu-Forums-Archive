---
title: "file searching and live cd"
date: 2010-12-10
forum: General Help
---

### Post by Zerocool Djx on 2010-12-10
I got a few things going on on 3 different computers..


I need help with these:

1) I need to know how to search for files in terminal, the command.

2) what is the name of the program in the repos that makes a live cd of your system? was it aptone CD? I think that just backs up the system.

Essentially, I have been making a custom version of Ubuntu and it's nearly complete and I need to create a live CD of it. I tried clonzilla, but that program has issues after I put in the system keyboard layout. I found a program in the repos a while ago, but I can't remember the name. 

Please help and thank you...

---

### Post by Zerocool Djx on 2010-12-10
Sorry I guess I have already asked about the live cd a few times,..

here is an old post of mine:

[http://ubuntuforums.org/showthread.php?t=1609663](http://ubuntuforums.org/showthread.php?t=1609663)

Is remastersys uploaded in Ubuntu by default? I read the website, but it doesn't say how that cd is burned, anyone know?


Still need to know how to search files..

P&T

---

### Post by tommcd on 2010-12-10
> **Zerocool Djx said:**
> 
1) I need to know how to search for files in terminal, the command.

Use the **find** command. For example, here is the command to search for any .new configuration files in the /etc directory when updating Slackware:
```
find /etc -name "*.new"
```
There are a great many options that can be used with the find command that I am not very knowledgeable of. You can see some examples here:
[http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Find_command_0](http://www.linuxquestions.org/linux/answers/Applications_GUI_Multimedia/Find_command_0)
[http://wiki.linuxquestions.org/wiki/Find](http://wiki.linuxquestions.org/wiki/Find)
[http://www.codecoffee.com/tipsforlinux/articles/21.html](http://www.codecoffee.com/tipsforlinux/articles/21.html)

---

### Post by Zerocool Djx on 2010-12-10
nice,.. and if I want to search the entire HD for that same file?

---

### Post by tommcd on 2010-12-10
> **Zerocool Djx said:**
> nice,.. and if I want to search the entire HD for that same file?
It would be something like:
```
find / -name "*.new"
```
You would have to use sudo for that in order to avoid *permission denied* errors for directories that your user does not have read access to.
Also, there is probably some way to avoid searching the virtual files on /proc and other directories that you may want to avoid searching, but I am not sure how to use find like that.

---

