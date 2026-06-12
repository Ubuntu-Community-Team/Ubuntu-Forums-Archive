---
title: "How to install a .deb through terminal?"
date: 2010-10-03
forum: General Help
---

### Post by HiTom on 2010-10-03
Hi! I just installed ubuntu (the most recent version, i dont know its number), and im a big newbie here, so i've got some basic questions:

How to use sudo command?

what is sudo command?

How to navigate into a folder in terminal (like when you have Windows xp os there would be something like Mycomputer/Localdisk/ProgramFiles/Lol/Lol.exe)?

Can you give me a site that lists all the commands that ubuntu has?


Sorry to be that rough, i know this isnt yahoo answers, they told me that i could freely post here any questions concerning ubuntu/linux.

Also, please excuse me if i put this question in the wrong topic thanks!

---

### Post by shashi859 on 2010-10-03
hi... 
There is great tutorial from psychocats covering a lot of newbie problems 
[www.psychocats.net/**ubuntu**/**install**ing**software **]("http://www.psychocats.net/ubuntu/installingsoftware")

here is a ubuntu forum posts for sudo [http://ubuntuforums.org/showthread.php?t=261204](http://ubuntuforums.org/showthread.php?t=261204)

---

### Post by shashi859 on 2010-10-03
[U]for terminal you can take a look into psychocats or 
this site [http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)
[/U][]("http://ubuntuforums.org/showthread.php?t=261204")

---

### Post by oldos2er on 2010-10-03
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

[http://linux.about.com/od/ubuntu_doc/a/ubudg24t4.htm](http://linux.about.com/od/ubuntu_doc/a/ubudg24t4.htm)

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by nikefalcon on 2010-10-03
> **HiTom said:**
> 
How to use sudo command?

type man sudo in the terminal ```
man sudo
```

> **HiTom said:**
> 
what is sudo command?

The sudo command is a sort of a modification of the "su"(switch user) command; which is is used to switch to another user(to gain their privileges etc.) "sudo" followed by a command performs the action as the "root" user(super user)

> **HiTom said:**
> 
How to navigate into a folder in terminal (like when you have Windows xp  os there would be something like  Mycomputer/Localdisk/ProgramFiles/Lol/Lol.exe)?

use the "cd"(change directory) command:
```

cd /root/home/user/ProgramFiles/Lol

```

> **HiTom said:**
> 
Can you give me a site that lists all the commands that ubuntu has?

try [http://www.linux.org/lessons/beginner/index.html](http://www.linux.org/lessons/beginner/index.html)
you can use this too: [http://www.tldp.org/LDP/Bash-Beginners-Guide/Bash-Beginners-Guide.pdf](http://www.tldp.org/LDP/Bash-Beginners-Guide/Bash-Beginners-Guide.pdf)

The key to learn bash-the ubuntu terminal- is patience and persistence. 
And another VERY IMPORTANT thing: never use a command is you have no idea of what it does; and be careful when doing tasks as the root user.
Good Luck

---

### Post by nikefalcon on 2010-10-03
Never download and manually install a .deb if it is available in the repositories(or a PPA). Dependency solving can be a REAL PAIN.

---

