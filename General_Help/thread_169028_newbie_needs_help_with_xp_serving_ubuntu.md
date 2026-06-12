---
title: "newbie needs help with xp serving ubuntu"
date: 2006-05-01
forum: General Help
---

### Post by cnc333 on 2006-05-01
just to get it out of the way... I am new to linux 100%.  I know my way around a PC pretty well, although networking is NOT my favorate thing about computers. I have a XP Home desktop wirelessly connected to my router and internet and a XP Home laptop wirelessly connected to my router and internet too.  I have put together a compter out of OLD spare parts (my frankenstein computer if you will) and put ubuntu on it until I can learn enough to have it as my primary computer. Using a KVM Switch and ethernet cable I have the 2 machines hooked up at the same time, BUT I CANT GET ONE TO RECOGINIZE THE OTHER. I'm sure someone has had this problem before and if someone can just post the url to the thread that would help me a lot, but remember I am new to linux. 
Neither computer will ping the other, but the windows pc will ping the laptop and router no problem. I have disabled the windows firewall until I get this figured out. ](*,)  HELP!!!
btw... whats samba?... I've came across quiet a few postings refering to this but I dont know what it is or how to get it.
thanks, 
cnc333

---

### Post by olsonar on 2006-05-01
Samba is a linux utility that lets you share files. It's nessecary if you want to share files with Windows. As for networking, I use Network Manager to manage my connections. To install just:

```
sudo apt-get install network-manager-gnome
```

To let Network Manager manager your connection you'll need to edit your /etc/network/interfaces file. 

```
sudo gedit /etc/network/interfaces
```

comment out everything except these lines:

```
auto lo
iface lo inet loopback

```

install samba

```
sudo apt-get install samba
```

then reboot and it should work.

---

### Post by cnc333 on 2006-05-01
I really apprecate the help, but so far this is not helping any.  This is a new install of ubuntu and the disk did check out to md5, but when i code 

sudo apt-get install network-manager-gnome

i enter my password and then the terminal shows:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package network-manager-gnome

I dont know if I'm at fault cuz i have NO CLUE what I'm doing or if its something deeper. The samba install (seemed to have) worked fine.

I also have another problem where i cant get my resolution higher. Right now its stuck at 640x480 :?: but for the moment I'm just worried about getting this machine online and sharing files.

And another question.. What is FireStarter?

thanks,
cnc333

---

### Post by olsonar on 2006-05-01
Try

```
sudo apt-get update
``` 
then do

```
sudo apt-get install network-manager-gnome
``` 
Firestarter is a firewall. once you get your networking working, I highly recommend you install it. Linux may not be as vulnerable as Windows, but its not perfect. Firestarter is what I use and so far as I can tell it doesn't interfere with file-sharing at all. I don't have know why it won't let your screen resolution go above 640x480. Perhaps the KVM switch is interfereing? Try connecting it directly to the monitor and see if that helps.

---

### Post by cnc333 on 2006-05-01
ok, sudo apt-get update didnt work. i got a LONG list of errors that i would love to post, but because i cant get online i cant. and i tried to put them in a text file and save them to floppy and for some reason the drive isnt working. im 90%+ sure it works. any ways the errors appeared to be from not being able to get on the net. a lot of the errors were temporary failure resolving security.ubuntu.com and temproray failure resolving us.archive.ubuntu.com.
any more help would be greatly appreciated.  I REALLY want to learn more about linux through hands on, but at this point its becoming really discouraging. i wont give up without a fight (or a reinstall) thought. 

thanks to the ubuntu community for your help,
cnc333

---

### Post by olsonar on 2006-05-02
I should have anticipated that. You can't get online because you have no networking!;) You can use System -> Administration -> Networking to configure your ethernet connection. click 'enable this connection' and tell it to use DHCP. Then try once again to update and install.

---

### Post by cnc333 on 2006-05-02
I think somewhere along these lines I severely screwed up everything, lol.
[QUOTE=olsonar]
To let Network Manager manager your connection you'll need to edit your /etc/network/interfaces file. 

```
sudo gedit /etc/network/interfaces
```

comment out everything except these lines:

```
auto lo
iface lo inet loopback

```
[/QUOTE]

Under network tools I only have the loopback interface for network device. Before I edited the interfaces file I had an ethernet option on there too.
Is there anyway to get the interfaces file back to how it was before this step? Naturally I didnt make a back up...

---

### Post by cnc333 on 2006-05-02
and another note, the resolution issue was not solved by connecting the monitor straight through...

