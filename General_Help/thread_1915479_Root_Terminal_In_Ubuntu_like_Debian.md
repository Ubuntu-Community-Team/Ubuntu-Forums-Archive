---
title: "Root Terminal In Ubuntu like Debian"
date: 2012-01-26
forum: General Help
---

### Post by khatkarrohit on 2012-01-26
> default user=user account created during ubuntu installation(not root)Today I installed Ubuntu 11.10 on my desktop. It did not ask for root password, instead it make the default user account administrator. After installation I downgraded the default user to standard user account but then I was not able to install new software as root account is locked and there is no user who can act as administrator.

Then I enable root account from GRUB menu.

But now I am not able to open root terminal like _*gksu gnome-terminal*_.

When I open terminal and type to get root privileges then following happens:

user@ubuntu-desktop:~$ sudo -i
[sudo] password for user: 
user is not in the sudoers file.  This incident will be reported.
user@user-desktop:~$ 

It do not ask for root password instead it ask for current user password.
I don't want to give any user the root privileges. I want a single root password which can be used install software from any standard user account. I don't want that any user get administrator privileges by using his/her account password.

I want a Debian like solution which has a _**ROOT Terminal**_ option along with simple user terminal.[U][B]

How do I get separate ROOT terminal in ubuntu just like Debian.[/B][/U]

---

### Post by Karlchen on 2012-01-26
Hello, khatkarrohit.

Supposing you had not messed around with your only admin user, then all you would have had to do would have been:

[LIST]
[*]Install the good old "Main Menu" (*alacarte*) through the Software Centre.
[*]Launch *alacarte* from a terminal window.
[*]Next go to "Applications" submenu and from there to the "System Utilities" submenu.
[*]There exists an unticked item, i.e. de-activated. It is labelled "Systemadministrator Terminal". It is exactly what you want: a terminal that opens with root privileges.
[/LIST]
 Of course, you are free to create a new launcher item in a different submenu or on your desktop and assign the commandline ```
gksu gnome-terminal
``` to it.

That's all.

To make one thing clear, the user whom you created during the installation does not have root privileges all the time. He may, however, elevate his privileges to those of root by prefixing "sudo" or "gksu" (whichever is appropriate) to a command.
Removing the only user having the right to elevate himself to act as root was not the most clever idea in the world. You may have to boot in Recovery Mode and revert the changes you have applied to your system.

Kind regards,
Karl

---

