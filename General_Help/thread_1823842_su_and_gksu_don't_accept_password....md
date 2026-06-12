---
title: "su and gksu don't accept password..."
date: 2011-08-12
forum: General Help
---

### Post by kvarley on 2011-08-12
I have this issue on both Ubuntu and Lubuntu 11.04 64-bit on 2 different machines. I have not tested 32-bit.

When I run synaptic or update-manager it presents me with gksu, not gksudo as it previously did in previous Ubuntu releases, no matter how many times I try **it will not accept my password**.

I have even given it command line arguments to print the password to the terminal and it's correct.

I have found a workaround - by running gksu-properties and changing the mode from su to sudo it will now display gksudo and accept my password.

However, I want to know why it won't accept my sudo password for the su and gksu commands? There are no error messages which are outputted, the gui just says incorrect password.

Any help would be much appreciated. :)

---

### Post by coffeecat on 2011-08-12
> **kvarley said:**
> I have found a workaround - by running gksu-properties and changing the mode from su to sudo it will now display gksudo and accept my password.

Since the default setting in gksu-properties is sudo, I cannot see how this is a workaround, rather a putting back of the system to the way it should be.

Check this. "gconf-editor" from the terminal. Then apps > gksu. Make sure the 'sudo-mode' box is ticked.

As far as "su" is concerned, that will prompt you for the root password which is locked by default in Ubuntu. You do not need su. Have a read of this:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by kvarley on 2011-08-12
Thanks for the speedy reply :) So the question is now - What caused the systems to choose su? A corrupt configuration file when updates ran?

---

### Post by coffeecat on 2011-08-12
> **kvarley said:**
> What caused the systems to choose su?

I don't follow what you mean, and what do you mean by this?

> **kvarley said:**
> When I run synaptic or update-manager it presents me with gksu, not gksudo as it previously did in previous Ubuntu releases,

Synaptic and update-manager don't **present** you with gksu - that doesn't make any sense. They are invoked with gksu or gksudo.

In a default installation, if you start Synaptic from the menu, it is started with "gksu synaptic", not "gksudo synaptic", although it makes no difference (in a default installation). That's just the way the menus are set up - probably to do with the preference of a developer. Other apps needing root privileges are started with gksudo - again that's just the way things are set up. If gksu-properties is set to sudo and the gconf-editor sudo-mode is ticked, then gksu effectively becomes an alias for gksudo. The system will prompt you for your login password. If gksu is not set up like this then invoking gksu will cause the system to prompt you for the root password - which is non-functional in a default Ubuntu install.

If by "what causes the system to choose su" you mean what would cause the sudo-mode to be not enabled, I'm not sure. The only time I've seen this myself was when I did a too-clever-by-half chroot netinstall of Maverick, which is hardly a standard way of installing Ubuntu. Threads about this pop up occasionally but I've never seen a pattern which would reveal an underlying cause.

---

### Post by sisco311 on 2011-08-12
> **coffeecat said:**
> Since the default setting in gksu-properties is sudo, I cannot see how this is a workaround, rather 
a putting back of the system to the way it should be.


The default mode in gksu (the package/application) is su. If you use the "normal" or "alternate" CD to install Ubuntu/Lubuntu/Xubuntu, then the installer sets it to sudo. So, if you do a minimal (CLI only) installation and only after that install a GUI and gksu, then you have to change the mode to sudo.

---

### Post by aysiu on 2011-08-12
*gksudo* and *gksu* operate in the same way on a default Ubuntu installation (both prompting for the *user* password of the administrator account currently logged in).

*su* without any other parameters prompts you for the root password, which is non-existent on a default Ubuntu installation (the root account is disabled for login).

---

### Post by coffeecat on 2011-08-12
> **sisco311 said:**
> The default mode in gksu (the package/application) is su. If you use the "normal" or "alternate" CD to install Ubuntu/Lubuntu/Xubuntu, then the installer sets it to sudo. So, if you do a minimal (CLI only) installation and only after that install a GUI and gksu, then you have to change the mode to sudo.

Thanks for the clarification. It explains what I observed in my let's-install-Ubuntu-as-you-would-Gentoo adventure. (Never to be repeated! :wink:)

---

### Post by sbraz on 2011-08-12
> **coffeecat said:**
> As far as "su" is concerned, that will prompt you for _the root password which is locked by default in Ubuntu_. You do not need su.[/url]
correct (i read somewhere that root has a password but it has a special hash pattern which can't match any possible password. nice trick :) ) but there's more:
quote from **man su**
> The su command is used to become another user during a login session. Invoked without a username, su defaults to becoming the superuser. 
that said i use **su** on a daily basis since it removes the need of typing **sudo** everytime i do something nasty. :)
thing is you need to be on a root enviroment in order to *become* root, so:

```
sbraz@sbraz-netbook:~$ su
Password: 
su: Authentication failure
sbraz@sbraz-netbook:~$ sudo su
[sudo] password for sbraz: 
**root**@sbraz-netbook:/home/sbraz#
```
tadaaa! :D

