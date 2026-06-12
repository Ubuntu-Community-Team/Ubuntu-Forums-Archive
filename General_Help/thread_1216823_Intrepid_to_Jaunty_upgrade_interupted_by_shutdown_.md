---
title: "Intrepid to Jaunty upgrade interupted by shutdown (E: _cache-&gt;open)"
date: 2009-07-18
forum: General Help
---

### Post by Marius Derekus on 2009-07-18
Hello everyone, I was updating from ubuntu studio 8.10 (intrepid) to ubnut studio 9.04 (Jaunty) on my laptop, but during the update my power chord came out and my computer shutdown during the upgrade. When i rebooted and tried to log into ubuntu it initially didnt work. However...i booted into recovery mode and ran the "dpkg" option, then the "fsck" option and then "xfix". After that i was able to boot into ubuntu BUT...whenever i try to finish installing my upgrades (or install any other programs that require "dpgk") my computer says the following:
 

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

However...when i run the command "sudo dpkg --configure -a" i get the following errors:

```
cameron@cameron-laptop:~$ sudo dpkg --configure -a
[sudo] password for cameron: 
Setting up initramfs-tools (0.92bubuntu29) ...
update-initramfs: deferring update (trigger activated)

Setting up cupswrapperdcp7020 (2.0.1-2) ...
/usr/local/Brother/cupswrapper/cupswrapperDCP7020-2.0.1: line 63: /usr/share/cups/model/DCP7020.ppd: No such file or directory
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
cp: cannot stat `/usr/share/cups/model/DCP7020.ppd': No such file or directory
dpkg: error processing cupswrapperdcp7020 (--configure):
 subprocess post-installation script returned error exit status 1
