---
title: "Help reinstall network manager with no Internet connection"
date: 2011-10-26
forum: General Help
---

### Post by mark111 on 2011-10-26
Boy did I get myself in a pickle.  Trying to install the latest version on PERL LWP resulted in the inadvertent removal of the network manager.  No worries - I will just reinstall - oops, no Internet connection.  So begins the saga.  I have tried two different approaches to reinstall and am stuck on both:

1.  I downloaded the tar file for the network manager, and edited the file sources.list as described in [http://ubuntuforums.org/archive/index.php/t-286445.html](http://ubuntuforums.org/archive/index.php/t-286445.html) with the addition of the line deb file:/home/tmp at the end of the file.  This crashed out with the error 'malformed line' in the line I added to that file and then entered sudo apt-get update.  I have looked around for a better description of how to fix this file to no avail.

2.  I downloaded network-manager-gnome.deb and double clicked on that, which launched gdebi.  This also required reverting to the old version of sources.list for the same reason as above.  This would not complete the installation because it wanted to download three files from the Internet (which, of course, I don't have access to...even when connected by cable).

So, I feel as if I have done a fair bit of work but am now stuck.  Can someone please help?

Btw, the problem I was trying to solve was to enable a script for Amazon Simple Email Service, which in turn required PERL version 6, but the installed version in the synaptic package manager was version 5.x.  Once I have a network connection I will have to figure out how to update LWP...but first things first.

---

### Post by oldtimer7777 on 2011-10-26
Did you use your rescue disk to repair your system? There is a reason everyone is supposed to have one in case of emergency. Otherwise you are going to need to make one.

> **mark111 said:**
> Boy did I get myself in a pickle.  Trying to install the latest version on PERL LWP resulted in the inadvertent removal of the network manager.  No worries - I will just reinstall - oops, no Internet connection.  So begins the saga.  I have tried two different approaches to reinstall and am stuck on both:

1.  I downloaded the tar file for the network manager, and edited the file sources.list as described in [http://ubuntuforums.org/archive/index.php/t-286445.html](http://ubuntuforums.org/archive/index.php/t-286445.html) with the addition of the line deb file:/home/tmp at the end of the file.  This crashed out with the error 'malformed line' in the line I added to that file and then entered sudo apt-get update.  I have looked around for a better description of how to fix this file to no avail.

2.  I downloaded network-manager-gnome.deb and double clicked on that, which launched gdebi.  This also required reverting to the old version of sources.list for the same reason as above.  This would not complete the installation because it wanted to download three files from the Internet (which, of course, I don't have access to...even when connected by cable).

So, I feel as if I have done a fair bit of work but am now stuck.  Can someone please help?

---

### Post by mark111 on 2011-10-26
This machine does not have a CD drive, but is dual boot.  I can access the Internet or network from the Windows side, but not a CD.  I could set up a thumb drive, but I have no desire to reinstall ubuntu in total just to reinstall a single package...

Thanks, and ideas gratefully received...

---

### Post by garvinrick4 on 2011-10-26
```

locate network-manager
```what you got in .deb still in cache?
> 
 I can access the Internet or network from the Windows side,
What about going in launchpad.net already built in .deb for packages you need download from windows to flash drive and install in your linux installation.
Drop .deb on Desktop:
```
cd Desktop
```
```
ls
```
Make sure only .debs you need on desktop
```
sudo dpkg -i *.deb
```

---

### Post by oldtimer7777 on 2011-10-26
You need a resque disc/USB live stick of Ubuntu pre made. Everyone who uses Linux as their only system with one partition of it, need to have one on hand. I can't help you without one. It might not require a reinstall, but without a way to readd that packge you need, you are out of luck. If you had a resque live stick of Ubuntu you can easily readd the package you want with Synaptic package manager, and mounting that USB stick of Live ubuntu..   If you want it done right, that is how it is supposed to be done.

---

### Post by mark111 on 2011-10-26
Heaps od network-manager files under locate since I had already uncompacted a tar ball but no .deb.  I am trying the download of the .deb from the mirror now - takes a bit since I have to reboot into win and then back...

Good suggestion - will come back to you with results...

---

### Post by oldtimer7777 on 2011-10-26
create a live stick of Ubuntu..

mount it to your broken ubuntu..

open synaptic.. and add volume 

then reinstall anything missing since it is like having your own personal repository attached directly to your USB....  that is how you fix this kind of issue with anything like this. . Always have resque disc/usb live stick on hand. You never know. :) 
> **mark111 said:**
> Heaps od network-manager files under locate since I had already uncompacted a tar ball but no .deb.  I am trying the download of the .deb from the mirror now - takes a bit since I have to reboot into win and then back...

Good suggestion - will come back to you with results...

---

### Post by mark111 on 2011-10-26
So downloading network-manager-pptp...deb did not work as I was informed a later version of this package was already installed.   I went back to the Packages site and the network-manager itself does not have a .deb that I can find.  Network-manager-gnome....deb does exist as a separate package, and I have already tried I stalling that but it couldn't get access tot the internet to download required files.  Which is a bit annoying since i am pretty sure I have all the required files on the hard drive, just not installed correctly or I the right order.

If I could just install the tar.gz file that I do have avaiable...

You guys are really helping...thanks...

---

### Post by oldtimer7777 on 2011-10-26
> **mark111 said:**
> So downloading network-manager-pptp...deb did not work as I was informed a later version of this package was already installed.   I went back to the Packages site and the network-manager itself does not have a .deb that I can find.  Network-manager-gnome....deb does exist as a separate package, and I have already tried I stalling that but it couldn't get access tot the internet to download required files.  Which is a bit annoying since i am pretty sure I have all the required files on the hard drive, just not installed correctly or I the right order.

If I could just install the tar.gz file that I do have avaiable...

You guys are really helping...thanks...

Mount a stick of Ubuntu that has the package you need to reinstall.. You can even just do 
sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

and anything else you want to reinstall that you might have accidentally removed from your system... But you can't just install over what is missing, like you are imagining... You need to uninstall the configuration settings and everything first. Order of operation is important when it comes to repairing something like this.

To mount the live stick of Ubuntu:

sudo synaptic

Then use "add volume" and select your USB stick of Ubuntu with the packages you need to "reinstall".

---

### Post by garvinrick4 on 2011-10-27
64 bit on bottom left .deb build 0.9.1.90
[https://launchpad.net/ubuntu/+source/network-manager/0.9.1.90-0ubuntu4/+build/2842294](https://launchpad.net/ubuntu/+source/network-manager/0.9.1.90-0ubuntu4/+build/2842294)

32 bit on bottom left .deb
[https://launchpad.net/ubuntu/+source/network-manager/0.9.1.90-0ubuntu4/+build/2842296](https://launchpad.net/ubuntu/+source/network-manager/0.9.1.90-0ubuntu4/+build/2842296)

---

### Post by mark111 on 2011-10-27
So, you guys have been really helpful, and I am still in the poo.  I have tried both methods recommended here:

1.  Old-timer recommended creating a boot flash drive and using that as an off-line source for the network manager.  I have done that using an old laptop, and now have a 9.10 bootable flash drive.  In synaptic, though, I see no 'add volume' option in the package manager.  Under Settings>Software Sources (which is what I assumed you meant), there is no option for a flash/media drive.  There is an option for 'installable from CD-ROM/DVD' under Ubuntu Software.  Under Other Software I can add, but only an APT line not a directory, and adding a directory address leaves the 'add' button greyed out.  And, there is a button for Add CD-ROM, but again the back-up is a flash drive.  Finally, there is File>Generate Download Script, but that requires navigating to a particular directory, which I don't know where all of the necessary files are for re-installing.

2.  Garvinrick made my day with the location for the network-manager .deb file.  I downloaded that and then installed by double clicking with GDebiKDE.  This said I was missing a dependency.  So I went and found that .deb file, double clicked that one, and found I was missing another dependency.  This went on for a while until installing a dependency did not allow the next file in the chain to be installed.  Playing around with various versions of the problem file (the problem file turns out to be libsnpr4, on which libnm-util2 depends) did not solve the problem.

So, guys, I remain grateful for your advice but am still stuck...

Cheers...

---

### Post by mark111 on 2011-10-27
Are you guys still out there?

---

### Post by varunendra on 2011-10-28
What is the line that you tried to add as a software source in order to add your flash drive as a source?

I just tried to add mine (which is mounted at /media/storage, "storage" is its label) and the "Add Source" button came alive. The line I am adding is: ```
deb /media/storage natty
```So it seems your line may not have been in accordance with the correct syntax which is: > <package type> <location> <distro> <category (not necessary)>Alternatively, you can download wicd/nm and their dependencies from here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

But adding your flash drive as repo should not be easier.

As another (a bit complex, but may be very-very useful) approach would be to boot into live session, then 'chroot' into the installed one to repair/install/reinstall packages on it. I haven't tried it yet, but its description suggests it can prove to be an ultimate magic wand in case of similar 'broken' system problems.

---

### Post by mark111 on 2011-10-28
Boy, I am in trouble and I appreciate your help.  Yikes.

So, with regard to these suggestions:

1.  Offline repositories I have been able to make work, but network-manager isn't on it.  I used system>administration>software sources (which is the same as Settings>Repositories in Synaptic.  I could point to the boot USB using file:/media/usbdisk under Other Software Sources>Add.  There are packages that I could install, just network-manager isn't one of them.  When I opened dists/lucid/main/binary-i386/packages.gz on the back-up disk using gedit and then search there is no mention of network-manager.  Shoot.

2.  Installing wicd was a really good idea, which I had also thought of.  Wicd does not have a .deb, unfortunately, but there is tar.gz available.  I installed that one, first not understanding that I needed to do it at the root and not as a user; no matter, I uninstalled as a user and re-installed at root.  Still no joy, and I am not sure why.  Typing wicd at the root gets a message saying wicd is currently not installed.  Going to the wicd directory at the root and typing start wicd gets start: unknown job: wicd.  Hmmm.  I may not have got the wicd inserted properly into the start-up scripts, but I thought if I could just invoke the package manually then I could go through repair and installation processes using apt-get when I had an Internet connection, but I still can't connect.  I also checked the dependencies in the install file, and I think I have them all - the install document is a bit vague.  In any case, I am running 10.04, so I am pretty much up-to-date.  Bummer again.

3.  Booting from the USB back-up seems a very sensible idea, but I must have messed something up while trying to fix this, and I am seriously concerned.  Ubuntu will boot, it will read the USB stick, and in point 1 above I was able to read the repositories.  But when I try to boot to USB I get a BIOS error that I need to install a bootable device.  The USB is OK, though, because I can boot from it on other machines.  Boy is this a bit of concern.  Bummer a third time.

Any ideas welcome...

---

### Post by varunendra on 2011-10-29
I just did an experiment (removed nm, got disconnected and configured eth0 manually) based on some obvious facts and with its success I've something more to suggest. However, I am assuming you have a wired connection. For wireless, something more can be required.

Boot into windows and note down the IP of your computer. Then boot into Ubuntu and do this:
```
sudo ifconfig eth0 192.168.1.22
```(assuming your ethernet interface is eth0. Change the IP with yours)

This should get you connected to your network. Now assuming you have DHCP enabled on your network, just make a DHCP request:
```
sudo dhclient
```....and you are connected to the internet.

However, if you can not have a wired connection, or have no DHCP enabled on the network, a few more steps would be required, but I think this approach should get you connected.


**_EDIT_:**
Actually, if DHCP is enabled on the network, only *sudo dhclient* command is sufficient. It also picks up the IP address for you. However, the target interface needs to be activated first (which automatically gets active if you assign an IP to it manually). To activate it: ```
sudo ifconfig eth0 up
``` (assuming the name of interface is eth0. You should change it as per yours). Then, to get connected: ```
sudo dhclient
```.

So even this way you have to supply two commands to get it connected. The benefit is that you don't have to know or guess the IP to be assigned, it is taken care of by the DHCP.

For non-DHCP network, please see 'Edit' of post#17. For manual configuration of wireless, follow the link in post #17.

---

### Post by mark111 on 2011-10-29
Varun:

You are my hero!  Fantastic, and so easy.  I really appreciate you and are sending you warm thoughts.

For posterity, merely connecting my laptop to the router was not sufficient for the router to assign an IP address.  Using another machine it was easy enough to get the DHCP client list and determine that the router would assign the next IP address to my laptop when it got connected.  So, the commands above where 

sudo ifconfig eth0 192.168.1.102

After the dhclient I was able to ping Yahoo.com and was away.  Reboot was required, as running nm-applet before reboot yielded errors, but network-manager ran automatically on re-boot.

Also, Varun, I was able to boot from USB after revising my BIOS settings, but that turned out to be unnecessary after your very easy fix.

---

### Post by varunendra on 2011-10-29
Wow! A really nice beginning of the day :)

Thanks for all those generous regards. But actually, I think I was rather stupid for not being able to think of such an obvious solution before. However, it's a consolation to know I was not alone.... Even experts like *garvinrick4 *and *oldtimer7777 *were with me on the line :lolflag:
Maybe because at times our brains get biased to see problems as 'complex ones' while they may not be.. ;)

Anyway, for those who have to deal with wifi: [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)



**_EDIT_:**
Forgot these-
Those who have a wired connection, but do not have DHCP enabled, it is only IP, Gateway and DNS that need to be manually supplied to the interface (subnet mask is picked up automatically based on your IP).

[LIST]
[*] For IP: ```
sudo ifconfig <IP address>
``` (eg- *sudo ifconfig 192.168.1.20*)
[/LIST]

[LIST]
[*] For Gateway: s```
udo route add default gw <IP of your gateway>
``` (eg- *sudo route add default gw 192.168.1.1*)
[/LIST]

[LIST]
[*] For DNS: Open resolv.conf file- ```
gksu gedit /etc/resolv.conf
``` and add this line > nameserver <IP of your preferred DNS server> (eg- *nameserver 4.2.2.2*)
[/LIST]

---

