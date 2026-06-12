---
title: "bcmwl kernel module failed to build"
date: 2010-07-24
forum: General Help
---

### Post by wobert on 2010-07-24
Hello I got some weeks trying to connect my M4400 dell to the internet without success. 
Ubuntu 10.04 @64 bits was installed.

These is the information from my network card:

   0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
  0c:00.0 0280: 14e4:4315 (rev 01)


I followed the instruction from these threads but can not make it to work.  

[http://ubuntuforums.org/showthread.php?t=1368699&highlight=14e4%3A4315](http://ubuntuforums.org/showthread.php?t=1368699&highlight=14e4%3A4315)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)


Additional, since I tried 

echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist


I can not see anyomore at the desktop toolbar the wireless connection option ...


Hope anyone can help me, thanks

---

### Post by mikewhatever on 2010-07-24
You shouldn't have needed to do any of that, instead, just hook up an ethernet cable, then open System->Admin->Hardware-Drivers.

---

### Post by wobert on 2010-07-24
by doing that, I have a list of two items:

1 broadcom B43 wireless driver
2 wireless controller broadcom STA

When I press to activate, both display errors

For 1, the isntallation of the controller failed, review the register file to see more details :
/var/log/jockey.log

For 2, SystemError:installAarchives()failed

---

### Post by mikewhatever on 2010-07-24
Perhaps you could post the jockey.log for review. I suspect you may have done a bit too much blacklisting and hacking.
```
cp /var/log/jockey.log ~/Desktop/jockey.log.txt
```

The command will copy the log to your desktop. If possible, attach it to your next post.
Edit: Fixed the command.

---

### Post by wobert on 2010-07-24
Hello Mike, thanks for your reply.
I pasted your command at the terminal, it displays me that it did not found the file or directory. I am at my user home folder, should I move to another one ?

---

### Post by mikewhatever on 2010-07-24
There was an error in the command, should work now.;)

---

### Post by wobert on 2010-07-24
Just tried again, an error occur 

could not create the regular file, does not exist the file or directory  