---

### Post by olsonar on 2006-05-02
can you post your /etc/X11/xorg.conf file? it could just be that the monitor wasn't configured properly when it was installed, because of the KVM switch. You could also try (with it connected directly to the monitor) this command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

which should automaticaly reconfigure your X-server.

---

### Post by cjae on 2006-05-03
I am really new to ubuntu but I would assume that you have to add more repositories to apt get to get the package you are trying to install.

I would be helpful to people if you knew what your graphics card or on board video was to help you with the resolution. Also he probably can't post his xorg.conf if he has to internet and no floppy. 

Ubuntu seems to be a good distro for ease of use so stick with it and it will come. Using google is a great way to search this forum. I have quite a few answers this way. This is not always the same with other distros. 
I mearly make google do the work insta=ead of the site. like eg.

ipaddress is not working ubuntu. 

You have a long road ahead of you but stick with as this is better than most. For example, when you learn about the linux kernel you will want to know possibly how to compile it. This site does a great step by job of that. Most sites just go ok put it in your src directory and generate an oldconfig then pick your which way you want to compile make make modules and copy it to your bootloader.

Now you tell me how the hell you are going to do that with that info.

---

### Post by olsonar on 2006-05-03
[quote=cnc333]I think somewhere along these lines I severely screwed up everything, lol.


Under network tools I only have the loopback interface for network device. Before I edited the interfaces file I had an ethernet option on there too.
Is there anyway to get the interfaces file back to how it was before this step? Naturally I didnt make a back up...[/quote]

just use System -> Administration -> Networking to reconfigure your ethernet. That's what generated the entry in the first place. Or just uncomment the lines you commented out.

---

### Post by cnc333 on 2006-05-03
I cant post a copy of the xorg.conf file, but i will duplicate part of it.  So i dont have to copy all of it, i will copy the sections that i think are going to be useful
```

Section "Device"
           Identifier:     "Intel Corporation i740"
           Driver:         "i740"
           BusID:         "PC:1:0:0"
EndSection

Section "Monitor"
           Identifier:              "Envision EFT"
           Option:                 "DPMS"
EndSection

Section "Screen"
           Identifier:              "Default Screen"
           Device:                 "Intel Corporation i740"
           Monitor:                "Envision EFT"
           DefaultDepth:         24
           SubSection "Display"
                       "Depth"                 1
                       "Modes"                 "1152x864" "1024x768"  "800x600"  "640x480"
           EndSubSection
           SubSection "Display"
                       "Depth"                 4
                       "Modes"                 "1152x864" "1024x768"  "800x600"  "640x480"
           EndSubSection
           SubSection "Display"
                       "Depth"                 8
                       "Modes"                 "1152x864" "1024x768"  "800x600"  "640x480"
           EndSubSection
           SubSection "Display"
                       "Depth"                 15
                       "Modes"                 "1152x864" "1024x768"  "800x600"  "640x480"
           EndSubSection
           SubSection "Display"
                       "Depth"                 16
                       "Modes"                 "1152x864" "1024x768"  "800x600"  "640x480"
           EndSubSection
           SubSection "Display"
                       "Depth"                 24
                       "Modes"                 "1152x864" "1024x768"  "800x600"  "640x480"
           EndSubSection
EndSection
```
If you need a different part of the code tell me which section and ill be glad to copy it. 

As for reconfiguring the x-server, i get an error ```
 sudo: dpkg-reconfigure: command not found
```
help ](*,)

---

### Post by threethirty on 2006-05-03
samba is the Linux implementation the SMB protocol (lets Windows and Linux dance together).... s(a)mb(a), get it?  its one of those funny naming things with linux.  wait till you figure out why apache is named the way it is

sorry doesnt really help you out but worthless info is my strong suite

---

### Post by olsonar on 2006-05-03
well, xorg.conf seems ok. don't know why won't it dpkg-reconfigure for you. If you get your networking working again (see my last post) don't bother with network manager. do a 

```
sudo apt-get update
```

and then a

```
sudo apt-get dist-upgrade
```

there have been aa lot of xorg upgrades recently. maybe one of them will fix your problem.

---

### Post by Incomingstm on 2006-05-03
[QUOTE=olsonar]Try

```
sudo apt-get update
``` 
then do

```
sudo apt-get install network-manager-gnome
``` 
Firestarter is a firewall. once you get your networking working, I highly recommend you install it. Linux may not be as vulnerable as Windows, but its not perfect. Firestarter is what I use and so far as I can tell it doesn't interfere with file-sharing at all. I don't have know why it won't let your screen resolution go above 640x480. Perhaps the KVM switch is interfereing? Try connecting it directly to the monitor and see if that helps.[/QUOTE]

