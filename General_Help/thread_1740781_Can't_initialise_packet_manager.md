---
title: "Can't initialise packet manager"
date: 2011-04-27
forum: General Help
---

### Post by nashpd on 2011-04-27
When I do update-manager, this is what I get:

Could not initialise the package information

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


I'm sorry if this has been asked before, I'm new to Ubuntu and Ubuntu Forums. And yeah, I use 11.04 beta 2...but have been installing all the recommended patches literally everyday.

---

### Post by KegHead on 2011-04-27
Hi!

Try;

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart

Advise

KegHead

---

### Post by nashpd on 2011-04-27
I tried what you recommended, but it still doesn't proceed. Something wrong with one of the package i guess...mostly this is what i see:


E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
nash@nash-Aspire-5742:~$ sudo apt-get upgrade -f
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
nash@nash-Aspire-5742:~$ sudo apt-get dist-upgrade -f
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

---

### Post by plucky on 2011-04-27
> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_i 18n_Translation-en
E: The package lists or status file could not be parsed or opened. 

Remove that list file with ```
sudo rm /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_i 18n_Translation-en
```

Then run ```
sudo apt-get update
``` to reload the list files.

Also as you are running 11.04,I would remove the google repository as it probably not ready for natty.

Good Luck

---

### Post by nashpd on 2011-04-27
Thanks for the help Plucky, but I get the following error:


nash@nash-Aspire-5742:~$ sudo rm /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_i 18n_Translation-en
[sudo] password for nash: 
rm: cannot remove `/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_i': No such file or directory
rm: cannot remove `18n_Translation-en': No such file or directory

---

### Post by nashpd on 2011-04-27
Would this help anyone diagnose the problem? There is no lists in lib


nash@nash-Aspire-5742:/lib$ dir
apparmor			      libcap.so.2		    libncurses.so.5	       libply-boot-client.so.2.0.0	libusb-0.1.so.4.4.4
brltty				      libcap.so.2.20		    libncurses.so.5.7	       libply.so.2			libusb-1.0.so.0
cpp				      libcrypto.so.0.9.8	    libncursesw.so.5	       libply.so.2.0.0			libusb-1.0.so.0.0.0
dbus-1.0			      libdevmapper-event.so.1.02.1  libncursesw.so.5.7	       libply-splash-core.so.2		libwrap.so.0
firmware			      libdevmapper.so.1.02.1	    libnih-dbus.so.1	       libply-splash-core.so.2.0.0	libwrap.so.0.7.6
hdparm				      libfuse.so.2		    libnih-dbus.so.1.0.0       libply-splash-graphics.so.2	libx86.so.1
i386-linux-gnu			      libfuse.so.2.8.4		    libnih.so.1		       libply-splash-graphics.so.2.0.0	libxtables.so.5
init				      libhistory.so.6		    libnih.so.1.0.0	       libpopt.so.0			libxtables.so.5.0.0
klibc-YHMcsdavQye9iuNwPByVrU6ZqHQ.so  libhistory.so.6.2		    libnss_mdns4_minimal.so.2  libpopt.so.0.0.0			linux-sound-base
ld-linux.so.2			      libip4tc.so.0		    libnss_mdns4.so.2	       libproc-3.2.8.so			lsb
libatasmart.so.4		      libip4tc.so.0.0.0		    libnss_mdns6_minimal.so.2  libreadline.so.6			modules
libatasmart.so.4.0.3		      libip6tc.so.0		    libnss_mdns6.so.2	       libreadline.so.6.2		plymouth
libatm.so.1			      libip6tc.so.0.0.0		    libnss_mdns_minimal.so.2   libsepol.so.1			security
libatm.so.1.0.0			      libipq_pic.so.0		    libnss_mdns.so.2	       libslang.so.2			systemd
libbrlapi.so.0.5		      libipq_pic.so.0.0.0	    libntfs-3g.so.79	       libslang.so.2.2.2		terminfo
libbrlapi.so.0.5.5		      libipq.so.0		    libntfs-3g.so.79.0.0       libssl.so.0.9.8			udev
libbsd.so.0			      libipq.so.0.0.0		    libparted.so.0	       libsysfs.so.2			ufw
libbsd.so.0.2.0			      libiptc.so.0		    libparted.so.0.0.1	       libsysfs.so.2.0.1		xtables
libbz2.so.1			      libiptc.so.0.0.0		    libpcsclite.so.1	       libulockmgr.so.1
libbz2.so.1.0			      libiw.so.30		    libpcsclite.so.1.0.0       libulockmgr.so.1.0.1
libbz2.so.1.0.4			      liblvm2app.so.2.2		    libply-boot-client.so.2    libusb-0.1.so.4

---

### Post by nashpd on 2011-04-27
Apologies for what appears as Spam, but I could delete the entry, and run the update. I had to do it manually for one more file which had %5GB at the end.

Thank you for the help. I also removed the google entry from the list in update manager.

Problem solved.

---

### Post by mrakhunathan on 2011-04-29
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update


WORKS FRIENDS...

---