Setting up dictionaries-common (1.0.0ubuntu1) ...
Can't locate Text/Iconv.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/perl5/Debian/DictionariesCommon.pm line 6.
BEGIN failed--compilation aborted at /usr/share/perl5/Debian/DictionariesCommon.pm line 6.
Compilation failed in require at /usr/sbin/update-default-ispell line 3.
BEGIN failed--compilation aborted at /usr/sbin/update-default-ispell line 3.
dpkg: error processing dictionaries-common (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on dictionaries-common (>= 0.10) | openoffice.org-updatedicts; however:
  Package dictionaries-common is not configured yet.
  Package openoffice.org-updatedicts is not installed.
  Package dictionaries-common which provides openoffice.org-updatedicts is not configured yet.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-style-human:
 openoffice.org-style-human depends on openoffice.org-common (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-style-human (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common; however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-officebean:
 openoffice.org-officebean depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-officebean (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-core:
 openoffice.org-core depends on openoffice.org-common (>> 1:3.0.1); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gtk:
 openoffice.org-gtk depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gtk depends on openoffice.org-style-human; however:
  Package openoffice.org-style-human is not configured yet.
dpkg: error processing openoffice.org-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-mobiledev:
 openoffice.org-filter-mobiledev depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org-filter-mobiledev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-filter-binfilter:
 openoffice.org-filter-binfilter depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-filter-binfilter (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-report-builder-bin:
 openoffice.org-report-builder-bin depends on openoffice.org-core (>> 1:2.3.0~oog680m1); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-report-builder-bin depends on openoffice.org-base (>= 2.3.0~src680m225); however:
  Package openoffice.org-base is not configured yet.
dpkg: error processing openoffice.org-report-builder-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base-core:
 openoffice.org-base-core depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-writer depends on openoffice.org-base-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-base-core is not configured yet.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org depends on openoffice.org-writer; however:
  Package openoffice.org-writer is not configured yet.
 openoffice.org depends on openoffice.org-calc; however:
  Package openoffice.org-calc is not configured yet.
 openoffice.org depends on openoffice.org-draw; however:
  Package openoffice.org-draw is not configured yet.
 openoffice.org depends on openoffice.org-base; however:
  Package openoffice.org-base is not configured yet.
 openoffice.org depends on openoffice.org-report-builder-bin; however:
  Package openoffice.org-report-builder-bin is not configured yet.
 openoffice.org depends on openoffice.org-officebean; however:
  Package openoffice.org-officebean is not configured yet.
 openoffice.org depends on openoffice.org-filter-mobiledev; however:
  Package openoffice.org-filter-mobiledev is not configured yet.
 openoffice.org depends on openoffice.org-java-common (>> 2.2.0-4); however:
  Package openoffice.org-java-common is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-gnome:
 openoffice.org-gnome depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-gnome depends on openoffice.org-gtk; however:
  Package openoffice.org-gtk is not configured yet.
dpkg: error processing openoffice.org-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
 openoffice.org-impress depends on openoffice.org-draw (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-draw is not configured yet.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (= 1:3.0.1-9ubuntu3); however:
  Package openoffice.org-core is not configured yet.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-vmlinuz-2.6.27-3-rt
Cannot find /lib/modules/vmlinuz-2.6.27-3-rt
update-initramfs: failed for /boot/initrd.img-vmlinuz-2.6.27-3-rt
dpkg: subprocess post-installation script returned error exit status 1
cameron@cameron-laptop:~$ lpadmin: No such file or directory

```

IS there anyway to fix this and get 9.04 installed properly or am i forced to reinstall ubuntu studio from disk.....

Thank you all for any replies

---

### Post by CrusaderAD on 2009-07-18
I've had this happen... big bummer. I had to reinstalled from the beginning.

---

### Post by Marius Derekus on 2009-07-18
Wow that sux, i pity...i really hope i dont have to do that LOL. Thank you for replying :D

I do have new news... i dont know what happened, but i opened update manager and it gave me the option to do a partial upgrade so i did. After i did  the partial upgrade i rebooted my computer and began to uninstall the programs that were in the previous error (shown on my previous post) using the "sudo apt-get remove" command. I believe it partially worked because after that...when i ran the "sudo dpkg --configure -a" command, it gave no errors. However....when i open "update manager" i get a notification telling me to do a partial upgrade (which i just completed) and it also gives me a notification that says the following:

```
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first
```

However, when i run the command "sudo apt-get install -f" it gives this error:

```
cameron@cameron-laptop:~$ sudo apt-get install -f
[sudo] password for cameron: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  hunspell-en-us iamerican ibritish openoffice.org-hyphenation
  openoffice.org-hyphenation-en-us wbritish
0 upgraded, 0 newly installed, 6 to remove and 1 not upgraded.
6 not fully installed or removed.
After this operation, 5460kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 255625 files and directories currently installed.)
Removing hunspell-en-us ...
/var/lib/dpkg/info/hunspell-en-us.postrm: line 5: update-openoffice-dicts: command not found
dpkg: error processing hunspell-en-us (--remove):
 subprocess post-removal script returned error exit status 127
Removing iamerican ...
/var/lib/dpkg/info/iamerican.postrm: line 6: /usr/sbin/remove-default-ispell: No such file or directory
dpkg: error processing iamerican (--remove):
 subprocess post-removal script returned error exit status 1
Removing ibritish ...
/var/lib/dpkg/info/ibritish.postrm: line 6: /usr/sbin/remove-default-ispell: No such file or directory
dpkg: error processing ibritish (--remove):
 subprocess post-removal script returned error exit status 1
Removing openoffice.org-hyphenation ...
/var/lib/dpkg/info/openoffice.org-hyphenation.postrm: line 5: update-openoffice-dicts: command not found
dpkg: error processing openoffice.org-hyphenation (--remove):
 subprocess post-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Removing openoffice.org-hyphenation-en-us ...
/var/lib/dpkg/info/openoffice.org-hyphenation-en-us.postrm: line 5: update-openoffice-dicts: command not found
dpkg: error processing openoffice.org-hyphenation-en-us (--remove):
 subprocess post-removal script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              Removing wbritish ...
Error: /usr/sbin/remove-default-wordlist not present or executable. Missing dependency on dictionaries-common?
dpkg: error processing wbritish (--remove):
 subprocess post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 hunspell-en-us
 iamerican
 ibritish
 openoffice.org-hyphenation
 openoffice.org-hyphenation-en-us
 wbritish
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any help on what to do next???????

Thanks for any replies and help

---

### Post by CrusaderAD on 2009-07-21
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=21672](http://ubuntuforums.org/showthread.php?t=21672)

Maybe your hard drive or partition is full?

---

### Post by Marius Derekus on 2009-08-20
no...i have plenty of room...thanks for the help..i will look at that thread........oh and sorry for hte late reply

---

### Post by matthewbpt on 2009-08-20
I had this happen once and I opened Synaptic Package Manager, and it offered to fix dependency problems, I let it and then it worked again. Try opening synaptic, if nothing comes up offering to fix, go to Edit > Fix Broken Packages and see what that does.

-Matt

---

### Post by Marius Derekus on 2009-09-10
Thanks for the help matt. Hoever i tried that just now and it has a similar error.

---

### Post by Marius Derekus on 2009-09-20
I am still looking how to fix this issue. Is there anyway to manually uninstall broken packages???

---

