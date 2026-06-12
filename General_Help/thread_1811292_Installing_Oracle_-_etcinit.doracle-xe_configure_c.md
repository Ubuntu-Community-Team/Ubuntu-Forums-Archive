---
title: "Installing Oracle - /etc/init.d/oracle-xe configure command missing?"
date: 2011-07-24
forum: General Help
---

### Post by boy18nj on 2011-07-24
I've AMD64 system with Ubuntu 11.04 installed. It's been rough ride for me to install oracle-xe-universal. I've already spent more than 2 days on this. Still unsuccessful.

1) First I downloaded the packages libaio_0.3.104-1_i386.deb and oracle-xe-universal_10.2.0.1-1.1_i386.deb
2) Then I ran 

sudo apt-get install bc (ran fine)
sudo dpkg -i --force-architecture libaio_0.3.104-1_i386.deb (ran fine)
sudo dpkg -i --force-architecture oracle-xe-universal_10.2.0.1-1.1_i386.deb (gave me dependency error for libc6 (>= 2.3.2), I modified the control file to remove dependency and rebuilt the package) (now worked fine)

Oracle xe is now installed. Then I tried to start the DB it started but it's HTTP client never started. So I decided to uninstall the oracle-xe=universal. None of the sudo apt-get remove oracle-xe-universal command's didn't worked for me. So i went for manual uninstallation directions as per oracle link.

I ran the following command-
--Manually uninstalling Oracle 10g--
sudo rm -rf /usr/lib/oracle /etc/oratab /etc/init.d/oracle-xe /etc/sysconfig/oracle-xe /usr/share/doc/oracle_xe /usr/share/doc/oracle_xe_client


Then I again ran the following command to install oracle-xe

sudo dpkg -i --force-architecture oracle-xe-universal_10.2.0.1-1.0_i386.deb

See below what I got as the output-

rocky@ubuntu:~/git/mygit/edas2/libaio$ sudo dpkg -i --force-architecture oracle-xe-universal_10.2.0.1-1.1_i386.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 184865 files and directories currently installed.)
Preparing to replace oracle-xe-universal:i386 10.2.0.1-1.1 (using oracle-xe-universal_10.2.0.1-1.1_i386.deb) ...
Unpacking replacement oracle-xe-universal:i386 ...
Setting up oracle-xe-universal:i386 (10.2.0.1-1.1) ...
Executing Post-install steps...
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
rocky@ubuntu:~/git/mygit/edas2/libaio$ 


Now if I try to run the following command, it says command not found-
rocky@ubuntu:~/git/mygit/edas2/libaio$ sudo /etc/init.d/oracle-xe configure
sudo: /etc/init.d/oracle-xe: command not found
rocky@ubuntu:~/git/mygit/edas2/libaio$ 


Even in applications menu I don't see the if oracle has been installed.

So i conclude first time installation was ok but somehow http client didn't worked. 
After manual uninstallation, second installation didn't even loaded/installed the oracle-xe in init.d directory.

Please help here.

---

### Post by boy18nj on 2011-07-24
Any help here. Guys?

---

