---
title: "Password suddenly stopped working on Ubuntu Server"
date: 2011-11-08
forum: General Help
---

### Post by TigerFire14 on 2011-11-08
Hello,

I recently installed ubuntu server to use as a LAMP server. I just logged in via SSH, and tried to execute a sudo command. It gave me the message: 
```
username is not in the sudoers file.  This incident will be reported.
```I tried logging in from the computer directly and it said my password was wrong!:confused:
I am using the original user I originally set up. This was working earlier today. I was about to do a reinstall, but thought I'd see if I could fix it first.
 
Anybody know whats going on?
Thanks!

---

### Post by papibe on 2011-11-08
Somehow to got yourself out of the admin group.

Here's a [guide ]("http://psychocats.net/ubuntu/fixsudo")to recover from that situation.

Regards.

---

### Post by TigerFire14 on 2011-11-08
Ok, when I hold down the shift key at boot, I see the boot options screen flash, and then it continues normally. How do i get it to stay?

---

### Post by papibe on 2011-11-09
Once you see the menu, I believe if you press the down arrow key, grub will set itself into interactive mode.

Regards.

---

### Post by TigerFire14 on 2011-11-09
So i got into the root shell prompt, and now it says:
```
Adding user 'username' to group 'admin'...
Adding user username to group admin
gpasswd: cannot lock /etc/group; try again later.
adduser: '/usr/bin/gpasswd -a username admin' returned error code 1. Exiting.
```What does that mean?

---

### Post by papibe on 2011-11-09
Looks like there are already locks (something went wrong?). Check it like this:
```
ls /etc/passwd.lock /etc/shadow.lock /etc/group.lock /etc/gshadow.lock
```
If you are in safe mode, with a root prompt (#) you can delete them:
```
rm -i /etc/passwd.lock /etc/shadow.lock /etc/group.lock /etc/gshadow.lock
```
And then try again to add yourself to the admin group.

Hope it helps,
Regards.

---

### Post by TigerFire14 on 2011-11-09
It says No such file or directory. Would it just be easier to reinstall everything?

---

### Post by TigerFire14 on 2011-11-09
Alright, I figured it out. Apparrently recovery mode was in read only mode. Once i fixed that:
```
mount -rw -o remount /
```
It worked perfectly. Thanks for the help!

---

### Post by papibe on 2011-11-09
#-o Oh my! very interesting!

:) Thanks for posting that! When you have the chance, mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people can take notice.

Kind Regards.

---

