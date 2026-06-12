---
title: "CD's won't run on my laptop"
date: 2009-12-12
forum: General Help
---

### Post by Jazzcat12 on 2009-12-12
Hi, I recently installed Ubuntu 9.10 on my NEC Versa (Think its an FM340). It installed fine :) But it doesn't run CDs. What I really want to work is my BT Wireless Internet. I have 2 problems. 1. My laptop won't connect to the HomeHub, it just keeps asking for the password over and over and
2. I can't run the BT Cd. When I put it in it comes up on the Desktop. When I open it up and click the Setup.exe I get the following error:

An error occurred while loading the archive

Archive:  /media/cdrom0/Setup.exe
[/media/cdrom0/Setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/Setup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/Setup.exe or
          /media/cdrom0/Setup.exe.zip, and cannot find /media/cdrom0/Setup.exe.ZIP, period.

I get errors like these with everything I try to run from the disc. I'm new to Ubuntu, please any help would be appreciated, to either issue.

Thank you.

---

### Post by wilee-nilee on 2009-12-12
> **Jazzcat12 said:**
> Hi, I recently installed Ubuntu 9.10 on my NEC Versa (Think its an FM340). It installed fine :) But it doesn't run CDs. What I really want to work is my BT Wireless Internet. I have 2 problems. 1. My laptop won't connect to the HomeHub, it just keeps asking for the password over and over and
2. I can't run the BT Cd. When I put it in it comes up on the Desktop. When I open it up and click the Setup.exe I get the following error:

An error occurred while loading the archive

Archive:  /media/cdrom0/Setup.exe
[/media/cdrom0/Setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom0/Setup.exe may be a plain executable, not an archive
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/Setup.exe or
          /media/cdrom0/Setup.exe.zip, and cannot find /media/cdrom0/Setup.exe.ZIP, period.

I get errors like these with everything I try to run from the disc. I'm new to Ubuntu, please any help would be appreciated, to either issue.

Thank you.

.exe is a windows format and wont run in linux.

---

### Post by karamu on 2009-12-12
As noted, your CD won't run with Linux as all these ISP discs are for Windows.

When you click on the network manager icon in the top right corner does it see your BT wireless network- if it does it *should* be a case of just connecting to that....

---

### Post by Jazzcat12 on 2009-12-13
No, it doesn't detect it. I know that my laptop is wireless enabled. And the family computer connects fine. My laptop automatically connects via the ethernet cable as it should but I don't know why the wireless isnt detected. :(

---

### Post by karamu on 2009-12-13
It could be the drivers for your wireless card need to be activated (I had the same problem with my Dell Mini- wireless networking didn't work until I did that).

Try System>>> Admin>>> Hardware Drivers and see if there are eg Broadcom drivers to activate. If there are you will need to connected via ethernet to download the drivers.

---

### Post by miniyak on 2009-12-13
right click on the panel icon that shows whether you are connected or not and see if wireless is enabled (it should show up as checked off)

if checked then click the desktop to deselect then left click the the network panel icon again, there the local wireless networks should appear here including yours unless bt hides the ssid. you should be able to select you network then enter in a your password for said network. 

now, ubuntu is going to want you to make a second password in order to encrypt yours when shuting down. When you log back in ubuntu will ask you for that second "keyring" password. this is kind of annoying but there is a simple solution to getting rid of it and i can point you to the tread that covers it if you would like.


Is BT your service provider or router maker?.. or do you mean Bluetooth?
tell us a little more about internet setup, for instance what type of router the "homehub" is, and whats the encyption type of security it uses (ive never heard of it and im assuming it will function just as a normal wireless router would)... ok forget it,  i just googled it... it seems to be a regular router with a phone and tv integrated or something

---

### Post by Jazzcat12 on 2009-12-13
OK, I've managed to establish a wireless connection to the router (Woo! Thank you :) ) It says that the connection is active and signal bars appear. But when I open Firefox it says it can't connect to the server. I'm really sorry most people would probably b able to fix this on their own lol I'm a bit of an ubuntu noob. Again thank u for the help and any more advice would b rly appreciated.

---

### Post by miniyak on 2009-12-13
definitely ok I think we all started off as noobs ;), glad to help.

 not connecting to server could mean a number of things so lets try a few of them out.

first check your homehub to see if there is a status light indicating that your online.... actually i assume you are considering your posting...

next try any website besides firefox's default home page, just to make sure its not a problem with a particular site

reset the connection, you can do this in a number of ways but lets just start by right clicking on the panel network icon (wireless bars) then unchecking wireless, wait a sec, the recheck it

normally you only ever have to restart something in linux for a kernal upgrade... but out of habit i still restart the computer when i run into little issues... ( i used windows for 8 years too long)

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
What do you get when you type ifconfig in the terminal? Applications>Accessories>Terminal

---

### Post by Jazzcat12 on 2009-12-14
Ok I have the connection established (Did that yesterday). But when I opened up my laptop today it asked for an encryption key or password, I dnt knw the password as I've tried every one I gt from BT (My personal password and the provided key) U mentioned a thread earlier to stop that? I've tried restarting the laptop and thats what I came up (it didnt ask me for that password when I established the connection)
I noticed when i connected to the wireless yesterday and right clicked on the network manager the signal bars had a padlock next to them? lol this is rather frustrating I've been sitting on the stairs using this laptop for too long

btw when I type ifconfig into my terminal i get:

eth0      Link encap:Ethernet  HWaddr 00:16:36:68:27:03  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:36ff:fe68:2703/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3137 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1199715 (1.1 MB)  TX bytes:281472 (281.4 KB)
          Interrupt:19 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:16:6f:a3:f7:1a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xe000 Memory:b0106000-b0106fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

Just a note incase my laptop uses wierd names eth0 is wired (it works) and eth1 is wireless :) Thanks again

---

### Post by miniyak on 2009-12-14
... i can't find the thread that explains the keyring manager... i though it was in my subscriptions...

oh well, simply put ubuntu, by default locks up your wireless passwords ect. when you log out with something called the keyring manager

without the keyring manager the passwords that it encypts on log-out can be seen apparently by someone other then your self... I'm pretty sure this means if someone has physical access to your computer and know where to look... but take that with a grain of salt im no expert

regardless to just make it go away, which is what i prefer. Right click on the network icon then choose edit connection. Choose your wireless connection the edit, enter user password, then check off "make available to all users" in the lower left hand corner

---

