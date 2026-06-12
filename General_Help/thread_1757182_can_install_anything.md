---
title: "can install anything"
date: 2011-05-13
forum: General Help
---

### Post by eyalmmm on 2011-05-13
Hello i formated my pc and i installed linux ubuntu server 
i wanted to install webmin but it asks me to install apt-show-versions i tried to install it but it asked somting else and again 
and not working 
i also tried to install the 32 bit binary and problem 
what can i do?

another thing 
i tried to open a game server for cs 1.6 
with bm mode that allow the user to save the blocks that he built in a file in the server folder 
but when i save it the file isnt created what can i do please help me

---

### Post by eyalmmm on 2011-05-13
please help me i need it so much

---

### Post by eyalmmm on 2011-05-13
dump
^^^

---

### Post by matt_symes on 2011-05-13
Hi

What version of Ubuntu are you using ? Post the output of 

```
cat /etc/lsb-release
```

and 

```
uname -a
```

from the console.

> **eyalmmm said:**
> Hello i formated my pc and i installed linux ubuntu server 
i wanted to install webmin but it asks me to install apt-show-versions i tried to install it but it asked somting else and again 
and not working 
i also tried to install the 32 bit binary and problem 
what can i do?

What command did you use to try to install webmin ? Where did you get the binary from ? Can you install any other package using apt-get such as htop ?

> another thing 
i tried to open a game server for cs 1.6 
with bm mode that allow the user to save the blocks that he built in a file in the server folder 
but when i save it the file isnt created what can i do please help me

What file is not created and where ?

Kind regards

---

### Post by eyalmmm on 2011-05-13
thank u very much 
so 
DISTRIB_ID = UBUNTU
DISTRIB_RELEASE = 11.04
DISTRIB_CODENAME = natty
DISTRIB_DESCRIPTION ="Ubuntu 11.04"

and the file is the name of the map .ex 
i mean the map that the blocks saved at 
ex de_dust2.ex 
and i can see that 
its in 
server/cstrike/addons/amxmodx/data/ex

Thank u

---

### Post by matt_symes on 2011-05-13
Hi

Can you also answer these three question please.

What command did you use to try to install webmin ? Where did you get  the binary from ? Can you install any other packages using apt-get such  as htop ?

Kind regards

---

### Post by eyalmmm on 2011-05-13
to install webmin I used [http://www.instructables.com/id/HLDS-Counter-Strike-16-Linux/step5/Installing-Webmin/](http://www.instructables.com/id/HLDS-Counter-Strike-16-Linux/step5/Installing-Webmin/)
and i can install htop

---

### Post by matt_symes on 2011-05-13
Hi

Sorry for the delay. I was eating. To install Webmin on your server follow these instructions in this web page.

[http://www.ubuntugeek.com/how-to-install-webmin-on-ubuntu-11-04-natty-server.html](http://www.ubuntugeek.com/how-to-install-webmin-on-ubuntu-11-04-natty-server.html)

That should get Webmin installed for you. After that we will look at counter strike.

Kind regards

---

### Post by eyalmmm on 2011-05-13
its working thank u so now how do i fix the save problem?

---

### Post by matt_symes on 2011-05-13
Hi

I'm glad webmin is fixed. I have never installed cs on a server so i might not be the best person to answer this.

If others have then please add your input.

In the meantime i want to check it's not a permissions issue.

```
server/cstrike/addons/amxmodx/data/ex
```This is a relative path. What is the full path ? When you know that can you post the output of

```
ls -l <full_path>
```where that is a small L after ls and <full_path> is the full path to sctrike/..../data/ex.

I will also read thought that guide for you and see if i can identify what the problem might be.

Kind regards

---

### Post by eyalmmm on 2011-05-13
hey dude i got problem with the webmin the pass i enter isnt right but it is the real pass i use to connect to ubuntu server

---

### Post by matt_symes on 2011-05-14
Hi

> **eyalmmm said:**
> hey dude i got problem with the webmin the pass i enter isnt right but it is the real pass i use to connect to ubuntu server

Sorry for the late reply. Time zones.  When you log into the server using webmin, are you using the user name and password you set up on the server ?

Also please post the output of 

```
uname -a
```

from the server so i can see if it is 32 or 64 bit.

Kind regards

---

### Post by eyalmmm on 2011-05-14
its 64 bit 
and the pass is the server pass i think 
thats what i tried

---

### Post by matt_symes on 2011-05-14
Hi

Have you installed the 32-bit libraries for counter strike to work ?

Kind regards

---

### Post by eyalmmm on 2011-05-14
i installed the 32 bit library and its works but the webmin doesnt work
edit 
how do i edit the premmision of a whole directory with files in it?

---

### Post by matt_symes on 2011-05-14
Hi

> **eyalmmm said:**
> webmin doesnt work

I have just read that installation guide i posted the link for thoroughly.

At the bottom it says

> You need to enter root username and password to login.This quite suprised me as i use webmin and it has always accepted my user name and password that i  set up on the server. That account is a member of the sudoers group.

Saying that, i did not install it via apt-get but installed it using a  deb file. I am wondering if there is some difference between the repository  install and the deb install.

This is installation instructions for the deb install.

[http://www.havetheknowhow.com/Configure-the-server/Install-Webmin.html](http://www.havetheknowhow.com/Configure-the-server/Install-Webmin.html)

Anyways, to get it working on your system with your current setup you are going to have to enable the root account.

Log into your server and type

```
sudo passwd root
```Enter your password. It will not be echoed to the screen. This is normal.

It will then ask you to enter roots password. Enter a password. It will then ask you to confirm roots password. Re-enter the password you just entered

The from your client open a browser and type the url to bring up the webmin login screen.

Enter  root as your user name and enter the password you set up in the preceding steps. That should log you in. Not my favoured solution but there you go.

Your other option is to try to install from the deb file after purging the apt-get version and that will hopefully allow you to log on using sudo privileges. This is the method i use.

Kind regards

---

### Post by eyalmmm on 2011-05-14
thank u so much this is working so now how do i make an ftp server with users that i can give them thier own directory and they cant go more then it 
example :
user : dude directory: /home
so the user dude cant go to /

---

### Post by matt_symes on 2011-05-15
Hi

Have a look at vsftp.

Kind regards

---

