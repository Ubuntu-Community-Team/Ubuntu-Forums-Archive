---
title: "Can't Install Java"
date: 2010-10-17
forum: General Help
---

### Post by Tarid on 2010-10-17
[SIZE=2]I am using[/SIZE][SIZE=2] Ubuntu 10.04 Netbook Edition[/SIZE] . Only been using it for a couple of weeks.

I get the follow error when runnin this

```
sudo apt-get install sun-java6-jre

``````
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
                 Depends: sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not installable
                 Recommends: gsfonts-x11 but it is not installable
```

---

### Post by sikander3786 on 2010-10-17
What if you try,

```
sudo aptitude install sun-java6-jre
```

---

### Post by Tarid on 2010-10-17
> **sikander3786 said:**
> What if you try,

```
sudo aptitude install sun-java6-jre
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  sun-java6-bin sun-java6-jre 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.8MB of archives. After unpacking 102MB will be used.
The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc which is a virtual package.
  sun-java6-jre: Depends: java-common (>= 0.24) which is a virtual package.
Unable to resolve dependencies!  Giving up...
The following packages are BROKEN:
  sun-java6-bin sun-java6-jre 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.8MB of archives. After unpacking 102MB will be used.
aptitude failed to find a solution to these dependencies.  You can solve them yourself by hand or type 'n' to quit.
The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc which is a virtual package.atz
  sun-java6-jre: Depends: java-common (>= 0.24) which is a virtual package.
Resolve these dependencies by hand? [N/+/-/_/:/?] 
```

What do I do next?

---

### Post by sikander3786 on 2010-10-17
Try

```
sudo aptitude install -f
```

and post the output.

---

### Post by Tarid on 2010-10-17
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  gstreamer0.10-fluendo-mpegdemux 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 52.5kB of archives. After unpacking 193kB will be used.
Do you want to continue? [Y/n/?] 


```

---

### Post by sikander3786 on 2010-10-17
Type 'y' to continue the above operation and again try to install sun-java6-jre.

What do you get now?

---

### Post by Waappu on 2010-10-17
Hi,

Open Synaptics Package Manager.
Settings->Repositories

Then from Other Software tab, enable "Canonical Partners"

Close package manager
```

sudo apt-get update
sudo apt-get install sun-java6-jre

```

---

### Post by linux-hack on 2010-10-17
Try installing the build-essential package before..

```
sudo apt-get install build-essential
```

---

### Post by Tarid on 2010-10-17
> **sikander3786 said:**
> Type 'y' to continue the above operation and again try to install sun-java6-jre.

What do you get now?


 ```
 sun-java6-bin sun-java6-jre 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.8MB of archives. After unpacking 102MB will be used.
The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc which is a virtual package.
  sun-java6-jre: Depends: java-common (>= 0.24) which is a virtual package.
Unable to resolve dependencies!  Giving up...
The following packages are BROKEN:
  sun-java6-bin sun-java6-jre 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.8MB of archives. After unpacking 102MB will be used.
aptitude failed to find a solution to these dependencies.  You can solve them yourself by hand or type 'n' to quit.
The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc which is a virtual package.
  sun-java6-jre: Depends: java-common (>= 0.24) which is a virtual package.
Resolve these dependencies by hand? [N/+/-/_/:/?] 

```

---

### Post by sikander3786 on 2010-10-17
Please post the output of

```
cat /etc/apt/sources.list
```

As **Waappu** suggested above, seems like you have disabled some repositories.

---

### Post by Tarid on 2010-10-17
> **Waappu said:**
> Hi,

Open Synaptics Package Manager.
Settings->Repositories

Then from Other Software tab, enable "Canonical Partners"

Close package manager
```

sudo apt-get update
sudo apt-get install sun-java6-jre

```

I checked off all of the URLs that where in there. Is that what you mean?

I ran the commands above and got the following errors

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
                 Depends: sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not installable
                 Recommends: gsfonts-x11 but it is not installable
```

---

### Post by Tarid on 2010-10-17
> **linux-hack said:**
> Try installing the build-essential package before..

```
sudo apt-get install build-essential
```

Got this. 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package build-essential is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate

```

---

### Post by Tarid on 2010-10-17
> **sikander3786 said:**
> Please post the output of

```
cat /etc/apt/sources.list
```As **Waappu** suggested above, seems like you have disabled some repositories.


# deb cdrom:[Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner

---

### Post by Tarid on 2010-10-17
Those repositories are probably wrong I have been working on this problem for a few days trying different stuff I found in this forum.

---

### Post by Tarid on 2010-10-17
bump

---

### Post by sikander3786 on 2010-10-17
Edit your sources.list

```
sudo gedit /etc/apt/sources.list
```

Comment out both these lines with #

```
deb http://archive.canonical.com/ubuntu jaunty partner
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
```

save, close and now

```
sudo apt-get update
```

And try again to install java.

---

### Post by Tarid on 2010-10-17
```
sudo aptitude install sun-java6-jre
```

Gets this

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages are BROKEN:
  sun-java6-bin sun-java6-jre 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.8MB of archives. After unpacking 102MB will be used.
The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc which is a virtual package.
  sun-java6-jre: Depends: java-common (>= 0.24) which is a virtual package.
Unable to resolve dependencies!  Giving up...
The following packages are BROKEN:
  sun-java6-bin sun-java6-jre 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.8MB of archives. After unpacking 102MB will be used.
aptitude failed to find a solution to these dependencies.  You can solve them yourself by hand or type 'n' to quit.
The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc which is a virtual package.
  sun-java6-jre: Depends: java-common (>= 0.24) which is a virtual package.
Resolve these dependencies by hand? [N/+/-/_/:/?] 
```

