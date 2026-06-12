---
title: "sshfs runs fine but can't see the mounted content"
date: 2011-07-31
forum: General Help
---

### Post by jieyunfu on 2011-07-31
Hi all, 

I was able to run sshfs successfully, but I am not able to access the mounted folder. For example, if I execute the following commands, I will get stuck at the last step "cd folder" forever. 

username@username-laptop:~$ sshfs username@IP_address: folder
username@IP_address's password: 
username@username-laptop:~$ cd folder

similarly, if I try to do a "ls" in the parent folder, it will also get stuck. 

I am able to ssh to the remote server though. 

Any idea why? 

Thanks!

---

### Post by spiky001 on 2011-07-31
When you have ssh in can you do ```
cd  /home/user/
```

---

### Post by jieyunfu on 2011-07-31
> **spiky001 said:**
> When you have ssh in can you do ```
cd  /home/user/
```

Yes, I can.

---

### Post by spiky001 on 2011-07-31
Where is the mounted folder /media/folder/

---

### Post by jieyunfu on 2011-07-31
It is just an ordinary folder in my local home directory. 

I used to be able to sshfs, but after I moved to this new (local) computer I can't do it anymore. weird. 

> **spiky001 said:**
> Where is the mounted folder /media/folder/

---

### Post by spiky001 on 2011-07-31
Have you tried running the ls command while ssh into server

---

### Post by jieyunfu on 2011-07-31
yes, everything on the remote server looks fine. 

> **spiky001 said:**
> Have you tried running the ls command while ssh into server

---

### Post by spiky001 on 2011-07-31
Ok I dont use sshfs just ssh, so cant help to much, I did find [this]("http://hintsforums.macworld.com/archive/index.php/t-65259.html")
Is there a reason for sshfs?

---

### Post by jieyunfu on 2011-07-31
> **spiky001 said:**
> Ok I dont use sshfs just ssh, so cant help to much, I did find [this]("http://hintsforums.macworld.com/archive/index.php/t-65259.html")
Is there a reason for sshfs?

well sshfs provides an easy way to work remotely. VNC is unnecessarily slow. I can just mount the remote projects and use local Eclipse to develop, rather than VNC/X11 forwarding, or using not-so-user-friendly command line tools such as emacs/vim.

---

### Post by spiky001 on 2011-08-01
Have you tried Remmina remote desktop i find it a lot faster than vnc, That is if you dont get to the bottom of sshfs problem, It also runs through ssh as well

---

### Post by pinki999 on 2012-06-17
Hi,

I too have the same problem.  How did you rectify it?


Cheers

---

