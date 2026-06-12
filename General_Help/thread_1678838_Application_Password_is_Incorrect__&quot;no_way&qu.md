---
title: "Application Password is Incorrect ? &quot;no way&quot;"
date: 2011-01-31
forum: General Help
---

### Post by ShipsRus on 2011-01-31
I installed Ubuntu Server 10.10 with the GUI on a spare box I had. This is my first experience with Ubuntu. I have never used Linux before this. The system works great and logging on is no problem. However I installed 2 applications, gparted and samba. When I go to open either application I enter my logon password and I am told that the password is not correct. I am the only user on this machine and went to the accounts setting and changed my account type from custom to administrator to no avail.
I formatted my drive and reinstalled the whole thing again and got all available updates also. I reinstalled gparted and samba a second time on the new install and I still am told that the password is incorrect again when opening thes apps. Is there a simple, easy to understand way for this first time Ubuntu 10.10 user to correct this. There must be a minor flaw in this OS that is denying me use of my apps. Thank You in advance.

---

### Post by arpanaut on 2011-01-31
This should help:  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Things be different in Linux...

---

### Post by ShipsRus on 2011-01-31
> **arpanaut said:**
> This should help: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
 
Things be different in Linux...
 
Thank-You for offering to help me. However, even when I use the sudo or gksudo command to open any apps I installed including samba and gparted I AM STILL prompted for a password, and if I type in my password I get a message telling me that it is incorrect. Remember, there is only one user and one password, and the account is administrator. Does anyone know how to open an app when you know the correct password and the app tells you the password is incorrect.
      Arpanaut, thanks for taking the time, but sudo or gksudo still asks for a password. There must be a fundamental flaw in the 10.10 OS with reference to passwords for applications. I mean, I can get updates and do other things that require the root password, but I can not open any application I install.

---

### Post by mcduck on 2011-01-31
> **ShipsRus said:**
> Thank-You for offering to help me. However, even when I use the sudo or gksudo command to open any apps I installed including samba and gparted I AM STILL prompted for a password, and if I type in my password I get a message telling me that it is incorrect. Remember, there is only one user and one password, and the account is administrator. Does anyone know how to open an app when you know the correct password and the app tells you the password is incorrect.
      Arpanaut, thanks for taking the time, but sudo or gksudo still asks for a password. There must be a fundamental flaw in the 10.10 OS with reference to passwords for applications. I mean, I can get updates and do other things that require the root password, but I can not open any application I install.

First, there is _never_ only one user on a Linux/Unix system. :D (Actually even your own message implies that you have two enabled user accounts, your normal user and root)

Second, your problems probably come from the fact that you have installed the desktop on the server system, which is configured to be handled from command-line (and unlike the desktop edition, has root account enabled). Most desktop applications are configured to fit the desktop editions security model.

Samba is a server, not an application, I don't know what password it might be asking from you but that would probably be the password for the server you are trying to connect to... or then you are trying to use it in a wrong way.

Anyway, if you really can't open _any_ application you install, like you said, your system definitely has some serious problem. As hardly any of the normal applications would require anything more than minimal user permissions anyway...

In the end, if you want to run a graphical desktop, with servers or not, you should install the desktop edition. Especially if you are not familiar with Linux. running desktop apps on the server install makes some things a bit more complicated than what is necessary, and doesn't really benefit you at all (it's easier and requires less downloading to add servers to the desktop setup than the other way)

---

### Post by ShipsRus on 2011-01-31
> **mcduck said:**
> First, there is _never_ only one user on a Linux/Unix system. :D (Actually even your own message implies that you have two enabled user accounts, your normal user and root)
 
Second, your problems probably come from the fact that you have installed the desktop on the server system, which is configured to be handled from command-line (and unlike the desktop edition, has root account enabled). Most desktop applications are configured to fit the desktop editions security model.
 
Samba is a server, not an application, I don't know what password it might be asking from you but that would probably be the password for the server you are trying to connect to... or then you are trying to use it in a wrong way.
 
Anyway, if you really can't open _any_ application you install, like you said, your system definitely has some serious problem. As hardly any of the normal applications would require anything more than minimal user permissions anyway...
 
In the end, if you want to run a graphical desktop, with servers or not, you should install the desktop edition. Especially if you are not familiar with Linux. running desktop apps on the server install makes some things a bit more complicated than what is necessary, and doesn't really benefit you at all (it's easier and requires less downloading to add servers to the desktop setup than the other way)
 
Thank You for the informative reply. I am going to try your suggestions along with reading and serious study. Thanks for taking the time to assist me in this matter to which I am grateful.

---

