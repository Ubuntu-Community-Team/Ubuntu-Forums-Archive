---
title: "permission denied"
date: 2011-05-27
forum: General Help
---

### Post by yvesbodson on 2011-05-27
[SIZE=1]Hello 

Two days ago I downloaded  [/SIZE][SIZE=1][COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C]Ubuntu 11.04 server
I cold reach the point of package management.  There I got lost ...
could not find out how and what to install because the interface just did not work for me.
The reason I need the server is to get a home server on which one I can do development instead of using the company server because the net is so bad here (south of France) that I have problems with data synch etc..
So I want to setup a Linux HTTP server with MySQL  and PHP.
My problem is that at the level of package management I just run out of knowing what to do., If I press gg I end up with the system telling me to restart and then failed.
To pass through that I have installed the desktop version, which works great.  Now I have downloaded Apache, MySQL and PHP .
I cannot install anything.  I get permission denied.
Can somebody help here...
I have been looking around for the permission system on Unix and I am quite ok with it, but in my case I don't seem to be able to get these apps installed???
Thanks in advance
Yves

[/COLOR][/FONT][/COLOR][/SIZE]

---

### Post by LordNeo on 2011-05-27
Reinstall just selecting the "LAMP" package (linux, apache, mysql, php) and follow the onscreen instrucctions for setting the mysql password and stuff.

After that i recommend you to install webmin to get a simple to use web interface

---

### Post by grahammechanical on 2011-05-27
Hi

I am not an expert but how did you download Apache, MySQL and PHP? Through the Ubuntu software Centre? Through the Synaptic Package Manager? Both of these utilities will require a password to work and should install the packages for you. If you have downloaded the files as .deb packages, and are trying to install them through a terminal then it is my guess that you need to use sudo in front of the commands. You will then be asked for the password for the operation to proceed.

Perhaps you could post the commands you are trying to run. and use a larger text size. Then others who are more capable on this subject might be able to help.

Regards.

---

### Post by yvesbodson on 2011-05-27
Ok will do thank you very much

---

### Post by LordNeo on 2011-05-27
> **grahammechanical said:**
> Hi

I am not an expert but how did you download Apache, MySQL and PHP? Through the Ubuntu software Centre? Through the Synaptic Package Manager? Both of these utilities will require a password to work and should install the packages for you. If you have downloaded the files as .deb packages, and are trying to install them through a terminal then it is my guess that you need to use sudo in front of the commands. You will then be asked for the password for the operation to proceed.

Perhaps you could post the commands you are trying to run. and use a larger text size. Then others who are more capable on this subject might be able to help.

Regards.
He is installing from Ubuntu Server so he doesn't have a graphical enviroment

---

