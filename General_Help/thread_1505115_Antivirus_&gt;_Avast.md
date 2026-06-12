---
title: "Antivirus &gt; Avast"
date: 2010-06-08
forum: General Help
---

### Post by Cpierce on 2010-06-08
I have installed Avast on a couple different Ubuntu versions. The program installs fine, but as soon as you update, the program shows error messages and won't load. Anyone else have this issue ? I only use it scan programs/files before I send them to my windows buddies. Anyone have a good AV besides clam and AVG ?

---

### Post by t0p on 2010-06-08
I have a suggestion.  When you send files to your Windows-using friends, tell them to scan the files for malware before they install.

If your Windows-using friends are in the habit of using files from a 3rd party before scanning them, the fault is theirs, not yours.  Why do you feel this need to molly-cuddle your friends in this way?  Their computer is their computer.  If they can't run their computers correctly, it's down to them.

---

### Post by howefield on 2010-06-09
> **Cpierce said:**
> Anyone have a good AV besides clam and AVG ?

Bitdefender.

---

### Post by dino99 on 2010-06-09
clamav (8 packages) is the trusted tool with ubuntu and many other linux distro

---

### Post by jimmers on 2010-06-09
I agree with howefield, try this tutorial:-
  	 	 	 	 	 	 	  **What is BitDefender ?**

  BitDefender is a program to check for Windows viruses and malware. It can be run in the background or on demand when required. Once installed it can be found under Applications - Systems Tools. It can be used as an alternative to clamav/clamtk.  
 **Installation**

  Add the repository by going to System - Administration - Software Sources, click on the 'Third Party Software' tab. Now click on 'Add' and enter  
 deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free  Click on 'Close' and press 'Reload' when prompted. Ignore the 'No repository key' error (if displayed). Now in Applications - Accessories - Terminal add the repository key:  
 wget [http://download.bitdefender.com/repos/deb/bd.key.asc](http://download.bitdefender.com/repos/deb/bd.key.asc) sudo apt-key add bd.key.asc  Now update the apt cache with  
 sudo apt-get update  Install the graphical interface and command line program with  
 sudo apt-get install bitdefender-scanner-gui Once complete you now need to log out and log back in again. a menu shortcut will be generated (Applications - System Tools - BitDefender Scanner).  
 Before running the scanner it's probably best to install the latest virus/malware signatures by clicking on the 'Update' button. 



You will still need to download the License Key, try Bitdefender for Unicies.




Luck

---

### Post by Cpierce on 2010-06-10
Thanks to all you guys. Really good info. Avast worked fine for years until about 6 months ago. If I find the solution, I will post it here. 
In the mean time, I will use one of these. Thanks again guys

---

### Post by PinchedNerve on 2010-06-10
> **jimmers said:**
> I agree with howefield, try this tutorial:-
                                      **What is BitDefender ?**

  BitDefender is a program to check for Windows viruses and malware. It can be run in the background or on demand when required. Once installed it can be found under Applications - Systems Tools. It can be used as an alternative to clamav/clamtk.  
 **Installation**

  Add the repository by going to System - Administration - Software Sources, click on the 'Third Party Software' tab. Now click on 'Add' and enter  
 deb [http://download.bitdefender.com/repos/deb/](http://download.bitdefender.com/repos/deb/) bitdefender non-free  Click on 'Close' and press 'Reload' when prompted. Ignore the 'No repository key' error (if displayed). Now in Applications - Accessories - Terminal add the repository key:  
 wget [http://download.bitdefender.com/repos/deb/bd.key.asc](http://download.bitdefender.com/repos/deb/bd.key.asc) sudo apt-key add bd.key.asc  Now update the apt cache with  
 sudo apt-get update  Install the graphical interface and command line program with  
 sudo apt-get install bitdefender-scanner-gui Once complete you now need to log out and log back in again. a menu shortcut will be generated (Applications - System Tools - BitDefender Scanner).  
 Before running the scanner it's probably best to install the latest virus/malware signatures by clicking on the 'Update' button. 



You will still need to download the License Key, try Bitdefender for Unicies.




Luck

Is Bitdefender needed for Ubuntu 10.04?

---

### Post by howefield on 2010-06-10
> **PinchedNerve said:**
> Is Bitdefender needed for Ubuntu 10.04?

Anti virus is not generally "needed" for Linux systems. In this case, the OP wants to check files before sending them to his friends who operate Windows systems.

A legitimate, if not completely necessary reason for using an anti virus application on linux, some might uncharitably suggest that it is his friends problem if they run a virus infected file.

I trust Bitdefender for a couple of reasons, mainly because it hasn't let me down, and works well on a bootable USB stick which is useful for scanning offline windows drives, the detection rate seems as good as any other and also because it has a 64 bit version unlike most of the others. 

This is an old(ish) document, but it details some of the reasons why some may want to run anti virus applications on linux systems.

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by Irony on 2010-06-10
> **t0p said:**
> I have a suggestion.  When you send files to your Windows-using friends, tell them to scan the files for malware before they install.

If your Windows-using friends are in the habit of using files from a 3rd party before scanning them, the fault is theirs, not yours.  Why do you feel this need to molly-cuddle your friends in this way?  Their computer is their computer.  If they can't run their computers correctly, it's down to them.
A very stupid suggestion. When sending files to friends and family one has a responsibility to ensure those files are safe, if they happen to scan it as well then that is an extra layer of protection.

---

### Post by howefield on 2010-06-10
> **Irony said:**
> A very stupid suggestion.

Talking about stupidity, this is worthy of a mention..

> ...if they happen to scan it as well then that is an extra layer of protection.

It is more beholden on the OPs Windows using buddies to keep their computing environment clean than it is on anyone else, to suggest that they might "happen" to scan files is laughable ?

---

### Post by wilee-nilee on 2010-06-10
And to the source we go reply #5.
[avast forum](http://forum.avast.com/index.php?topic=57812.0)

If you run this command it works every time, there are explanations within this thread and in other threads on the forum.

Personally I only use avast in windows.

Always love a good sniping session count me in.;)

---

### Post by Breambutt on 2010-06-10
The anti-Linux Windows fanbois in general have an attitude like "antivirus software is useless, my computer is safe, it only slows down, you Linux nerds just can't use Windows properly, you can't get infected by accident". The rest of the bunch just feel indifferent about all this and don't even see their computers as delicate instruments.

---

### Post by wilee-nilee on 2010-06-10
> **Breambutt said:**
> The anti-Linux Windows fanbois in general have an attitude like "antivirus software is useless, my computer is safe, it only slows down, you Linux nerds just can't use Windows properly, you can't get infected by accident". The rest of the bunch just feel indifferent about all this and don't even see their computers as delicate instruments.

Aren't we always right in our own reality, oh thats what your saying.;)

Just remember Google is your friend in the search for answers to most OS problems.

---

### Post by rizzeh on 2010-06-10
imo most common use of anti virus in linux is on mail servers for windows clients, a very common scenario.

---

### Post by Cpierce on 2010-06-14
I didn't mean to get an anti virus war going. Just wanted to fix Avast on my computer and the others I have converted to Linux. Here is the response from Avast:

[COLOR=Red]Hello,
some people might report that avast4linux/Workstation doesn't work with 
latest VPS (problem started with 100328-1 for them). The reason is that 
"macro"-block in 400.vps is now depacked to something bigger than 
33554432 bytes - this is an artificial SHM block limitation in some 
Linux kernels (kernel.shmmax).

Solution? Set the limit to higher values (as root):

sysctl -w kernel.shmmax=128000000
OR
echo 128000000 >/proc/sys/kernel/shmmax

Place those lines to /etc/init.d/rcS or equivalent file (it's 
distribution-specific a bit - see /etc/inittab, the sysinit runlevel) to 
have them set automatically (after boot).[/COLOR]


[COLOR=Black]Since I am somewhat of a newbie, some please verify the correct steps I need to take. It looks like I should run [/COLOR]"[COLOR=Black]sudo [/COLOR][COLOR=Black]sysctl -w kernel.shmmax=128000000" in terminal. And then add some line to a startup file.  What line in what file ? I am running 10.04

Can someone help me out ? step by step please. 
[/COLOR]

---

### Post by Cpierce on 2010-06-17
bump

---

### Post by greerd on 2010-06-25
Incase you haven't got this going yet, just type in a terminal

gksudo gedit /etc/crontab

then enter the command so your crontab looks like this:

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
@reboot root sysctl -w kernel.shmmax=128000000
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

regards

---

### Post by dcstar on 2010-06-25
> **greerd said:**
> Incase you haven't got this going yet, just type in a terminal
..........
regards

And why is this totally irrelevant post made here?

He doesn't need to run cron jobs.

---

### Post by dcstar on 2010-06-25
> **Cpierce said:**
> I didn't mean to get an anti virus war going. Just wanted to fix Avast on my computer and the others I have converted to Linux. Here is the response from Avast:

[COLOR=Red]Hello,
some people might report that avast4linux/Workstation doesn't work with 
latest VPS (problem started with 100328-1 for them). The reason is that 
"macro"-block in 400.vps is now depacked to something bigger than 
33554432 bytes - this is an artificial SHM block limitation in some 
Linux kernels (kernel.shmmax).

Solution? Set the limit to higher values (as root):

sysctl -w kernel.shmmax=128000000
OR
echo 128000000 >/proc/sys/kernel/shmmax

Place those lines to /etc/init.d/rcS or equivalent file (it's 
distribution-specific a bit - see /etc/inittab, the sysinit runlevel) to 
have them set automatically (after boot).[/COLOR]


[COLOR=Black]Since I am somewhat of a newbie, some please verify the correct steps I need to take. It looks like I should run [/COLOR]"[COLOR=Black]sudo [/COLOR][COLOR=Black]sysctl -w kernel.shmmax=128000000" in terminal. And then add some line to a startup file.  What line in what file ? I am running 10.04

Can someone help me out ? step by step please. 
[/COLOR]

This will show you what you system is already set to:

```
sudo sysctl -a | grep shmmax
```

**If **you need to increase the existing entry, then:
```
gksudo gedit /etc/sysctl.conf
```

Add in a new entry at the bottom (this is the value my system uses):

```
kernel.shmmax = 268435456
```

---

