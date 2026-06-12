---
title: "HP DM1z Wifi issues."
date: 2011-08-22
forum: General Help
---

### Post by Snoopy_Corleone on 2011-08-22
:-k

So, trying to install 11.04 Ubuntu on an HP Dm1z.

Now, it seems I could install Ubuntu on a million machines.. and I would know to expect a million wireless driver issues.. and that would be the only problem/s I'd have with it.

tried following these instructions the best I could. 

Here are the steps I took to get my wireless DWA-525 PCI to work(adapted to your specific card):

> 1. Download the correct driver from [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2). ([http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2).) In my case it was RT3062PCI/mPCI/CB/PCIe(RT3060/RT3062/RT3562/RT3592). You most likely need to to download RT5390PCIe.

2. Unzip the 2010_1217_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO.zip you just downloaded.

3. Open the folder you just unzipped and navigate to os -> linux. There you will find a file named config.mk. Open it with your favourite text editor of choice.

4. Change the following:

Code:
#Support Antenna Diversity
HAS_ANTENNA_DIVERSITY_SUPPORT=n

to:

Code:
#Support Antenna Diversity
HAS_ANTENNA_DIVERSITY_SUPPORT=y

And then save and close.

5. Enter the following commands to compile the driver(note that you may need to enter the last two commands as root):

Code:
cd 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO
make
make install

6. Now in my case my driver conflicts with the rt2800pci driver so you may need to blacklist it in order for the driver you just compiled to work(the thread I looked at on the *buntu forums seems to confirm this). Open a command line and enter the following command as root:

Code:
nano /etc/modprobe.d/blacklist-rt2800pci.conf

Nano is a command line text editor in case you're wondering what's going on after you enter that command. Type in the following:

Code:
blacklist rt2800pci

Hit Crtl+o and then enter to save. Then hit Crtl+x to exit.

7. Reboot.

8. After rebooting enter the following commands in a command line:

Code:
modprobe rt5390sta
ifconfig ra0 inet up

And that's it. Hopefully these instructions worked for you. Good luck.

Things to note:

1. I used the newer driver version which should be.
2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO and I did not see a "HAS_ANTENNA_DIVERSITY" in the config.mk file.

2. my kernel version (just for the sake of having it up here) is 2.6.38-11-generic

3. I had an issue with the "Nano /ect/modeprobe..." part because, when I would hit ctrl + O it didn't want to save.

4. skipping the last step, when running the modprobe rt5930STA and inet up commands, it wouldn't tell me anything is wrong, but the wireless drivers still don't work.

Sorry if I am making some totally idiotic mistake, any help would be appreciated.

---

### Post by Snoopy_Corleone on 2011-08-22
my apologizes if "bumping" is highly frowned upon, but this is about four pages back, and I need ubuntu working for class soon..

---

### Post by Redblade20XX on 2011-08-23
In order to run those commands you couldn't run, you needed to have root permission. Try and use sudo in front of the commands you'll have to enter in the terminal.
Hopefully, that was your only problem! :)

-Red

---

