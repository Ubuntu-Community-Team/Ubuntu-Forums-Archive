---
title: "virtualbox error when starting VM"
date: 2010-10-03
forum: General Help
---

### Post by m00nshine on 2010-10-03
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

I get this when I try to start a VM. I've issued the command with no success. I've also tried reinstalling and:

aptitude update
aptitude install dkms
/etc/init.d/vboxdrv setup

Nothing works! Help please!

---

### Post by snowpine on 2010-10-03
The command you listed all need to be run as "root" so use sudo:

```
sudo aptitude update
sudo aptitude install dkms
sudo /etc/init.d/vboxdrv setup

```

---

### Post by m00nshine on 2010-10-03
I ran them all as root

---

### Post by snowpine on 2010-10-03
> **m00nshine said:**
> I ran them all as root

I don't understand.

Please copy & paste the output of the exact commands I suggested.

---

### Post by m00nshine on 2010-10-03
What do you mean? I ran those commands in a root shell....

---

### Post by CharlesA on 2010-10-03
Post the output of those commands please.

I've had to kill anything related to virtualbox and start it back up after kernel updates before.

---

### Post by m00nshine on 2010-10-03
> **CharlesA said:**
> Post the output of those commands please.

I've had to kill anything related to virtualbox and start it back up after kernel updates before.

