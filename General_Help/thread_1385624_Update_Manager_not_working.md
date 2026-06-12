---
title: "Update Manager not working"
date: 2010-01-19
forum: General Help
---

### Post by tvillamil on 2010-01-19
I am having issues with Update Manager after cancelling an Update.

The Update Manager shows a number of required updates, but when I click on Install Updates... Nothing happens

When I launch sudo dpkg --configure -a in a terminal I receive the following message:

dpkg: status database area is locked by another process.

On another forum i saw something regarding a gksu.lock file that needed to be deleted... but I can't find any such file....

If I try to launch update manager via a terminal:  sudo update-manager I get the following error:

requiredDownload could not be calculated: E:Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages (2), E:Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages (1), E:Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages (2), E:Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages (2), E:Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages (1)

Anyone have any ideas... I'm two clicks short of re-installing from a backup.  :sad:

Thanks,

---

### Post by michy99 on 2010-01-19
What is the output of```
sudo apt-get update
```

---

### Post by tvillamil on 2010-01-19
Thanks for responding!!!!


Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by michy99 on 2010-01-19
Do you have any other package manager open? Synaptic, Update Manager, Software Center, dpkg?

---

### Post by tvillamil on 2010-01-19
Sorry... I must have...  here is the new output:

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done

After doing this.... I went into Update manager, and it still shows the packages needing to be updated...  and I click on Install Updates..... nothing....

tv

---

### Post by michy99 on 2010-01-19
Okay, run this in the terminal:```
sudo apt-get upgrade
```

---

### Post by tvillamil on 2010-01-19
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic vpnc
The following packages will be upgraded:
  cpp-4.4 firefox firefox-3.5 firefox-3.5-branding firefox-3.5-gnome-support
  firefox-gnome-support gcc-4.4 gcc-4.4-base gimp gimp-data gnome-screensaver
  lib32gcc1 lib32stdc++6 libc-bin libc-dev-bin libc6 libc6-dev libc6-i386
  libgcc1 libgimp2.0 libgomp1 libgssapi-krb5-2 libk5crypto3 libkrb5-3
  libkrb5support0 libpurple-bin libpurple0 libsmbclient libssl0.9.8 libstdc++6
  libthai-data libthai0 libwbclient0 linux-libc-dev openssl rhythmbox
  samba-common samba-common-bin smbclient transmission-common transmission-gtk
  xserver-xorg-video-intel xulrunner-1.9.1 xulrunner-1.9.1-gnome-support
44 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
E: The package index files are corrupted. No Filename: field for package libc6-i386.
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages (2)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages (2)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages (2)
E: Unable to parse package file /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages (1)

---

### Post by michy99 on 2010-01-19
Try this```
sudo mv /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages_backup
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by tvillamil on 2010-01-19
SOLVED!!!

It worked.  Thank you!!!

So ........ any idea what caused it??

tv

---

### Post by michy99 on 2010-01-19
There was something in that package list that was messed up. By renaming it, the system had to download the whole list again. If you want, you can delete the backup. (It's the messed up list.)```
sudo rm /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_karmic-updates_main_binary-amd64_Packages_backup
```

---

