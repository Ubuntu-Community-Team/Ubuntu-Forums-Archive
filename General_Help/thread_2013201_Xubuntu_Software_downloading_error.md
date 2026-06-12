---
title: "Xubuntu Software downloading error"
date: 2012-06-30
forum: General Help
---

### Post by vokevybez on 2012-06-30
[FONT=Courier New][SIZE=2]I am currently using Xubuntu 12.04 on my netbook[/SIZE][/FONT][FONT=Courier New][SIZE=2].However, I have started to experiencing a persistent problem. Basically, I cannot install any software! This problem is largely due to the fact that the programs which I usually use to install applications (namely Synaptic Package Manager, Ubuntu Software Center and the default Xubuntu terminal emulator) cannot download the packages needed to begin the installation. For example running [/SIZE]```
sudo apt-get install mencoder
```[/FONT][FONT=Courier New][SIZE=2] outputs [/SIZE]```
0% [Connecting to ke.archive.ubuntu.com (155.232.191.229)]
```[/FONT][FONT=Courier New][SIZE=2] and fails outputting [/SIZE]```
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```When I try these commands they don´t fix the problem[/FONT][FONT=Courier New][SIZE=2]. I know that this is not due to the fact that I do not have an internet connection because I am able to browse the internet using Firefox and even download files using a combination of Aria2c and Flashgot.Restarting the computer does not help. Does anyone know how to fix this issue? ***I would greatly appreciate any help***[/SIZE] 
[/FONT]

---

### Post by cwsnyder on 2012-06-30
First question: Are you getting the software updates on your notebook?  If not check the Software Center >> Edit >> Software Sources . . . >> Download From setting to see if you are pointing to a valid server which is in your country.

---

### Post by vokevybez on 2012-06-30
> **cwsnyder said:**
> First question: Are you getting the software updates on your notebook?  If not check the Software Center >> Edit >> Software Sources . . . >> Download From setting to see if you are pointing to a valid server which is in your country.
Fortunately, its pointed to a valid server which is in my country. Unfortunately, the problem also affects the update manager and it cannot even load the software list, leave alone ***downloading*** and installing updates

---

### Post by vokevybez on 2012-06-30
This is just an update but when I ran the command ```
sudo apt-get clean
``` and followed this by trying to install mencoder by running ```
sudo apt-get install mencoder
``` the command briefly worked but stopped midway through. Moreover, I am now able to download updates using Synaptic Package Manager but only partially. Is that a solution?

---

### Post by cwsnyder on 2012-07-02
When you do a ```
sudo apt-get update && sudo apt-get upgrade
``` are there errors during the update, or only during the upgrade portion?

Yes, Synaptic can also mark upgrades and download partial upgrades when the full upgrade has problems.  I have posted a bug report because Quantal's software updater crashes, and Precise's updater may be having some of the same problems, although I haven't had any problems, so far.

The only package you have mentioned in your posts is **mencoder**.  Have there been other packages giving the same problem installing?

---

### Post by jmfal on 2012-07-02
Try this in a terminal:

```
  sudo apt-get install --fix-missing       
```

If there are any errors post back

---

### Post by cwsnyder on 2012-07-22
You can also try from the terminal:```
sudo apt-get update && sudo apt-get dist-upgrade
```I have found out lately that this is the only way to fix packages held back during a software update.

---