---

### Post by Tarid on 2010-10-17
disregard my previous post i am trying those suggestions now

---

### Post by Tarid on 2010-10-17
> **sikander3786 said:**
> Edit your sources.list

```
sudo gedit /etc/apt/sources.list
```Comment out both these lines with #

```
deb http://archive.canonical.com/ubuntu jaunty partner
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
```save, close and now

```
sudo apt-get update
```And try again to install java.

this:
```
sudo aptitude install sun-java6-jre
```

gets this:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  sun-java6-bin sun-java6-jre 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.8MB of archives. After unpacking 102MB will be used.
The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc which is a virtual package.
  sun-java6-jre: Depends: java-common (>= 0.24) which is a virtual package.
Unable to resolve dependencies!  Giving up...
The following packages are BROKEN:
  sun-java6-bin sun-java6-jre 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 35.8MB of archives. After unpacking 102MB will be used.
aptitude failed to find a solution to these dependencies.  You can solve them yourself by hand or type 'n' to quit.
The following packages have unmet dependencies:
  sun-java6-bin: Depends: unixodbc which is a virtual package.
  sun-java6-jre: Depends: java-common (>= 0.24) which is a virtual package.
Resolve these dependencies by hand? [N/+/-/_/:/?] 
Abort.
```

---

### Post by Tarid on 2010-10-17
This

```
sudo apt-get install sun-java6-jre
```gets this
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
                 Depends: sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not installable
                 Recommends: gsfonts-x11 but it is not installable
E: Broken packages

```

---

### Post by Tarid on 2010-10-17
Sources:


```
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://packages.medibuntu.org/ lucid free non-free
##deb http://archive.canonical.com/ubuntu jaunty partner
##deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
deb http://us.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe
deb http://archive.canonical.com/ lucid partner
deb http://archive.canonical.com/ lucid partner
```

---

