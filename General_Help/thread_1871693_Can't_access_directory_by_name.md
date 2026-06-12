---
title: "Can't access directory by name"
date: 2011-10-29
forum: General Help
---

### Post by refuser on 2011-10-29
I have a command line install of Oneric on my server and I now have a directory that I cant access.

myname@server:/home/torrents/download$ ls -land R*
drwxrwxr-x 2 1000 1000 4096 2011-10-27 16:55 Röyksopp - Senior (FLAC)

myname@server:/home/torrents/download$ stat R*
  File: `Röyksopp - Senior (FLAC)'
  Size: 4096            Blocks: 8          IO Block: 4096   directory
Device: 803h/2051d      Inode: 31588493    Links: 2
Access: (0775/drwxrwxr-x)  Uid: ( 1000/   einar)   Gid: ( 1000/   einar)
Access: 2011-10-29 08:35:38.325796401 +0200
Modify: 2011-10-27 16:55:02.019088730 +0200
Change: 2011-10-29 08:30:25.797798751 +0200

myname@server:/home/torrents/download$ sudo rm -rf Röyksopp\ -\ Senior\ \(FLAC\)

myname@server:/home/torrents/download$ ls -land R*
drwxrwxr-x 2 1000 1000 4096 2011-10-27 16:55 Röyksopp - Senior (FLAC)

The name can not be autocompleted unless it's the only file in the directory starting with "Rö" but if it is I can autocomplete and cd into the dir.

I can remove it by using "find . -inum -exex rm -rfi {} \;"

Can someone tell me what is going on here???

Thanks!

---

### Post by BillyBoa on 2011-10-29
Did you try to access it by using sudo nautilus on your terminal?

---

### Post by CharlesA on 2011-10-29
> **BillyBoa said:**
> Did you try to access it by using sudo nautilus on your terminal?
Use gksu instead of sudo when running GUI applications as root, otherwise you could run into permission problems.

---

### Post by nothingspecial on 2011-10-29
@BillyBoa


> **refuser said:**
> I have a command line install of Oneric on my server 

+1 CharlesA

---

### Post by CharlesA on 2011-10-29
I wonder if the special symbol is what is causing the problem.

---

### Post by refuser on 2011-10-29
BillyBoa, it's a comand line install.

CharlesA
It seems like the problem is with som special character, yes. I managed to do a:

find . -inum 1234567 -exec cp -dR {} ./Roeyksopp...

and I could access the new directory just fine. Even when I renamed it Röyksopp... again.

My guess is that there somehow are two different symbols that renders like 'ö' in the terminal.

=/

---

### Post by CharlesA on 2011-10-29
That could be. What are you using to access the shell?

---

