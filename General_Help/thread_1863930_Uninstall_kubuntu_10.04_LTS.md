---
title: "Uninstall kubuntu 10.04 LTS"
date: 2011-10-18
forum: General Help
---

### Post by Latintrans on 2011-10-18
NEWBIE HERE: I have a laptop with windows 7 home and kubuntu 10.04 LTS, but I want to uninstall Kunbuntu.

I need some help to do this, when my lap starts I get some options to choose kubuntu or windows to start, but can I uninstall kubunto from windows or must I do it from kubuntu?.

I do not get to see any wireless conection from kubuntu, only from windows, I have tried to install the drivers but kubuntu is still not showing any networks.

Some help please

I want to uninstall my lap is having to many problems now:(

---

### Post by mörgæs on 2011-10-18
If you don't give up we might be able to help you getting Kubuntu to work. What other problems do you have except from the wirefree connection?

---

### Post by Latintrans on 2011-10-18
The biggest problem is that no wireless networks are to be seen to conect with, i have paid money even to a technitian to install the drivers but even so not network is shown. I have tried to conect manually to my wireless conenction without succes. 

What else can I do?

---

### Post by Redblade20XX on 2011-10-18
Post the specs of the laptop and we will see what we can do! ;)

- Red

---

### Post by tartalo on 2011-10-18
[http://computersight.com/operating-systems/ubuntu/ubuntu-how-to-remove-ubuntu-windows-vista/](http://computersight.com/operating-systems/ubuntu/ubuntu-how-to-remove-ubuntu-windows-vista/)

Very important, make sure you do have a bootable Windows 7 installation CD before trying to follow the instructions above.

---

PS: About wireless in Kubuntu. You don't mention what computer you have, it might be that your hardware is still not supported in 10.04. If that's the case, an possible solution is to upgrade (you can do that with a CD).

---

### Post by Latintrans on 2011-10-18
I do not have  a windows cd but a kubuntu 10.04 

This are the spec of the toshiba laptop

windows 7 home premium
service pack 1
procesor pentium R dual core cpu t4500 @ 2.30 GHz
memory 4 Gb (3,87 gb available)
type system 64 bits

I hope this is what you mean.

---

### Post by mörgæs on 2011-10-18
How does Kubuntu work with wired internet access?

---

### Post by tartalo on 2011-10-18
1) IF YOU STILL WANT TO REMOVE KUBUNTU

When you installed Kubuntu, it installed a program called Grub in the Master Boot Record of your hard disc. Grub is the program that shows you a list of the OS you have available when you boot. This is done because unlike Windows' equivalent it allows you to boot any operating system (Windows loader only recognizes Windows installations).

The thing is that if you now simply remove the Kubuntu partition, grub will be unusable because it stores information in the Kubuntu partition, and nothing will boot, so you would need to install the Windows loader back.

I haven't tried it myself but apparently you can create a recovery disk from Windows 7:
[http://www.guidingtech.com/3816/system-repair-recovery-disc-windows-7/](http://www.guidingtech.com/3816/system-repair-recovery-disc-windows-7/)

In that article it says that one of the options is "Startup Repair" which sounds a lot like reinstalling Windows loader in the MBR.

I repeat, I haven't done this myself, you are on your own.

2) IF YOU WANT TO FIX WIRELESS IN KUBUNTU

To diagnose why it's not working it's very useful to know what wireless card you have now, this information is not among the specs you sent.

2.1 Discover what wireless card you have from Kubuntu:

To open a terminal press Alt+F2 and then type konsole

In the terminal type this:
```
lspci
```
Each line refers to a piece of hardware, see if you are able to recognize the wireless card, and if so write it down and send it here.

if you don't recognize it:

```
lspci > myhardware.txt
```

This will put the info in a text file in your home folder, copy it to a flash drive, boot to windows and copy the contents here.


2.2 Discover what wireless card you have from Windows:

I believe this is the best equivalent to lspci for Windows, but I can't give you instructions about how to use it:
[http://rh-software.com/](http://rh-software.com/)

---

### Post by Latintrans on 2011-10-18
Hi again the wireless card is atheros AR9285, everything would be Ok if I just could make the wireless in kubuntu work.

The wired is not even working with windows.
I do not have any window cd I prefer to try make kubuntu work

i have usde kubuntu many times in other laptops before but I never got it conected to the internet.

---

### Post by mörgæs on 2011-10-18
There have been some trouble with these cards earlier, so I believe that it is a good investment to begin with a fresh install of Kubuntu 11.10. 

If neither Windows nor Kubuntu 10.04 are working properly and you want to erase it all, you can just select 'use entire drive for Kubuntu' during installation.

---

### Post by tartalo on 2011-10-18
According to this there's a backport now:
[https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285](https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285)

This is what I would do in your situation:

First you need to know if you are running the 32 bits or 64 bits version of Kubuntu, you can discover that by typing in a terminal this:
```
uname -a
```
At the end it will say either i386 GNU/Linux or x86_64 GNU/Linux

Now, with windows (or something that connects to internet) go here:
[http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-lucid-generic](http://packages.ubuntu.com/lucid/linux-backports-modules-wireless-lucid-generic)

Do you see where it says i386 and amd64? click on the appropriate one (on the word i386 or amd64, not on "list of files"), it will send you to a page with mirror servers, choose one to download your package.

The previous package depends on this one, download it too:
[http://packages.ubuntu.com/lucid/linux-backports-modules-compat-wireless-2.6.34-2.6.32-34-generic](http://packages.ubuntu.com/lucid/linux-backports-modules-compat-wireless-2.6.34-2.6.32-34-generic)

Put these two .deb files somewhere like a flash drive and boot Kubuntu.

Open the terminal, go to where the .deb files are (if you are unsure about where your flash drive has been mounted remember that you can drop a folder to the terminal) and type this to install them:
```
sudo dpkg -i *.deb
```

(Hopefully you will have all needed dependencies, otherwise write down what is missing go again to the last link I gave you to download any other dependency needed.)

Reboot.

Now the network manager (the icon is either an ethernet cable with a plug or an antenna with concentric circles) should be seeing your wireless network.

---

### Post by tartalo on 2011-10-18
> **mörgæs said:**
> There have been some trouble with these cards earlier, so I believe that it is a good investment to begin with a fresh install of Kubuntu 11.10.

You wrote your answer while I was writing mine. Do these problems also occur with the backport?

---

### Post by mörgæs on 2011-10-19
I can't say for sure - have not used the card myself. Let the experiments begin!

---

### Post by Latintrans on 2011-10-20
The network problems are to heavy in both systems I have decided to start from scratch with both systems, I am right now dowloading an iso of windows and I will first install it and then give a try again to kubuntu with a second install, the only thing I need to know is if I do need extra freeware to make different partions?

I have a legitimate version serial code for 5 windows premium 7, and I guess i can the same way download the last version of kubuntu, can someone point me the link to the last version of kubuntu?

---

### Post by tartalo on 2011-10-20
Download Kubuntu from here:
[http://www.kubuntu.org/getkubuntu/download](http://www.kubuntu.org/getkubuntu/download)

You don't need any other software to make your partitions, Kubuntu includes a partition manager, and I believe Windows 7 also has one.

First install Windows, then Kubuntu (so it installs Grub in your MBR and you can boot both OS)

One tip, when you install Kubuntu it's a good idea to have /home in a separate partition (The installer offers you that option)

---