sometimes issuing a command with sudo doesn't work, but as real root it does.

who's concerned about leaving an open root shell flying around, can also chain commands in a terminal like this:
```
sbraz@sbraz-netbook:~$ sudo su && exit
[sudo] password for sbraz: 
root@sbraz-netbook:/home/sbraz# apt-get update && apt-get -y upgrade && exit
```
that way the terminal closes entirely at the end of the queue (yes, a ctrl+c still does the trick but hey... :) ).

---

### Post by sisco311 on 2011-08-12
> **sbraz said:**
> correct (i read somewhere that root has a password but it has a special hash pattern which can't match any possible password. nice trick :) ) but there's more:
quote from **man su**

that said i use **su** on a daily basis since it removes the need of typing **sudo** everytime i do something nasty. :)
thing is you need to be on a root enviroment in order to *become* root, so:

```
sbraz@sbraz-netbook:~$ su
Password: 
su: Authentication failure
sbraz@sbraz-netbook:~$ sudo su
[sudo] password for sbraz: 
**root**@sbraz-netbook:/home/sbraz#
```
tadaaa! :D

sometimes issuing a command with sudo doesn't work, but as real root it does.

who's concerned about leaving an open root shell flying around, can also chain commands in a terminal like this:
```
sbraz@sbraz-netbook:~$ sudo su && exit
[sudo] password for sbraz: 
root@sbraz-netbook:/home/sbraz# apt-get update && apt-get -y upgrade && exit
```
that way the terminal closes entirely at the end of the queue (yes, a ctrl+c still does the trick but hey... :) ).

`sudo -i' is the recommended command to start a root shell in Ubuntu. Just like in other distributions where the root account is enabled, the recommended command for starting a root shell is `su -', `su -l' or `su --login'. ;)


`sudo su' is just a redundant construct like: `pkexec sudo su -c "bash -c 'ping ubuntuforums.org'" -' :evil:

---

### Post by coffeecat on 2011-08-12
> **sbraz said:**
> 
that said i use **su** on a daily basis since it removes the need of typing **sudo** everytime i do something nasty. :)
thing is you need to be on a root enviroment in order to *become* root, so:

```
sbraz@sbraz-netbook:~$ su
Password: 
su: Authentication failure
sbraz@sbraz-netbook:~$ sudo su
[sudo] password for sbraz: 
**root**@sbraz-netbook:/home/sbraz#
```
tadaaa! :D

The use of sudo su (or sudo -i - better) is descibed in the link I posted in post #2. It's worth reading if you're using Ubuntu.

> **sbraz said:**
> sometimes issuing a command with sudo doesn't work, but as real root it does.

I guess you're thinking of those occasions where you are using a bash redirect, such as:

```
sudo echo *string* > /path/to/file
```

... which fails. All you need is the use of a pipe and tee, as in:

```
echo *string* | sudo tee /path/to/file
```

No need for sudo su-ing all over the place. :)

---

### Post by sisco311 on 2011-08-12
> **coffeecat said:**
> Thanks for the clarification. It explains what I observed in my let's-install-Ubuntu-as-you-would-Gentoo adventure. (Never to be repeated! :wink:)

No problem.

BTW, I always use debootstrap & chroot to install Ubuntu. ;)

---

### Post by sbraz on 2011-08-12
> **sisco311 said:**
> `sudo -i' is the recommended command to start a root shell in Ubuntu. Just like in other distributions where the root account is enabled, the recommended command for starting a root shell is `su -', `su -l' or `su --login'. ;)
yeah i remember with debian i used **su** and **bash** to become root.

> **coffeecat said:**
> The use of sudo su (or sudo -i - better) is descibed in the link I posted in post #2. It's worth reading if you're using Ubuntu.

I guess you're thinking of those occasions where you are using a bash redirect, such as:

```
sudo echo *string* > /path/to/file
```

... which fails. All you need is the use of a pipe and tee, as in:

```
echo *string* | sudo tee /path/to/file
```

No need for sudo su-ing all over the place. :)

well i don't remember exactly as it happened a long time ago, but i think it had something to do with setting some sysctl parameters, or echoing stuff in /sys/*.

in the link you posted earlier i've found this link [http://ubuntuforums.org/showpost.php?p=6188826&postcount=4](http://ubuntuforums.org/showpost.php?p=6188826&postcount=4) which contains this table:
```
				                     corrupted by user's 
		HOME=/root	uses root's PATH     env vars
**sudo -i		Y		Y[2]                 N**
sudo -s		N		Y[2]                 Y
sudo bash	N		Y[2]                 Y
**sudo su		Y		N[1]                 Y**
```
so since $PATH is the same under both user and root (in my case at least) i guess the main advantage of sudo -i over sudo su is about enviroment variables...? :confused:

thank you all for your advices. :)

---

### Post by kvarley on 2011-08-13
Thank you for all the responses.

I still do not know what caused the change to su mode, however there is enough information in this thread for other users to solve the problem.

---

