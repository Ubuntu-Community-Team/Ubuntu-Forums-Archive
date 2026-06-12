---
title: "log on"
date: 2006-03-01
forum: General Help
---

### Post by billh1241 on 2006-03-01
I finally have Breezy Badger installed but I either have forgotten my login or my password as I can not get into the program.  It says "login incorrect".

Is there a way that I can get around this.   Thanks. bill

---

### Post by Bachstelze on 2006-03-01
Reinstalling Ubuntu. I don't think there's another way.

---

### Post by glug101 on 2006-03-01
The only way that I can think of is by logging in using the root account.  

Userid: root
Passwd: (Whatever you set it to during installation)

open a terminal and type in:
```
ls /home/
```

The directory names listed will give you all the user names on the computer (except root).  Now:

```
passwd uid
```

Replace 'uid' with your userid and then follow the prompts to change your passwd.  

If you don't know your root passwd I regret that all is lost :(  Reinstall.

Hope this helps :)

---

### Post by Bachstelze on 2006-03-01
@glug : Ubuntu sets **no** root password during installation (unless run in expert mode)

---

### Post by Ramses de Norre on 2006-03-01
Boot into recovery mode, that will give you a root prompt, there you can do passwd user_name to set a new password.
If you've forgotten your username you will need to make a new user.
do useradd -d /home/user_name -g admin user_name

---

### Post by glug101 on 2006-03-01
That's right, I forgot that I had to do a 'sudo su' in order to set it up.  I'm used to other versions of linux.  

However, if it is the userid that is the problem (unlikely), he could use the livecd to view the home directory.

---

### Post by glug101 on 2006-03-01
[QUOTE=Ramses de Norre]Boot into recovery mode, that will give you a root prompt, there you can do passwd user_name to set a new password.
If you've forgotten your username you will need to make a new user.
do useradd -d /home/user_name -g admin user_name[/QUOTE]
Ubuntu has a recovery mode that lets you boot into root?  Tell me you need an install disk to do that.

---

### Post by Ramses de Norre on 2006-03-01
That's even a better way:)
(why do I always think of the hard ways..)

EDIT: yes the recovery mode gives you a root shell, I don't think there are restrictions on using it. But I'm not totally sure (never used it myself yet). You can set a password on your grub menu if you want.

---

### Post by glug101 on 2006-03-01
[QUOTE=Ramses de Norre]That's even a better way:)
(why do I always think of the hard ways..)

EDIT: yes the recovery mode gives you a root shell, I don't think there are restrictions on using it. But I'm not totally sure (never used it myself yet). You can set a password on your grub menu if you want.[/QUOTE]
Ok, I feel much better knowing that you can passwd protect it :)  I was afraid that anybody that could physically reboot the computer could make whatever changes they wanted. (*whew!*)

Now I can run Ubuntu and sleep at night :D

---

### Post by billh1241 on 2006-03-01
Thanks for the help, everybody.  I had to re install but my hard drive is old and small 6.5G so I could only install the basic program. I now am logged in but it only shows a black screen with the longin name and~$ is my hd too  small for any other ubuntu programs?

---

### Post by Ramses de Norre on 2006-03-01
Did you do a server install? try startx.
If that doesn't work: sudo apt-get install ubuntu-desktop (with the install cd inserted)

---

