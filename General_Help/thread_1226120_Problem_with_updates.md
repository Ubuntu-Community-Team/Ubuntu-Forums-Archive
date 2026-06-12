---
title: "Problem with updates"
date: 2009-07-29
forum: General Help
---

### Post by jkchrisman on 2009-07-29
I am new to ubuntu and unix.  I just installed Ubuntu 9.4 on my computer.  Things seemed to be going fine.  A notification popped up that there were updates for the system so I told it to download them.

Apparently there was an error of some kind.  The package manager says that I have four broken packages. 

I am not sure where to go from here.  Any help would be appreciated.

Jim

---

### Post by nikhilk on 2009-07-29
Post output of the following commands
```
sudo aptitude update
sudo aptitude safe-upgrade
```

---

### Post by Psycho.mario on 2009-07-29
System>Administration>Synaptic Package Manager
Enter your password
Click "Edit" (Next to "File" top left), Then click "Fix broken packages"

That should fix your problem

---

### Post by jkchrisman on 2009-07-29
I'm sorry, but I am not sure how or where to post these commands:)

---

### Post by nikhilk on 2009-07-29
> **jkchrisman said:**
> I'm sorry, but I am not sure how or where to post these commands:)

Open a terminal to type the commands in. Terminal can be opened by pressing Alt-F2 to open a run dialog and then type in "gnome-terminal", without the quotes.

Probably first try what Psycho.mario has said and if that does not help, paste the output from the two commands in a post on this thread.

---

### Post by craig10x on 2009-07-29
Or just go to "Applications" tab on top...then "Accessories" then "Terminal"...... ;)

---

### Post by jkchrisman on 2009-07-29
I tried what Psycho suggested but I am still be told I have broken packages.

here is the output to the first command - sudo aptitude update:

jim@jim-laptop:~$ sudo aptitude update
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Reading package lists... Done

jim@jim-laptop:~$ 

Here is the output to the second command - sudo aptitude safe - upgrade:

jim@jim-laptop:~$ sudo aptitude safe - upgrade
Unknown command "safe"
aptitude 0.4.11.11
Usage: aptitude [-S fname] [-u|-i]
       aptitude [options] <action> ...
  Actions (if none is specified, aptitude will enter interactive mode):

 install      - Install/upgrade packages
 remove       - Remove packages
 purge        - Remove packages and their configuration files
 hold         - Place packages on hold
 unhold       - Cancel a hold command for a package
 markauto     - Mark packages as having been automatically installed
 unmarkauto   - Mark packages as having been manually installed
 forbid-version - Forbid aptitude from upgrading to a specific package version.
 update       - Download lists of new/upgradable packages
 safe-upgrade - Perform a safe upgrade
 full-upgrade - Perform an upgrade, possibly installing and removing packages
 forget-new   - Forget what packages are "new"
 search       - Search for a package by name and/or expression
 show         - Display detailed information about a package
 clean        - Erase downloaded package files
 autoclean    - Erase old downloaded package files
 changelog    - View a package's changelog
 download     - Download the .deb file for a package
 reinstall    - Download and (possibly) reinstall a currently installed package
 why          - Show the manually installed packages that require a package, or
                why one or more packages would require the given package
 why-not      - Show the manually installed packages that lead to a conflict
                with the given package, or why one or more packages would
                lead to a conflict with the given package if installed

  Options:
 -h             This help text
 -s             Simulate actions, but do not actually perform them.
 -d             Only download packages, do not install or remove anything.
 -P             Always prompt for confirmation or actions
 -y             Assume that the answer to simple yes/no questions is 'yes'
 -F format      Specify a format for displaying search results; see the manual
 -O order       Specify how search results should be sorted; see the manual
 -w width       Specify the display width for formatting search results
 -f             Aggressively try to fix broken packages.
 -V             Show which versions of packages are to be installed.
 -D             Show the dependencies of automatically changed packages.
 -Z             Show the change in installed size of each package.
 -v             Display extra information. (may be supplied multiple times)
 -t [release]   Set the release from which packages should be installed
 -q             In command-line mode, suppress the incremental progress
                indicators.
 -o key=val     Directly set the configuration option named 'key'
 --with(out)-recommends    Specify whether or not to treat recommends as
                strong dependencies
 -S fname       Read the aptitude extended status info from fname.
 -u             Download new package lists on startup.
 -i             Perform an install run on startup.

                  This aptitude does not have Super Cow Powers.
jim@jim-laptop:~$

---

### Post by nikhilk on 2009-07-29
> **jkchrisman said:**
> 
jim@jim-laptop:~$ 

Here is the output to the second command - sudo aptitude safe - upgrade:

You got the second command wrong mate. There are no spaces between safe and - and - and upgrade. It is continuous, single word safe-upgrade. Try that again and let us know the output.

---

### Post by jkchrisman on 2009-07-29
Sorry about that.  Here is the new data:

