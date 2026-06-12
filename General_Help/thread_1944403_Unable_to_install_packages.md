---
title: "Unable to install packages"
date: 2012-03-21
forum: General Help
---

### Post by achu91 on 2012-03-21
I tried to install samba but resulted i have pasted below.Kindly help to install the same.


achuthan@achuthan-desktop:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 samba : Depends: samba-common (= 2:3.5.11~dfsg-1ubuntu2) but 2:3.5.11~dfsg-1ubuntu2.1 is to be installed
         Depends: libwbclient0 (= 2:3.5.11~dfsg-1ubuntu2) but 2:3.5.11~dfsg-1ubuntu2.1 is to be installed
E: Unable to correct problems, you have held broken packages.
achuthan@achuthan-desktop:~$

---

### Post by Bucky Ball on 2012-03-21
What release are you using? If you have Synaptic Package Manager you could open that and 'Fix Broken Packages'. 

But firstly, open a terminal and paste these commands, one at a time:

```
sudo apt-get update
sudo apt-get upgrade
```

This WILL NOT upgrade the release, only packages and dependencies that need upgrading. Then try installing Samba again. ;)

See if any of that helps and if not post the errors back here, please.

---

### Post by cortman on 2012-03-21
In addition to Bucky Ball's suggestions, you can run

```
sudo apt-get install -f
```

to fix broken packages.

---

### Post by achu91 on 2012-03-21
i am using Ubuntu 11.10 ,i just wanted to share some documents with other PC and i am just installing samba for that reason.i am sorry that i didn't mentioned it earlier.

i did as per your instruction and tried to re install samba by issuing the command sudo apt-get install samba.

The output is pasted  below.

achuthan@achuthan-desktop:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 samba : Depends: samba-common (= 2:3.5.11~dfsg-1ubuntu2) but 2:3.5.11~dfsg-1ubuntu2.1 is to be installed
         Depends: libwbclient0 (= 2:3.5.11~dfsg-1ubuntu2) but 2:3.5.11~dfsg-1ubuntu2.1 is to be installed
E: Unable to correct problems, you have held broken packages.
achuthan@achuthan-desktop:~$

[COLOR="Red"]in addition to that i have issued sudo apt-get install -f
and output for that is[/COLOR]

achuthan@achuthan-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

then i ried to installed samba but still got the above pasted errors. Kindly help

---

### Post by Bucky Ball on 2012-03-21
Have you tried, one at a time:

```
sudo apt-get update
sudo apt-get upgrade

```
... then tried to install Samba again, as I suggested in my last post? What is the other box running? Ubuntu or Windows? Regardless, if the machines have static IP addresses Filezilla is another option (my preferred one).

---

### Post by raja.genupula on 2012-03-21
> **achu91 said:**
> i am using Ubuntu 11.10 ,i just wanted to share some documents with other PC and i am just installing samba for that reason.i am sorry that i didn't mentioned it earlier.

i did as per your instruction and tried to re install samba by issuing the command sudo apt-get install samba.

The output is pasted  below.

achuthan@achuthan-desktop:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 samba : Depends: samba-common (= 2:3.5.11~dfsg-1ubuntu2) but 2:3.5.11~dfsg-1ubuntu2.1 is to be installed
         Depends: libwbclient0 (= 2:3.5.11~dfsg-1ubuntu2) but 2:3.5.11~dfsg-1ubuntu2.1 is to be installed
E: Unable to correct problems, you have held broken packages.
achuthan@achuthan-desktop:~$

[COLOR="Red"]in addition to that i have issued sudo apt-get install -f
and output for that is[/COLOR]

achuthan@achuthan-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

then i ried to installed samba but still got the above pasted errors. Kindly help


look for those two packages in synaptic and install from there and try again .

---

### Post by achu91 on 2012-03-21
bucky ball :i have tried one after one but still the same error!. i  didnt understand the other part of your question"[COLOR="Red"]What is the other box running? Ubuntu or Windows? Regardless, if the machines have static IP addresses Filezilla is another option (my preferred one)."[/COLOR]

---

### Post by Bucky Ball on 2012-03-21
Well, Filezilla is a file transfer program that uses ftp and/or ssh, but the machine's need to have static IP addresses (actually, they don't, but more convenient if they do). 

[http://filezilla-project.org/](http://filezilla-project.org/)

... and features here:

[http://filezilla-project.org/client_features.php](http://filezilla-project.org/client_features.php)

---

### Post by stinkeye on 2012-03-21
Have you disabled oneiric-updates because that is where the latest
**samba-common**(2:3.5.11~dfsg-1ubuntu2.1) and **libwbclient0**(2:3.5.11~dfsg-1ubuntu2.1)
were installed from on my 11.10 install.

The easiest way just to share a few documents would be using samba with Nautilus-share.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?t=1547389[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1547389")

---

### Post by Bucky Ball on 2012-03-21
Off topic, but nice signature and nice tip, stinkeye. Australia, I'm standing in it!

---

### Post by stinkeye on 2012-03-21
> **Bucky Ball said:**
> Off topic, but nice signature and nice tip, stinkeye. Australia, I'm standing in it!
lol, I was trying to work out how someone from Orstraya new about "Australia, I'm standing in it"...
was about to google Orstraya. ](*,)
Get a dog up ya.

---

### Post by Bucky Ball on 2012-03-21
> **stinkeye said:**
> 
get a dog up ya.

ha! ;)

---

### Post by achu91 on 2012-03-22
i followed the instruction as  stinkeye post#9 and hurry i have installed samba!!!!!!!!! thanks all for solving my issue....

---

