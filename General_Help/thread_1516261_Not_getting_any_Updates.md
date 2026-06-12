---
title: "Not getting any Updates"
date: 2010-06-23
forum: General Help
---

### Post by joek71 on 2010-06-23
Hello Guys

I have not been getting any updates at my home machine, but in the office i get updates, same OS same version, when I look for updates it home it does not show me any update.
Can someone please assist me with this problem?

Thanks,
Joe

---

### Post by snowpine on 2010-06-23
Hi Joe, try opening a terminal (Applications, Accessories, Terminal), copy & pasting the commands below, and then copy & pasting the output back here in the forums so we can help you troubleshoot.

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by joek71 on 2010-06-23
Thanks will try soon as i get home, it is very strange no errors or anything.  The only difference between home & work machines is home I upgrade from 9.10 and work did fresh install.

Thanks will keep you post soon as i get home.

Thank you

---

### Post by joek71 on 2010-06-23
This is what i got:


joe@joe:~$ sudo apt-get update
[sudo] password for joe: 
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid Release.gpg
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/main Translation-en_US 
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/restricted Translation-en_US
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/universe Translation-en_US
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates Release.gpg
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-security Release.gpg
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-security/main Translation-en_US
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid Release                         
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates Release                 
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-security Release                
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                 
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/main Packages                   
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/restricted Packages
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/main Sources                    
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/restricted Sources              
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/universe Packages               
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/universe Sources                
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/multiverse Packages             
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid/multiverse Sources              
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/main Packages           
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/restricted Packages     
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/main Sources            
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/restricted Sources      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/universe Packages       
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/universe Sources
Ign [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable/main Translation-en_US
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/multiverse Packages
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-updates/multiverse Sources
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-security/main Packages
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-security/restricted Packages
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-security/main Sources
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-security/restricted Sources
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-security/universe Packages
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-security/universe Sources
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-security/multiverse Packages
Hit [http://mirrors.ccs.neu.edu](http://mirrors.ccs.neu.edu) lucid-security/multiverse Sources
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,544B]
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [1,073B]
Fetched 3,806B in 0s (3,845B/s)
Reading package lists... Done
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_lucid_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
joe@joe:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joe@joe:~$

---

### Post by snowpine on 2010-06-23
No big deal, there appears to be a duplicate entry in your software sources list, we can fix this easily.

```
gksu gedit /etc/apt/sources.list
```

Find the line that says something like

> deb [http://archive.canonical.com](http://archive.canonical.com) lucid/partner main 

Type a # symbol at the beginning of the line, commenting it out so the system skips it:

> #deb [http://archive.canonical.com](http://archive.canonical.com) lucid/partner main 

Save the file and quit Gedit. Now do your "sudo apt-get update" and "sudo apt-get upgrade" thing again, hopefully this time you will not get the warning about the duplicate entry. :)

If the sources.list file looks weird to you, you can copy & paste the contents of the file here for someone to take a look. The usual disclaimer: Be careful using "sudo" to edit system files, make sure you trust the person giving you advice (me) and that you understand what the commands do.

---

### Post by joek71 on 2010-06-23
I dont have what you wrote, this is what i have:

[B]# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid main restricted
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates main restricted
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid universe
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid universe
deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates universe
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid multiverse
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid multiverse
deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates multiverse
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.

deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-security main restricted
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-security main restricted
deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-security universe
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-security universe
deb [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-security multiverse
deb-src [http://mirrors.ccs.neu.edu/ubuntu/](http://mirrors.ccs.neu.edu/ubuntu/) lucid-security multiverse[/B]

---

### Post by snowpine on 2010-06-23
OK, what about if you go to the System menu, Administration, Software Sources. Do you see the duplicate "partners" entry there?

---

### Post by joek71 on 2010-06-23
yes i see duplicates and i unchecked one, and tried to do update and still nothing

---

### Post by snowpine on 2010-06-23
> **joek71 said:**
> yes i see duplicates and i unchecked one, and tried to do update and still nothing

What do you mean by "still nothing"? Are you getting an error message, or is it telling you that your system is up to date?

---

### Post by TRoe on 2010-06-23
I may be off-base here, but shouldn't he UNcheck the partners selections?

EDIT: As in, ALL of them?

---

### Post by joek71 on 2010-06-23
It is all good thank you, what i did was uncheck duplicates and changed the server to main.

Thank you

---