jim@jim-laptop:~$ sudo aptitude safe-upgrade
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages will be REMOVED:
  linux-headers-2.6.28-11{u} linux-headers-2.6.28-11-generic{u} 
The following packages will be upgraded:
  gnome-desktop-data gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 
The following partially installed packages will be configured:
  gnome-about linux-generic linux-image-2.6.28-13-generic 
  linux-image-2.6.28-14-generic linux-image-generic 
  linux-restricted-modules-2.6.28-13-generic 
  linux-restricted-modules-2.6.28-14-generic 
  linux-restricted-modules-generic 
5 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/1461kB of archives. After unpacking 74.7MB will be freed.
Do you want to continue? [Y/n/?]

---

### Post by nikhilk on 2009-07-29
And what happens if you press 'Y' and continue the safe-upgrade command?

---

### Post by jkchrisman on 2009-07-29
When I went back to terminal again and typed the command it didn't bring up the same message that ended with the Y/N response, but posted the following:

jim@jim-laptop:~$ aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jim@jim-laptop:~$

---

### Post by wojox on 2009-07-29
```
sudo aptitude safe-upgrade
```

---

### Post by jkchrisman on 2009-07-29
This is what I got when I continued the safe upgrade command:

jim@jim-laptop:~$ sudo aptitude safe-upgrade
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages will be REMOVED:
  linux-headers-2.6.28-11{u} linux-headers-2.6.28-11-generic{u} 
The following packages will be upgraded:
  gnome-desktop-data gvfs-backends gvfs-bin gvfs-fuse libgvfscommon0 
The following partially installed packages will be configured:
  gnome-about linux-generic linux-image-2.6.28-13-generic 
  linux-image-2.6.28-14-generic linux-image-generic 
  linux-restricted-modules-2.6.28-13-generic 
  linux-restricted-modules-2.6.28-14-generic 
  linux-restricted-modules-generic 
5 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B/1461kB of archives. After unpacking 74.7MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/libgvfscommon0_1.2.2-0ubuntu2_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/gvfs-backends_1.2.2-0ubuntu2_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/gvfs-bin_1.2.2-0ubuntu2_i386.deb
E: Invalid archive signature
E: Prior errors apply to /var/cache/apt/archives/gvfs-fuse_1.2.2-0ubuntu2_i386.deb
debconf: apt-extracttemplates failed: Bad file descriptor
(Reading database ... 140940 files and directories currently installed.)
Preparing to replace gnome-desktop-data 1:2.26.1-0ubuntu1 (using .../gnome-desktop-data_1%3a2.26.1-0ubuntu2_all.deb) ...
Unpacking replacement gnome-desktop-data ...
dpkg: error processing /var/cache/apt/archives/gnome-desktop-data_1%3a2.26.1-0ubuntu2_all.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
Errors were encountered while processing:
 /var/cache/apt/archives/gnome-desktop-data_1%3a2.26.1-0ubuntu2_all.deb
touch: cannot touch `/var/lib/update-notifier/dpkg-run-stamp': Stale NFS file handle
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.28-13-generic (2.6.28-13.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
cp: accessing `/var/lib/ucf/hashfile.4': Stale NFS file handle
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.28-13-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of gnome-about:
 gnome-about depends on gnome-desktop-data (= 1:2.26.1-0ubuntu2); however:
  Version of gnome-desktop-data on system is 1:2.26.1-0ubuntu1.
dpkg: error processing gnome-about (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.28-14-generic (2.6.28-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-14-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
cp: accessing `/var/lib/ucf/hashfile.4': Stale NFS file handle
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.28-14-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-14-generic:
 linux-restricted-modules-2.6.28-14-generic depends on linux-image-2.6.28-14-generic; however:
  Package linux-image-2.6.28-14-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-14-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-13-generic:
 linux-restricted-modules-2.6.28-13-generic depends on linux-image-2.6.28-13-generic; however:
  Package linux-image-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-13-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-14-generic; however:
  Package linux-image-2.6.28-14-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-14-generic; however:
  Package linux-restricted-modules-2.6.28-14-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.14.19); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.14.19); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.28-13-generic
 gnome-about
 linux-image-2.6.28-14-generic
 linux-restricted-modules-2.6.28-14-generic
 linux-restricted-modules-2.6.28-13-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

jim@jim-laptop:~$

---

### Post by Soul-Sing on 2009-07-29
seems a general problem with the latest kernel update:
[http://ubuntuforums.org/showthread.php?t=1226182](http://ubuntuforums.org/showthread.php?t=1226182)

---

### Post by jkchrisman on 2009-07-29
Can I just reinstall my OS and then not do the updates?

---

### Post by nikhilk on 2009-07-30
> **jkchrisman said:**
> Can I just reinstall my OS and then not do the updates?

Yes, you can do that. As a safety measure, always wait for some after new updates are available, do not install them right away.

You can then keep an eye on the forums to see if there is a widespread problem caused by the latest updates, if not then probably it is safe to update.

---

