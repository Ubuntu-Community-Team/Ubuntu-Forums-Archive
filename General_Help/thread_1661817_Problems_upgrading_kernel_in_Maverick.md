---
title: "Problems upgrading kernel in Maverick"
date: 2011-01-07
forum: General Help
---

### Post by iosuna86 on 2011-01-07
As seen in the screenshot, my update manager won't let me mark the proposed kernel updates for installation.

I have heard that I would be able to mark them after a few days have passed ( I don't know the reason, though). Well, now it's been 3 weeks that I have them as "proposed updates" and I still can't mark them.

I decided to run apt-get upgrade in the terminal and here is the output:

```
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```Then, I tried to manually install the packages:

```
~$ sudo apt-get install linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
 linux-headers-generic-pae : Depends: linux-headers-2.6.35-24-generic-pae but it is not installable
 linux-image-generic-pae : Depends: linux-image-2.6.35-24-generic-pae but it is not installable
E: Broken packages
```Next:

```
~$ sudo apt-get install linux-headers-2.6.35-24-generic-pae linux-image-2.6.35-24-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.35-24-generic-pae is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
Package linux-image-2.6.35-24-generic-pae is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'linux-headers-2.6.35-24-generic-pae' has no installation candidate
E: Package 'linux-image-2.6.35-24-generic-pae' has no installation candidate

```So what do I have to do? Any suggestions?

Thanks in advance

---

### Post by iosuna86 on 2011-01-07
Nobody?

---

### Post by snowpine on 2011-01-07
Try:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

"sudo apt-get upgrade" alone will not install new kernels (as you discovered).

---

### Post by davidmohammed on 2011-01-07
what is the result of

sudo apt-get update && sudo apt-get upgrade

also try

sudo apt-get -f install

---

### Post by iosuna86 on 2011-01-07
Hey, thanks for the replies.

I had already tried that before with the same result to both commands:

```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```Regarding the 

```
sudo apt-get -f install
```I tried to force the install of linux-generic-pae to start with and here is the result:

```
sudo apt-get install linux-generic-pae -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-image-generic-pae (= 2.6.35.24.30) but 2.6.35.23.25 is to be installed
E: Broken packages
```There is one thing I don't quite understand about Ubuntu. I try to install something, but it says that it depends on something else to be installed. I try to install that, but the same thing happens. Is this an endless chain or are there any basic packages that I should install in order to have pretty much everything available to install? I am loving Ubuntu, though. It's just that I'm kinda new to it and I don't how some things work.

Thanks for your help.

---

### Post by iosuna86 on 2011-01-09
Bump.

I really need some help here.

---

### Post by iosuna86 on 2011-01-15
It is now _SOLVED_. I just ran Update Manager and I have been able to mark all the upgrades for installation. 

I guess I just had to wait some weeks (about 4).

---

### Post by sergey1369 on 2012-04-20
Same problem.

# apt-get dist-upgrade 

Solved it for me.

---

