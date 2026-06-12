---
title: "Conecting your windows mobile phone to Ubuntu"
date: 2010-05-07
forum: General Help
---

### Post by nucleuskore on 2010-05-07
**This has been tested on Ubuntu Karmic, Lucid and Maverick, 32 and 64 bit versions, using the HTC ELF (running Windows Mobile 6).**

You will find many sites advising you on how to access/synchronise your windows mobile  with Ubuntu. This tutorial attempts to simplify the process of connecting your phone to your pc. You will be able to browse your phone filesystem and copy/paste files, and set up sync relationships. **What you will not be able to do is browse the internet on your phone through the usb cable.**

[list]
[*]Adding the required repository. Open a terminal (Applications->Accessories->Terminal) and type the following

[B]sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D246C25D
[/B]
and press ENTER.

[*]Now click on System->Administration->Synaptic
And in that, Settings->Repositories->Other Software

and add if you are running Ubuntu 10.04 (lucid) add these one at a time
**deb [http://ppa.launchpad.net/synce/ppa/ubuntu](http://ppa.launchpad.net/synce/ppa/ubuntu) lucid main**
**deb-src [http://ppa.launchpad.net/synce/ppa/ubuntu](http://ppa.launchpad.net/synce/ppa/ubuntu) lucid main**

If you are using Ubuntu 10.10 add these:
**deb [http://ppa.launchpad.net/synce/ppa/ubuntu](http://ppa.launchpad.net/synce/ppa/ubuntu) maverick main**
**deb-src [http://ppa.launchpad.net/synce/ppa/ubuntu](http://ppa.launchpad.net/synce/ppa/ubuntu) maverick main**
**deb [http://ppa.launchpad.net/opensync/opensync-0.22/ubuntu](http://ppa.launchpad.net/opensync/opensync-0.22/ubuntu) maverick main**

and click close and then the reload button.

[*]Now search for and install

[B]opensync-plugin-synce
synce-gvfs
synce-trayicon[/B]

and the dependencies that you are prompted to.

[*]After the install logout and then login. Now connect your phone via the USB cable. The icon should appear automatically near the clock and on your desktop. Right click on it for options to browse the filesystem on your device.[/list]

A few things that I learnt:
1. When you install the sync software you have to logout/login to make it work. I guess it's integrated with nautilus
2. I thought **synce-gnomevfs** would work, but it didn't, so I removed it through synaptic and used **synce-gvfs**, as above, and that worked for me.

I would really appreciate is someone could give me an idea on how to browse the internet on the phone through the USB cable connected to my desktop/laptop. I have read about network bridging, but /etc/network/interfaces does not even have eth0. I guess that is because these things are handled by network manager. Someone suggested to change the mode in eth0 (connected to the internet) from DHCP to shared with other computers. This does not work, as on reboot eth0 fails to take an IP by DHCP.

---

### Post by sylvester_0 on 2010-05-07
Connecting to the Internet through your phone (tethering) really depends on your carrier and your phone. Most likely you will be adding a new connection (Mobile Broadband) through the network manager. If you can find PPP instructions for your carrier+phone that will work with Windows most likely they could be adopted to Linux fairly easily.

Also, if your phone has WiFi there are Windows Mobile apps out there that will turn your phone into an access point. This doesn't look attractive if you're running both devices off of battery but it may be easier than using USB/Bluetooth etc.

---

### Post by nucleuskore on 2010-05-07
You misunderstood.
I do not want to connect to the internet through my phone.

Let me give you can example. I have Kaspersky antivirus on my phone, and I want to update it. I normally use wifi. But if my phone is connected to my internet enabled pc, I can update Kaspersky without having to turn on the wifi in Windows. I want to be able to do this in Ubuntu.

---

### Post by sowjendra on 2010-05-18
[]("http://ubuntuforums.org/member.php?u=579183")Hi Nucleuskore,

Thank you for the help.. I have windows mobile which is running in version 5. I followed like what u said and installed the softwares. 

when I connect my mobile to PC, after 5 to 10 minutes my system gets hang.. there won't be any movement in my system. All  I need to do is restart (Cold boot) my system. Please help me out.

Regards

Surendra M

---

### Post by nucleuskore on 2010-05-18
Am afraid I do not really have the answer to that

---

### Post by nucleuskore on 2010-05-20
@sowjendra

I have a suggestion, in the settings of your windows mobile phone go to usb to pc connections and uncheck advanced functionality, and restart your phone. Now try to connect to your ubuntu via usb.

---

### Post by sowjendra on 2010-06-01
I Think your suggestion has helped me out .. now my system din't stoped .. 

Thank you for your valuable suggestion .. 

and will you please explain me why this has happend .. 

Regards

M. Surendra

---

### Post by sowjendra on 2010-08-01
Hi Nucleuskore,

Sorry to disturb once again, I was happy with your suggestions. Today when i tried to copy some files to my mobile .. after copying some files connection was disconnected and connected automatically, it is not allowing to copy files

It displays

The folder contents could not be displayed.
Sorry, could not display all the contents of "Filesystem": An unspecified failure has occurred.

When I restart the system for some time the process goes and once again lands up with the same error

please help me out.

Regards
M.surendra

---

### Post by nucleuskore on 2010-08-01
I haven't faced this problem and so am not in a position to help. Sorry.

---

### Post by Zumilandi on 2010-08-01
At your first step I already have a problem. I get:

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu --recv-keys D246C25D
gpg: requesting key D246C25D from hkp server keyserver.ubuntu
gpgkeys: HTTP fetch error 6: Couldn't resolve host 'keyserver.ubuntu'
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0


Any ideas?

---

### Post by nucleuskore on 2010-08-02
Sorry there was a typo, I fixed it, try again

---

### Post by Zumilandi on 2010-08-02
So the key works...but still no syncing.  The PPA doesn't even show up in the software center, so it makes me wonder if it is working.

---

### Post by Zumilandi on 2010-08-07
Now the PPA is updating, but still no sync to my phone.

---

### Post by maiemi on 2010-12-20
Dear nucleuskore,

thank you for this article to connect a windows mobile phone to ubuntu.

I am using ubuntu 10.4 and installed the packages you suggested.
The connection works fine, but there is no way to synchronisize my windows mobile (6.5) phone with evolution.

I am using kde4 desktop and synce-kpm (correctly I am using both, the synce-kpm program and the gnome-synce-icon, both are working)

I can see the files on my Phone and the software, installed on my phone and I can press the "Sync" Button in Synce-kpm and the synce-process is running.

But there are no data synchornisized in my evolution and none on my phone, too.

In an other article, I read, that the opensync-package for ubuntu 10.4 is broken.

When I am installing the "opensync-plugin-synce", the installation is finished without any failures, but when I want to configure a member to my Sync-Group with the plugin, I only get the message: opensync-plugin-synce not found.

So what can I do to become synchronisizing my Mobile Phone (HTC) with Evolution work ?

Thank you for helping and please excuse  my bad English, I am a German....

greetings,

maiemi

---

### Post by nucleuskore on 2010-12-20
I too am having issues on Ubuntu 10.10. Am afraid I do know how to solve your problen

---

### Post by maiemi on 2010-12-21
sorry, I am not using Ubuntu 10.10 (maverick), but 10.4(Lucid) 64 Bit
If I read your thread attended, it is the same version, your are using, so my last hope is you can help me out.

It is very difficult to find a description, how to get a successful connection on Ubuntu 10.4 to synchronisize a windows mobile phone with evolution. At the German Forums, too.

I spent a lot of time to crawl the web to find a solution and your article is the nearest to the solution.

In Ubuntu 10.10. the package msynctools is no longer available, the new package is opensync. This is the reason, I changed to Ubuntu 10.4, because some people writed that synchronisation between a windows mobile phone and evolution is possible.
But later, I read that it seemed that the opensync package is broken for Ubuntu 10.4.

I have installed opensync-plugin-synce, but when I want to configure a partnership between the created group  "Zuhause" with the opensync-plugin, I only get the message that the plugin cannot be found.

The evolution Plugin willl be found an can be configured, but not the opensync-plugin.

nucleuskore, please write down your installed packages (and the sources) and how you did configure these to synchronisize your windows mobile phone with evolution.

Thank You very much,

maiemi

---

### Post by nucleuskore on 2011-02-05
Original post updated for maverick

---

### Post by fernandofat on 2011-02-11
Hi, I have Ubuntu 10.04.

I followed the instructions above and it worked as charm. My goal was to simply copy music to the Motorola Q11.

It works for me.

Thanks nucleuskore.

---

### Post by Joe325 on 2011-05-04
This is the post Ive been looking for. Well done - worked like a charm

---

### Post by wirelesscity on 2012-03-17
Shop for cell phones, cell phone plans, prepaid phones, free phones, iphone, android,virgin mobile,wireless pc cards, blue tooth headsets at wirelesscitystore. [http://www.wirelesscitystore.com](http://www.wirelesscitystore.com)

---

