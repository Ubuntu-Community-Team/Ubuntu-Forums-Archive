---
title: "New to Ubuntu."
date: 2009-10-11
forum: General Help
---

### Post by Romanrp on 2009-10-11
As of yesterday,I have installed ubuntu on my whole hard drive on a nearly brand new laptop.
My laptop is an Asus K50In.
I have a few questions.
1.When I click on Hardware drivers (system/administration/hardware drivers) it comes up with an empty box which says "no propriertary drivers are use in the system"
What does it mean and what does it do?
And how should I get my NVIDIA driver activated?
My graphics card is NVIDIA GEFORCE G102M cuda  512MB.
I ahve looked at the nvida page and they have no driver for my graphics card.
What should I do?
And last but not least,At the moment I have no internet connection on my laptop.But I do have a working pc and a usb stick.
I have downloaded a linux program,put it on my memory stick but I can't seem to install it,any help?
Thanks!

---

### Post by Romanrp on 2009-10-11
Yeah,I settled down on ubuntu,opensuse was too slow,mandriva didn't work,pc bsd didn't work,fedora-meh.
At least ubuntu worked.
But I burned the 9.10 beta but that doesn't work.
I am just unlucky.

---

### Post by Redundant Username on 2009-10-11
Propitary drivers are closed-souce drivers made by other companies.
What is the extention (.tar, .tar .gz,. zip, .rar, .deb) of the program you want to install?
What is the brand and model number of your wireless card?
I suggest you start reading the Ubuntu help section, in the top right corner of your page.

---

### Post by MelDJ on 2009-10-11
> **Romanrp said:**
> Yeah,I settled down on ubuntu,opensuse was too slow,mandriva didn't work,pc bsd didn't work,fedora-meh.
At least ubuntu worked.
But I burned the 9.10 beta but that doesn't work.
I am just unlucky.

dont use 9.10. its still in beta. use 9.04 instead

---

### Post by Romanrp on 2009-10-11
My wireless card was made by Atheros.
802.11bgn module:AW-785
model number:AR5B95

The program I want to install is tar.gz.

---

### Post by Redundant Username on 2009-10-11
Then you'll need to compile. [Here is a guide.]("https://help.ubuntu.com/community/CompilingEasyHowTo")
Most Atheros cards work out of the box. Go to preferences -> network connections and set up your wireless there.

---

### Post by Romanrp on 2009-10-12
Thanks,I will try that!
I just hope my graphics card will be that easy.
Does recompiling work on anything?
EG. can I turn a NVDIA driver for vista into a driver for xp?

---

### Post by azmo35 on 2009-10-12
Mate i;m note a computer savvy but for me when i upgrade "clean install" i do the first upgrade through yellow cable and then you will have the wireless card workig.My bad is nvidia card!Anyhow on my sony after the first update it give me two drivers i use the 180 as recommended.

---

### Post by P4man on 2009-10-12
> **Romanrp said:**
> Thanks,I will try that!
I just hope my graphics card will be that easy.
Does recompiling work on anything?
EG. can I turn a NVDIA driver for vista into a driver for xp?

Compiling works on most things, but you need SOURCE code to compile. Compiling is essentially translating human readable source code in to machine specific binary instructions. Now if you can get nVidia to release the source code of their drivers, you could probably compile it. Feel free to ask them :p (don't bother, they don't release their sources).

Anyway, im kind of surprised your videocard doesnt prompt the hardware driver app to install nvidia binary drivers. perhaps its too new, but /me thinks latest nvidia linux drivers should support your card. I'll check a bit later.

---

### Post by undecim on 2009-10-12
Welcome to Ubuntu!

To answer your questions:

Proprietary drivers are drivers written by the companies that created the hardware it drives. They are disabled by default because they are considered a security risk (if there is a vulnerability in the driver, you have to rely on the hardware vendor to update the driver, and some companies are bad about updates). Also, some drivers cannot be included on Ubuntu CDs and must be downloaded after installation because of copyright issues (since Canonical doesn't charge money for Ubuntu, they can't pay to bundle everything)

Fortunately though, you can download them yourself, and Ubuntu makes the process easy. First, you will need an ethernet (wired) internet connection (this is just temporary; so you can install your wireless drivers...) Once you are connected to the internet, install your updates by using the update manager: System/Administration/Update Manager (you may want to leave the updater overnight, or while you are at work or something)

Then. check your hardware drivers again. Install drivers for any hardware you will use, and reboot.

Also, if you want to install software, you should see if it's in the Add/Remove application first. It will download software directly from the Ubuntu repositories, meaning it is pre-compiled and ready to run on your computer. It is also much safer, because the code from those programs is reviewed and determined to be safe.

You may also want to enable more applications by choosing "All Available Applications" from the drop-down menu in the corner, or "All Open Source Applications" if you want less choice, but more security.

And one more little hint: If you can't find an program in the Add/Remove application, some software websites allow you to download a".deb" file, which will install much more easily than compiling from source. Its often called a "Ubuntu Package" or a "Debian Package"

---

### Post by Romanrp on 2009-10-12
> **azmo35 said:**
> Mate i;m note a computer savvy but for me when i upgrade "clean install" i do the first upgrade through yellow cable and then you will have the wireless card workig.

What do you mean yellow cable?

@undecim
Is it possible for me to do that via a memory stick?

---

### Post by azmo35 on 2009-10-12
Sorry about my mistake, but have u made any updates to your system?

---

### Post by Romanrp on 2009-10-12
I can't,no internet.
I just found a driver for my wireless card.
It is on my usb stick and it is a tar.gz file.
How would I install this,from my memory stick?

---

