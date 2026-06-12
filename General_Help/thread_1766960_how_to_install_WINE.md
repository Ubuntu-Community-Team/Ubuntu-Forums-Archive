---
title: "how to install WINE?"
date: 2011-05-25
forum: General Help
---

### Post by Perkomate on 2011-05-25
hey guys. I've installed 11.04 on my netbook, but in order to get inernet access I have to install WINE and emulate the .exe files for the drivers. But, I can't seem to find a way to install WINE without an internet connection. Please help!!!:confused:

---

### Post by linuxinstalledfromhdd on 2011-05-25
[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by wildmanne39 on 2011-05-25
> **Perkomate said:**
> hey guys. I've installed 11.04 on my netbook, but in order to get inernet access I have to install WINE and emulate the .exe files for the drivers. But, I can't seem to find a way to install WINE without an internet connection. Please help!!!:confused:
Hi, you can use the livecd I think, then  go into synaptic,to settings, click on repositories and put a check by install from cd rom.I have never heard of connecting to the internet through wine only, I am sure you have to set ubuntu up to connect to the internet before wine can use it like for a web browser,

---

### Post by Perkomate on 2011-05-25
it's not to connect to the internet through WINE, it's to get the Windows-only drivers to run. And it doens't have a disc drive.

---

### Post by Perkomate on 2011-05-25
my wireless internet switch doesn't work without the drivers, nor the ethernet port

---

### Post by cayphed on 2011-05-25
Assuming your using another pc to access the net, you probably wanted to download the wine pack and install it from a usb, you've mostlike went here [http://www.winehq.org/download/](http://www.winehq.org/download/) and noticed they only show how to get your ubuntu machine to download it, when your machine has no net... **pointless much**
Go to here, [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html) here you'll get a Front End for wine called PlayOnLinux in a easy to install .deb package and theres also packages of wine for the PlayOnLinux Front End to install, play on linux can take you through it step by step....

---

### Post by ApOgEEs on 2011-05-25
Running command:
```
$ lspci
```
will show what kind of wireless adapter you are using. Paste output of the above command here. Hopefully, we can sort out how to make your device work in ubuntu.

---

### Post by Perkomate on 2011-05-26
it's a Broadcom 4322AG 802.11. I didn't use the code, I just used hardware manager. All this model of netbook have this problem, I have the Windows driver, all I need to do is get Wine working so I can install it.

---

### Post by ApOgEEs on 2011-05-26
If you want to install WINE, I suggest, you plug your laptop with wired ethernet and then follow this instructions:
[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

If you want to make your wireless card working, consider reading this thread:
[http://ubuntuforums.org/showthread.php?t=1380560](http://ubuntuforums.org/showthread.php?t=1380560)

---

### Post by Perkomate on 2011-05-27
The wired ethernet port doesn't work either. I think that the driver drives everything to do with internet.

---

### Post by ApOgEEs on 2011-05-27
In order to install wine without internet connection, you have to download all required packages. Here is the steps:

[LIST=1]
[*]Find any computer which have internet connection and go to this site:
[http://apt-web.dahsy.at/](http://apt-web.dahsy.at/)

[*]Select your base distribution.

[*]Select the mirror to download

[*]Type 'wine' in the Packages field

[*]Click submit

[*]you will get a list of *.deb files to download. Download all of them.

[*]Open your ubuntu pc and install all *.deb files you just downloaded by double clicking on the file. You may follow the list order (on the apt-web page) from top to bottom.
[/LIST]

---

### Post by grahammechanical on 2011-05-27
I think that you are looking in the wrong direction. Please forgive me if you have already tried this and it failed. I think that you should be using something called ndiswrapper. It is designed to install and use Windows drivers on a Linux system.

Here is a link to Wireless Trouble shooting guide, if you do not have it.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

Regards.

---

### Post by Perkomate on 2011-05-29
I'm attempting to install ndiswrapper, can you have a look at what I'm doing to see what i'm doing wrong?
I downloaded it, put it on a USB and put it on the netbook. I then extracted it using the Archive Manager to a folder. I then opened Terminal and ran Documents/drivers/ndiswrapper-1.56 make
that did nothing. I then did the same thing, except with install. Still no luck. What am I doing wrong??

---

### Post by Perkomate on 2011-05-31
shameless self-bump. i need answers please!

---

### Post by ApOgEEs on 2011-05-31
I'm not clear how you run the command to make. Perhaps, you didn't do it right.

You suppose to 'cd' to the directory like this:
```
$ cd Documents/drivers/ndiswrapper-1.56 
```

then in the directory, you run make in the directory like this:
```
$ make
```

when successful, you should then do 'make install' with root privileges to install it.

You can find complete instructions here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Perkomate on 2011-05-31
wait, no. I did what you said and got the .deb files and installed wine. It installed fine, and I extracted the files from the .exe like it's meant to. But, when I tried to install the actual driver, it gave me an error. It was setup.rul 143, and caused the install of the driver to terminate.

---

### Post by Mark Phelps on 2011-05-31
Unless I missed it, apparently, no-one told you that you can NOT install MS Windows drivers using Wine.  Wine is used to allow SOME MS Windows programs to run by substituting Linux OS system calls for MS Windows OS system calls.  That has nothing whatsoever to do with MS Windows drivers.

NDISWrapper allows you to use MS Windows network drivers -- but it has nothing whatsoever to do with Wine.

And, any .exe file you get is most likely to be a self-extracting archive that is intended to run in MS Windows.

You need to get the proper networking drivers in their native MS Windows format -- an .inf file and a few driver (.sys) files.

---

### Post by Perkomate on 2011-05-31
ok. so, if I get the native friver files, NDISwrapper will run and install them for me?

---

### Post by Perkomate on 2011-05-31
when I tried to install NDISwrapper: i got the following errors:
error: unkwon field 'ioctl' specified in initializer:
then the following errors when Terminal tries to exit the directory:
error 1
error 2
error 2
error 2

---

### Post by ApOgEEs on 2011-05-31
I bet you already follow this instructions [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

However, in which part of the steps did you get the error?

---

### Post by Perkomate on 2011-06-02
it says error: unkown fiel 'ioctl' specified in the directory
warning: initialistaion from incompatible
make [3] ***(directory) error 1
make [2] *** error 2
make [2] leaving directory /usr/src/linux/Documents/drivers/ndiswrapper-1.56
make [1] *** [modules] error 2
leaving directory
make: *** [all] Error 2
 
please help!

---

### Post by ssreddy555 on 2011-06-02
This is not to install WINE, but to install wireless(wl)driver for Broadcom wl adopter. 
Ubuntu has almost all of the drivers in it to make all the devices work out of the box except the driver for Broadcom wl adopters.

Connect to internet with a wire or a wi fi USB adopter.

In the Terminal, copy & paste & enter the following codes one after the other:

```
sudo apt-get update
```

Then,

```
sudo apt-get install bcmwl-kernel-source
```

This will install the necessary driver for your wl adopter.

Next, go to  System > Administration > Hardware/Additional Drivers, then activate STA driver.

Your wl will be up & running.

Wired connection should work even without this driver. May be some other prob with your NIC if it's not working.

---

### Post by mastablasta on 2011-06-02
@ ssreddy555 - he can't connect to internet to use those commands. he says even wired conneciton does not work.
 
 
 
also forget about Wine for drivers...

---

### Post by Perkomate on 2011-06-02
yeah, the driver makes both the wired AND wireless ports work. At the moment I'm just trying to get ndiswrapper to work because i'm told that that's how the other guys with this model of netbook get it to work.

---

### Post by ssreddy555 on 2011-06-02
> **Perkomate said:**
> yeah, the driver makes both the wired AND wireless ports work. At the moment I'm just trying to get ndiswrapper to work because i'm told that that's how the other guys with this model of netbook get it to work.

 But, I think the drivers are different for the wired & wl; because, whenever I install a different version of ubuntu in my Lenovo netbook, I always have to install the STA driver for my Broadcom wl adopter, which is a proprietory driver & so doesn't come pre installed within the box, whereas the wired connection just works out of the box.

---

### Post by Perkomate on 2011-06-02
nope, my netbook is built a silly way. As I said before, all other people who have this model and put Ubuntu on it have the same problem. One of the guys I was reading about said that he used a USB modem, but unfortunately I don't have that luxury

---

### Post by mastablasta on 2011-06-02
yeah you could borrow a linux compatible Wi-FI USB key from someone to run those commands. though i am sure they are not so expencive- but still it would be silly to buy it if you actually have the chip for same function in computer

---

### Post by Perkomate on 2011-06-03
none of my friends have USB modems. Please please help me, i really need this to work as Windows 7 is just too slow on my netbook

---

### Post by Perkomate on 2011-06-08
shameless self bump yet again. I need answers.

---

