---
title: "execute files on the server"
date: 2011-04-13
forum: General Help
---

### Post by mark5907 on 2011-04-13
Hi, everyone, I am quite new to linux world and I have a question about executing some files o the server. 


I have already connected to the server, it is in my .gvfs directory. 

[email]mark5907@mark5907:~/.gvfs[/email]$ ls
software on arcvfs.arc.xxx.xxx


but the directory name is "software on arcvfs.arc.xxx.xxx", it has spaces in between. So when I use cd, it gives me the error:


[email]mark5907@mark5907:~/.gvfs[/email]$ cd software on arcvfs.arc.xxx.xxx
bash: cd: software: No such file or directory



Eventually I want to run some file in this directory name "install" e.g. software on arcvfs.arc.xxx.xxx/install 


Can anyone tell me how to do so ? 


Thanks !

---

### Post by ~Plue on 2011-04-13
> **mark5907 said:**
> 
but the directory name is "software on arcvfs.arc.xxx.xxx", it has spaces in between. So when I use cd, it gives me the error:
[EMAIL="mark5907@mark5907:%7E/.gvfs"]mark5907@mark5907:~/.gvfs[/EMAIL]$ cd software on arcvfs.arc.xxx.xxx
bash: cd: software: No such file or directory

you can use quotes, back slashes before spaces or use tab auto completion

```
cd 'software on arcvfs.arc.xxx.xxx'
cd software\ on\ arcvfs.arc.xxx.xxx
cd softw<press tab>
```

---

### Post by rubylaser on 2011-04-13
All of the above directions are spot on.  Just so you understand why it works this way, BASH divides each line into words at whitespace.  This is a great guide to understand BASH.

[http://mywiki.wooledge.org/BashGuide/CommandsAndArguments]("http://mywiki.wooledge.org/BashGuide/CommandsAndArguments")

---

### Post by NFblaze on 2011-04-13
Also, next trime you can try typing part of the name and pressing TAB key it may fill in the rest with the escaping backslashes.

---

