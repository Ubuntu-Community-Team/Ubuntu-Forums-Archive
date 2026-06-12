---
title: "Permissions problem"
date: 2010-05-20
forum: General Help
---

### Post by held7over on 2010-05-20
Ubuntu 10.04

I have the following statement in a script and it worked great yesterday:

```
sudo echo deb http://download.virtualbox.org/virtualbox/debian lucid non-free >> /etc/apt/sources.list
```


But today, from the command line the same statement gives me:

> bash: /etc/apt/sources.list: Permission denied

What could be causing this problem? Why wouldn't sudo have permission? I originally tested the above statement on the command line before I put it in my script and had no problems. 

(I got an authentication error this morning and I manually removed the url from sources.list and removed the key, and then discovered my statement wouldn't put the url back into the sources.list, whereas it originally put it there in the first place! Ha!) 

Thanks!

---

### Post by 3Miro on 2010-05-20
Try:
```
ls -al /etc/apt/sources.list
```

What I get is:
```
-rw-r--r-- 1 root root *some stuff here* /etc/apt/sources.list
```

If you see something else, then you have messed the permissions somehow.

To fix the root root part:
```
sudo chown root:root /etc/apt/sources.list 
```

To fix the -rw-r--r-- part
```
sudo chmod 644 /etc/apt/sources.list
```

---

### Post by held7over on 2010-05-20
lucky@ispy:~$ ls -al /etc/apt/sources.list
-rw-r--r-- 1 root root 3002 2010-05-20 11:52 /etc/apt/sources.list

Hmmmm. That doesn't appear to be the problem.

---

### Post by 3Miro on 2010-05-20
Try entering the PPA from the software source manager. System -> Admin -> Software Sources. Go to third party and select "add". You need to add:

```
deb http://download.virtualbox.org/virtualbox/debian lucid non-free
```

---

### Post by held7over on 2010-05-20
3Miro.  There is no problem entering the url from the GUI. However, I need it to work from my script. 

(Currently, I am assuming if it doesn't work from the command line, it is not working from my script either.)

---

### Post by 3Miro on 2010-05-20
> **held7over said:**
> 3Miro.  There is no problem entering the url from the GUI. However, I need it to work from my script. 

(Currently, I am assuming if it doesn't work from the command line, it is not working from my script either.)

If doesn't work form the command line, it will not work from the script.

If your permissions are correct, there is no reason why bash would return "Permission Denied". I would try it again in another terminal to make sure the original command wasn't misspelled, but you have probably already done that. I am out of ideas unfortunately.

---

### Post by held7over on 2010-05-20
I wrote it by hand in a new Terminal Window and got the same result:

> lucky@ispy:~$ sudo echo deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) lucid non-free >> /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied


This is just plain weird. I have even rebooted the machine.

---

### Post by bodhi.zazen on 2010-05-21
> **held7over said:**
> I wrote it by hand in a new Terminal Window and got the same result:




This is just plain weird. I have even rebooted the machine.

You can not re-direct with echo & sudo ....

You can either 

```
sudo bash -c "echo 'deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian)  lucid non-free' >> /etc/apt/sources.list"
```

Or use tee

```
echo 'deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian)  lucid non-free' | sudo tee -a /etc/apt/sources.list
```

[http://notfaq.wordpress.com/2007/09/26/unixlinux-redirect-output-as-sudo/](http://notfaq.wordpress.com/2007/09/26/unixlinux-redirect-output-as-sudo/)

[http://initialprogramload.blogspot.com/2007/06/toturial-caveat-with-redirecting-from.html](http://initialprogramload.blogspot.com/2007/06/toturial-caveat-with-redirecting-from.html)

---

### Post by held7over on 2010-05-21
Thanks bodhi.zazen! Those work great. I will study the references you also kindly included. It appears I am learning a lot of scripting lessons on this little project!

I have another sudo based question if you have the time. I am chaining a set of shell scripts sequentially one after another, all of which have sudo commands inside of them and normal commands, and I launch the first one with this command:

sudo ./program_1

Is it necessary after that for the next program being chain launched  from the first program to again use sudo in front of the program path and name being called, to carry sudo authorization to that next program?  (I am only wanting to have to enter my password once at the beginning...)

---

### Post by bodhi.zazen on 2010-05-21
> **held7over said:**
> Thanks bodhi.zazen! Those work great. I will study the references you also kindly included. It appears I am learning a lot of scripting lessons on this little project!

I have another sudo based question if you have the time. I am chaining a set of shell scripts sequentially one after another, all of which have sudo commands inside of them and normal commands, and I launch the first one with this command:

sudo ./program_1

Is it necessary after that for the next program being chain launched  from the first program to again use sudo in front of the program path and name being called, to carry sudo authorization to that next program?  (I am only wanting to have to enter my password once at the beginning...)

You should write a bash script :

```
#!/bin/bash

command 1 
command 2 

...

exit 0
```

Save the script in ~/bin for personal use, /usr/local/bin for shared use. The script will then be on your path.

If you run the script with sudo, all the commands in the script will be run as root. So, if you run sudo script_name you will enter you password only once.

If you run a script as a user, but need to call a few commands as root, configure sudo to allow you to run those commands without a password.


You can use sudo to set an alternate user if needed.

sudo -u user command

In scripts:

1. Use full paths to commands.

2. If the script, or parts of it, are to be run as root (via sudo) it should be owned by root and only root should be able to write to the script.

---

