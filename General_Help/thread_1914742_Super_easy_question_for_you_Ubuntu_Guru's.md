---
title: "Super easy question for you Ubuntu Guru's"
date: 2012-01-25
forum: General Help
---

### Post by kcirrab on 2012-01-25
ok if I manually type the following into terminal it works perfectly.

$ cd '/home/debra/teamspeak3-server_linux-x86'
$ sudo ./ts3server_startscript.sh start

now I would love to make a file like a .bat file (.sh on Ubuntu I believe) to run this at startup or atleast where i can click it and it will run? any help?

Thanks!

PS Im running Ubuntu 11.04

---

### Post by sgage on 2012-01-25
You can put those commands at the end of the rc.local script in /etc/init.d, and they will run at startup.

---

### Post by Dngrsone on 2012-01-25
You can script it thus:

```
#!/bin/bash
cd '/home/debra/teamspeak3-server_linux-x86'
sudo ./ts3server_startscript.sh start

```

It will ask you for a password, since you are calling sudo.

---

### Post by raja.genupula on 2012-01-25
you have to disable sudo passwod prompt for that script . 
follow this link , it will explain you what you need ,
[https://help.ubuntu.com/community/RootSudo#Remove_Password_Prompt_For_sudo](https://help.ubuntu.com/community/RootSudo#Remove_Password_Prompt_For_sudo)

[https://help.ubuntu.com/community/UbuntuBootupHowto#Init_scripts](https://help.ubuntu.com/community/UbuntuBootupHowto#Init_scripts)

all the best.

---

### Post by gsgleason on 2012-01-25
You would be better off making an ubuntu style startup script that will automatically run at your runlevel.

Or, just put this in /etc/rc.local:

/home/debra/teamspeak3-server_linux-x86/ts3server_startscript.sh start

---

### Post by kcirrab on 2012-01-25
> **Dngrsone said:**
> You can script it thus:

```
#!/bin/bash
cd '/home/debra/teamspeak3-server_linux-x86'
sudo ./ts3server_startscript.sh start

```

It will ask you for a password, since you are calling sudo.

This is not working :/ I decided not to call sudo.. I only did it just to be sure there was no problems but either with or without its not working... although if i copy and paste the two commands from the .sh file it works -.- idk I will include my file maybe Im doing it wrong

*will include in 5 min when computer reboots

---

### Post by kcirrab on 2012-01-25
Ok I figured out I do need to keep sudo although the .sh file is not working. i will attach it below for viewing

PART 2 of above post

---

### Post by bouncingwilf on 2012-01-25
You need to mark the script as executable before it will run;

chmod+x Teamspeak.sh should do it or right click with nautilus and click on permissions and allow executing as a program

Bouncingwilf

---

### Post by kcirrab on 2012-01-25
> **bouncingwilf said:**
> You need to mark the script as executable before it will run;

chmod+x Teamspeak.sh should do it or right click with nautilus and click on permissions and allow executing as a program

Bouncingwilf

I did this. and it pops up I click run in terminal terminal appears for a second looks like it does something and disappears although the file has infact NOT been started

---

### Post by ZaidQazi on 2012-01-25
Hi 
Now my problem is a bit scratchy.. 
I am try LAMP development
but i am facing some good probs..
I successfully configured the LAMP and its running pretty fine...
At first i had problem using it as it didn't allow me to copy-paste into /var/www directly until i used sudo at terminal
which later on i did bypass :guitar:
I successfully configured Wordpress folder over it
but now I have a problem creating my own folder and creating an index.php(i.e. my own row development) but that does not open on the browser 

example::
I have created a folder TestWeb
and I have index.php in it 
LAMP running
and localhost working fine in browser
even localhost/wordpress runs great
but localhost/TestWeb doesn't..
So I try localhost/TestWeb/index.php
Following Error msg shows up
------------------------------------------------
Server error
The website encountered an error while retrieving [http://localhost/TestWeb/](http://localhost/TestWeb/). It may be down for maintenance or configured incorrectly.
HTTP Error 500 (Internal Server Error): An unexpected condition was encountered while the server was attempting to fulfill the request.
------------------------------------------------

Help!!!! :confused:

---

### Post by kcirrab on 2012-01-25
> **zaidqazi said:**
> hi 
now my problem is a bit scratchy.. 
I am try lamp development
but i am facing some good probs..
I successfully configured the lamp and its running pretty fine...
At first i had problem using it as it didn't allow me to copy-paste into /var/www directly until i used sudo at terminal
which later on i did bypass :guitar:
I successfully configured wordpress folder over it
but now i have a problem creating my own folder and creating an index.php(i.e. My own row development) but that does not open on the browser 

example::
I have created a folder testweb
and i have index.php in it 
lamp running
and localhost working fine in browser
even localhost/wordpress runs great
but localhost/testweb doesn't..
So i try localhost/testweb/index.php
following error msg shows up
------------------------------------------------
server error
the website encountered an error while retrieving [http://localhost/testweb/](http://localhost/testweb/). It may be down for maintenance or configured incorrectly.
Http error 500 (internal server error): An unexpected condition was encountered while the server was attempting to fulfill the request.
------------------------------------------------

help!!!! :confused:

what the hell you hijacked my thread?!

---

### Post by bouncingwilf on 2012-01-25
Open a separate terminal to run it then you will be able to see any error messages before it closes.

Bouncingwilf

---

### Post by kcirrab on 2012-01-25
if i copy and paste the contents (the commands) it works perfectly.. if I use a .sh file it does not

---

