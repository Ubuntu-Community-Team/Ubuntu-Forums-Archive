---
title: "Giving up waiting for root device."
date: 2010-05-14
forum: General Help
---

### Post by BareSand on 2010-05-14
Hello.  I installed 10.04 on my laptop earlier this week and everything was running smoothly. Today, I decided I was going to install a few packages. So, I go about "[FONT=Courier New]sudo apt-get *stuff*[/FONT]" from the command line and in the process, I broke the boot process.

When I reboot my system, I got the "Giving up waiting for root device." spiel and an alert that says:
[FONT=Courier New]ALERT! /dev/disk/by-uuid/f9...80 does not exist. Dropping to a shell![/FONT]
When I wait maybe 30 or so seconds and type [FONT=Courier New]exit[/FONT], I am taken to the login screen for Ubuntu and am able to continue as normal and the disk does exist.

When I rebooted, I had (in this order, as best I remember) ran:
[LEFT][FONT=Courier New][SIZE=1]sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ecryptfs-utils
[/SIZE][/FONT][FONT=Courier New][SIZE=1]sudo apt-get autoremove
sudo apt-get autoclean[/SIZE][/FONT]

I was following the instructions to set up a private directory from [here]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Mount%20Passphrase"). I did the autoremove and autoclean because it said there were two linux-header packages that were unused and no longer needed.

Somehow, I think I got rid of the Ubuntu loading screen during boot and that is why it is dropping me into the shell. So, I am here wondering how to restore it. I can reinstall Ubuntu if needed, but would at least like to know what I messed up to avoid future problems ;)
[/LEFT]

---

