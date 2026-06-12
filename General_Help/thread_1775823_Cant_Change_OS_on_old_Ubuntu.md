---
title: "Cant Change OS on old Ubuntu"
date: 2011-06-05
forum: General Help
---

### Post by XxDeathXx on 2011-06-05
"The output from the commands show the disk you got was for Ubuntu 7.04 (Feisty Fawn). That release of Ubuntu has not been supported since [correction, October 2008] April 2010. The book and disk are outdated. You can't get updates for unsupported releases.

You will need to download a newer release of Ubuntu, make a boot-able CD or USB, and install it. I would go to [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) and select the 10.04 LTS release for download. The 10.04 LTS release is supported until April 2013." 
This was how [Old_Gray_Wolf]("http://ubuntuforums.org/member.php?u=376436") resolved my last thread, but leaves me stuck where I am still.

Since i have an older version of Ubuntu, the instructions on the website to make a bootable usb are a fail.
it says to go to

System
Administration
Startup Disk creator

Alas, there is no Startup Disk Creater in my old version...
I hate being at a stand still.
recommendations? how do i do this now, or am i screwed til i buy a new cd?

---

### Post by pqwoerituytrueiwoq on 2011-06-05
google unetbootin

---

### Post by TeoBigusGeekus on 2011-06-05
Go to Synaptic and search for startup disk creator.
It will be in the repos if you're lucky.

---

### Post by Old_Grey_Wolf on 2011-06-05
> **pqwoerituytrueiwoq said:**
> google unetbootin

The oldest version of Unetbootin on their website is for 8.04 (Hardy). XxDeathXx has 7.04 installed.

Maybe XxDeathXx can get someone with a computer (Windows or Linux) to make the USB for him using Unetbootin. Or, let him use their computer to do it.

---

### Post by Old_Grey_Wolf on 2011-06-05
> **TeoBigusGeekus said:**
> Go to Synaptic and search for startup disk creator.
It will be in the repos if you're lucky.

I don't think the startup disk creator came out until 8.10.

The 7.04 repositories have been moved to [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/).

XxDeathXx will need to copy the following lines into /etc/apt/sources.list file using the command "gksudo gedit /etc/apt/sources.list":

```
deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security universe
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-security universe
deb http://old-releases.ubuntu.com/ubuntu/ feisty-security multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-security multiverse
deb http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
```

---

### Post by linuxinstalledfromhdd on 2011-06-05
Try installing it from a disc? 

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

> **XxDeathXx said:**
> "The output from the commands show the disk you got was for Ubuntu 7.04 (Feisty Fawn). That release of Ubuntu has not been supported since [correction, October 2008] April 2010. The book and disk are outdated. You can't get updates for unsupported releases.

You will need to download a newer release of Ubuntu, make a boot-able CD or USB, and install it. I would go to [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) and select the 10.04 LTS release for download. The 10.04 LTS release is supported until April 2013." 
This was how [Old_Gray_Wolf]("http://ubuntuforums.org/member.php?u=376436") resolved my last thread, but leaves me stuck where I am still.

Since i have an older version of Ubuntu, the instructions on the website to make a bootable usb are a fail.
it says to go to

System
Administration
Startup Disk creator

Alas, there is no Startup Disk Creater in my old version...
I hate being at a stand still.
recommendations? how do i do this now, or am i screwed til i buy a new cd?

---

### Post by Old_Grey_Wolf on 2011-06-05
> **linuxinstalledfromhdd said:**
> Try installing it from a disc? 

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

It would be easier to burn a Live CD. Instructions are at [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download).

---

