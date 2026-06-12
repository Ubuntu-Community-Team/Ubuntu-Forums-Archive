---
title: "Boot Issue"
date: 2010-06-03
forum: General Help
---

### Post by johnathanamber on 2010-06-03
Hello,

I am getting this error during boot... it takes an eztra 5-10 seconds until this error displays. Once grub selected the option to boot... the system halts until this error displays for 1 second. Then the Ubuntu boot image displays and continues to load.

"xx.xxxxxx: mmc0 unknown controller version (2). You may experience problems."

How can I tell what this is that is causing the booting delay?

Thank you and God bless,
Johnathan

---

### Post by johnathanamber on 2010-06-08
Anyone have any ideas as to where to start or which logs to find this out?

---

### Post by oldfred on 2010-06-08
You can check logs with System, Administration, Log File Viewer.

There is a long list. demesg & message may be good ones to look at but I have reviewed most. Not sure if log file is not just going to show the same error. Google tells me mmc is 

iW-SD/SDIO/*MMC Controller* interfaces SD / MMC / SDIO card to any processor with a generic interface. The interface towards the SD card is realized by the SD [B]...
[/B]
Do you have a flash or memory card plugged in?

---

### Post by johnathanamber on 2010-06-08
@oldfred,

I do have that device, however there is no card inserted... just a dummy insert.

That device works fine BTW.

I've looked at the dmesg log (mmc0 shows up three times):
> 
[   21.377126] mmc0: Unknown controller version (2). You may experience problems.
[   21.377306] sdhci-pci 0000:1a:00.1: Will use DMA mode even though HW doesn't fully claim to support it.
[   21.377321] sdhci-pci 0000:1a:00.1: setting latency timer to 64
[   21.377364] Registered led device: mmc0::
[   21.377410] mmc0: SDHCI controller on PCI [0000:1a:00.1] using DMA


In message log it shows twice with the same ingo:
> 
Jun  8 08:24:29 7727609341 kernel: [   21.377364] Registered led device: mmc0::
Jun  8 08:24:29 7727609341 kernel: [   21.377410] mmc0: SDHCI controller on PCI [0000:1a:00.1] using DMA


Searching other logs...

---

### Post by johnathanamber on 2010-06-10
This is all I've found... the same as the above log entries.

Is there not a Device manager that can be installed that might be able to assist in finding out what is causing this or maybe rectify the issue?

Thank you and God bless,
Johnathan

---

### Post by johnathanamber on 2010-06-10
OK, I did install gnome-device-manager.

I see plenty of unknown devices... any suggestions on finding out which one it is?

---

### Post by oldfred on 2010-06-10
There is an older bug that they think was solved.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323159](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323159)

and a newer one, that seems a duplicate of the above one:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568766](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568766)

Try the command to see what you have.
 lspci | grep SD
and/or
lspci -nn | grep MMC

---

### Post by johnathanamber on 2010-06-10
@oldfred,

Here is what I get:
> 
lspci | grep SD
1a:00.1 SD Host controller: O2 Micro, Inc. Device 8120 (rev 01)


Nothing is displayed with the other command.

---

### Post by johnathanamber on 2010-06-10
Looking at the Gnome Device Manager it does show it being the MMC Card Reader. (See Attached)

So since I do not want to disable the device, I do use it, how can we get it to stop the polling or the error during boot time?

---

### Post by oldfred on 2010-06-10
Do not know any fixes. 

I would suggest you sign up on launchpad and add your problem to the list of users with the bug.

---

### Post by johnathanamber on 2010-07-08
Hey,

I was wondering, if you open Synaptic, and you search for 'mmc'... what packages do you have installed?

Also, I've found this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323159](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323159)

Looks to be a similar issue.

---

### Post by johnathanamber on 2010-07-10
Evidently, others are having similar problems:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323159](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/323159)

[http://ubuntuforums.org/showthread.php?t=1471138&page=3](http://ubuntuforums.org/showthread.php?t=1471138&page=3)

---

### Post by johnathanamber on 2010-07-16
Continued on:
[http://ubuntuforums.org/showthread.php?p=9597289#post9597289](http://ubuntuforums.org/showthread.php?p=9597289#post9597289)

Solving Thread due to above!

---

