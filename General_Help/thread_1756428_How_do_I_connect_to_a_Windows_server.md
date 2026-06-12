---
title: "How do I connect to a Windows server?"
date: 2011-05-12
forum: General Help
---

### Post by semisquirrel on 2011-05-12
Hello,

I am a Ubuntu user in a Windows workplace. They tolerate me, because I make the rules, but my IT guy has surprisingly little knowledge about Linux.

Anyway, we just got a server. It's sitting behind me as we speak, humming away, arrogant in its knowledge that I can't get to its creamy centre.

How do I access its juicy bits? I know the IP and name (server). I accessed it once by chance, but when I restarted my computer, the folders were gone, so I need a way to make my computer connect automatically.

I appreciate any help!

Thank you.

---

### Post by coldraven on 2011-05-12
Sack the "IT" guy and find a proper one :) or at least one who can find information on topics that he knows little about.

---

### Post by semisquirrel on 2011-05-12
> **coldraven said:**
> Sack the "IT" guy and find a proper one :) or at least one who can find information on topics that he knows little about.

Well, it's complicated. He's a contractor making way more than me, and since I'm the only Ubuntu user (and the guy who pays the bills......) I don't really want to pay him to do research from the ground up when he's a miracle worker everywhere else.

---

### Post by frotzed on 2011-05-12
I also work inside a Windows Domain environment.  I've not yet tried connecting my ubuntu laptop to the domain but I'll be sure to give it a shot and if I gain any ground I'll post it here.

Certain things I'm wondering are:

1) Are you just trying to connect to the domain? or
2) Are you trying to use an exchange server for your mail also?

Edit: After a quick search I found an application called "Likewise Open" that says it will connect a linux PC to a Windows Active Directory environment.  [http://www.likewise.com/products/likewise_open/](http://www.likewise.com/products/likewise_open/)

---

### Post by semisquirrel on 2011-05-12
> **frotzed said:**
> 
Certain things I'm wondering are:

1) Are you just trying to connect to the domain? or
2) Are you trying to use an exchange server for your mail also?


This is mostly for a few shared folders on the server, all of which are password protected.

---

### Post by cek on 2011-05-12
It's relatively straight forward.

First, make a mount point for it, anywhere you want, I used /mnt to keep all my mount points in a similar location.
```
sudo mkdir /mnt/windows_share
```

Now, mount it.  Replace 1.1.1.1 with the server's IP address, and ShareName with the name of the share you want to access.

```
sudo mount -t cifs -o username=<your user name> //1.1.1.1/ShareName /mnt/windows_share
```

Note, this line of code may prompt you for a password TWICE, the first prompt is for sudo (your local password) the second prompt will be for the password of the user specified with username in the mount options.

If you are OK with storing the password to the machine in plain text on your ubuntu box, you can set this up to mount automatically in fstab.  However, since that is unlikely, I'll save that for another post.

---

### Post by YesWeCan on 2011-05-12
Presumably, you can also connect using Nautilus:
Places/Connect to Server, choose Windows Share, etc.
This should mount the share and display an icon for it on your desktop.

---

