---
title: "Installing Audio Drivers"
date: 2009-12-09
forum: General Help
---

### Post by Delco239 on 2009-12-09
Hi
I have just installed my first Linux, ubuntu 9.10 and am very impressed. I have a dual boot machine and intend to get to the state where I only use Windows XP for running games.  In fact I am only one step away and that is the problem.  I do a lot of audio work for the local school and use a Sound Blaster FXI Platinum card.  
There are drivers for it on the Creative website and I have them downloaded. They are XFiDrv_Linux_Public_US_1.00.tar.gz and come with quick install instructions but I need someone to explaine the Terminal commands to install them, The Doc says, In terminal,
 
1) Goto source directory 
2) Execute make command as root 
   make 
   make install.

I am assuming that as it was a tar.gz file it needed extracting and this I have done. I know the basic Terminal commands but, they do not seem to cover this. Can someone be so kind as to list the sequence of commands for me.

Delco

---

### Post by LuisGMarine on 2009-12-09
When it says to run "these commands as root", all you need to do is throw a 'sudo' before that command.

So it would look something like this:

```
sudo make
```

Here is the link that explains the whole ordeal with root and Ubuntu.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Ubuntu doesn't have a root user.  Instead it temporarily grants those "root" permissions to a user.  Root is the equivalent to running Windows with Administrative account.  Hope this helps you!

---

