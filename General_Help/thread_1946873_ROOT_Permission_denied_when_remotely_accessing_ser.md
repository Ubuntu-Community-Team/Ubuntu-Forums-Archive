---
title: "ROOT Permission denied when remotely accessing server"
date: 2012-03-25
forum: General Help
---

### Post by spindler on 2012-03-25
I have a weird problem.

I am attempting to edit some files on my Linux 11.04 server remotely through the SSH port 22.   I am using Putty to access the command line and I am using WinSCP to copy files from my windows desktop to the linux directory.

When I attempt to create a file using putty I do the following:

log in as the root.
go to director /etc/php5/apache2/conf.d
pico uploadprogress.ini   (  this is suppose to create a new file uploadprogress... and it does)
I then create my file inside the pico program.
when I save the file I get a error

permission denied.

I even attempted to create the file on my windows machine and transfer the file using WINSCP.  Again i get an error Permission denied.

What is going on?   I am using the SUDO command and something without the SUDO command.  Nothing seams to work.

Is it possible that somehow I lost SUDO privileges?

Why can't I transfer a file to the system folders as ROOT?

---

### Post by CharlesA on 2012-03-25
The root account is disabled on Ubuntu by default. You'd use sudo instead.

What happens if you use sudo?

---

### Post by spindler on 2012-03-25
I am using SUDO with an account that has SUDO permission.   This is the issue I have.  I can understand if my account did not have this permission but it does.   When I am located at the server I can do the changes required but when I remotely login and get this error.

---

### Post by perspectoff on 2012-03-25
I have had the same problem, but only since Maverick (it worked in Lucid). 

I have root login enabled on my system (which only requires setting a root password, since it really isn't disabled by default), but it is something to do with the SSH code. Haven't quite figured out the solution, yet.

Instead, I continue to do stuff as a user with sudo privileges when working in SSH/VNC, and that seems to work fine.

---

### Post by CharlesA on 2012-03-25
> **spindler said:**
> I am using SUDO with an account that has SUDO permission.   This is the issue I have.  I can understand if my account did not have this permission but it does.   When I am located at the server I can do the changes required but when I remotely login and get this error.
Run this on the server and post the output please:

```
sudo touch /etc/php5/apache2/conf.d/uploadprogress.ini
```

---

### Post by spindler on 2012-03-25
Well that did something.


When I ran....  Sudo touch /etc/php5/apach2/conf.d/uploadprogress.ini.... the file was created.  This is good.

Once the file was created using touch  I was then able to edit the file using pico.  This has worked to finish my current task.   

I am concerned that I still cannot upload other files. 

Any idea as to how to fix this issue so I can use WINSCP?

---

### Post by CharlesA on 2012-03-25
You'd have to login as root to upload files to somewhere other than your home directory. Are you trying to upload something to /var/www ?

---

### Post by spindler on 2012-03-25
I am logged in as a user with SUDO permission.... Since I only have one user with SUDO it is the root.   I did not set up a separate root user.

I am attempting to upload a file from my windows machine to a directory such as var/www  or etc/php5/apache2/conf.d.   This does not work.... I always get a permission denied error. 

When I upload a file as a SUDO user from my Windows machine to the home directory I can transfer the file just fine.

When I upload a file using a different user(without SUDO) into the home directory of that user then I can also transfer files just fine. 

I am only having issues with my SUDO user when I want to work with system files, which is most of the time since when I log in as the SUDO user I only work on system level files.  Other work involving projects or websites is done using the standard user.

---

### Post by CharlesA on 2012-03-25
Being able to use sudo and being root are two different things. See here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

You can either just ssh in and move the files from the home directory to their destination using sudo, or just ssh in and edit the files directly using sudo.

Either that or activate the root account and use that to transfer file (bad idea imo). The linked page will tell you how to do that, but I wouldn't advise it.

---

### Post by spindler on 2012-03-25
Yes I can edit the files now...as you have provided me the touch command.  So i can create a file now.  then just edit it with what I need.

I will look at the link you provided.

Thanks,

---

