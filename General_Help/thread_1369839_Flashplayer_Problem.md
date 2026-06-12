---
title: "Flashplayer Problem"
date: 2010-01-01
forum: General Help
---

### Post by Bradj47 on 2010-01-01
I can't see any flash widgets. I have this problem in both Firefox and Chrome. I found old solutions online but those were all for 7.10. I'm on 9.04. For example I can't see YouTube videos. There's just a blank space where a video should be. I've tried loading YouTube videos with flashplugin-nonfree installed and not installed. I'm not sure if I have the latest version of it or not. I'm just using whatever is currently in the 9.04 repos. (**sudo apt-get install flashplugin-nonfree**). Anyone know how to fix this?

---

### Post by markthefart on 2010-01-01
Had same problem in both Firefox and Chrome. You need to install the 64-bit flash player. Follow this guide: [http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/]("http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/")

---

### Post by Bradj47 on 2010-01-01
Even if I'm not using 64-bit Ubuntu? And by the looks of the tutorial it seems that it would only work on Firefox. Chrome is my default browser.

---

### Post by LuisGMarine on 2010-01-01
First I would remove all the flash plugins that you installed through the repos.  Easiest way is to open up your Add/Remove program by going to Applications > Add/Remove.. type in "flash" in the query and remove everything that is installed.  

After you have cleansed your system of all the flash plugins possible, head over to the adobe website and download and install the .deb for Ubuntu 8.04+.

