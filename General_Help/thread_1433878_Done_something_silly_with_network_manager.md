---
title: "Done something silly with network manager"
date: 2010-03-19
forum: General Help
---

### Post by tilii on 2010-03-19
Hi everybody, long time reader, first time poster.

I've been using Ubuntu on my Amilo laptop since Intrepid and have a dual boot wubi installation. Love it. I wish I'd discovered Linux earlier. The update to Jaunty went really well with no apparent problems but since updating to Karmic I've found that my Three E220 USB modem doesn't connect well and sometimes it takes 4 or 5 goes to get a connection.

Having viewed a few threads, there were various things to try out... I added a few more ntp servers and this seemed to help a bit with the initial connection but it still seemed to lose connection after a while (perhaps half an hour) for some reason.

Now to the silly part... Network manager was installed as default but I decided to tryout wicd to see if it made any difference.... only to find that it doesn't support dongles (yeah I know I should've checked) and therefore I've had to go back to Vista for the moment.

I downloaded the networkmanager tar.gz and had a go at installing that but i guess there's other dependencies I need coz I got an error when it needed intltool version 0.35.0 or better. I'm assuming there will be other files I need too... so will it be easier for me to use the wicd and "borrow" a wired or wifi connection and just reinstall networkmanager through synaptic? Or persist with the manual install of the necessary files?

Opinions greatly appreciated.

---

### Post by DawieS on 2010-03-20
I would recommend that you uninstall the following packages with Synaptic (mark for removal, not complete removal):

wicd
network-manager
network-manager-gnome

Now reboot to get rid of incorrect network settings in the system. Re-install the following with Synaptic to get back to your original configuration (they should still be there, you don't have to download them):

network-manager
network-manager-gnome

---

### Post by tilii on 2010-03-20
Thanks for the reply DawieS.

Both the network packages weren't installed as these were removed when wicd was downloaded.

Removed wicd and rebooted but there was no option to reinstall the network packages. They are currently in the uninstalled (residual config) section of synaptic.

You seemed confident that they should still be around... does that indicate further issues?

---

### Post by alexfish on 2010-03-20
Hi tilii

Hope you get NM reinstalled again

once this is achieved then the problem with the connection may be resolved by editing the ppp options file

Code:

sudo gedit /etc/ppp/options

Add this line and save:


replacedefaultroute

you may wish to add a comment above the entry as to why the line was added , precede the comment with a #

if you are really stuck then there is an alternate way of connecting by using the ppp details here , 
  	 	 	 	 	 	  
[LIST=1]
[LIST=1]
[*][Alternative 		Way 2 (using pppconfig & pon/poff)]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#Alternative%20Way%202%20%28using%20pppconfig%20&%20pon/poff%29")
[/LIST]
[/LIST]

---

### Post by tilii on 2010-03-20
Thanks for the link alexfish. that's a thread i hadn't found before. there seems to be a lot of different threads about the problem. some say it's to do with DNS settings... some the NTP (which as you know i updated.) Some say it is a known karmic issue with recent kernels as there were no problems in Jaunty.

I understand there is going to be a firmware update from Three for all their modems during March but it has to be done on Windows. Whether that will help things along remains to be seen.

---

### Post by alexfish on 2010-03-20
hi

The problems seems to be more persistent in karmic but from reading various post this has been a problem that exist in other versions of Ubuntu and different versions of linux.

when I mention problems , there is more than one issue that can happen , this can be the type of modem it's self , and the firmware as you mention, so obvious if the firmware has to be upgraded for windows then it would be understandable that there may be problems with linux

if after upgrading the firmware the problems still exits in linux then try the above in the options file, further to ,if this does not work please let know as there are other means of gaining a stable connection.


as a mater of interest which kind of modem are you using, also could your post the details of the output from the terminal with this command

Code:

lsusb

regards

alexfish

---

### Post by tilii on 2010-03-21
Here's the output of lsusb

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Still waiting for the firmware update.

---

### Post by phen0m on 2010-03-21
Still having issues installing NetworkManager?
You tried using a .deb package instead of a tarball?

[http://packages.ubuntu.com/source/karmic/i386/network-manager/download](http://packages.ubuntu.com/source/karmic/i386/network-manager/download)

---

### Post by alexfish on 2010-03-22
Hi tilii

Which model number is shown on the modem it's self

regards

alexfish

---

### Post by tilii on 2010-03-22
Its the E220... as mentioned in original post. Still no dates posted for the upgrade of this particular model.

[http://www.three.co.uk/Help_Support/Mobile_Broadband_Help](http://www.three.co.uk/Help_Support/Mobile_Broadband_Help)

In the meantime I going to try to go with my original idea of "borrowing" a wired or wifi connection as I would guess that should be relatively simple now that wicd is installed.

I've only ever used the dongle which suits my needs. I don't have any real requirement for speed so I'm interested as to how a different connection would work. I've never regarded the dongle as being particularly slow, in fact when everything's working well it's blinding despite what any technical figures may suggest.

It's all a learning curve.

---

### Post by tilii on 2010-03-23
Just had notification via the modem's sms area that the upgrade is due 27.3.10 so I should be able to give feedback on any improvement/problems by the weekend.

---

### Post by tilii on 2010-03-24
Good news. Borrowed a wired connection using wicd and installed network-manager again. This was far easier than the manual installation methods and I'd recommend this route to anyone who, like myself, hasn't fully embraced the power of the terminal command line.

If my connection problems persist at least I can now consider some of the fixes suggested although I will wait until the firmware upgrade has taken place this weekend in case that raises any further issues.

---