root@slave1ubuntu:/# aptitude update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                   
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release.gpg                   
Hit [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                     
A
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release.gpg                
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release                            
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_CA  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release               
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,310B]                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Packages                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Packages           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [964B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Sources
Fetched 2,465B in 0s (3,227B/s)
Reading package lists... Done

root@slave1ubuntu:/# aptitude install dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

root@slave1ubuntu:/# /etc/init.d/vboxdrv setup
bash: /etc/init.d/vboxdrv: No such file or directory
root@slave1ubuntu:/#

---

### Post by CharlesA on 2010-10-03
Hrm. On my machine that script is in /etc/init.d/

Try this:

```
locate vboxdrv | less
```

How did you install virtualbox?

---

### Post by m00nshine on 2010-10-03
> **CharlesA said:**
> Hrm. On my machine that script is in /etc/init.d/

Try this:

```
locate vboxdrv | less
```

How did you install virtualbox?

Thanks for the help!

/etc/init.d/vboxdrv.dpkg-bak
/etc/rc0.d/K20vboxdrv
/etc/rc1.d/K20vboxdrv
/etc/rc2.d/S20vboxdrv
/etc/rc3.d/S20vboxdrv
/etc/rc4.d/S20vboxdrv
/etc/rc5.d/S20vboxdrv
/etc/rc6.d/K20vboxdrv
/lib/modules/2.6.31-22-generic/updates/dkms/vboxdrv.ko
/lib/modules/2.6.32-25-generic/updates/dkms/vboxdrv.ko
/var/lib/update-rc.d/vboxdrv

I downloaded from their site...

---

### Post by snowpine on 2010-10-03
I have never used Ubuntu with "[root]("https://help.ubuntu.com/community/RootSudo")" account unlocked. Sorry I cannot be of further assistance.

---

### Post by CharlesA on 2010-10-03
There should be a lot more files then that. Did you install the OSE or the non-free version of Virtualbox?

---

### Post by m00nshine on 2010-10-03
ose I think. The AMD64 version from their site. 

[http://dlc.sun.com.edgesuite.net/virtualbox/3.2.8/virtualbox-3.2_3.2.8-64453~Ubuntu~lucid_amd64.deb](http://dlc.sun.com.edgesuite.net/virtualbox/3.2.8/virtualbox-3.2_3.2.8-64453~Ubuntu~lucid_amd64.deb)

I have upgraded to 10.04 btw

---

### Post by CharlesA on 2010-10-03
That's the right version.

Try running this:

```
sudo apt-get install -f
```

It is easier (IMHO) to just add the repo to /etc/apt/sources.list and apt-get it.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by m00nshine on 2010-10-03
root@slave1ubuntu:/# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@slave1ubuntu:/# 

Add the repositories? Oh is that when I add the URL to that file and just run apt-get update? And which lines would I have to add? Sorry I'm so noobish... I have most things working! lol. Had no problem on 32 bit...

---

### Post by CharlesA on 2010-10-04
> **m00nshine said:**
> root@slave1ubuntu:/# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@slave1ubuntu:/# 

Add the repositories? Oh is that when I add the URL to that file and just run apt-get update? And which lines would I have to add? Sorry I'm so noobish... I have most things working! lol. Had no problem on 32 bit...

Add this to sources.list:

```
deb http://download.virtualbox.org/virtualbox/debian lucid non-free
```

Then run:

```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

Then:

```
sudo apt-get update && sudo apt-get install virtualbox-3.2
```

---

### Post by m00nshine on 2010-10-04
No go :-( Should I uninstall and try again? 

root@slave1ubuntu:/etc/apt# wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
OK
root@slave1ubuntu:/etc/apt# sudo apt-get update && sudo apt-get install virtualbox-3.2
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [191B]
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_CA       
Get:2 [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release.gpg [197B]                  
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_CA   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_CA       
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,310B]                             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release.gpg                             
Get:5 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_CA [10.3kB]
Ign [http://download.virtualbox.org/virtualbox/debian/](http://download.virtualbox.org/virtualbox/debian/) lucid/non-free Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_CA
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_CA
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [38.5kB]               
Get:7 [http://dl.google.com](http://dl.google.com) stable/main Packages [964B]                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Get:8 [http://download.virtualbox.org](http://download.virtualbox.org) lucid Release [3,445B]                    
Get:9 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_CA [425B]
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Get:10 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_CA [663B]
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_CA    
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release.gpg [198B]           
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid Release                               
Get:12 [http://download.virtualbox.org](http://download.virtualbox.org) lucid/non-free Packages [1,322B]         
Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates Release [44.7kB]             
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [87.1kB]        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Packages             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/main Sources      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid/multiverse Sources
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Packages [319kB]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [31.5kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]      
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [43.5kB]   
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [10.9kB]     
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [1,869B]  
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [656B]
Get:23 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Packages [3,267B]
Get:24 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/main Sources [124kB]
Get:25 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/restricted Sources [1,443B]
Get:26 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Packages [123kB]
Get:27 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/universe Sources [49.6kB]
Get:28 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Packages [3,651B]
Get:29 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) lucid-updates/multiverse Sources [1,739B]
Fetched 905kB in 1s (462kB/s)                                
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
virtualbox-3.2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@slave1ubuntu:/etc/apt# 

Thanks!

---

### Post by CharlesA on 2010-10-04
Yeah. Try purging it and installing it again.

---

### Post by hitman_dreams on 2010-10-04
I've had issues with vbox in the past as well. Usually it's when a new kernel update is installed. When this happens the terminal line they give you to run doesn't work; that's when you try this:

1. run in terminal to get your kernel version (2.6.32-25-generic) for example:
     uname -a

2. download the linux headers via terminal (replace versionNumber with the number from the last step):
     sudo apt-get install linux-headers-versionNumber

3. run in the terminal:
     sudo /etc/init.d/vboxdrv setup

Virtualbox should be back to normal after this. If it works you'll most likely have to do this every time the kernel updates, so be aware of that.

Hope this helps, let me know how it goes.

---

### Post by snowpine on 2010-10-04
If you install dkms (as the message from VirtualBox suggests) you will not need to worry about kernel updates.

---

### Post by isecore on 2010-10-04
I know this is wildly off-topic but....

It's not that difficult, and you don't need to "unlock" the root-user either. Just do sudo -i or sudo -s (there's some subtle difference between them) and you elevate your userlevel for that shell permantently until you use exit. Basically it's the same as using su to become root, but applicable on distros such as Ubuntu that prefer the sudo-mechanism.

I use this all the time to keep a root-shell open and not have to preface every command with sudo, and not have to give my password a whole bunch.

> **snowpine said:**
> I have never used Ubuntu with "[root]("https://help.ubuntu.com/community/RootSudo")" account unlocked. Sorry I cannot be of further assistance.

---

### Post by hitman_dreams on 2010-10-04
> **snowpine said:**
> If you install dkms (as the message from VirtualBox suggests) you will not need to worry about kernel updates.

while I agree; he seems to be having an issue with installing dkms. Once he gets that working it'll be fine. But until then, a re-install of virtualbox will only help until the next kernel update...as will my solution, which takes less time.

---

### Post by m00nshine on 2010-10-04
It didn't work... 

emperor@slave1ubuntu:~$ su root
Password: 
root@slave1ubuntu:/home/emperor# apt-get remove virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@slave1ubuntu:/home/emperor# apt-get remove virtualbox-ose
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox-ose is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@slave1ubuntu:/home/emperor# uname -a
Linux slave1ubuntu 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64 GNU/Linux
root@slave1ubuntu:/home/emperor# apt-get install linux-headers-2.6.32-25-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.32-25-generic is already the newest version.
linux-headers-2.6.32-25-generic set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@slave1ubuntu:/home/emperor# /etc/init.d/vboxdrv setup
bash: /etc/init.d/vboxdrv: No such file or directory
root@slave1ubuntu:/home/emperor# dpkg -list | grep virtualbox
dpkg: conflicting actions -i (--install) and -l (--list)

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
root@slave1ubuntu:/home/emperor# dpkg -l | grep virtualbox
ii  virtualbox-3.2                       3.2.8-64453~Ubuntu~lucid                        Oracle VM VirtualBox
rc  virtualbox-ose                       3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - base binaries
rc  virtualbox-ose-qt                    3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - Qt based user 
root@slave1ubuntu:/home/emperor# apt-get remove virtualbox*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting virtualbox for regex 'virtualbox*'
Note, selecting virtualbox-ose-dbg for regex 'virtualbox*'
Note, selecting virtualbox-ose-source for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-dkms for regex 'virtualbox*'
Note, selecting virtualbox-ose-dkms for regex 'virtualbox*'
Note, selecting virtualbox-ose-qt for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-source for regex 'virtualbox*'
Note, selecting virtualbox-ose for regex 'virtualbox*'
Note, selecting virtualbox-2.0 for regex 'virtualbox*'
Note, selecting virtualbox-2.1 for regex 'virtualbox*'
Note, selecting virtualbox-2.2 for regex 'virtualbox*'
Note, selecting virtualbox-3.0 for regex 'virtualbox*'
Note, selecting virtualbox-3.1 for regex 'virtualbox*'
Note, selecting virtualbox-3.2 for regex 'virtualbox*'
Note, selecting virtualbox-ose-fuse for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-utils for regex 'virtualbox*'
Note, selecting virtualbox-ose-guest-x11 for regex 'virtualbox*'
Note, selecting virtualbox-guest-additions for regex 'virtualbox*'
The following packages will be REMOVED:
  virtualbox-3.2
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 97.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 151030 files and directories currently installed.)
Removing virtualbox-3.2 ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_CA.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for ureadahead ...
Processing triggers for python-support ...
root@slave1ubuntu:/home/emperor# dpkg -l | grep virtualbox
rc  virtualbox-3.2                       3.2.8-64453~Ubuntu~lucid                        Oracle VM VirtualBox
rc  virtualbox-ose                       3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - base binaries
rc  virtualbox-ose-qt                    3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - Qt based user 
root@slave1ubuntu:/home/emperor# apt-get remove virtualbox-ose-qt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox-ose-qt is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@slave1ubuntu:/home/emperor# apt-get remove virtualbox-ose
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package virtualbox-ose is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
root@slave1ubuntu:/home/emperor# dpkg -l | grep virtualbox
rc  virtualbox-3.2                       3.2.8-64453~Ubuntu~lucid                        Oracle VM VirtualBox
rc  virtualbox-ose                       3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - base binaries
rc  virtualbox-ose-qt                    3.1.6-dfsg-2ubuntu2                             x86 virtualization solution - Qt based user 
root@slave1ubuntu:/home/emperor# 

It seems that I'm not successfully removing virtualbox? What the hell is going on here, linux, LOL

---

### Post by m00nshine on 2010-10-04
OK I'm using the commands CharlesA gave me and it seems to be downloading virtualbox. 

I'll post more in a bit...

---

### Post by hitman_dreams on 2010-10-05
make sure to get dkms working or you'll have to go through the steps I posted on page two when a kernel update installs. hope it's working for you again soon.

---

### Post by CharlesA on 2010-10-05
If you use apt-get to install it, that should get all the dependancies installed.

Best of luck.

---

### Post by m00nshine on 2010-10-05
Ok well I'll see what I can do when I get home. Is there an alternative to this prog that is hopefully as easy to use? Thanks again, guys.

---

### Post by CharlesA on 2010-10-05
There is KVM and VMware, but I've found VBox to be the easiest of them to deal with.

---