[http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")

Doing this makes flash work in Firefox and Chrome, hopefully it will do the same to you without the need of doing any more configuration.

---

### Post by markthefart on 2010-01-01
Hmm, okay, I wasn't aware you had a 32-bit installation. From looking at your specs bellow your post, I thought you were running x64 Ubuntu. I've never heard of the buttons not working correctly on the 32-bit Ubuntu. Is it only in Chrome or in both Chrome and Firefox? You might want to try this tutorial. Looks like it might be more beneficial for you. [http://maketecheasier.com/enable-flash-support-in-google-chrome-in-ubuntu/2009/08/19]("http://maketecheasier.com/enable-flash-support-in-google-chrome-in-ubuntu/2009/08/19")
> **Bradj47 said:**
> Even if I'm not using 64-bit Ubuntu? And by the looks of the tutorial it seems that it would only work on Firefox. Chrome is my default browser.

---

### Post by running_rabbit07 on 2010-01-01
Flash will never work correctly for Linux.

---

### Post by Bradj47 on 2010-01-01
I open up the .deb for 8.04+ file at the link you gave me and it gives me this error: **[COLOR="Red"]Error: Cannot install 'libnspr4-dev'[/COLOR]**.

---

### Post by Bradj47 on 2010-01-01
> **markthefart said:**
> Hmm, okay, I wasn't aware you had a 32-bit installation. From looking at your specs bellow your post, I thought you were running x64 Ubuntu. I've never heard of the buttons not working correctly on the 32-bit Ubuntu. Is it only in Chrome or in both Chrome and Firefox? You might want to try this tutorial. Looks like it might be more beneficial for you. [http://maketecheasier.com/enable-flash-support-in-google-chrome-in-ubuntu/2009/08/19]("http://maketecheasier.com/enable-flash-support-in-google-chrome-in-ubuntu/2009/08/19")

Yes, I do have an AMD 64 processor but I'm running Ubuntu 9.04 32-bit because I wasn't aware my processor was 64-bit until I had installed Ubuntu 32-bit and started using it. 

I get an error when i try to run **sudo apt-get install flashplugin-installer** like it says in the tutorial. 
```

brad@rockstar:~$ sudo apt-get install flashplugin-installer
[sudo] password for brad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flashplugin-installer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flashplugin-installer has no installation candidate
brad@rockstar:~$ 

```

---

### Post by LuisGMarine on 2010-01-01
> **Bradj47 said:**
> I open up the .deb for 8.04+ file at the link you gave me and it gives me this error: **[COLOR="Red"]Error: Cannot install 'libnspr4-dev'[/COLOR]**.

All you need to do is open up a Terminal window ( Applications > Accessories > Terminal ) and type this in:

```
sudo apt-get install libnspr4-dev
```

And try to install the Ubuntu 8.04+ .deb.

---

### Post by markthefart on 2010-01-01
Try this:

First uninstall your current flash player:
If you install via apt-get
```
sudo apt-get remove --purge flashplugin-installer
```
or if you installed it manually:
```
rm -f ~/.mozilla/plugins/libflashplayer.so
```
and
```
rm -f /usr/lib/flashplugin-installer/libflashplayer.so
```
and
```
rm -f /usr/lib/adobe-flashplugin/libflashplayer.so
```
Then, open up a terminal and download the new flash player:
```
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p2_linux_121709.tar.gz
```
Next type
```
tar -xzf flashplayer10_1_p2_linux_121709.tar.gz
```
Create the directory, if it's not already created:
```
mkdir -p ~/.mozilla/plugins
```
Copy the file to that directory:
```
cp install_flash_player_10_linux/libflashplayer.so ~/.mozilla/plugins
```
Create the directory for Chrome:
```
sudo mkdir /opt/google/chrome/plugins
```
Copy the file in to that directory:
```
cp install_flash_player_10_linux/libflashplayer.so /opt/google/chrome/plugins
```
Copy the file also here:
```
cp install_flash_player_10_linux/libflashplayer.so /usr/lib/adobe-flashplugin
```
and here:
```
cp install_flash_player_10_linux/libflashplayer.so /usr/lib/flashplugin-installer
```

Hopefully that will work for you.

---

### Post by ajgreeny on 2010-01-01
It is also worth checking that you do not have gnash or swfdec installed as these will conflict with adobe flash.

@ running_rabbit07.
Flash in 32 bit 9.04 works perfectly for me so I don't think your comment is quite true.  OK many people have problems with flash, but either I  am just lucky with my hardware, not new by any means, or I just do things differently from most people, and use the package adobe-flashplugin in the canonical-archives repository.  It is a long time since I have had a big problem with flash!

---

### Post by running_rabbit07 on 2010-01-01
That is the one I have for 64 bit. Everywhere I look, I see "64 bit flash is still in beta", yet it works fine in Windows. Nothing like having to click pause ten times on youtube, before it actually works, if it works. Or making the video full screen just to have it go small moments later.

---

### Post by sigurnjak on 2010-01-01
I am running 64 bit flash from sevenmachine ppa and love it so far . Websites that would never render properly render great , full screen video works great .
But not all is well in 64bit flash .
1 Facebook Yoville for my wife is not working , i strongly believe it is game  and not flash . For here i have Seamonkey2 with flash 9 32 bit and it does job fine .

2 When i play music and browse and come across flash video it kicks out my music player (audcious or rhythmbox ) . In 32bit linux there is libflashsupport.so to fix it , but so far i have not been able to find one for 64 bit Karmic . 

If anyone have any trick up their sleeve let me know !:)

---

### Post by Bradj47 on 2010-01-01
> **LuisGMarine said:**
> All you need to do is open up a Terminal window ( Applications > Accessories > Terminal ) and type this in:

```
sudo apt-get install libnspr4-dev
```

And try to install the Ubuntu 8.04+ .deb.

I try: 
```

brad@rockstar:~$ sudo apt-get install libnspr4-dev
[sudo] password for brad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libnspr4-dev: Depends: libnspr4-0d (<= 4.7.5-0ubuntu0.8.10.1.1~) but 4.7.5-0ubuntu0.9.04.1 is to be installed
E: Broken packages

```

It says it depends on libnspr4-0d. So I try: 
```

brad@rockstar:~$ sudo apt-get install libnspr4-0d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libnspr4-0d is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

Which doesn't make much sense to me.

---

### Post by Bradj47 on 2010-01-01
> **markthefart said:**
> Try this:

First uninstall your current flash player:
If you install via apt-get
```
sudo apt-get remove --purge flashplugin-installer
```
or if you installed it manually:
```
rm -f ~/.mozilla/plugins/libflashplayer.so
```
and
```
rm -f /usr/lib/flashplugin-installer/libflashplayer.so
```
and
```
rm -f /usr/lib/adobe-flashplugin/libflashplayer.so
```
Then, open up a terminal and download the new flash player:
```
wget http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_p2_linux_121709.tar.gz
```
Next type
```
tar -xzf flashplayer10_1_p2_linux_121709.tar.gz
```
Create the directory, if it's not already created:
```
mkdir -p ~/.mozilla/plugins
```
Copy the file to that directory:
```
cp install_flash_player_10_linux/libflashplayer.so ~/.mozilla/plugins
```
Create the directory for Chrome:
```
sudo mkdir /opt/google/chrome/plugins
```
Copy the file in to that directory:
```
cp install_flash_player_10_linux/libflashplayer.so /opt/google/chrome/plugins
```
Copy the file also here:
```
cp install_flash_player_10_linux/libflashplayer.so /usr/lib/adobe-flashplugin
```
and here:
```
cp install_flash_player_10_linux/libflashplayer.so /usr/lib/flashplugin-installer
```

Hopefully that will work for you.

THANK YOU markthefart. As far as I can tell all flash now works for me. This has been a problem for me as long as I've had Ubuntu Jaunty. Thanks a lot.

---

### Post by marvin04 on 2010-07-18
> **LuisGMarine said:**
> First I would remove all the flash plugins that you installed through the repos.  Easiest way is to open up your Add/Remove program by going to Applications > Add/Remove.. type in "flash" in the query and remove everything that is installed.  

After you have cleansed your system of all the flash plugins possible, head over to the adobe website and download and install the .deb for Ubuntu 8.04+.

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Doing this makes flash work in Firefox and Chrome, hopefully it will do the same to you without the need of doing any more configuration.
 
this may sound stupid,, but i don't know how to go to add/remove programs in ubuntu.. its not in my application... hope you can help me here

---