### Post by undecim on 2009-10-12
If you want to upgrade/install stuff via external drives instead of over the internet, look at Keryx: [http://keryxproject.org/](http://keryxproject.org/)

I've never used it before, but I've been told that it works well for that. It says it's cross-platform, so you should be able to use it from even a Windows computer to download updates and driver packages for Ubuntu. though depending on the capacity of your memory stick, it may require multiple transfers. I have no idea how big the first update will be.

(Just added "try Keryx" to my todo list)

---

### Post by azmo35 on 2009-10-12
Well a bit of googling i found that your lap have the j45 for the yellow cable to connect to eternet lan so u can use this yellow cable to connect with your wireless/moden to get the updates.

---

### Post by Romanrp on 2009-10-12
I will try the kerrix project
and I will also look into the yellow cable.-never heard of it before.

---

### Post by Redundant Username on 2009-10-12
I forgot to mention, when compiling, make sure the .tar.gz is transfered to the hard drive before starting, otherwise when you remove the flashdrive, you won't be able to acsess your program.

---

### Post by sarloth on 2009-10-12
> **Romanrp said:**
> As of yesterday,I have installed ubuntu on my whole hard drive on a nearly brand new laptop.
My laptop is an Asus K50In.
I have a few questions.
1.When I click on Hardware drivers (system/administration/hardware drivers) it comes up with an empty box which says "no propriertary drivers are use in the system"
What does it mean and what does it do?
And how should I get my NVIDIA driver activated?
My graphics card is NVIDIA GEFORCE G102M cuda  512MB.
I ahve looked at the nvida page and they have no driver for my graphics card.
What should I do?
And last but not least,At the moment I have no internet connection on my laptop.But I do have a working pc and a usb stick.
I have downloaded a linux program,put it on my memory stick but I can't seem to install it,any help?
Thanks!

Your main problem at the moment appears to be lack of internet.

The proprietary drivers should be installed for you once you get connected.

What these people are trying to say when they mention "Yellow Cable" (which is insane, since network cables can be many colors) or "Ethernet" is that you need to plug into a network via a network cable, cat5, rj45, wired ethernet/internet. 

Once you do this you will be connected and then when you go to the drivers menu it should ask if you would like to install drivers for your proprietary hardware.

If you do not have access to a wired connection (not sure why you wouldn't) I am fairly certain it is possible to download the .deb files from Ubuntu online and save those to the USB. I would not suggest trying to compile from source as a beginner, it isn't easy or fun.

I will try to find the .debs and post again if I do (I am at work so I may not get around to it.)

---

### Post by Giblet5 on 2009-10-12
The NVidia drivers will work with that GPU. Problem is, NVidia is very slow to certify drivers against their M-class chips.

Odds are, if you download the latest manual-install driver from nvidia.com and run the installer, it will work perfectly. You just won't get notifications when a newer driver is available.

Nvidia's manual installer script can handle checking/upgrading the driver, so do try out the --help option.

---

### Post by sarloth on 2009-10-12
Sorry, no time to find them for ya, but the packages you need should be available here, you can transfer them to the machine via USB and double-click to install.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by P4man on 2009-10-12
A quick google turned up this:
[http://ubuntuforums.org/showthread.php?t=1247196](http://ubuntuforums.org/showthread.php?t=1247196)

So if you get your network sorted with a cable, the driver manager WILL prompt you for nvidia drivers, but **those drivers will apparently mess up your screen resolution. **

So, I would suggest you apply that person's solution **before** you reboot (and after installing those drivers), otherwise you will end up with a machine with no graphical interface, and being new to ubuntu, that is not what you want.

In steps (after getting online):
1. go to system > adminstration > hardware drivers
Select the suggested nvidia 185 drivers, and apply. Do NOT reboot when prompted.

2. Press alt+F2 and type (or copy paste) this command:
```
gksudo gedit /etc/[COLOR="Red"]X[/COLOR]11/xorg.conf
```

(note the red X is in uppercase!)
Locate the "device" section in that text file. It will look similar to this (its mine):

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1440+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```


Add a line so it looks like
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1440+0"
   **Option "ModeValidation" "NoTotalSizeCheck"**
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

Save the file, reboot, cross fingers :)

---

### Post by Romanrp on 2009-10-13
Wow!Thanks guys for all your help.
I tried to connect it with my pcs USB internet but it didn't work so I will try the packages.
Thanks again.
If this fails then I don't know what will work...

---

### Post by Wrathe on 2009-10-25
[SIZE=3][COLOR=Black]So does it work?[/COLOR][/SIZE]

I got an ASUS K50IN as well.

The method I tried worked for a little while, until I went to Hardware Drivers (System > Admininstration) and clicked enabled (which froze it and then something happened and now it is disabled..  Below is what I did.  They are my notes on what happened in case there is a reason to do it again.  [COLOR=Red]IT IS SUGGESTED YOU DO NOT DO THIS IF THE ABOVE WORKS![/COLOR]

                                   
> Download NVIDIA-Linux-x86-185.18.36-pkg2.run (x86_64 for AMD64) from [[COLOR=#000080]_www.nvidia.com_[/COLOR]]("http://www.nvidia.com/") to desktop.
 

 You must close X (the Graphical User Interface aka GUI).  Open terminal and type:  
  
 sudo  /etc/init.d/gdm stop


  
 Press Ctrl + Alt + F1 (or F2 - F6) to open a different desk.  Login with your username and password.  Now type: 
  
 cd Desktop 
 sudo sh NVIDIA [press Tab] 



  
 Now go through the NVIDIA installer.
 However I have not yet installed the Ubuntu updates.  That may be why it did not work.

---

