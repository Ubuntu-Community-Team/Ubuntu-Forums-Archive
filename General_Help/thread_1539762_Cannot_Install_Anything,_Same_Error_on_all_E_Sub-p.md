---
title: "Cannot Install Anything, Same Error on all: E: Sub-process /usr/bin/dpkg returned an"
date: 2010-07-26
forum: General Help
---

### Post by Garetty on 2010-07-26
I've been getting this error for quite a while off and on, I am usually able to find ways to fix it. Now, I cannot find a way to fix it. I've tried just about everything I could find. 

But I have noticed that I get this error with everything I try to install:

```
Setting up linux-image-2.6.32-24-generic (2.6.32-24.38) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-24-generic
Found kernel: /boot/vmlinuz-2.6.32-23-generic
Found kernel: /boot/memtest86+.bin
User postinst hook script [/sbin/update-grub] exited with value 10
dpkg: error processing linux-image-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: also configuring `linux-image-generic' (required by `linux-generic')
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-2.6.32-24-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
 linux-image-generic
Processing was halted because there were too many errors.

```
```

austin@DOWNSTAIRS-PC:~$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-24-generic (2.6.32-24.38) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-24-generic
Found kernel: /boot/vmlinuz-2.6.32-23-generic
Found kernel: /boot/memtest86+.bin
User postinst hook script [/sbin/update-grub] exited with value 10
dpkg: error processing linux-image-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.24.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.32-24-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And I'm not sure if this has to do with anything, but when I try to run Ubuntu Software Center, it gives me this error: 
```
sorry, cannot open the software database.
Please re-install the 'software-center' package.
```
I have tried that, but I get the first error above.

---

### Post by heimo on 2010-07-27
I would try removing linux-image-2.6.32-24-generic (sudo aptitude --purge remove linux-image-2.6.32-24-generic), then run "sudo aptitude update" and see if you get any errors. If so, remove any conflicting packages (be sure not to remove anything needed to run your system), flush package cache ("sudo aptitude clean"), "dpkg --configure -a" and then "sudo aptitude upgrade" again.

---

### Post by aidenscool09 on 2010-07-27
Isn't that the kernel image though, even though ubuntu comes shipped with 2 and their recovery mode versions.

---

### Post by aidenscool09 on 2010-07-27
Also, open up Synaptic, you might get a notification when you open it. Sometimes it tells you what is wrong if not then try installing something through there and see what happens.

---

### Post by wojox on 2010-07-27
How about 

```
sudo apt-get -f install
```

```
sudo apt-get upgrade
```

---

### Post by aidenscool09 on 2010-07-27
Good idea.

---

### Post by aidenscool09 on 2010-07-27
God, half past five in the morning and i'm still on ubuntu forums trying to help people :) i'm so generous.

---

### Post by Garetty on 2010-07-27
> **heimo said:**
> I would try removing linux-image-2.6.32-24-generic (sudo aptitude --purge remove linux-image-2.6.32-24-generic), then run "sudo aptitude update" and see if you get any errors. If so, remove any conflicting packages (be sure not to remove anything needed to run your system), flush package cache ("sudo aptitude clean"), "dpkg --configure -a" and then "sudo aptitude upgrade" again.

Ok, I did that, and I removed then reinstalled Firefox to see what would happen. It removed and installed, but I still get this:

```
austin@DOWNSTAIRS-PC:~$ sudo apt-get install firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  firefox-branding
Suggested packages:
  firefox-gnome-support kmozillahelper latex-xft-fonts
The following NEW packages will be installed:
  firefox firefox-branding
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.5MB of archives.
After this operation, 30.8MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/ lucid/main firefox-branding 3.6.9~hg20100725r34460+nobinonly-0ubuntu1~umd1~lucid [155kB]
Get:2 http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/ lucid/main firefox 3.6.9~hg20100725r34460+nobinonly-0ubuntu1~umd1~lucid [11.3MB]
Fetched 11.5MB in 32s (357kB/s)                                                
Selecting previously deselected package firefox-branding.
(Reading database ... 
dpkg: warning: files list file for package `libxcomposite-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-power-manager' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-2.6.32-22-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libio-string-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wwwconfig-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglade2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gconf-defaults-service' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gtk2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxau6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblaunchpad-integration1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-bengali-fonts' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblockfile1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pulseaudio-module-bluetooth' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lsof' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `netcat' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdb4.7-java-gcj' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome-media0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkrb5-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cups' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwrap0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `awn-applets-python-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gcc-4.4-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `usbmuxd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `protobuf-compiler' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnotski' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-assistant' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcupsimage2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libid3tag0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcoin40c2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-twisted-names' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libilmbase-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnupg-curl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pptp-linux' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `upower' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcursor-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `software-properties-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `policykit-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdevel-symdump-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libapr1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwpd8c2a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglib2.0-doc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcap2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-launchpadlib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `limewire-basic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-opensymbol' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpt2.6.5-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-sound-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `readline-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-gb-gui' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `usb-creator-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmodplug0c2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gir1.0-gconf-2.0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `aisleriot' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxt6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtext-charwidth-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-tseng' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-sqlite2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wodim' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgomp1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `swell-foop' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnet-dbus-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libio-compress-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-session-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdesktop-agnostic-vfs-gio' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `intltool' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-configglue' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdata6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglib2.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgphoto2-port0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libapparmor1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-client-5.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfreetype6-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `less' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `winpdb' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sun-java6-plugin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ibus-m17n' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libraptor1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dbconfig-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-headers-2.6.32-22' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-headers-2.6.32-23' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `festlex-poslex' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-headers-2.6.32-21' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `erlang-crypto' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsqlite3-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-lazr.restfulclient' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglib2.0-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-corlib1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-l10n-es' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-alsa' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpackagekit-qt-12' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `php5-mysql' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libart-2.0-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpolkit-qt-1-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-corlib2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cdparanoia' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfaad2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `binutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-siliconmotion' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-ati' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `fortunes-min' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-server' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xorg-docs-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome-bluetooth7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libboost-program-options1.40.0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wv' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsqlite0-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-debian' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xmoto-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `vim-tiny' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gvfs-fuse' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `strace' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `update-notifier-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ca-certificates' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `evolution-indicator' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pulseaudio' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmlt++3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhtml-tagset-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-gb-db' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `iputils-arping' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plasma-scriptengine-javascript' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-system2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtelepathy-farsight0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbonobo2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apport' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `nautilus-sendto' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libprotoc5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `klipper' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `zip' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-i740' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11-xfs-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhttp-server-simple-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `scim' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpcsclite1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvisual-0.4-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libstdc++6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xsane' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `network-manager-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `powermgmt-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cpio' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `konqueror' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglew1.5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libservlet2.5-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rsyslog' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfontenc1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hplip' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmad0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `m4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkworkspace4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apparmor' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `popularity-contest' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmlt-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdesktop-agnostic-fdo-glib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubuntu-minimal' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-x' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-uno' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rhythmbox-plugin-cdrecorder' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libneon27' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-server-core-5.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `po-debconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `reiserfsprogs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `avahi-daemon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `computer-janitor-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmusicbrainz4c2a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome-mag2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmeanwhile1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt3-compat-headers' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `update-manager' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `devhelp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xfonts-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libindicator0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglitz1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcursor1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `speech-dispatcher' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-desktopcouch-records' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `patchutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ekiga' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblouis-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libapparmor-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `make' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpcre3-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bash' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbusmenu-qt2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsasl2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-opengl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rpm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libblas3gf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-xmlpatterns' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmetacity-private0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcommons-beanutils-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdebase-workspace-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml-twig-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `iptables' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdelibs4-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bzrtools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-2.6.28-18-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-sharpzip0.84-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-security1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdevkit-power-gobject1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxklavier16' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-xv0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpixman-1-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdjvulibre21' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcompress-raw-bzip2-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-writer' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-httplib2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmpeg2-4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `defoma' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnutls-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libapm1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `udev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-help-de' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `adobe-flashplugin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `evolution-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsmpeg-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcommons-compress-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-about' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-desktop-agnostic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-geode' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsolidcontrolifaces4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `erlang-syntax-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apt-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdepim-runtime' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-sharpzip2.84-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libode1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpt-1.10.10' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxmu-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpng12-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaccess-bridge-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk2-imageview-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sat4j' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-plugins-good' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxxf86vm1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compizconfig-backend-gconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libattr1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-help-pt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-bugbuddy' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dput' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `foomatic-db' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `php5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `untex' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libstlport4.6ldbl' missing, assuming package has no files currently installed.
(Reading database ... 5%
dpkg: warning: files list file for package `ghostscript-cups' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wvdial' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpam-ck-connector' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `phonon-backend-xine' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sun-java6-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdb4.7-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-selector-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomevfs2-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `onboard' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-gb-qt-ext' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpt-1.10.10-plugins-v4l' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglib2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dhcp3-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sun-java6-source' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-test' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mobile-broadband-provider-info' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `w3m' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `freepats' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `notify-osd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tracker' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsm6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-nv' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `recordmydesktop' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcommons-logging-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-desktopcouch' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libc6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtalloc1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtalloc2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pidgin-otr' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaa1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11proto-composite-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ntpdate' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libiw30' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libplrpc-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-openssl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-hyphenation-en-us' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `vbetool' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmysqlclient-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-khmeros-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openssh-client' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `firebird2.1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-l10n-bn' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cpu-checker' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `totem-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libopenobex1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libselinux1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnet-libidn-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libntfs-3g75' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `time' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libx11-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtrackerclient0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-applets' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libesd0-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnih-dbus1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libatk1.0-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcupsppdc1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsysfs-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libspectre1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmjpegtools-1.9' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-shape0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfaac0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkrb5-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sun-java6-jdk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libzephyr4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `m17n-contrib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk2.0-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libplasmagenericshell4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libparse-debianchangelog-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvte9' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpcrecpp0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-apt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pppoeconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `light-themes' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnibbles' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libesd0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-libxml2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libice6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-base-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomeprintui2.2-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `unixodbc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kerneloops-daemon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-vlgothic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `fuse-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-input-mouse' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `acpi-support' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnspr4-0d' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dcraw' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `librpm0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `aspell' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `inputattach' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libipc-run-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libindicate4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-sazanami-gothic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `nano' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubuntu-docs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpostproc51' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-security2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcdparanoia0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxtst6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-dejavu' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libedit2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-oauth' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-pygame' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `fontconfig-config' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `imagemagick' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `network-manager-pptp-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libarchive1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgcj-bc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkdb5-4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmail-sendmail-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-input-all' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-mag' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sun-java6-javadb' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome-keyring0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bluez-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubuntu-system-service' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-xml' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cron' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `fglrx-modaliases' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libicu42' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-couchdb' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpackagekit-glib2-12' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libacl1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sysvinit-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome-vfs2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xml-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libedata-cal1.2-6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libclucene0ldbl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `phonon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxine1-x' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbusmenu-gtk1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-de-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hplip-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-plugins-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-pygoocanvas' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `zenity' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxine1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libldap-2.4-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ant-optional' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apache2.2-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libapache2-mod-php5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `guile-1.8-libs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mime-support' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `alsa-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblpint-bonobo0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gconf2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gcj-4.4-jre-lib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bogofilter-bdb' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpolkit2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-pt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgupnp-1.0-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `librasqal2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-firmware' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `php5-cli' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libc-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-client3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-qt3support' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtksourceview2.0-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-2.6.32-17-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `php5-mcrypt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwnck22' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lp-solve' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpciaccess0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `zlib1g-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubuntu-mono' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `devhelp-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `f-spot' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `unzip' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-imaging' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apache2.2-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgphoto2-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-notify' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavformat52' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwnck-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsub-name-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcucul0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvorbis0a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libx11-xcb1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-de' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xscreensaver-gl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl1.2debian-pulseaudio' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libio-pty-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `konqueror-nsplugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `telepathy-salut' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtag1c2a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtiff4-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgucharmap7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-system-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `notification-daemon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblua5.1-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libggzmod4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-gnome-es' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-screensaver' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `oxygen-icon-theme' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rhythmbox-ubuntuone-music-store' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wireless-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-gnome-en' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdrm-intel1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `comerr-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gcc-4.3-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gtk2-doc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcupscgi1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdrm-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdvdnav4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-es-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `iagno' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-rdflib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-virtkey' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `evolution' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-wadllib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-user-guide-en' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-user-guide-es' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libc6-i686' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-qt4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `console-terminus' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhtml-parser-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `network-manager' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `scim-bridge-agent' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-xh-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `unixodbc-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `friendly-recovery' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnautilus-extension1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtkhtml2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcaca0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnm-glib2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpolkit-gtk-1-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhyphen0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11proto-damage-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-mach64' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rarian-compat' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-utidylib' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcairo-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `system-config-printer-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmikmod2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmp3lame0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `indicator-messages' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libedata-book1.2-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-launchpad-bugs' missing, assuming package has no files currently installed.
(Reading database ... 10%
dpkg: warning: files list file for package `eclipse-platform-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdirectfb-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cups-bsd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `automake' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `thunderbird-locale-en-gb' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `flightgear' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdotconf1.0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libomniorb4-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-intel' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-pyatspi' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgsl0ldbl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-i18n2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-i18n-west2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-system1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvisual-0.4-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-chips' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnautilus-burn4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `im-switch' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `screen-resolution-extra' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `indicator-application' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-panel-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libproc-simple-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbz2-1.0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdata-google1.2-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwmf0.2-7-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-aptdaemon-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `firebird2.1-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xtrans-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `iputils-tracepath' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-trident' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxp6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `diff' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-system-web2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ubuntuone-storageprotocol' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `seed' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-dejavu-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `espeak-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-cairo2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ibus-table' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-scripttools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblcms1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-awn' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `iputils-ping' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libx11-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `diffstat' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libopenthreads12' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-s3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl-ttf2.0-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pulseaudio-esound-compat' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-crypto' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libprocesscore4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-xdg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ghostscript' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmcrypt4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-themes' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglade2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-desktop-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libio-socket-ssl-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwebkit-1.0-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libilmbase6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `busybox-initramfs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gimp-help-en' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gcc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `alsa-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gimp-help-es' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `irqbalance' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-user-share' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbonoboui2-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `totem-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfile-copy-recursive-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libssl-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl-ttf2.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcap-ng0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `eject' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-pulseaudio' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `samba-common-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tsconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `min12xxw' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dmsetup' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaa1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `aptdaemon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnobots2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbeagle1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-opengl-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11proto-core-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gdebi' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tracker-search-tool' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-telepathy' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `info' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdelibs-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-numpy' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-cairo1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `anacron' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-calc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gksu' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gst0.10' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `vino' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gtkglext1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-twisted-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rss-glx' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcanberra-gtk0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtkglext1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxine1-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwvstreams4.6-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-compat-libdnssd1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `build-essential' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xbitmaps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-pam' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pidgin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcommons-el-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-cupshelpers' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libplib1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-hyphenation' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `eclipse-rcp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-xapian' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sun-java6-demo' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `acpi' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubuntu-keyring' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-server-5.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `launchpad-integration' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmimic0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblocale-gettext-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmagickcore2-extra' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwebkit-1.0-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-simplejson' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libncursesw5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml-sax-expat-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x-ttcidfont-conf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaudio-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-mahjongg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `phpmyadmin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsort-naturally-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpt-1.10.10-plugins-alsa' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblua50-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `iso-codes' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pkg-config' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libept0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubuntu-desktop' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkdecorations4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gsfonts-x11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `aptitude' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpcre3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-feedparser' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxvidcore4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `quickly-ubuntu-template' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt3-headers' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnet-ssleay-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-chardet' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-pyinotify' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgail-gnome-module' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dpkg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwww-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gzip' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomeui-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `syslinux' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-gnonlin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-i128' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblircclient0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpulse-browse0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `insserv' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbrasero-media0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-symbol-replacement' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcurl4-gnutls-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-qt3-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `poppler-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `notify-osd-icons' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgpm2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbus-1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-mga' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dbus-x11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgirepository1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xsltproc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaccess-bridge-java-jni' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wisotool' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnutls26' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libomniorb4-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfile-desktopentry-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdelibs5-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnomine' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hunspell-en-ca' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `evolution-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libplist1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnss-mdns' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cpp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-common3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `brltty' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcroco3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtkhtml3.14-19' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkadm5clnt-mit7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavfilter0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `netcat-traditional' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libexiv2-6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkfontinst4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `junit4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpng12-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libopal3.6.6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglibmm-2.4-1c2a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqimageblitz4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdepimlibs5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-numeric' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnih1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libopenexr-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-posix1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblzma1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-dejavu-extra' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `quadrapassel' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gir1.0-gstreamer-0.10' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libssh-4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-gnome-bn' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-l10n-pt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-applets-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgcj-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhesiod0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsidplay1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-gb-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-central' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libatk1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gvfs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `nautilus' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpolkit-backend-1-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `couchdb-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openssh-server' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `acl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsigc++-2.0-0c2a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gobject' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tsclient' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpaper1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `e2fsprogs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gtk2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rdesktop' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cabextract' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libido-0.1-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpangomm-1.4-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgmime-2.4-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `jockey-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libao2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-l10n-de' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsmpeg0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `media-player-info' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-help' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libspeex-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-pitfdll' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcanberra0' missing, assuming package has no files currently installed.
(Reading database ... 15%
dpkg: warning: files list file for package `gnome-terminal-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ksysguard' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjasper1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsensors4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-compizconfig' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsensors3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libx11-6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xfonts-encodings' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `app-install-data-partner' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `devscripts' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomevfs2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtidy-0.99-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxau-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt3-mt-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libstdc++6-4.4-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dosfstools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-nouveau' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liboobs-1-4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libksgrd4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libusplash0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `erlang-runtime-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `fortune-mod' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomevfs2-extra' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgail-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xz-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-distutils-extra' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomecanvas2-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgweather-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxft2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkonqsidebarplugin4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbsd0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdebase-workspace-kgreet-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `findutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apache2-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtaskmanager4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `at-spi' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rpm2cpio' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtksourceview2.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `qt4-qmake' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libunique-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gucharmap' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-common-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-plugins-ugly-multiverse' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `command-not-found' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compizconfig-settings-manager' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libss2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcv4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xinput' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-runtime' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apparmor-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liborbit2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglew1.5-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz-fusion-plugins-main' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libiptcdata0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdatrie1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libblkid1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `initscripts' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhtml-template-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apache2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pnm2ppa' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-metacity' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdc1394-22' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `nvidia-173-modaliases' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libslang2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl-mixer1.2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-rsvg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ufw' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libebackend1.2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lua50' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kde-minimal' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdjvulibre-text' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xauth' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-disk-utility' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgstreamer0.10-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xdg-user-dirs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gtksourceview2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcompizconfig0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblualib50-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `librsvg2-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `docbook-xml' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `foomatic-db-engine' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaudio2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgladeui-1-9' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-headers-2.6.32-21-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `geoip-database' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpam-runtime' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpisock9' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libggzcore9' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libstartup-notification0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `screen' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libstreamanalyzer0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gnomekeyring' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python2.6-minimal' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpthread-stubs0-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libacl1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-farsight' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libplasma3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ggzcore-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `fakeroot' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dmz-cursor-theme' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-quickly-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xkb-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pidgin-libnotify' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-dateutil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bsd-mailx' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-l10n-en-gb' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-webkit' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hostname' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libimlib2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `evolution-exchange' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libequinox-osgi-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bsdmainutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libiec61883-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kfind' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsox-fmt-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xfonts-75dpi' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `passwd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsasl2-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsasl2-modules' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `obexd-client' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkate1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkonq5-templates' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bash-completion' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomekbd-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcwidget3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ftp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wbritish' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `command-not-found-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libseed0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcamel1.2-14' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgfortran3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `update-manager-kde' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpoppler5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgadu3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdebase-runtime-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmng1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaspell-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ureadahead' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libx264-85' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-core6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mlocate' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcompress-zlib-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sgml-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-neomagic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `telepathy-idle' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libphonon4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `upstart' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-render0-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libijs-0.35' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `php5-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmysqlclient16' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxaw7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11-xserver-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpoppler-glib-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome2.24-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmlt2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxdamage1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `foomatic-filters' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `autoconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sqlite' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcurl3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libodbcinstq1c2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnss3-1d' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-designer' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomeprint2.2-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `glchess' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwv-1.2-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `toshset' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kbd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-problem-report' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `nvidia-96-modaliases' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-codec-install' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `jarwrapper' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdenlive' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ubuntuone' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ghostscript-x' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-cups' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdrm-nouveau1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `yelp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libofa0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhpmud0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk2.0-doc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plymouth' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmpg123-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-gnome-es-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libprocessui4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libx86-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gparted' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11proto-record-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-gb-form' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `busybox-static' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plymouth-label' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome-pilot2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wine1.2-gecko' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaprutil1-ldap' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libopenexr6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tomboy' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgraphviz4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `esound-clients' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-gobject0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `smbclient' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `deskbar-applet' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdata1.2-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-paramiko' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libiw29' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `grep' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `checkbox-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsexy2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkadm5srv-mit7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `nvidia-185-modaliases' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `acpid' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libschroedinger-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdebian-installer4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxmu6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `debconf-i18n' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plasma-widget-folderview' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfs6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libntfs10' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `unattended-upgrades' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xdg-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `myspell-en-za' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcanberra-pulse' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblouis0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-r128' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk2.0-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgutenprint2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-addins0.2-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsndfile1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pm-utils-powersave-policy' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-glade2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `smartdimmer' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `unrar' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libndesk-dbus-glib1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblualib50' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnet-daemon-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxfixes3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ca-certificates-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `net-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxdamage-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libomnithread3-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libopenal1' missing, assuming package has no files currently installed.
(Reading database ... 20%
dpkg: warning: files list file for package `librsvg2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libscim8c2a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgail18' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libplasmaclock4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11-apps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rtkit' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdb4.8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxmu-headers' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdb4.7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdb4.6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `virtuoso-nepomuk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `arista' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcryptui0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ltrace' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnewt0.52' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libubuntuone-1.0-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bluez-cups' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-cirrus' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpst4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhamcrest-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbrlapi0.5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjasper-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsilcclient-1.1-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnupg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gnomedesktop' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-system-web1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpoppler-glib4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `groff-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-bluetooth' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk2-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plymouth-theme-ubuntu-text' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-ark' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-arphic-uming' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-orca' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `update-notifier' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-speechd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libopencore-amrnb0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libedataserverui1.2-8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubuntu-sounds' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mawk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lm-sensors' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbabl-0.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-serial' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liborc-0.4-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-en-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdirectfb-extra' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ibus' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcomerr2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-packagekit' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `uno-libs3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpaper-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `file-roller' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubuntu-wallpapers' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjack0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `librsvg2-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgme0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-opengl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11proto-xinerama-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `consolekit' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaprutil1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-avahi' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml-namespacesupport-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdelibs-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `transmission-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdebase-apps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `swh-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bind9-host' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `at' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `indicator-applet-session' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `uuid-runtime' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `nautilus-sendto-empathy' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsqlite0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `base-passwd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwpg-0.1-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtkhtml-editor0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgl1-mesa-glx' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnice0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml-simple-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `scim-gtk2-immodule' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wget' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtkglext1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcdio-paranoia0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-louis' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgmime2.4-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `human-theme' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-wqy-microhei' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gweather' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `samba-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kpackagekit' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-session' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkrb5support0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgs8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsoundtouch1c2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `festvox-kallpc16k' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libeggdbus-1-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-wxversion' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `human-icon-theme' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lintian' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsilc-1.1-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libclutter-gtk-0.10-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dictionaries-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `brasero-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xfonts-100dpi' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `radeontool' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `glade' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-unfonts-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `udisks' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gir1.0-atk-1.0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xfonts-scalable' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gdebi-kde' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apache2-mpm-prefork' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kinfocenter' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `thunderbird' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-smbc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome-menu2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `e2fslibs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `g++' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpolkit-gnome0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-common-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gnomeprint' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdebase-workspace-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `splix' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libm17n-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblapack3gf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `indicator-sound' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mdetect' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `klibc-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `firebird2.1-common-doc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdelibs5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhunspell-1.2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome2-gconf-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-vte' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaudiofile0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtiff4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvte-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libshout3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-gnome-pt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hwtest-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `evince' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lshw' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtksourceview1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-punjabi-fonts' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ntfsprogs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgpg-error-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavdevice52' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-tdfx' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk2.0-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tracker-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpulse0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-wqy-zenhei' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-gb-form-dialog' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libswscale0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libupower-glib1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `shared-desktop-ontologies' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-data-tds1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-multimedia' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11proto-kb-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11proto-randr-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-fluendo-mp3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-render0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-icon-theme' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tcpdump' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `scim-modules-socket' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gimp-help-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hdparm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `exiv2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libatm1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtheora0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `brltty-x11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-kacst' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libggz2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ddrescue' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `eclipse-platform' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libidn11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sed' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `genisoimage' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rpm-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsnmp15' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-2.6.32-23-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libspeexdsp1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhtml-tree-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl-sound1.2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bluez-alsa' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsmbios2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome-keyring1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpcap0.8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-dbus' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-2.6.31-20-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxine1-console' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-client' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdaemon0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gtk2-engines-pixbuf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-sisusb' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-gnome-xh-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xfonts-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-i18n1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomecups1.0-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libattr1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xinit' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gtop' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cups-driver-gutenprint' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-ffmpeg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhal1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxi6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kappfinder' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-freefont' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `perlmagick' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdevmapper1.02.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `songbird' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `usbutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `erlang-ssl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `intltool-debian' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsage2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcairomm-1.0-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hwtest' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxft-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `odbcinst1debian1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdu0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblwres60' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libevent-1.4-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-script' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libass4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gdata' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkscreensaver5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-draw' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdca0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtwolame0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-pyorbit' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gir1.0-pango-1.0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sg3-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-gb-desktop' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `initramfs-tools-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-plugins-ugly' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plasma-desktop' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `patch' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-evolution' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbd-mysql-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apmd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsoprano4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libopenjpeg2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdenlive-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libportaudio2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libterm-readkey-perl' missing, assuming package has no files currently installed.
(Reading database ... 25%
dpkg: warning: files list file for package `libportaudio0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `synaptic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `humanity-icon-theme' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gcalctool' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcaca-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdiplus' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libx11-protocol-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libproxy0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libopenscenegraph56' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libevview2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xmoto' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `checkbox' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `indicator-me' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-themes-ubuntu' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dvdauthor' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-control-center' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubuntu-artwork' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdirectfb-1.2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libomnithread3c2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglu1-mesa-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-netstatus-applet' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubuntuone-client-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-kacst-one' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglut3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `software-properties-kde' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgsf-1-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bogofilter-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `simple-scan' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-rendition' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxt-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome2-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `docbook-xsl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcommons-collections3-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpam-gnome-keyring' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libparted0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblaunchpad-integration1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libasm3-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-atom1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `erlang-mnesia' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `iproute' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-sql-mysql' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-media' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `nvidia-current-modaliases' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-pilot' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wine' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-plugins-bad' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `postfix' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gobject-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `librarian0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libexpat1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango1.0-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libltdl7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `alacarte' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plymouth-theme-ubuntu-logo' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl-image1.2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `logrotate' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rdate' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-xh' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvorbisenc2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `parted' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `telepathy-haze' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgmime-2.0-2a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `packagekit-backend-apt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkeyutils1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `erlang-inets' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-pt-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-aux0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgp11-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `melt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lksctp-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11proto-render-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxxf86misc1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-cairo' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kubuntu-debug-installer' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgcj10' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `odbcinst' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `frei0r-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ppp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apport-hooks-medibuntu' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxerces2-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnunit2.4-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglib-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango1.0-doc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `fdupes' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-network' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libevdocument2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tasksel-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lockfile-progs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-menus' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libldap2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpod-coverage-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `casper' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-gnome-bn-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cdrdao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rsync' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `system-tools-backends' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome2-vfs-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmpcdec3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome2-wnck-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsage-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libplymouth2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libncurses5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `festlex-cmu' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-appindicator' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfreezethaw-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plasma-dataengines-workspace' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreadline6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreadline5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `espeak' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgksu2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpq-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `winetricks' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-vesa' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-qt3-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pm-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjsch-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-input-synaptics' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libappindicator0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libflickrnet2.2-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gmenu' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-gnome-de-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `console-setup' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdata-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gnome2-desktop' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcups2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libuuid-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cups-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `app-install-data-commercial' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpixman-1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtext-iconv-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `fancontrol' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsqlite3-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libffi-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcdio10' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-totem-plparser' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtksourceview-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-gb-form-mdi' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcupsdriver1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gtk2-engines' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libopencore-amrwb0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gdm-guest-session' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libasound2-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpt2.6.5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pcmciautils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-kochi-gothic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mount' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `system-config-printer-udev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnotravex' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `base-files' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-session-canberra' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libspeechd2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mesa-common-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tangerine-icon-theme' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbluetooth3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsmbclient' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-games' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libieee1284-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `evolution-webcal' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `app-install-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cli-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgpgme11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libasound2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcdio-cdda0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwxbase2.8-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `grub' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `php5-gd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-lao' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hal' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjpeg62-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `realpath' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcvaux4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `totem-mozilla' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libneon27-gnutls' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libslang2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwmf0.2-7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdv4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libncurses5-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxv1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubuntu-xsplash-artwork' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `librpmbuild0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `metacity-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gbrainy' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `junit' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libidl0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bluetooth' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bluez-gstreamer' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-event1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `orbit2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `m17n-db' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-webkit' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libklibc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpt-1.10.10-plugins-v4l2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11proto-fixes-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gimp-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-addins-gui0.2-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mousetweaks' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-math' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcommons-httpclient-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsys-hostname-long-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gir1.0-gtk-2.0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libice-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcomposite1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdebconfclient0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libck-connector0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-games-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `psfontmgr' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libweather-ion4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libidn11-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgcc1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pppconfig' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-support-writing-en' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsm-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdevhelp-1-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tasksel' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-indic-fonts-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `eclipse-jdt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `policykit-1-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ed' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `manpages' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `network-manager-pptp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `librpmio0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdebase' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python2.6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmldbm-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libservlet2.4-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcommons-codec-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-system-runtime2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `update-manager-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `html2text' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `locales' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmms0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-all' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfontconfig1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsox1a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-support' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdmx1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgconf2.0-cil' missing, assuming package has no files currently installed.
(Reading database ... 30%
dpkg: warning: files list file for package `libxcb1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libedataserver1.2-11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcupsmime1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-ui0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `adduser' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libotf0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kwrite' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-l10n-en-za' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `javascript-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-doc-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsvn1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-sexy' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gsfonts' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-newt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-headers-2.6.32-23-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-lazr.uri' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglu1-mesa' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `os-prober' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `telepathy-butterfly' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxrandr2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ant-gcj' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdeskbar-tracker' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmailtools-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbonobo2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-xkit' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gnomecanvas' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hal-cups-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `awn-applets-c-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-mscorefonts-installer' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libapt-pkg-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libespeak1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `fastjar' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bogofilter' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `totem-gstreamer' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libindicate-gtk2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `eclipse-pde' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-sudoku' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `zlib1g' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxi-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvpx0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-bn-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `winbind' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `fgfs-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ffmpeg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `freeglut3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfribidi0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjtidy-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtasn1-3-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdebase-runtime' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libotr2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `netcat-openbsd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `librpc-xml-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `foo2zjs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-evince' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomeprintui2.2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-js-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `nautilus-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdns64' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `subversion' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtkhtml-editor-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `vinagre' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavutil-extra-49' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqtcore4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `indicator-session' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libksignalplotter4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `icoutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-system-data1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdecoration0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfont-afm-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `totem' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdrm-radeon1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libattica0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnl1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liburi-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl-image1.2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `packagekit' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `scim-bridge-client-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gdbm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gcc-4.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gcc-4.3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gdebi-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `indicator-applet' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-liberation' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgsf-1-114' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `file' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rhythmbox' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libimobiledevice0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tar' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-protobuf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz-fusion-plugins-extra' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtdb1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-awn-extras' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpanel-applet2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-keyring' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-pexpect' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxpm4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `evolution-data-server' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-takao-pgothic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkephal4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libimlib2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `polkit-kde-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-l10n-xh' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-l10n-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libthai-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11proto-xext-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxtst-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-libc-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsctp1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gawk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libregexp-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsnmp-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gconf2-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfile-mimeinfo-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtracker-gtk0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libebook1.2-9' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwvstreams4.6-extras' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-style-galaxy' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomevfs2-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python2.6-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-input-evdev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtag1-vanilla' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liboil0.3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpolkit-agent-1-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `qt3-dev-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `doc-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `eclipse-plugin-cvs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libslp1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-headers-2.6.32-22-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libatasmart4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk2.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgstreamer-plugins-base0.10-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-help-en-gb' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgavl1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxvmc1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `aspell-en' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `diffutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhal-storage1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libecal1.2-7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdesktop-agnostic-cfg-gconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-nettool' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libthai0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libenchant1c2a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pidgin-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `software-center' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxfont1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgoocanvas-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-fbdev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-savage' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dhcp3-client' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dbus' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwww-mechanize-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hal-info' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtop2-7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-svg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgimp2.0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libc-dev-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgcr0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmagickwand2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `transmission-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome2-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkpathsea4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkpathsea5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mountall' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcos4-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `docbook-xsl-doc-html' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxrender1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbonobo2-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lupin-casper' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `erlang-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpurple-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gvfs-backends' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hunspell-en-us' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsgutils2-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpurple0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcolamd2.7.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ksysguardd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjs-mootools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11-session-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhighgui4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblucene2-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-radeon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-i18n-west1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libts-0.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libogg0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `myspell-en-gb' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblua50' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xterm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libusb-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl-net1.2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libatk1.0-doc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgconf2-4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-accessibility-themes' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxext6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglade2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxxf86dga1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssh-askpass-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaprutil1-dbd-sqlite3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wdiff' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ifupdown' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-gnomevfs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome-window-settings1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-input-wacom' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfontconfig1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gettext' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbz2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rhythmbox-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxrandr-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-apport' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `obex-data-server' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libv4l-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libudev0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-glib1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `avahi-autoipd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomecanvas2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tzdata' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-vmware' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpam-modules' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdu-gtk0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apt-transport-https' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtkmm-2.4-1c2a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dmidecode' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaspell15' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libisccc60' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsepol1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdesktop-agnostic0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcompress-raw-zlib-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxapian15' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpulse-mainloop-glib0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ntfs-3g' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bzr' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libstreams0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cups-client' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-openchrome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkonq5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgsm1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `whiptail' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtotem-plparser17' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libecj-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-mime-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libidl-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libestools1.2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-dev' missing, assuming package has no files currently installed.
(Reading database ... 35%
dpkg: warning: files list file for package `libdrm2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmagic1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libart2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `netbase' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `medibuntu-keyring' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-gnome-pt-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdirac-encoder0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgupnp-igd-1.0-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmp4v2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-configobj' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dnsmasq-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libk5crypto3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpopt-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `librdf0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mtr-tiny' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pulseaudio-module-gconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpoppler-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `startupmanager' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgif4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libalut0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomeui-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-kde4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gedit' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libio-compress-zlib-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpulse-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pxljr' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mtools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgc1c2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `grub-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `telepathy-gabble' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gir1.0-clutter-1.0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-launchpad-integration' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-support-en' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxres1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-panel' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libicu4j-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubuntu-standard' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `manpages-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libquicktime1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-media-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango1.0-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpthread-stubs0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomeprint2.2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-bn' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tzdata-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbus-glib-1-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gcj-4.4-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-render-util0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pciutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libasound2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfbclient2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgif-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gir1.0-glib-2.0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtiffxx0c2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxdmcp-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libanthy0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plymouth-theme-fade-in' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-brlapi' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gamin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-data-tds2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libatspi1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjasper-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dvgrab' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxine1-misc-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxslt1.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wine1.2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sgml-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjetty-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `policykit-desktop-privileges' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bluez' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libisc60' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubuntuone-client' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `akonadi-server' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libegroupwise1.2-13' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmtp8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-impress' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libexchange-storage1.2-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `brasero' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `telepathy-mission-control-5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libusbmuxd1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libndesk-dbus1.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-help-es' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcairo2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxrender-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libaudiofile-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `branding-ubuntu' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-gnome-en-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtimedate-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plasma-widgets-workspace' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sysv-rc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `perl-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ncurses-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtelepathy-glib0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `byobu' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ddclient' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xorg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libical0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgcrypt11-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-software-properties' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglib2.0-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `desktopcouch' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `modemmanager' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gnupginterface' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome2-canvas-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openssl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-thai-tlwg' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `install-package' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-render-util0-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `computer-janitor' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-wxgtk2.8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gir1.0-freedesktop' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-exe-thumbnailer' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-doc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt4-sql' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xfsprogs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gettext-kde' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwavpack1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `vim-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bzip2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liba52-0.7.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ant' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `java-package' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdebase-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnm-util1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libssl0.9.8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libnotify1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libc6-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcanberra-gtk-module' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-s3virge' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsamplerate0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxslt1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dctrl-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `erlang-xmerl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-ide' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml-xpath-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl-mixer1.2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libuniconf4.6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `intel-gpu-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dpkg-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl-sound1.2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqt3-mt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apport-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssl-cert' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `soprano-daemon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgudev-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xdg-user-dirs-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `krb5-multidev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `update-inetd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liborbit2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubuntu-restricted-extras' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `debhelper' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-twisted-web' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgpod4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-arabeyes' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lsb-release' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxkbfile1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgweather1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-pilot-conduits' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxext-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfile-basedir-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apport-symptoms' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxss1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqca2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libflite1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libloudmouth1-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-posix2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-sazanami-mincho' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `install-info' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `eclipse' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpolkit-grant2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwbclient0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-voodoo' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk-vnc-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libio-compress-base-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpolkit-dbus2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libexpat1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `jockey-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dvd+rw-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavcodec-extra-52' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `system-config-printer-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `usb-creator-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-thesaurus-en-us' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdict-1.0-6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnect' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hicolor-icon-theme' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgvfscommon0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-fstab' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcdaudio1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sqlite3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-mako' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `policykit' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-mediaprofiles' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfile-homedir-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sensible-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mono-gac' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `adium-theme-ubuntu' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gedit-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `seahorse' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-apm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xbase-clients' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgl1-mesa-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bsdutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `perl-modules' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lftp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `avahi-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgssrpc4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ucf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-thesaurus-en-au' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dolphin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `psmisc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbusmenu-glib1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgpg-error0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavc1394-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpython2.6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libusb-0.1-4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxfixes-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cdbs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `autotools-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libportmidi0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `capplets-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gnomeapplet' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xsplash' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpci3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `awn-settings' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `hpijs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libopenspc0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-gb-settings' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-plugins-bad-multiverse' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xsane-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml-sax-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libterm-size-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpam0g' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `quickly' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-support-translations-en' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpopt0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libflac-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubiquity-casper' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-quickly-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcommons-digester-java' missing, assuming package has no files currently installed.
(Reading database ... 40%
dpkg: warning: files list file for package `libauthen-sasl-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libawn1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wamerican' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ncurses-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tcl8.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libglitz-glx1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-zope.interface' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `nautilus-share' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `whois' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libplasma-geolocation-interface4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mesa-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libv4l-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apt-xapian-index' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libakonadiprivate1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfuse2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwildmidi0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdvdread4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-selector' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdesudo' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ibus' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-minimal' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mscompress' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libspeex1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgssapi-krb5-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libqtgui4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-gnome-xh' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtool' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdebase-workspace' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `avant-window-navigator-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtkimageview0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ibus-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ttf-kochi-mincho' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `binfmt-support' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dnsutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgeoip1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-es' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcos4-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-user-guide-pt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apturl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-themes-selected' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-en' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcups2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `nvidia-180-modaliases' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wpasupplicant' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-nice' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `g++-4.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome-desktop-2-17' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-2.6.32-21-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `procps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libiodbc2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `user-setup' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cpp-4.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sreadahead' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cpp-4.3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `metacity' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxinerama-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdebase-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `language-pack-gnome-de' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-help-pt-br' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `odt2txt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjpeg62' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libparted0debian1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-style-human' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomepanel2.24-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-help-en-us' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gtali' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `compiz' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libparse-debcontrol-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-vobject' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsoup-gnome2.4-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjline-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `fontconfig' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-settings-daemon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcurl3-gnutls' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lsb-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsoup2.4-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtasn1-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `w32codecs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gconf-editor' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tk8.4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-user-guide-de' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgd2-xpm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsolidcontrol4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblcms1-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-l10n-pt-br' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libavahi-client-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-papyon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `konsole' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtk2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtop2-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libuuid1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-system-monitor' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `screensaver-default-images' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lzma' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxinerama1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl1.2debian' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `evolution-data-server-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-wnck' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `plymouth-x11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpisync1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdepimlibs-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgegl-0.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `eog' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gimp-help-de' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-sis' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cvs' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kde-window-manager' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-dbus' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xcursor-themes' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `lightsoff' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwps-0.1-1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libogg-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libplasma-applet-system-monitor4' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbind9-60' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjs-jquery' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgcrypt11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtie-ixhash-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-video-v4l' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-ubuntuone-client' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsox-fmt-alsa' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libexif12' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdbm3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pulseaudio-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libhtml-format-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libesd-alsa0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcairo2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `localechooser-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libibus1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `erlang-public-key' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgstfarsight0.10-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `myspell-en-au' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `man-db' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpango-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libffi5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libenca0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgraphite3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgamin0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `module-init-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libflac8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvorbis-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gettext-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libvorbisfile3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `festival' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gambas2-gb-qt' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `glines' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libperl5.10' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-user-guide' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbus-1-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openssl-blacklist' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgmp3c2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cups-ppdc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `systemsettings' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxplc0.3.13' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ssh' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xscreensaver-data' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `desktop-file-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `example-content' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gpgv' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdelibs4c2a' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kgrab' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `login' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgoocanvas3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `telnet' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `avant-window-navigator' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11-xkb-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gstreamer0.10-plugins-base-apps' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wireless-crda' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `laptop-detect' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-usb' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `makedev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `initramfs-tools' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `x11proto-input-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libprotobuf5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-twisted-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gdm' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `menu' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gdb' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libcelt0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsdl1.2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gnome-terminal' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openoffice.org-emailmerge' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ant-optional-gcj' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxmuu1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libisccfg60' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libclass-accessor-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmikmod2-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml-parser-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxcb-shm0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libwxgtk2.8-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `finger' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbi-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sun-java6-fonts' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pulseaudio-module-x11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdesdk-scripts' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ubufox' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `openprinting-ppds' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xfonts-mathml' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsysfs2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `bcmwl-modaliases' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `debianutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfreetype6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sudo' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libsane' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `cupsddk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libzip1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `coreutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ure' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libatk1.0-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmono-system-data2.0-cil' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `empathy' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `esound-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gvfs-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgl1-mesa-dri' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `seahorse-plugins' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxdmcp6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmpfr1ldbl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-beagle' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnome-speech7' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpq5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libt1-5' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `shared-mime-info' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libraw1394-11' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mktemp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpolkit-gobject-1-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-sip' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libart-2.0-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmagickcore2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mono-runtime' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtest-pod-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-gnome2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gimp' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `dash' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libltdl-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `app-install-data-medibuntu' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `memtest86+' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libelf1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gtk2-engines-murrine' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `kdepasswd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-aptdaemon' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `googleearth' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjaxp1.3-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libmng-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgnomekbd4' missing, assuming package has no files currently installed.
(Reading database ... 45%
dpkg: warning: files list file for package `librecode0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libpth20' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `debconf' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mono-2.0-gac' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libkwineffects1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `jfsutils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libio-stringy-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `pitivi' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libjson-glib-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgssdp-1.0-2' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `apturl-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfile-which-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-lxml' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `java-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `gir1.0-clutter-gtk-0.10' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `empathy-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgpod-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `linux-image-2.6.27-17-generic' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `sane-utils' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libclutter-1.0-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libtext-wrapi18n-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libfftw3-3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libbonoboui2-0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `mysql-client-core-5.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libslf4j-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `tcpd' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `python-pkg-resources' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgtkspell0' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdb-je-java' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libexempi3' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxml-libxml-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `xserver-xorg-input-vmmouse' missing, assuming package has no files currently installed.
(Reading database ... 20828 files and directories currently installed.)
Unpacking firefox-branding (from .../firefox-branding_3.6.9~hg20100725r34460+nobinonly-0ubuntu1~umd1~lucid_i386.deb) ...
Selecting previously deselected package firefox.
Unpacking firefox (from .../firefox_3.6.9~hg20100725r34460+nobinonly-0ubuntu1~umd1~lucid_i386.deb) ...
Processing triggers for python-gmenu ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Setting up firefox-branding (3.6.9~hg20100725r34460+nobinonly-0ubuntu1~umd1~lucid) ...
Setting up firefox (3.6.9~hg20100725r34460+nobinonly-0ubuntu1~umd1~lucid) ...
Please restart all running instances of firefox, or you will experience problems.

Processing triggers for menu ...
austin@DOWNSTAIRS-PC:~$ 

```

I still get all those dpkg errors, which is getting really annoying...


> **wojox said:**
> How about 

```
sudo apt-get -f install
```

```
sudo apt-get upgrade
```
**sudo apt-get -f install**
```
austin@DOWNSTAIRS-PC:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
**sudo apt-get upgrade**
```
austin@DOWNSTAIRS-PC:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by aidenscool09 on 2010-07-27
Sounds like it's fixed. You probably are up to date anyway. Try installing something. And check your Software Sources ( System>Administration>Software Sources ) just in case.

---

### Post by wojox on 2010-07-27
Open Synaptic > Custom Filters > Broken.

See if that does anything.

Also try Synaptic > Custom Filters > Missing Recommends.

---

### Post by aidenscool09 on 2010-07-27
Your good at helping people aren't you. I'm just not so good at explaining. I find it 10x easier in person though.

---

### Post by Garetty on 2010-07-27
> **wojox said:**
> Open Synaptic > Custom Filters > Broken.

See if that does anything.

Also try Synaptic > Custom Filters > Missing Recommends.

Did that, had a few Missing Recommends. I installed them, but still get those dpkg errors.

---

### Post by wojox on 2010-07-27
What does this command give us?

```
ls /var/cache/apt/archives
```

---

### Post by Garetty on 2010-07-27
> austin@DOWNSTAIRS-PC:~$ ls /var/cache/apt/archives[COLOR=Red]
evolution-couchdb_0.4.5-0ubuntu1_i386.deb
firefox_3.6.9~hg20100725r34460+nobinonly-0ubuntu1~umd1~lucid_i386.deb
firefox_3.6.9~hg20100727r34463+nobinonly-0ubuntu1~umd1~lucid_i386.deb
firefox-branding_3.6.9~hg20100725r34460+nobinonly-0ubuntu1~umd1~lucid_i386.deb
firefox-branding_3.6.9~hg20100727r34463+nobinonly-0ubuntu1~umd1~lucid_i386.deb
firefox-gnome-support_3.6.9~hg20100725r34460+nobinonly-0ubuntu1~umd1~lucid_i386.deb
gdm_2.30.2.is.2.30.0-0ubuntu3_i386.deb
gwibber_2.30.1-0ubuntu1_all.deb
gwibber-service_2.30.1-0ubuntu1_all.deb
language-pack-de_1%3a10.04+20100714_all.deb
language-pack-de-base_1%3a10.04+20100714_all.deb
language-pack-es_1%3a10.04+20100714_all.deb
language-pack-es-base_1%3a10.04+20100714_all.deb
language-pack-gnome-de_1%3a10.04+20100714_all.deb
language-pack-gnome-de-base_1%3a10.04+20100714_all.deb
language-pack-gnome-es_1%3a10.04+20100714_all.deb
language-pack-gnome-es-base_1%3a10.04+20100714_all.deb
libcouchdb-glib-1.0-2_0.6.3-0ubuntu1_i386.deb
libdesktopcouch-glib-1.0-2_0.6.3-0ubuntu1_i386.deb
libdvdcss2_1.2.10-0.3medibuntu1_i386.deb
[COLOR=Black]lock[/COLOR]
[COLOR=RoyalBlue]partial[/COLOR]
python-egenix-mxdatetime_3.1.3-2ubuntu1_i386.deb
python-egenix-mxtools_3.1.3-2ubuntu1_i386.deb
python-gtkspell_2.25.3-4.1ubuntu4_i386.deb
python-indicate_0.3.0-0ubuntu1_i386.deb
python-pycurl_7.19.0-3_i386.deb
software-center_2.0.7_all.deb
thunderbird_3.0.7~hg20100727r4892+nobinonly-0ubuntu1~umd1~lucid_i386.deb
xserver-xorg-video-amd_2.11.8-4_i386.deb
xulrunner-1.9.2_1.9.2.9~hg20100727r34463+nobinonly-0ubuntu1~umd1~lucid_i386.deb[/COLOR]
Lots of red... I have a feeling that isn't good. :|

---

### Post by Garetty on 2010-07-28
Bump.

---

### Post by linux18 on 2010-07-28
this will fix it 90% of the time

```
  sudo apt-get -f || echo "ERROR 0"
 sudo rm /var/lib/apt/lists/partial/* || echo "ERROR 1: no partial packages - harmless error"
 sudo rm /var/cache/apt/*.bin || echo "ERROR 2"
 sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ')
 sudo apt-get clean || echo "ERROR 3"
 sudo apt-get autoclean || echo "ERROR 4"
 sudo apt-get autoremove || echo "ERROR 5"
 sudo apt-get update || echo "ERROR 6"
 sudo apt-get --fix-broken upgrade || echo "ERROR 7 
```

---

### Post by Garetty on 2010-07-28
Didn't fix the errors.

---

### Post by Garetty on 2010-07-28
Bump.

---

### Post by blackbelt27 on 2010-08-01
i have the same problem, i install 10.04 genome to a usb drive, boot up, enable all the sources, and download updates, it seems to be an issue with the kernel version release because it appears everything installs fine except for the linux firmware and kernels, like the system junk, and once that errors out nothing else will install and when i reboot it it wont even work, i have to reformat everytime i try to solve this problem,

---

### Post by napaki on 2010-12-22
Take a look at this thread.  You would have to reinstall all those corrupted packages manually, but it did the trick for me. 

[http://www.uluga.ubuntuforums.org/showthread.php?t=1634994](http://www.uluga.ubuntuforums.org/showthread.php?t=1634994)

---

