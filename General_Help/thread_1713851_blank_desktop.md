---
title: "blank desktop"
date: 2011-03-24
forum: General Help
---

### Post by albert2 on 2011-03-24
hey all im new to this so go easy I tried searching could not find my issue.
I have an HP ze4420us laptop running winxp and dual booting ubuntu 10.10(or the latest version just got it) my issue is this linux starts up fine I get to login screen enter password and then the desktop appears with the default background and nothing else except for the mouse pointer. 
I can then reboot and start in "safe mode" using the low graphics setting and everything is fine at that point but I want it to boot normal this is the second laptop I have dual booting and the first one has no issues.
the laptop has an ati radeaon chip I downloaded the ati driver but dont know how to install it any help would be great

---

### Post by Krytarik on 2011-03-24
First, did you change anything after the installation, like trying to enable desktop effects?

Then, I looked up the hardware specs of your laptop to get the exact video chip modell, and I hope you did at least upgrade the RAM (the default is 256 MB). ;)

The laptop has a fairly old video chip installed, because of that you can forget about the proprietary driver, the one you mentioned. But the Open Source Edge driver should provide a fairly good performance.

So, boot into low graphics mode, like you usually do, and run those commands to install the OSED:
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

Then reboot.

---

### Post by albert2 on 2011-03-24
SOLVED
thanks so much for the help this is a friends laptop I am working on for him and I did put a gig of memory in it for him because the 256 was just killing me. I managed to figure out that if I right click the file and clicked property's there was some settings in there that allowed me to install the the driver I had downloaded and as of now it's working, he only plans on using the machine for net and email use so as long as the graphics hold up he should be fine. Again thanks so much for the reply

---

### Post by Krytarik on 2011-03-24
I'm wondering where you did grab the driver, and what the output of
```
lspci |grep VGA
```
eventually is?

---

### Post by albert2 on 2011-03-25
do I type that code in the terminal ? im real ne to doing this stuff  i have been playing with linux for awhile but if it did not install something then  I didnt have it so im real green here. and I will post back on that drive not to sure were I got it but I can give you the version number and all if that would help.

---

### Post by albert2 on 2011-03-25
I typed that code into terminal and this is what I got.

01:05.0 VGA compatible controller ATI tech. INC Radeaon mobility U1
thats it
I have another issue I did not want to create a new thread hope thats ok.
 on my machine I was able to mount my iPhone cant remember what I did but I know it works so on this laptop I am trying the same and get the this error: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
Thats the same error I had on my box but am unable to figure it out on this one. any help would be great

---

### Post by Krytarik on 2011-03-25
Sorry, I can't immediately help with the iPhone issue, I would have to research that also.

As for the driver, yeah, please say its version number and anything you know.
Also, please post the output of
```
lshw -c video
```
You may use the code-tags therefore, the #-button in the editor., it's far more readable then.

---

### Post by albert2 on 2011-03-26
> **Krytarik said:**
> Sorry, I can't immediately help with the iPhone issue, I would have to research that also.

As for the driver, yeah, please say its version number and anything you know.
Also, please post the output of
```
lshw -c video
```
You may use the code-tags therefore, the #-button in the editor., it's far more readable then.

I got the iPhone issue fixed if you have the phone plugged in and close out the error then launch software update it downloads what is needed.
I gave the laptop back to my buddy I should be there today so I will post back on my findings with that other code I do know that I tried to turn on desktops features and they dont work so the driver is just running in low mode.

---

