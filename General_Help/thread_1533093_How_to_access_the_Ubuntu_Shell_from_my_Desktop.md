---
title: "How to access the Ubuntu Shell from my Desktop"
date: 2010-07-17
forum: General Help
---

### Post by tsreekaanth on 2010-07-17
*Hi All*
 
*I need to access the shell prompt rather than GUI of Ubuntu. I have installed Ubuntu in Microsoft Virtual PC 2007 Sp1 wherein installation is successfull.*
 
*Now i have downloaded PuTTy to my WinXP Desktop. So by what IP can i connect with Ubuntu Shell. How to configure IP in both Ubuntu and in Windows XP so that this will look like i am accessing the shell remotely. *
 
*Can anyone help me in fixing this?*
 
*Thanks,*
*Sreekaanth*

---

### Post by wojox on 2010-07-17
You probably need to install [OpenSSH Server]("https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html")

---

### Post by Zorgoth on 2010-07-17
Indeed, ssh is the solution.  You can even run ssh -X to get a terminal capable of both command-line and graphical operations.

---

### Post by tsreekaanth on 2010-07-18
> **wojox said:**
> You probably need to install [OpenSSH Server]("https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html")
I tried to install Open SSH Server using the cmd 
 
>sudo apt-get install openssh-client
Successfull
>sudo apt-get install openssh-server
E: Package openssh-server has no installation candidate installation candidate
 
I am using ubuntu 8.10 Desktop Edition on Virtual PC 2007 and my Desktop is Win XP... 
 
Could you pls assist me further??

---

### Post by wojox on 2010-07-18
That's weird. Try them together and see what happens:

```
sudo apt-get install openssh-server openssh-client
```

---

### Post by tsreekaanth on 2010-07-19
> **wojox said:**
> That's weird. Try them together and see what happens:
 
```
sudo apt-get install openssh-server openssh-client
```
 
 
Still the same,
>sudo apt-get install openssh-server openssh-client
 
Reading package lists... Done
Building dependency tree
Reading state information.. Done
Package openssh-server is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package openssh-server has no installation candidate.

---

### Post by tsreekaanth on 2010-07-21
Should i need to update the Ubuntu Package manager to get Open SSH Server?? Please Advise...

---

### Post by tsreekaanth on 2010-07-27
How can we set IP address to Network configuration i.e. how can i include IP's in etc/host...

---

### Post by wojox on 2010-07-27
See what aptitude does

```
sudo aptitude update; sudo aptitude install openssh-server
```

Sometimes this will give you better results.

---

