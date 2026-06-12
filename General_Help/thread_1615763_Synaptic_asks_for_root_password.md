---
title: "Synaptic asks for root password"
date: 2010-11-07
forum: General Help
---

### Post by brumb on 2010-11-07
Evening all,

I can't use synaptic. Starting it from the gui appears to make it ask for the root password (of which there is none!). If i sudo synaptic, it starts fine with the appropriate privileges.

I ran into this problem first when I used rhythmbox for the first time. It needed to install plugins for my mp3s, but I can't authenticate into synaptic. The dialogue asks for "Password for root:", where I think it should ask for "Password for $USER:"

Why is this, and what can I do about it.

Thanks in advance,

Charlie

PS, This is a fresh install of 10.10. When transferring my old userfiles over from my old Karmic install I had to userdel the user I used when installing, and then create another user with the same name and details. The reasons for this escape me at the moment, and no doubt were entirely of my own making, but that's what happened. Has this got something to do with it?

---

### Post by dino99 on 2010-11-07
give your user password when synaptic ask for it

system -> admin -> synaptic

*** note: you ALWAYS need "sudo" to run app into a terminal and give the user password, otherwise it ask for root password (thats how linux deal with security)

see links below for more info

---

### Post by sisco311 on 2010-11-07
Hi,

Run:```
gksu-properties
```and set the *Authentication mode* to sudo.

---

### Post by coffeecat on 2010-11-07
> **brumb said:**
> PS, This is a fresh install of 10.10. When transferring my old userfiles over from my old Karmic install I had to userdel the user I used when installing, and then create another user with the same name and details. The reasons for this escape me at the moment, and no doubt were entirely of my own making, but that's what happened. Has this got something to do with it?

I believe so. I came across this issue when I did a netinstall chrooting from another partition and creating a user from the terminal. sisco311's reply will fix it. You can also do gconf-editor > apps > gksu > tick sudo-mode.

Before you do this, try Synaptic with gksudo and gksu. With gksudo you are prompted for your user password; with gksu the (non-existent) root password.

---

### Post by sisco311 on 2010-11-07
> **coffeecat said:**
> 
Before you do this, try Synaptic with gksudo and gksu. With gksudo you are prompted for your user password; with gksu the (non-existent) root password.

gksudo is just a symbolic link to gksu...

---

### Post by coffeecat on 2010-11-07
> **sisco311 said:**
> gksudo is just a symbolic link to gksu...

True, but that makes no difference. Have a look at this:

[http://ubuntuforums.org/showthread.php?t=1577781](http://ubuntuforums.org/showthread.php?t=1577781)

Your  point puzzled me and I mention it  in my first post

---

### Post by ajgreeny on 2010-11-07
> PS, This is a fresh install of 10.10. When transferring my old userfiles  over from my old Karmic install I had to userdel the user I used when  installing, and then create another user with the same name and details.  The reasons for this escape me at the moment, and no doubt were  entirely of my own making, but that's what happened. Has this got  something to do with it?When you made the new user did you make sure that he/she had admin group membership?  Only the first user has this by default, so it is possible that your new one does not.  To put that right you will need to reboot in recovery mode and run 
```
adduser <username> admin
```or ```
usermod -aG admin <username>
``` using your current username where I have typed that of course.  Note that as you will be in recovery mode you will not need **sudo** for the command.

---

### Post by brumb on 2010-11-07
> **ajgreeny said:**
> When you made the new user did you make sure that he/she had admin group membership?  Only the first user has this by default, so it is possible that your new one does not.  To put that right you will need to reboot in recovery mode and run 
```
adduser <username> admin
```or ```
usermod -aG admin <username>
``` using your current username where I have typed that of course.  Note that as you will be in recovery mode you will not need **sudo** for the command.

I added my main user acc the to admin group, but this didn't solve the synaptic privileges issue. It did mean I could remove the user's very own line from the sudoers file though! (I couldn't understand why the newly created user with the same name as the old user I'd deleted couldn't sudo anything. Now I guess I do.)

The gksu-properties solution did the trick with the synaptic issue though.

Thank you all.

---

### Post by sisco311 on 2010-11-07
> **coffeecat said:**
> True, but that makes no difference. Have a look at this:

[http://ubuntuforums.org/showthread.php?t=1577781](http://ubuntuforums.org/showthread.php?t=1577781)

Your  point puzzled me and I mention it  in my first post

Thanks!

---

