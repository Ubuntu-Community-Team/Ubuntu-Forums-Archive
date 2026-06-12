---
title: "Ubuntu Update Error Message"
date: 2012-05-29
forum: General Help
---

### Post by jrgonzalez on 2012-05-29
I have been a very happy Ubuntu user for a couple of years (Evil Bill Gates is gone from my laptop). I have not had that many problems.

But recently a problem popped up while trying to get new updates or upgrades.

Here is the message that I am getting:

                                  _***Could not calculate the upgrade  ***_
  
 _***An unresolvable problem occurred while calculating the upgrade.  ***_
 :mad: 
 _***Please report this bug against the 'update-manager' package and include the following error message:  ***_
 _***'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'***_


How do I solve this problem? Thanks for any help you may offer. ):P


JRG

---

### Post by kc1di on 2012-05-29
try the following in a terminal one line at a time.


```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by jrgonzalez on 2012-05-29
> **kc1di said:**
> try the following in a terminal one line at a time.


```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```


O.K. I will try it. I will come back today or tomorrow and report what happened.

Thanks,

JRG

---

### Post by jrgonzalez on 2012-05-29
Here is the list from the terminal session:
Let me know what I have to do next.

_**Thanks.**_

JRG

  	 	 	 	 	 	   jorge@ubuntu:~$ sudo apt-get autoclean 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 jorge@ubuntu:~$ sudo apt-get update 
 Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg 
 Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US 
 Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B] 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US 
 Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B] 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US 
 Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US 
 Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release 
 Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB] 
 Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages 
 Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [57.3kB] 
 Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages [1,386kB] 
 Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages [6,208B] 
 Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources [659kB] 
 Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources [3,775B] 
 Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages [5,448kB] 
 Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources [3,165kB]            
 Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages [180kB]           
 Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources [119kB]            
 Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [613kB]         
 Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [4,617B]  
 Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [221kB]          
 Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [2,194B]   
 Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [269kB]     
 Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [99.6kB]     
 Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [11.3kB]  
 Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,537B]   
 Fetched 12.3MB in 29s (420kB/s)                                                 
 Reading package lists... Done 
 W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages) 
 W: You may want to run apt-get update to correct these problems 
 jorge@ubuntu:~$

---

### Post by jrgonzalez on 2012-05-29
I will be back tomorrow after 10 a.m.

I have to go and do some other stuff.

I tank you for your help.

JRG  (somewhere in Central Florida)

---

### Post by shafi.dude99 on 2012-05-29
Open the sources.list in gedit gksudo gedit /etc/apt/sources.list and look for the line"
  deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner   and comment it out by adding # before at the beginning of that line so 
  #deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner    you just comment it  out instead of deleting it, you should be fine.

---

### Post by jrgonzalez on 2012-06-01
> **shafi.dude99 said:**
> Open the sources.list in gedit gksudo gedit /etc/apt/sources.list and look for the line"
  deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner   and comment it out by adding # before at the beginning of that line so 
  #deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner    you just comment it  out instead of deleting it, you should be fine.

Sorry that it took me so long to return, but I have been busy with other stuff. Thanks for your answer. I appreciate it.

I ran gksudo gedit /etc/apt/sources list  (from terminal screen)

I could not find any line that says "lucid partner"

Did I do something wrong? I am thoroughly confused now!

Here is the list that came out when when I did gksudo gedit ......

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse

---

### Post by dino99 on 2012-06-01
i dont know how you have built your sources.list, but mixing 2 distro at a time is not a good idea. Isuppose you want Lucid only, so erase everything else (intrepid) and update again.

note: update-manager often popup this error (too buggy to me) so better to use synaptic.

---

### Post by jrgonzalez on 2012-06-04
> **dino99 said:**
> i dont know how you have built your sources.list, but mixing 2 distro at a time is not a good idea. Isuppose you want Lucid only, so erase everything else (intrepid) and update again.

note: update-manager often popup this error (too buggy to me) so better to use synaptic.

Thanks for your answer. I also do not know what happened or how it happened.

When I boot up Ubuntu in the morning, it shows that I am using Intrepid (10.04) and not Lucid.

But now I can no longer get updated from Ubuntu.

So, by now, I am thoroughly confused. One person says one thing, and another person say another thing, and adds even more confusion.

I am at a point that I may go back to the hated Microsoft! They were not much help when I had problems. The same thing is happening to me with Ubuntu now.

I hope that you can offer some help. You are the third person to offer advice, and I am still "stuck" about not being able to get any new Ubuntu "help."

TOTALLY FRUSTRATED IN CENTRAL FLORIDA (JRG)

---

### Post by matt_symes on 2012-06-04
Hi

> **jrgonzalez said:**
> I am at a point that I may go back to the hated Microsoft! They were not much help when I had problems. The same thing is happening to me with Ubuntu now.

I hope that you can offer some help. You are the third person to offer advice, and I am still "stuck" about not being able to get any new Ubuntu "help."

TOTALLY FRUSTRATED IN CENTRAL FLORIDA (JRG)

To be totally honest, after the above comments i was not going to post in this thread. As this is a free support service run by unpaid volunteers, threatening to use another operating system is just daft.

However try this.

Open a terminal and type

```
sudo rm -rf /var/lib/apt/lists/*
```

Enter your password. It will not be ecoed to the screen. This will delete you lists files.

Then type

```
sudo apt-get update
```

The references to Intrepid in your sources.list file are fine as they are commented out.

I assume you upgraded the operating system from 8.04 to 10.04 at some point.

I can only see one reference to the partner repo in your sources.list  and, unless it is referenced in a file in the sources.list.d directory, then hopefully the above commands will fix it for you.

Kind regards

---

### Post by jrgonzalez on 2012-06-06
> **matt_symes said:**
> Hi



To be totally honest, after the above comments i was not going to post in this thread. As this is a free support service run by unpaid volunteers, threatening to use another operating system is just daft.

However try this.

Open a terminal and type

```
sudo rm -rf /var/lib/apt/lists/*
```Enter your password. It will not be ecoed to the screen. This will delete you lists files.

Then type

```
sudo apt-get update
```The references to Intrepid in your sources.list file are fine as they are commented out.

I assume you upgraded the operating system from 8.04 to 10.04 at some point.

I can only see one reference to the partner repo in your sources.list  and, unless it is referenced in a file in the sources.list.d directory, then hopefully the above commands will fix it for you.

Kind regards

Thanks for your help.

Below is what I got:

jorge@ubuntu:~$ sudo rm -rf /var/lib/apt/lists/*
jorge@ubuntu:~$ sudo apt-get update
E: Lists directory /var/lib/apt/lists/partial is missing.
jorge@ubuntu:~$ ^C
jorge@ubuntu:~$ 

What now?

---

### Post by jrgonzalez on 2012-06-06
More error messages (a few minutes ago): [FONT=Liberation Serif, serif]:sad:[/FONT]

  	 	 	 	 	[FONT=Liberation Serif, serif]Could not download all repository indexes[/FONT]
 

 [FONT=Liberation Serif, serif]The repository index may no longer be available[/FONT]
 [FONT=Liberation Serif, serif]or could not be contacted because of network problems.[/FONT]
 [FONT=Liberation Serif, serif]If available an older version of the failed index will be[/FONT]
 [FONT=Liberation Serif, serif]used. Otherwise the repository will be ignored. Check your network[/FONT]
 [FONT=Liberation Serif, serif]connection and ensure the repository address in the preference[/FONT]
 [FONT=Liberation Serif, serif]is correct.[/FONT]
 

 [FONT=Liberation Serif, serif]List directory /var/lib/apt/lists/partial is missing.[/FONT]


[FONT=Liberation Serif, serif]However, the red icon with a - in the middle is gone.  
[/FONT]

---

### Post by matt_symes on 2012-06-06
Hi

Open a terminal and type

```
sudo mkdir /var/lib/apt/lists/partial
```

Then type

```
sudo apt-get update
```

Kind regards

---

### Post by jrgonzalez on 2012-06-12
The Ubuntu community was never able to solve my problem. I still have the same problem. I thank those who tried.  I do realise that having to rely on unpaid volunteers means that the level of expertise is close to ZERO.  Good bye Ubuntu. You are not any different than Microsoft.  JRG Pissed off in Central Florida.

---

### Post by uylug on 2012-06-12
> **jrgonzalez said:**
> The Ubuntu community was never able to solve my problem. I still have the same problem. I thank those who tried.  I do realise that having to rely on unpaid volunteers means that the level of expertise is close to ZERO.  Good bye Ubuntu. You are not any different than Microsoft.  JRG Pissed off in Central Florida.

Oh come on. There are quite a lot of experts around here willing to help you for free, so quit acting like you're so important to waste your time here.

And if that's the case, then just leave.

---

### Post by jrgonzalez on 2012-06-27
:( This problem has not been closed by me.

First of all, I want to thank all the volunteers that tried to help, unsuccessfully.

I do not believe in volunteering in a capitalist society: you do the work, someone else gets the money. 

I do not mean my comment as trying to "attack" anyone. It is just an expression of my beliefs. I do hope that you guys believe in Freedom Of Speech.

Now, back to the problem.  I am still NOT ABLE to get new updates from Ubuntu.

I get the following message: List directory /var/lib/apt/lists/partial is missing.

I hope that someone with more experience can help me.

Thank You.

JRG

---

### Post by jrgonzalez on 2012-06-27
> **uylug said:**
> oh come on. There are quite a lot of experts around here willing to help you for free, so quit acting like you're so important to waste your time here.

And if that's the case, then just leave.

get lost buddy!

---

