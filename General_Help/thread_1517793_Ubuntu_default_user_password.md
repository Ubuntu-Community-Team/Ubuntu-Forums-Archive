---
title: "Ubuntu default user password"
date: 2010-06-25
forum: General Help
---

### Post by benwaynet on 2010-06-25
followed [http://bit.ly/bYuKmd]("http://bit.ly/bYuKmd")  

when it boots, it auto logs in as unbuntu as the user, but I dont know the password. never prompted during "install". 

My goal is to be able to ssh into the box once I know the password. I installed the ssh-server

thanks,jb

---

### Post by 3Miro on 2010-06-25
> **benwaynet said:**
> followed [http://bit.ly/bYuKmd]("http://bit.ly/bYuKmd")  

when it boots, it auto logs in as unbuntu as the user, but I dont know the password. never prompted during "install". 

My goal is to be able to ssh into the box once I know the password. I installed the ssh-server

thanks,jb

How do you install anything? Password is needed for updates and installing things from the software center. If you can do that, then you know the password. Other th an that, you can use this howto:

[http://www.botskool.com/geeks/how-recover-your-ubuntu-1004-password](http://www.botskool.com/geeks/how-recover-your-ubuntu-1004-password)

BTW during install, it asks for the password at the same time as it asks for the username and weather or not you want to auto-login.

---

### Post by benwaynet on 2010-06-25
There really wasn't in install. I used the universal usb installer. It never prompted me for anything.

I just checked the user name by whoami

I'm booting off a USB stick and running off the USB also.

---

### Post by sisco311 on 2010-06-25
> **benwaynet said:**
> followed [http://bit.ly/bYuKmd]("http://bit.ly/bYuKmd")  

when it boots, it auto logs in as unbuntu as the user, but I dont know the password. never prompted during "install". 

My goal is to be able to ssh into the box once I know the password. I installed the ssh-server

thanks,jb

The default password is blank, just press Enter when you are prompted for it. I would strongly suggest you to set up a strong password.

And for ssh you should use public key authentication instead of passwords.

[uhelp]community/SSH/OpenSSH/Keys[/uhelp]

---

### Post by benwaynet on 2010-06-25
even with blank it wouldn't let me change the password. but it let me create a new account with a password I know.

This is just a liveUSB install running for a temp reason to copy some files. 

thanks for your help

---

### Post by burton247 on 2010-06-25
```

sudo passwd USER

```

Should allow you to reset your password but if you don't know your password thats not that good. If you know roots password you could log into root first
```

su

```

then try it
```

passwd USER

```

---

### Post by efflandt on 2010-06-25
Assuming that you have persistent data (casper-rw file), even if you set a password for user ubuntu, that user auto logs in during live boot on USB iso.  But you can add another user and set a password for that user.  And you could put keys in their ~/.ssh/ dir.

I never allow ssh to work without keys, even locally, because my wireless is using 64(40) bit WEP.  But my wireless/modem/router is in the basement, so someone would have to be in my driveway to get a signal (drops off rapidly beyond my front porch).

---

