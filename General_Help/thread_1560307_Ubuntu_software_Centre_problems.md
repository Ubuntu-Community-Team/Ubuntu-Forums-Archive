---
title: "Ubuntu software Centre problems"
date: 2010-08-24
forum: General Help
---

### Post by Complexes on 2010-08-24
Excuse me if this is in the wrong place, or I'm doing something wrong, but I'm very new, without the slightest idea what I am doing...

I was running a Ubuntu live disk, looking around the software centre and decided to install a game. Despite it seeming quite stupid to install a game when you are running the OS on a disk. Well, instillation messed up and I couldn't play the game. After a while on the live disk, forgetting about the game, I installed Ubuntu into my computer. Now whenever I try and install anything from the software center It says that the last instillation messed up and I need to sort it out. So, what should I do?

---

### Post by s.fox on 2010-08-24
Hello and welcome to the Ubuntu Forums :)

Do you see  something like "broken packages" in the message?

If so you will need to open a terminal

 **Applications menu** -> **Accessories** -> **Terminal**. 

and run this command:

```
sudo apt-get install -f
```

You will be prompted for a password (you will not be able to see the characters you enter)

Hope this helps,

-Silver Fox

---