I think that would be ```
sudo apt-get install network-manager
``` this worked for me..

thanks :D

---

### Post by pizzaboy0023@gmail.com on 2006-05-03
i need help i cant instill ubntu linux 

i have win xp pro sp2

when i try to install the linux it will freeze on me 

do you why that is happing to me??

---

### Post by olsonar on 2006-05-03
[quote=Incomingstm]I think that would be ```
sudo apt-get install network-manager
``` this worked for me..

thanks :D[/quote]

network-manager-gnome will install the network-manager package. network-manager-gnome is a frontend to network manager.

---

### Post by cnc333 on 2006-05-03
install network-manager
install network-manager-gnome
updates

all create errors... im really starting to wonder if i dont have a problem with the install.  something like: it installed enough to work, but not work right.  Im not getting discouraged with linux because i knew it would be a challenge, but i am about more than willing to reinstall.  

OH... when i was trying to install... i had an error the first few times i tried to install...
```

----------install the base system-----------
unable to install the selected kernel

an error was returned while trying to install the kernel into the target system.
kernel package: 'linux-386.'
check /traget/var/log/bootstrap.log for the details.

```
i finally got it to install correctly when i went back and redone the partitions. im wondering if there isnt some lingering problems from this error. 
until next time,
cnc333

---

### Post by Incomingstm on 2006-05-04
[QUOTE=olsonar]network-manager-gnome will install the network-manager package. network-manager-gnome is a frontend to network manager.[/QUOTE]

well...i dont think u shud send a newbie to get a file that doesnt exist without added repositories... but network-manager-gnome does not exist in regular repositories...but anyways...](*,)

---

### Post by rcarring on 2006-05-04
A small suggestion: if newbies want to try out Ubuntu, they might like to consider the vmware browser appliance. You will need the vmplayer itself and about 8-10Gb of free disk space ultimately, as when you start installing stuff in the VM it very quickly grows in size.

As regards Windows, it might help if both Windows machines are in the same workgroup. This is usually something like MSHOME, but you can use any other name just as long as the Workgroup name is the same on both machines.

If you have a wireless router, you might consider a wireless card for Frankenstein.

Failing that maybe a hardwired router with RJ45 cabling to all three machines...

---

### Post by ypout on 2006-05-04
Just wanted to say stick with it, Ubuntu is worth the effort.  I've just bought myself a router and am trying to get my XP and Linux boxes talking. I'll let you know how it goes...

So far not so good ---http://www.ubuntuforums.org/showthread.php?t=170629 (PC Hangs!)

Bummer!

---

### Post by cnc333 on 2006-05-08
OK, sorry its been so long since my last post. Heres the latest. I reinstalled 5.10, however when it was detecting network devices or whatever it said that the system may not be on DHCP or devices may not be working properly. so i entered the ip and all that good stuff manually. since im not good at networking and i honestly hate it, when it says default gateway, do i put my xp machine's ip, which is what the linux machine is directly linked to, or do i put the default gateway that the xp machine has? on any note, i was able to get samba installed but i still cannot get network-manager-gnome OR network-manager to install. heres the code 
```

sudo apt-get install network-manager
Reading package list... Done
Building dependency tree... Done
Package network-manager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source.
E: Package network-manager has no instillation candidate

sudo apt-get install network-manager-gnome
Reading package list... Done
Building dependency tree... Done
E: Couldn't find pagkage network-manager-gnome

```

i installed the updates w/ no problem but when i do dist-upgrade i get ```

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

```

and also about the floppy problem, it drive is good but when i click on it i get an error saying ```

Unable to mount the selected volume.
Error: given UDI is not a mountable volume.
```

any help is appreciated
thanks,
cnc333

---

### Post by drkavnger99 on 2006-05-08
Now I'm very new to linux not quite as green as you but still very new.  With that said I'm a networking guru.  Is this how you have your network setup


Frakenstein-----------------\
                                         > Wireless Router
Windows XP-----------------/

Or

Frankenstein------------------->Windows XP------------------->Wireless router

If your using the first one your good the second one requires a special cable between the frank and win machines.

---

### Post by cnc333 on 2006-05-08
[QUOTE=drkavnger99]Is this how you have your network setup


Frakenstein-----------------\
                                         > Wireless Router
Windows XP-----------------/

Or