:(

---

### Post by mikewhatever on 2010-07-24
Odd, as I actually checked the command on my computer. Perhaps you don't have the jockey.log file. Let's check:
```
ls /var/log/ | grep jockey
```

---

### Post by wobert on 2010-07-24
Here the result

jockey.log
jockey.log.1
jockey.log.2.gz

---

### Post by mikewhatever on 2010-07-25
Well, the files are there, let's use a Gedit text editor to save them.
```
gedit /var/log/jockey.log
gedit /var/log/jockey.log.1
```
Use the 'Save as' dialog to save them to the desktop.

---

### Post by wobert on 2010-07-25
Hello Mike,

For the first file, jockey.log, a window prompt when I was about to save the data it closed and at the terminal it displayed this message:
   Gtk:ERROR:/build/buildd/gtk+2.0-2.20.0/gtk/gtkfilesystemmodel.c:330:node_set_visible: assertion failed: (row < model->files->len)


I am attaching you the file jockey.log.1


I really appreciate your help, thanks

---

### Post by mikewhatever on 2010-07-26
There is nothing particularly interesting in the log you posted. The last entry is from July 24, 11:17, so I am not quite sure it's relevant, also searching the log for errors from post #3 returns no results. I suspect you'll need to post a more recent log.

---

### Post by wobert on 2010-07-26
I retried by going to the controller activation, I was able to open the jockey.log file!

hopefully you find something interesting, 

thanks

---

### Post by wobert on 2010-07-26
could not attached it on the previous post because I was editing
here the attachment

---

### Post by mikewhatever on 2010-07-27
No, this log doesn't reveal much either, at least to my unexperienced eye. I was hoping there would be some explicit info about installing and failing, but it's not there.
Let's backtrack to post #1. It looks like you've tried installing the STA driver, Ndisrapper, and then b43. Obviously, the tree can not happily coexist. The output of the command below should show which of the three are still installed.
```
dpkg -l | grep -i 'bcmwl\|ndiswrapper\|b43'
```

---

### Post by wobert on 2010-07-27
Here the response:

   ii  b43-fwcutter                         1:012-1build1                                   Utility for extracting Broadcom 43xx firmwar
iF  bcmwl-kernel-source                  5.60.48.36[FONT=&quot]&#28119;[/FONT]0ubuntu3                       Broadcom 802.11 Linux STA wireless driver so
ii  bcmwl-modaliases                     5.60.48.36[FONT=&quot]&#28119;[/FONT]0ubuntu3                       Modaliases for the Broadcom 802.11 Linux STA
ii  ndisgtk                              0.8.5-1                                         graphical frontend for ndiswrapper (installa
ii  ndiswrapper-common                   1.54-2ubuntu1                                   Common scripts required to use the utilities
ii  ndiswrapper-utils-1.9                1.54-2ubuntu1                                   Userspace utilities for the ndiswrapper Linu

---

### Post by mikewhatever on 2010-07-27
Great, you have all of them installed. Remove all but bcmwl-...
```
sudo apt-get --purge autoremove b43-fwcutter ndiswrapper-common ndiswrapper-utils
```
Post the output of that please.

---

### Post by wobert on 2010-07-27
Displays:

E: Uknown option from the line of order ´p´ [from -purge]

---

### Post by mikewhatever on 2010-07-27
> **wobert said:**
> Displays:

E: Uknown option from the line of order ´p´ [from -purge]

Fixed the command, try it again.

---

### Post by wobert on 2010-07-27
Let me know if I press Yes
here the message:

The package ndiswrapper-utils is not installed, will not be eliminated

The following packages will be eliminated:

b43-fwcutter* ndisgtk* ndiswrapper-common* ndiswrapper-utils-1.9*

total of 1229kB after this operation

  want to continue y/n

---

### Post by mikewhatever on 2010-07-27
Yes, please proceed. When done reboot the computer, and hopefully, the wireless will just work.

---

### Post by wobert on 2010-07-27
Wireless is not working.

An error message was displayed:

Failed the installation of updating the package bcmwl-kernel-soruce

---

### Post by mikewhatever on 2010-07-27
Try removing the bcmwl-kernel-source package and then reinstalling it.
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get install bcmwl-kernel-source
```

---

### Post by wobert on 2010-07-27
Do not have wireless :(

I plug the ethernet cable , went to system, adm, hardware controllers

the list is now only for one item, and is the wireless broadcom STA controller
tried to activate it but fail

---

### Post by mikewhatever on 2010-07-27
Activating the driver from the Hardware Drivers GUI is the same as installing the bcmwl-kernel-source package. Have you run the commands to remove and reinstall the package? Please try again and post the outputs.

---

### Post by wobert on 2010-07-27
I am attaching you the messages after installation

the system was setup in spanish, please let me know if you need me to translate something

thanks

here goes everything again

---

### Post by mikewhatever on 2010-07-27
Hm..., not sure now. The module fails to build, I don't know why.
Let's try the following:
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get clean
```

Then reboot, connect the cable and try installing again:
```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by wobert on 2010-07-27
:(

I really appreciate your help 
I am very interested on using only ubuntu

---

### Post by mikewhatever on 2010-07-27
Didn't help, there is still a building error. :confused:
```
Building only for 2.6.32-21-generic
Building for architecture x86_64
Building initial module for 2.6.32-21-generic
/usr/sbin/dkms: línea 35: patch: orden no encontrada
Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error al procesar bcmwl-kernel-source (--configure):

```

The only thing I can think of now is purging the package, then updating the system with the Update Manager and then trying again. The current kernel version in Lucid is 2.6.32-24 and I just hope the module is going to build with that kernel.
Accidentally, I have exactly the same card, but running 32bit Ubuntu.

---

### Post by wobert on 2010-07-27
shoud I reinstall everything again?

I need the 64 bit so it can use the 8 gigas of ram and I want to do CAD work...

I will appreciate if you have more ideas , 

let me know the commands if possible please, I am new at linux and just started to learn

thanks

Just tried a couple of more times as you mentioned but did not work :(

---

### Post by mikewhatever on 2010-07-27
Reinstalling is also an option, but if you do, go straight for the graphical Hardware Drivers utility and get either STA or b43. I've used both drivers on Lucid and Karmic, and both worked.

---

### Post by wobert on 2010-07-27
now reinstalling...

hopefully it will work! :)

---

### Post by wobert on 2010-07-28
Reinstall ubuntu, have not been able to connect to the network.

Take a look to the first trial:

   wobert@wobert-laptop:~$ dpkg -l | grep -i 'bcmwl\|ndiswrapper\|b43'
ii  bcmwl-modaliases                     5.60.48.36+bdcom-0ubuntu3                       Modaliases for the Broadcom 802.11 Linux STA
wobert@wobert-laptop:~$

Going at system, adm, hardware drivers 
it did not found any, "no proprietary drivers are in use on this system"

---

### Post by mikewhatever on 2010-07-28
> **wobert said:**
> Reinstall ubuntu, have not been able to connect to the network.

Take a look to the first trial:

   wobert@wobert-laptop:~$ dpkg -l | grep -i 'bcmwl\|ndiswrapper\|b43'
ii  bcmwl-modaliases                     5.60.48.36+bdcom-0ubuntu3                       Modaliases for the Broadcom 802.11 Linux STA
wobert@wobert-laptop:~$

Going at system, adm, hardware drivers 
it did not found any, "no proprietary drivers are in use on this system"

Is the ethernet cable connected? The Hardware Drivers needs to contact the repositories and download the packages.

---

### Post by wobert on 2010-07-28
yes it is plugged, no options at the list 


I can not configure the ethernet connection because I do not know the mac address ...

---

### Post by mikewhatever on 2010-07-28
Isn't it the same wired connection you used yesterday? I don't know your setup, but it sounds odd that you can't configure something that was in use less then a day before.:confused:

---

### Post by wobert on 2010-07-28
It is the same cable 
 
I did two reinstallations because I forgot to disconnect the cable
When I left the ethernet cable plugged at the very end of the installation the black screen displayed some notifications (not sure if errors because it lasted few seconds only) I was able to read something related to the network card ...
 
went to the graphical menu, no items listed to install...
 
Then I disconnected the cable, reinstall ubuntu, at the very end of the installation the black screen showed several more messages (very different) , not sure if related to the network card , I could only notice that it refer to a website to be checked and recommended to follow instructions... Went again to the graphical menu to check for hardware drivers once I plugged the cable, the result was the same.
Then I started some combinations, plugging, unplugging, moving the wireless network switch, nothing made the list change

---

### Post by wobert on 2010-07-28
I setup the 32 bit version and happens the same, can not connect either via ethernet nor wireless.

:(

More Ideas?

---

### Post by mikewhatever on 2010-07-28
How did you get the wired connection working before?

---

### Post by wobert on 2010-07-28
I honestly doubt that it worked...
If it was working just because it was displaying the couple of options of hardware drivers then nothing special was done, just plugged the ethernet cable (as now)

Could those drivers be displayed by the installation of some of the files from the links of post 1 ?

---

### Post by mikewhatever on 2010-07-29
The wired connection did work before, at least according to one of the logs you posted, where the package we wanted is downloaded.
Try putting the live cd into the tray, add it to software sources using System->Admin->Software Sources, and then try installing bcmwl-kernel-source.
```
sudo apt-get install bcmwl-kernel-source
```
It used to work with Karmic, as the package was on cd, but I am not sure it still works with Lucid.

---

### Post by wobert on 2010-07-29
wobert@wobert-laptop:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for wobert: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot patch
Suggested packages:
  diffutils-doc
The following NEW packages will be installed:
  bcmwl-kernel-source dkms fakeroot patch
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1,205kB of archives.
After this operation, 3,764kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/restricted bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu3
  File not found
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main fakeroot 1.14.4-1ubuntu1
  File not found
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/ lucid/main patch 2.6-2ubuntu1
  File not found
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/restricted/b/bcmwl/bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb  File not found
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/f/fakeroot/fakeroot_1.14.4-1ubuntu1_i386.deb  File not found
Failed to fetch cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/pool/main/p/patch/patch_2.6-2ubuntu1_i386.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
wobert@wobert-laptop:~$

---

### Post by wobert on 2010-07-29
after rebooting now the hardware drive manager shows broadcom b43 and sta wireless drivers
tried activating the b43 and guess what ?  it displayed
sorry installation of this driver fail
please have a look at the log file for details /var/log/jockey.log

(I connected the ethernet cable..)

---

### Post by P4man on 2010-10-15
There are licensing issues with the broadcom firmware which is needed for those drivers to work, so they cant be provided out of the box. But this howto should get you going:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by wobert on 2010-10-28
Sorry for my late response, I was waiting on the other thread.

Should I install the STA drivers and the b43 drivers or just one of it?

thanks

---

### Post by P4man on 2010-10-29
Just one (the STA driver probably)

---

### Post by wobert on 2010-10-30
YES!!!!!!!!!!!!!!!!!!!!!!!!!!

IT IS WORKING PERFECTLY!!!

I feel great after the dvd was not giving me access to the files but I made it happen with the usb.  It was very strange that  I could not get through the terminal to the folders of the dvd and the name I was putting is what it is stating on the properties ....

I will continue with the missing installation of the other thread.

THANK YOU VERY VERY VERY MUCH!! Is there a way I can rank or provide good feedback to you?

good bye windows, finally I can say it!

---

### Post by P4man on 2010-10-30
> **wobert said:**
> YES!!!!!!!!!!!!!!!!!!!!!!!!!!

IT IS WORKING PERFECTLY!!!

Glad to hear at least someone gets his wifi trouble solved :)

> THANK YOU VERY VERY VERY MUCH!! Is there a way I can rank or provide good feedback to you?


Nope, but you can mark this thread as "solved" in thread tools, making it easier for others to find the solution.

---

