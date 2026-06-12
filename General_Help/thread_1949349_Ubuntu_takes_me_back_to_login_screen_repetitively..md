---
title: "Ubuntu takes me back to login screen repetitively..."
date: 2012-03-30
forum: General Help
---

### Post by voodoochild16 on 2012-03-30
Hey all, I'm using a Dell Inspiron 17R right now and I have Ubuntu 11.10 installed and it runs pretty smoothly BUT... it likes to take me back to the login screen alot. Like small things trigger this, I'm talking when I click "empty trash" or when I click on almost anything and it happens only once in awhile like once or twice in an hour. It doesn't give me a kernal panic and not do anything, nothing like that. It just takes me to the log in screen. 

Other issues I had before was it not booting properly, I have it dual booting with Windows 7, so I disconnected all usb storage devices and that fixed it.. just thought I'd mention that. Any suggestions would be awesome, once I fix this issue I'll have it completely working as I have fixed all the other problems which I have not mentioned because they are not relevant but just this one problem.

---

### Post by Los Frijoles on 2012-03-30
Have you tried using another linux distro with the same kernel version as Ubuntu running on either a live CD or installed on your hard drive itself to see if the problem is common over all linux versions on your computer? If another version works then you can know that it is an Ubuntu specific problem.

Also, what do the system logs (/var/log/syslog) say right after you get kicked back to the login screen?

---

### Post by HomerWill on 2012-05-28
Hello, I am currently having this same problem with 12.04 and I need help. My friend is the one who installed Ubuntu. I have recently changed my password, and now I can only log in as a guest. When I type in the wrong password it says incorrect password. When I type it in correctly it takes me to a black screen for a minute then back to the login page. If there is any way to fix this easily I would greatly appreciate it.

---

### Post by HomerWill on 2012-05-28
Hello, I am seeking help. I have Ubuntu 12.04 installed, but it was installed by a friend so I cant just reinstall it. I dont know a lot about Linux, so if you guys dont help me I'm sort of going to be really upset that I can't get any help whatsoever. Why cant I log onto my own computer? I have the correct password and it keeps sending me back to the login page. Thanks in advance.

---

### Post by irv on 2012-05-28
> **HomerWill said:**
> Hello, I am seeking help. I have Ubuntu 12.04 installed, but it was installed by a friend so I cant just reinstall it. I dont know a lot about Linux, so if you guys dont help me I'm sort of going to be really upset that I can't get any help whatsoever. Why cant I log onto my own computer? I have the correct password and it keeps sending me back to the login page. Thanks in advance.

One thing about linux is it is case sensitive. When you enter your pass word at install and if you had the cap lock set you need to make sure you have it set when typing it in again. Or if it was not set when you enter it in at install, make sure it is not on when you try to login.  The password has to be exact if not you will never get logged in. Linux is a very secure OS, so if you forgot your password the only thing is to do a reinstall. The friend that install it for you might be able to help. Have you asked that person for help yet?

---

### Post by rmil on 2012-05-28
1. Generally it might be that your GDM is getting down for some reason try other layout such as kde, lxdm or xdm, you might have better response. I would also check what says dmesg command.

2. No need to reinstall ubuntu it is enough to use live CD in rescue mode and to reset password with or to go to rescue mode form grub menu

```
sudo passwd user
```

---

### Post by steeldriver on 2012-05-28
> **HomerWill said:**
> Hello, I am seeking help. I have Ubuntu 12.04 installed, but it was installed by a friend so I cant just reinstall it. I dont know a lot about Linux, so if you guys dont help me I'm sort of going to be really upset that I can't get any help whatsoever. Why cant I log onto my own computer? I have the correct password and it keeps sending me back to the login page. Thanks in advance.

If it sends you back to the login screen WITHOUT giving you a message (i.e. no 'incorrect password' or 'login incorrect' or somesuch) then it sounds like your xsession is failing to start - that is sometimes because of wrong ownership / permissions on your .Xauthority file

Try logging in to one of the virtual terminals (e.g. Ctrl-Alt-F1) - if that works then there is nothing wrong with your login or password - from there you can do

```
ls -al ~/.Xauthority
```which should respond with something like

```
-rw------- 1 yourusername yourusername 49 2012-05-23 09:55 /home/yourusername/.Xauthority
```It sometimes happens that this file becomes owned by 'root' - if so then unless your friend added you to the sudo/admin group, you will have to have someone with sudo privileges log in and then remove the file 

```
sudo rm /home/<yourusername>/.Xauthority
```

If logging in to the virtual terminal doesn't work then try the password reset described by rmil

---