### Post by lisati on 2012-01-26
Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by khatkarrohit on 2012-01-26
Thanks [Karlchen]("http://ubuntuforums.org/member.php?u=1256016"), you wrote the right solution and I have enabled the Root Terminal from Main Menu. But problem is not solved ,the root terminal do not accept root password, it asks for current user password.
Thanks [[COLOR=#d40000]**lisati**[/COLOR]]("http://ubuntuforums.org/member.php?u=327635") for pointing me to that article. Below is the lines from that article which are helpful in understanding my problem. 
> **Logging in as another user**

 **Please don't use this to become Root,** see further down in the page for more information about that. 
sudo -i -u <username>
For example to become the user amanda for tape management purposes. 
sudo -i -u amanda
The password being asked for is your own, not amanda's. But the problem is still not solved. If I replace amanda with root then it asks for current user account password not root's password. To start the Root Terminal I have to authenticate it with Root password but when I give root password it does not accept root password. Here is the situation:

1. All the users are Standard users (not in sudoser list) and do not have administrative privileges. 
2. There is root user which was deactivated in Ubuntu. I activated it using
```
sudo passwd root
```3. I run the command :
```
gksu gnome-terminal
or
gksu /usr/bin/x-terminal-emulator
```4. Then it ask for password asking "Enter your password to perform Administrative Tasks". 

[LIST]
[*]Now if I enter the root password then it asks again for password means it do not accept root's password to run a application with root privileges.
[*]If I enter the current user password then it gives an error( see the attachment), because current user is not in administrator group.
[/LIST]
The article pointed by [[COLOR=#d40000]**lisati**[/COLOR]]("http://ubuntuforums.org/member.php?u=327635") says that root should not be used instead use sudo or gksu.
What inside Ubuntu is happening Ubuntu locked the root account and use current user password to get root privileges if user type is administer.

_** Here is other situation that I faced after installation:**_

1. I installed Ubuntu and it asks for user-name and password during installation but did not asks for root password and root is locked in Ubuntu.

2. Installation is successful and I login with the user-name which was created during Installation.

3. I went to User account settings in Ubuntu.

4. What I saw that Ubuntu gave "account type : Administrative " to that user.

5. I changed the user type to standard using user account password. 

6. Now there is only one user and that user account type is changed to standard from Administrator.

**7. **[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]** Now there is no administrator of that computer and root is locked in Ubuntu.**

8. Thats why I enabled the root user from GRUB menu.

[LIST]
[*][IMG]https://picasaweb.google.com/lh/photo/BKQ--CvX64J8J5VItk3somVwOcA5QBfmRE_hl-LMRH0?feat=directlink[/IMG]
[/LIST]

---

### Post by snowpine on 2012-01-26
If you have enabled the root password and disabled sudo/gksudo (not recommended/supported on these forums), then you need to use **su** for administrative tasks.

---

### Post by ottosykora on 2012-01-26
@khatkarrohit

read here: [http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

that is why you do not get much support on that subject...

---

### Post by CharlesA on 2012-01-26
The account created during install has admin (sudo) rights.

Setting a password for the root account isn't recommended as you can use sudo do to the same things you'd need to login as root to do.

---

### Post by Karlchen on 2012-01-26
Hello, khatkarrohit.

When I started using Ubuntu, no sooner than in the Karmic Koala period, I had worked on various Unix version for almost 20 years.
On all of them, the root account had been active. So logging in as root directly to perform administrative tasks had been part of the daily routine. sudo had hardly been used on any of the systems that I had worked on. Very often, nobody had even bothered to configure it at all.
So having to use sudo was a new experience. And in the beginning I was a little worried, too, that sudo might not allow me to perform all the administrative tasks that the direct root login had always permitted me to perform.
Yet, this proved to be absolute nonsense. There is nothing which you cannot do just because you login as yourself and use sudo to elevate to root status whenever required.
You will get used to entering your password, not root's password, when running a sudo or gksu command, pretty quickly.
You lose nothing except an old habit, but you gain security and an increasing knowledge about sudo (if you care to).

Kind regards,
Karl

---

### Post by sisco311 on 2012-01-27
> **khatkarrohit said:**
> 
**7. **[IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]** Now there is no administrator of that computer and root is locked in Ubuntu.**

8. Thats why I enabled the root user from GRUB menu.



I'd suggest you to reset the default settings. Add your user to the admin group and lock the root account password:
[http://psychocats.net/ubuntu/fixsudo](http://psychocats.net/ubuntu/fixsudo)

> **snowpine said:**
> If you have enabled the root password and disabled sudo/gksudo (not recommended/supported on these forums), then you need to use **su** for administrative tasks.

+1

Also, in Ubuntu, gksu defaults to run in *sudo mode*. But, you can change the authentication mode to su, just run:
```
gksu-properties
```

---

### Post by khatkarrohit on 2012-01-28
I used the following method to set the root password from GRUB.
> 
[**The Other Way**]("https://help.ubuntu.com/community/LostPassword")

 If the "Standard Way" does not work for you and you recieve the "Give root password for maintenance" message,  you can recover your password using the following steps 
1. Reboot your computer 
2. Press **SHIFT** or **ESC** at the grub prompt (as earlier). 
3. Select your image. 
4. Highlight the line that begins kernel and press 'e' to edit 
5. Go to the very end of the line, change the ro to rw and add init=/bin/bash 
press enter, then press b to boot your system. 
Your system will boot up to a password less root shell. 
6. Type in **passwd username** 
7. Set your password. 
8. Type in [B]reboot
[/B]After this I used the graphical Add User program to add new user with type administrator using root password and disabled the root using:
```
sudo passwd -dl root
```Now I get back to GRUB menu to reverse the changes that I made in step 5 but the changes reversed automatically ( rw was ro and init=/bin/bash was not there), everything is back to default as it was before making any changes.

Now there is one account with administrator privileges and other account is of type standard and everything is fine now as nothing happened.

**_So , here is my conclusion:_**
Ubuntu has different security and authentication model from Debian and it is not possible to get back to Debian way in Ubuntu. 
The root terminal```
 gksu /usr/bin/x-terminal-emulator
``` is of no use and all the administrative work can be done by using```
sudo
or 
sudo su 
``` in normal terminal.

---

### Post by haqking on 2012-01-28
> **khatkarrohit said:**
> 

**_So , here is my conclusion:_**
Ubuntu has different security and authentication model from Debian and it is not possible to get back to Debian way in Ubuntu. 
The root terminal```
 gksu /usr/bin/x-terminal-emulator
``` is of no use and all the administrative work can be done by using[B]```
sudo
or 
sudo su 
``` in normal terminal[/B].

that is why sudo exists.

and Ubuntu is not debian ;-)

Peace

---

