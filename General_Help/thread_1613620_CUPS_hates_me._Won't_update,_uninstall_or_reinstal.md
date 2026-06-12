---
title: "CUPS hates me. Won't update, uninstall or reinstall"
date: 2010-11-04
forum: General Help
---

### Post by bmeakings on 2010-11-04
I'm having a big problem with CUPS. I did a check for updates and some for CUPS were found so I installed them, but when it installs the updates it gets to "Preparing to replace cups 1.4.4-6ubuntu2.1 (using .../cups_1.4.4-6ubuntu2.2_amd64.deb) ..." and nothing happens, the installation just sits there with no disk activity or CPU use. The system is still usable but the installer hangs up. The only way to stop it is to reboot the system or close the terminal and force-close the installer.

On booting up, when I run the update manager it gives the "Not all updates can be installed" error and offers to do a partial upgrade. It sees that cups had an error installing but I get the same lock-up at "Preparing to replace cups 1.4.4-6ubuntu2.1 (using .../cups_1.4.4-6ubuntu2.2_amd64.deb) ...".

I've also tried these:
Running "sudo apt-get purge cups" gives me "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."
Running "sudo dpkg --configure -a" gives me "dpkg: error processing cups (--configure):
Package is in a very bad inconsistent state - you should
reinstall it before attempting configuration.
Errors were encountered while processing:
cups"
Running "sudo apt-get install --reinstall cups" gives the same hang-up problem as described.

I tried cleaning the apt cache (sudo apt-get clean) in case the update was corrupted. The files re-download but I still get the same problem. I also tried starting a TTY session and stopping the CUPS service with "sudo service cups stop" but it also hangs up and I have to ctrl+c to abort it.

I'm at my wit's end here :(

---

### Post by dcstar on 2010-11-04
> **bmeakings said:**
> 
.........
I've also tried these:
Running "sudo apt-get purge cups" gives me "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."
Running "sudo dpkg --configure -a" gives me "dpkg: error processing cups (--configure):
Package is in a very bad inconsistent state - you should
reinstall it before attempting configuration.
Errors were encountered while processing:
cups"
Running "sudo apt-get install --reinstall cups" gives the same hang-up problem as described.

I tried cleaning the apt cache (sudo apt-get clean) in case the update was corrupted. The files re-download but I still get the same problem. I also tried starting a TTY session and stopping the CUPS service with "sudo service cups stop" but it also hangs up and I have to ctrl+c to abort it.

I'm at my wit's end here :(

Try to remove the package in Synaptic, and also try deleting the config files as well:

/etc/cups
/usr/lib/cups
/usr/share/cups

---

### Post by bmeakings on 2010-11-04
I'll try deleting the config files, but removing via Synaptic has so far proved impossible.

---

### Post by bmeakings on 2010-11-04
Well, after deleting the config files I tried the usual things but the problem seemed to still be there. But on running sudo apt-get update and sudo apt-get dist-upgrade the updates seemed to be successfully applied. But reinstalling CUPS still has the same problems.

I'll try tinkering around some more, but at least the updates have been applied. Thanks :)

---

### Post by exXplode on 2010-11-06
I'm having the same problem. Just to tell you, you're not alone with the problem.

---

### Post by gwiener on 2010-11-08
Same here. This is a real menace. Also, after a couple of failed attempts, now CUPS does not work. Any progress on that?

---

### Post by bmeakings on 2010-11-09
I think I managed to sort it out, but the method was a bit extreme - After getting nowhere and losing my patience, I basically beat CUPS into submission by running the gnome-search-tool as root, searching for "cups" and deleting everything that turned up (one file wasn't related to CUPS, so be careful). Afterwards I rebooted and used Synaptic to re-install packages related to CUPS and printing (libcups2, cups-ppdc, cups-client, libcupsdriver1, etc) before re-installing the main cups package.

It seemed to work and my printer is working fine, but it was a last-ditch attempt. I was ready to reinstall the OS.

---

### Post by itsterry on 2011-01-04
Bleah. I'm having major cups problems, too. 

Even sudo apt-get purge cups just hangs the terminal.

Going to try your "Gnome search as root" route: thanks for the suggestion

T

---

### Post by roadrash on 2011-01-09
i did what was done above and it cured the error in updates but I am now unable to print anything.  I have set the printer up in system/administration but every print dialog only gives the option to print to file.

**Solved I reinstalled libgtk2 & I have the printer back in print dialouges**

---

### Post by scofflan on 2011-01-10
It appears that Cups is hanging on the update process. For some reason Cups needs to be restarted to allow the update to continue normally. When updating if the process stops on cups or cup-ppdc open a terminal and enter the command 
sudo start cups

This allows the update to continue without causing all of the package problems.

---

