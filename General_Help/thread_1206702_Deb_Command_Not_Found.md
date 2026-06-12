---
title: "Deb Command Not Found"
date: 2009-07-07
forum: General Help
---

### Post by Bradj47 on 2009-07-07
Sites tell me to use the deb command to install packages all the time but I always get this: 
```

brad@rockstar:~$ deb http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu jaunty main
bash: deb: command not found

```
So then I try: 
```

brad@rockstar:~$ sudo apt-get install deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package deb

```
How do I get deb?

---

### Post by Ra-Hoor-Khuit on 2009-07-07
See the "**Adding Other Repositories**" section (kinda towards the bottom) of this tutorial:

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by starcraft.man on 2009-07-07
> **Bradj47 said:**
> Sites tell me to use the deb command to install packages all the time but I always get this: 
```

brad@rockstar:~$ deb http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu jaunty main
bash: deb: command not found

```
So then I try: 
```

brad@rockstar:~$ sudo apt-get install deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package deb

```
How do I get deb?

There's no such thing as the deb command, you want dpkg. That is the command line installer for .deb files.

The command to install package is: ```
dpkg -i package
```

Where package is replaced with the deb you downloaded and want to install. Why do you need to use a deb though, most software is in the repos and it is preferable to install that way. When you install a package from a binary like deb instead of a repository, you won't get updated to the new version when it's released automatically. See my signature for explanation.

---

### Post by Bradj47 on 2009-07-07
> **starcraft.man said:**
> There's no such thing as the deb command, you want dpkg. That is the command line installer for .deb files.

The command to install package is: ```
dpkg -i package
```

Where package is replaced with the deb you downloaded and want to install. Why do you need to use a deb though, most software is in the repos and it is preferable to install that way. When you install a package from a binary like deb instead of a repository, you won't get updated to the new version when it's released automatically. See my signature for explanation.

I'm trying to install handbrake. I couldn't find it in the repositories and I was led to this link [https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa](https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa) in another post I made here: [http://ubuntuforums.org/showthread.php?t=1206230](http://ubuntuforums.org/showthread.php?t=1206230)

---

### Post by michy99 on 2009-07-07
This:```
deb http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu jaunty main

```is not a command. It is a repository that you can add to your sources. Read the link provided by Ra-Hoor-Khuit above.

---

### Post by philinux on 2009-07-07
Easy way is to get the package from getdeb.

[http://www.getdeb.net/app/HandBrake](http://www.getdeb.net/app/HandBrake)

Download the appropriate package to your desktop. Double click it to install.

---

