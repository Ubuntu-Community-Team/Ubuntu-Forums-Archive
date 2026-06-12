---
title: "PROFTPD Help!"
date: 2011-11-27
forum: General Help
---

### Post by singh763173 on 2011-11-27
Hi all,

I have been playing around with Ubuntu Server 11.10 with basic OpenSSH package installed from setup.

I have installed proftpd and have been playing around with users and directories etc but came across one issue. I now have two users using the following command
sudo useradd username -p password -d /home/directory -s /bin/false

the above works great but what I really want to do is, make "username" only see "directory". At present, when I log in with "username" I am pointed to "directory" but I can back out of that directory and go to the home directory thus allowing access to other directories (using filezilla on windows).

User, how would I go about editing and deleting users? I have also been looking at trying to remove and edit permissions but I cant seem to figure it out.

Hopefully you guys understand what I mean!

Thanks in advance

---

### Post by Dry Lips on 2011-11-27
> **singh763173 said:**
> Hi all,

I have been playing around with Ubuntu Server 11.10 with basic OpenSSH package installed from setup.

I have installed proftpd and have been playing around with users and directories etc but came across one issue. I now have two users using the following command
sudo useradd username -p password -d /home/directory -s /bin/false

the above works great but what I really want to do is, make "username" only see "directory". At present, when I log in with "username" I am pointed to "directory" but I can back out of that directory and go to the home directory thus allowing access to other directories (using filezilla on windows).

User, how would I go about editing and deleting users? I have also been looking at trying to remove and edit permissions but I cant seem to figure it out.

Hopefully you guys understand what I mean!

Thanks in advance

In order for this to work you'll have to add this line to **/etc/shells**
```
/bin/false
```

Generally speaking I'd say that ssh is generally considered a safer choice than regular
ftp. The downside is that locking the user in their home directory is a bit more tricky.

---

### Post by singh763173 on 2011-11-27
Hey dry lips, I have added that line into the shells file - from what I have seen, these only means that users cant log in to the server? am i wrong?

so when I use filezilla and log in with a user, i go directly to the path that was setup but i can still see the home path and click into that which then shows all other directories. - The aim is, once I have mastered it, I can then allow for other users to host sites on my server via FTP or SSH.

also, ssh would be great but im still a little bit of an amateur with linux - need to find a writeup/ howto explaining ssh and user management. 

I am more than proficient with Windows Server and have managed them for a while so understand the way things work, its just getting the hands on experience atm.

If you know of any write ups on ssh access and user management, please feel free to link me to them!

---

### Post by Dry Lips on 2011-11-27
> **singh763173 said:**
> Hey dry lips, I have added that line into the shells file - from what I have seen, these only means that users cant log in to the server? am i wrong?
 

It removes shell access from the FTP users... I saw that you used **-s /bin/false**,
I just pointed out that you would have to add this "false" shell to the shells file
in order for this to work. (I assumed you knew what this meant ;))

> 
so when I use filezilla and log in with a user, i go directly to the path that was setup but i can still see the home path and click into that which then shows all other directories. - The aim is, once I have mastered it, I can then allow for other users to host sites on my server via FTP or SSH.


If you use SSH you could chroot your users in order to jail your users. (Give me a couple of minutes and I'll try to see if I can dig up a little more information for you.)

---

### Post by singh763173 on 2011-11-27
> **Dry Lips said:**
> If you use SSH you could chroot your users in order to jail your users. (Give me a couple of minutes and I'll try to see if I can dig up a little more information for you.)

Cheers dude :)

Is it actually possible with FTP aswell? Want to try and get both working if possible.

---

### Post by singh763173 on 2011-11-27
Dry Lips!

I've figured it out. Dont ask me why I thought to do this... I dont even know myself haha. I was looking for a web interface for Ubuntu Server and found WebMin. So I installed it... after all its just a test server.

Found the proftpd server settings under servers and then click Files and Directories and changed the option to Home Directory. Restarted proftpd and there you have it. No access to other files :D

I dont care about accessing system files because I can just use root with WinSCP or even SSH with Putty to move files around.

I'm quite proud of myself lol - But if I have done anything wrong, please do let me know!

---

### Post by Dry Lips on 2011-11-27
Excellent! I don't use webmin that much myself, but if you've tested it then I guess it
works. ;)

If you sometime need to setup chrooted SSH, you could check out this tutorial:
[http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny](http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny)

Cheers,
Dry Lips

---

### Post by singh763173 on 2011-11-27
Thanks mate, You dont mind if I add you as a friend - if I have any issues with the CHRooted SSH, maybe I could send you a message?

Cheers

---

### Post by Dry Lips on 2011-11-27
> **singh763173 said:**
> Thanks mate, You dont mind if I add you as a friend - if I have any issues with the CHRooted SSH, maybe I could send you a message?

Cheers

No problem at all... Glad to be able to help!

---

