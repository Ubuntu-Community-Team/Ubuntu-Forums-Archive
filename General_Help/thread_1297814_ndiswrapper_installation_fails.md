---
title: "ndiswrapper installation fails"
date: 2009-10-22
forum: General Help
---

### Post by gigurra on 2009-10-22
Hi

I'm somewhat new to linux and Ubuntu.
I just installed it (64bit) on my home PC and I've run into
a problem. My wireless adapter is not supported, so I've 
been told I need to install ndiswrapper, however
this installation fails every time I try.

I don't have any internet connection at all from within linux,
since I'm entirely on wireless here, but i've used another
computer to download the packages described here in this thread:
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)

However when I try to run :
sudo dpkg -i ndiswrapper-common_1.54-1ubuntu1_all.deb I get the error
"dpkg: error processing ndiswrapper-common_1.54-1ubuntu1_all.deb (-- install): cannot access archive: No such file or directory".

I have both the common deb and the utils deb in this directory,
but it complains like the above.

I also tried doubleclicking/running the deb and it then asks
me if I want to install it, which I click yes to everything,
but then I get the error
"dpkg: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor"
The file even has rwx for all users so I dont know what 
could be the issue..

I've redownloaded the deb files of different versions even
but they all give this error. So I've run out of ideas.

ALl help greatly appreciated as this basically makes the computer
useless ...

---

### Post by gigurra on 2009-10-22
Ok i gave up the deb packages and downloaded the latest
source 1.55 from sourceforge and compiled it.

That worked. Then it installed the drivers for my wga311v3 
and it gave no errors. I got the Wireless icon up in Gnome, 
and I selected the network I wanted and typed the wpa key...
However, when I try to connect to the network
it just sits there and tries to connect
forever, and never actually connects. In fact this connection attempt even kicks other users off the wireless access point, 
they lose their connection

I have to disable the connection attempt to actually be able to 
reconnect with my laptop...

---

### Post by ajgreeny on 2009-10-22
You may have needed to use ```
sudo dpkg -i ndis*
``` from the folder where the packages were, assuming both package names begin with ndis, as I think they may both be inter-dependent, ie, you can't install either one without the other.  If they are named differently, you would need to add both package names to the command to install.

Also bear in mind that some netgear cards will not work with WPA, only with WEP, when using ndiswrapper.  I have one of them, unfortunately.

---

### Post by gigurra on 2009-10-22
> **ajgreeny said:**
> You may have needed to use ```
sudo dpkg -i ndis*
``` from the folder where the packages were, assuming both package names begin with ndis, as I think they may both be inter-dependent, ie, you can't install either one without the other.  If they are named differently, you would need to add both package names to the command to install.

Also bear in mind that some netgear cards will not work with WPA, only with WEP, when using ndiswrapper.  I have one of them, unfortunately.

I got around the ndiswrapper issue by building the source v1.55
instead of using the deb files (i never got them to work)

Still, I cannot connect to our WPA network. Could be that Netgear-
WPA bug then. I am able to connect to other networks that are not 
secured... Must be my lucky day.

I think I will just use my laptop as a router and plug a cable 
from the PC into it...as it is not possible to disable WPA on the
network here =/

Do you know of any wireless network cards and/or usb sticks that work
natively in ubuntu 64 without using ndiswrapper?

---

### Post by gigurra on 2009-10-22
MAY be solved...

I did some searching on wpa and linux and found something
called "wpa supplicant". I don't really understand what it does
but it would seem it is installed on Ubuntu by default, because
I followed the instructions here 
[http://www.linuxquestions.org/linux/answers/Networking/Netgear_WG511_v3_Made_in_China_with_WPA_on_Ubuntu_6_06_LTS_Dapper](http://www.linuxquestions.org/linux/answers/Networking/Netgear_WG511_v3_Made_in_China_with_WPA_on_Ubuntu_6_06_LTS_Dapper)
to create the wpa_supplicant config file like described.
Then I rebooted and to my big surprise...now it connects with
WPA to the network...

*totally confused BUT with working internet connection* :)
it seems to be going up, down, up down ...hehe
it doesnt say it goes down, but opening a new webpage goes very slow every now and then
(it looks like it doesnt lose connection if I have some keepalive going in the background,
or just a regular large file download will do the trick and the connection wont be interrupted)

---