Frankenstein------------------->Windows XP------------------->Wireless router

If your using the first one your good the second one requires a special cable between the frank and win machines.[/QUOTE]

I have the Frankenstein *linux* hooked up to the windows XP machine which has the wireless card. they are connected through a rj-45 cable. what other kind of cable is there to use besides maybe a serial...?  

i also have a few ?'s to clear up about how windows should be configured exactly with ports? proxys? firewall *windows and zonealarm*? static or dhcp ip? how should all of the stuff in linux be configured too? also because i have the xp w/ wireless, do i have to do something to "activate" the onboard NIC, besides installing the drivers, which i have done?

thanks for the help thus far,
cnc333

---

### Post by drkavnger99 on 2006-05-09
RJ45 is the right type of connection but you need a crossover cable between them it switches the send and recieve pairs on the cable to allow for data over the line.  In windows xp you'll want to goto network connections and right click the the wireless  connection and goto properties.  Select advanced tab and put a check mark in Allow other computers to connect through this computers internet connection.  Turn off your firewall for the time being till you get the line to come up.  These are two things you will have to fix to just get the connection between the two to work.  BTW if your not sure what a crossover cable is just goto into your local computer sales place and ask them for a crossover cable like this [http://www.bestbuy.com/site/olspage.jsp?skuId=6991963&type=product&id=1099390830926](http://www.bestbuy.com/site/olspage.jsp?skuId=6991963&type=product&id=1099390830926) 
That is half your problem atm.

---

### Post by cnc333 on 2006-05-09
[QUOTE=drkavnger99] BTW if your not sure what a crossover cable is just goto into your local computer sales place and ask them for a crossover cable like this [http://www.bestbuy.com/site/olspage.jsp?skuId=6991963&type=product&id=1099390830926](http://www.bestbuy.com/site/olspage.jsp?skuId=6991963&type=product&id=1099390830926) 
That is half your problem atm.[/QUOTE]
I would make my own cable, i have access to all of the tools necessary. but i cant remember if a crossover is the:
white-orange, orange, white-green, blue, white-blue, green, white-brown, brown *this is what i have*
or the other kind. I always have trouble remembering its setup, lol.

even if i didnt have the xp machine set up to let another pc share the internet connection, shouldnt i be able to ping it, with the firewalls turned off?

thanks for the help, 
cnc333

---

### Post by cnc333 on 2006-05-09
And i just realized that i already had that option checked anyway...

---

### Post by cnc333 on 2006-05-10
Yeah, ok. so i need a *crossover cable.*
white-orange, orange, white-green, blue, white-blue, green, white-brown, brown on one end and then
white-green, green, white-orange, blue, white-blue, orange, white-brown, brown on the other end.
does it matter which end gets which? like the server gets one and the host gets the other?
I will hopefully get this made today and get back to  ya asap.
its gonna be like $.25 to make or $25 to buy....

---

### Post by drkavnger99 on 2006-05-10
shouldn't matter which end goes where as long as the pairs are right.  Sorry about the delayed response I made the booboo of forgetting one of the many passwords I have.  Only reason I said to open up the firewall is it makes it easier to test things before clamping down the security and possibly creating some connectivity issues.

Let me know how the crossover cable works.

---

### Post by cnc333 on 2006-05-11
ok, so i now have the crossover cable and another NIC to go with it. nothing will work as far as apt-get update or install network-manger or network-manager-gnome, however it does say that I do have the newest version of samba. The last error on all of the apt-get commands, even the update, says "You may want to run apt-get update to correct these problems" i dont know whats up. can someone tell me exactly what all of my networking settings should be on my linux machine?  i have it on DHCP. i dont really know what else i should do. 

thanks,
cnc333 ](*,)

---

### Post by drkavnger99 on 2006-05-11
You should leave it DHCP thats correct.  The settings I'm more concerned with are on your winxp machine.  You've got a PM

---

### Post by cnc333 on 2006-05-11
Thanks drkavnger99. Now that I have been able to get my updates my floppy will mount correctly. linux is begining to really become fun. 

Now all I need to do is figure out how to get my resolution problem fixed.

thanks again,
cnc333

---

### Post by CameronCalver on 2006-05-12
yeah my resoulution is stuck at 640x480 when on windows i have it on 1042x????

---

### Post by cnc333 on 2006-05-12
ok so now i have my resolution problem fixed by doing ```
sudo dpkg-reconfigure xserver-xorg
```
then i chose my vid card model from the list and it worked fine. 
thanks for everyones help.
cnc333

---