### Post by scouser73 on 2010-10-17
Please follow the instructions on the website for installing the latest version of Java: [ [COLOR="Red"]**Easy Linux Tips Project - Install Java**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by gandaran on 2010-10-17
> ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
[COLOR="DarkRed"]deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner[/COLOR]
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed restricted main multiverse universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates restricted main multiverse universe
[COLOR="DarkRed"]deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner[/COLOR]

look your sources list is a mess, remove those lines in red from the list then update the package list.
you will also need to fix the broken packages before installing again, use synaptic package manager to fix that.

---

### Post by Tarid on 2010-10-17
> **scouser73 said:**
> Please follow the instructions on the website for installing the latest version of Java: [ [COLOR=Red]**Easy Linux Tips Project - Install Java**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java")

Thanks this is going take awhile to do this. I will let you know if this works.

---

### Post by Tarid on 2010-10-17
> **gandaran said:**
> look your sources list is a mess, remove those lines in red from the list then update the package list.
you will also need to fix the broken packages before installing again, use synaptic package manager to fix that.


I will try this next.

---

### Post by gandaran on 2010-10-17
> **Tarid said:**
> Thanks this is going take awhile to do this. I will let you know if this works.
look you will not go any where with any instructions until you fix your sources list unless you install sun-java by downloading the .bin file from the sun-java website and installing this package and it can be a bit difficult for you to install the .bin package and it is not recommended to install java this way, so it would just be easier to fix the sources list and install java from the system repositories.

---

### Post by Tarid on 2010-10-17
> **gandaran said:**
> look your sources list is a mess, remove those lines in red 

Did that

> **gandaran said:**
> 
then update the package list.



new to linux, how can i do this?

> **gandaran said:**
> 

you will also need to fix the broken packages before installing again, use synaptic package manager to fix that.


new to linux, how can i do this? do i just select **fix broken packages. **If so I did that and received the same error messages in terminal

---

### Post by gandaran on 2010-10-17
okay now run the update package list command 
```
sudo apt-get update
```
now the install command
```
sudo apt-get install sun-java6-plugin
```
post any error messages if you get them

---

### Post by Tarid on 2010-10-17
> **gandaran said:**
> look you will not go any where with any instructions until you fix your sources list unless you install sun-java by downloading the .bin file from the sun-java website and installing this package and it can be a bit difficult for you to install the .bin package and it is not recommended to install java this way, so it would just be easier to fix the sources list and install java from the system repositories.

Thanks I fixed the source list as you suggested. I went back into the repository and selected sun-java6-jre to install

I got this


```

sun-java6-jre:
 Depends: java-common (>=0.24) but it is not installable
 Depends: sun-java6-bin but it is not going to be installed or
     ia32-sun-java6-bin (>=6.20dlj-1ubuntu3) but it is not installable
 Recommends: gsfonts-x11  but it is not installable
```This is my source list 
```
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://packages.medibuntu.org/ lucid free non-free
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main
deb http://us.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe
```

---

### Post by gandaran on 2010-10-17
> **Tarid said:**
> Thanks I fixed the source list as you suggested. I went back into the repository and selected sun-java6-jre to install

I got this


```

sun-java6-jre:
 Depends: java-common (>=0.24) but it is not installable
 Depends: sun-java6-bin but it is not going to be installed or
     ia32-sun-java6-bin (>=6.20dlj-1ubuntu3) but it is not installable
 Recommends: gsfonts-x11  but it is not installable
```This is my source list 
```
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb http://packages.medibuntu.org/ lucid free non-free
[COLOR="DarkRed"]deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu jaunty main[/COLOR]
deb http://us.archive.ubuntu.com/ubuntu/ lucid-proposed restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates restricted main multiverse universe
```
did you run the update command first?
the sources list looks okay now except the one in red, you choose the wrong version jaunty, should have been lucid to match your lucid system, I don't know if it has anything to do with your problem but you could try disabling it and update again

---

### Post by Tarid on 2010-10-17
After I removed line you mentioned. 
I ran the following 
```
sudo apt-get update
```
Then

```
sudo apt-get install sun-java6-jre
```
Got this 

```
Reading package lists... Done
Building dependency tree... 50%
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
                 Depends: sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not installable
                 Recommends: gsfonts-x11 but it is not installable

```

---

### Post by Tarid on 2010-10-17
Thanks for your help everyone. I wil be back in a few hours. I need some fresh air. Can't believe it is this difficult to install the JRE on  Ubuntu

---

### Post by gandaran on 2010-10-17
> **Tarid said:**
> After I removed line you mentioned. 
I ran the following 
```
sudo apt-get update
```
Then

```
sudo apt-get install sun-java6-jre
```
Got this 

```
Reading package lists... Done
Building dependency tree... 50%
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jre: Depends: java-common (>= 0.24) but it is not installable
                 Depends: sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.20dlj-1ubuntu3) but it is not installable
                 Recommends: gsfonts-x11 but it is not installable

```
theres some packages missing thats why you get these errors and I cant figure out why!
post the full output of the sudo apt-get update command just to check if any repo failed.

---

### Post by gandaran on 2010-10-17
> **Tarid said:**
> Thanks for your help everyone. I wil be back in a few hours. I need some fresh air. Can't believe it is this difficult to install the JRE on  Ubuntu
no its not difficult but something has gone wrong with your system!

---

### Post by Tarid on 2010-10-17
Back for a little

Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg                                             
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                                  
Ign [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu/) lucid/main Translation-en_US           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US                           
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                                         
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US              
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US                
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg                               
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US      
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                             
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release                                            
Ign [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_US          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release.gpg                                
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-proposed/universe Translation-en_US              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US        
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                                         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed Release                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages                               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-proposed/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Reading package lists... Done

---

### Post by Tarid on 2010-10-17
Anymore help on this?

---

### Post by nlneilson on 2010-10-17
[http://aroundtheweb.info/2010/10/install-sun-java-ubuntu-10-10-maverick-meerkat-official-partner-repository/](http://aroundtheweb.info/2010/10/install-sun-java-ubuntu-10-10-maverick-meerkat-official-partner-repository/)

Worked for me.

---

### Post by buknoii on 2010-10-17
in terminal type the following

- type sudo apt-get install update or update your synaptic package manager

- type sudo apt-get install sun-java6-jdk

---

### Post by sikander3786 on 2010-10-18
> **Tarid said:**
> Anymore help on this?
As a last resort, I'll recommend you to install the ubuntu-restricted-extras package. Contains java, flash, codecs, fonts etc.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Tarid on 2010-10-19
> **sikander3786 said:**
> As a last resort, I'll recommend you to install the ubuntu-restricted-extras package. Contains java, flash, codecs, fonts etc.

```
sudo apt-get install ubuntu-restricted-extras
```

no luck

Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.

---

### Post by Tarid on 2010-10-19
> **buknoii said:**
> in terminal type the following

- type sudo apt-get install update or update your synaptic package manager

- type sudo apt-get install sun-java6-jdk

sudo apt-get install update 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update
~$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (>= 6.22-0ubuntu1~10.04) but it is not going to be installed
                 Recommends: visualvm but it is not going to be installed
E: Broken packages

---

### Post by ankitaggarwal on 2012-03-15
i didnt fin the 2 line what you said to delete 
so i execute the update command and its showing the following error.What will i do next?

"W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release](http://in.archive.ubuntu.com/ubuntu/dists/oneiric-updates/Release)  Unable to find expected entry 'restrictedjaunty/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead."

---

