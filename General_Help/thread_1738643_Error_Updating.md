---
title: "Error Updating"
date: 2011-04-25
forum: General Help
---

### Post by maxwjackson on 2011-04-25
I have a HP Pavilion DV6 64bit running 10.10 and I have been for about 5 months since I gave up on windows.

This happened a few months ago and I somehow got around it and got it to update and all was fine til like last week.

When it went to do the auto update I got a error

> E: Type 'eb' is not known on line 59 in source list /etc/apt/sources.list


No matter how I try to update it whether with sudo apt-get update sudo apt-get upgrade or using the update center it will not update.

The application center won't open either when I try to open it...

Not really sure what the issue is so I am reaching out to try to get it solved and hopefully help anyone else who has this issue.

Thanks in advance

---

### Post by Rubi1200 on 2011-04-25
Hi and welcome to the forums :-)

Take a look at this link:
[http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html](http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html)

If you are unsure, post the results of this command:

```
cat /etc/apt/sources.list
```

---

### Post by maxwjackson on 2011-04-25
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Take a look at this link:
[http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html](http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html)

If you are unsure, post the results of this command:

```
cat /etc/apt/sources.list
```
Awesome, I looked all over google and stuff and couldnt find anyone with the same issue, but I will try it when I get home and post the results.
 
Thanks :thumbsup:

---

### Post by KegHead on 2011-04-25
Hi!

Have you tried:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

Advise.

KegHead

---

### Post by maxwjackson on 2011-04-26
> **KegHead said:**
> Hi!

Have you tried:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart.

Advise.

KegHead
Cant do that.

> smax@max-HP-Pavilion-dv5-Notebook-PC:~$ sudo apt-get update
[sudo] password for max: 
E: Type 'eb' is not known on line 59 in source list /etc/apt/sources.list
E: The list of sources could not be read.
max@max-HP-Pavilion-dv5-Notebook-PC:~$ 



Trying the first method right now.

---

### Post by maxwjackson on 2011-04-26
> **Rubi1200 said:**
> Hi and welcome to the forums :-)

Take a look at this link:
[http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html](http://ubuntu4beginners.blogspot.com/2011/01/restore-your-sources-list-to-defaults.html)

If you are unsure, post the results of this command:

```
cat /etc/apt/sources.list
```
I tried the update but the warning update failed thing still is up at the top of the screen.

This is what I got when i did that code you suggested after I did the first step.

> max@max-HP-Pavilion-dv5-Notebook-PC:~$ cat /etc/apt/sources.list
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-security main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted universe multiverse 

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Banshee - [https://edge.launchpad.net/~banshee-team](https://edge.launchpad.net/~banshee-team)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) maverick main

#### Wine - [https://launchpad.net/~ubuntu-wine/+archive/ppa/](https://launchpad.net/~ubuntu-wine/+archive/ppa/)
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main


####### 3rd Party Source Repos

#### Banshee (Source) - [https://edge.launchpad.net/~banshee-team](https://edge.launchpad.net/~banshee-team)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E80C6B7
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) maverick main

#### Wine (Source) - [https://launchpad.net/~ubuntu-wine/+archive/ppa/](https://launchpad.net/~ubuntu-wine/+archive/ppa/)
## Run this command:  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F9CB8DB0
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) maverick main 





---

### Post by plucky on 2011-04-27
What have you got in sources.list.d

Post output of ```
ls -l /etc/apt/sources.list.d/
cat /etc/apt/sources.list.d/*.list
```

---

