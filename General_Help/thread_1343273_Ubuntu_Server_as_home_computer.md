---
title: "Ubuntu Server as home computer"
date: 2009-12-01
forum: General Help
---

### Post by jakslev on 2009-12-01
Dear Everybody, 

I am watching most of my tv programmes via websites and other content that is played in Firefox, Totem or similar. 

I am therefore considering setting up a local network in the house, with a main computer that I will plug into the main HD tv (probably end up buying Dell Zino HD). This computer will be on most of the day and I was going to use it as a file server and back up location for our laptops. 

Now the question is should I install:

1) Ubuntu desktop edition
2) Ubuntu server edition

Obviously we are a small home so the idea of the server edition might be "shooting" over the goal? The main jobs for the main computer will be to show content on our TV and make available music, video and files for the laptops and the other TV-sets. 

What I would like with a server would be the ability to define user rights and sharing centrally (we change our laptops every 6 months), to obtain something like what I had with the Evil Empires Small Bussiness Server. But is that straight-forward? or does it require a lot of terminal window configs?

Is there any idea in using a server for this? 

Thanks, 

jakslev

---

### Post by blueridgedog on 2009-12-01
There is nothing dramatically different between the two, and you will need the server process for file sharing.  You can either install Desktop, then install the server processes or Server, then install the Desktop.  Most go for the server then add a desktop.  It should not be overwhelming for one who changes laptops every six months, but take it one server process at a time, starting with samba as that will be the central file sharing tool.  Good luck!

---

### Post by tgalati4 on 2009-12-01
The server edition doesn't have the sleep scripts or other hooks needed to put the machine in sleep/suspend mode.  Not a problem if you want to leave it on 24/7 like a real server.

For home use, desktop version runs just fine as a server.  I still have a dapper drake desktop machine running with several server daemons running 24/7 for over 3 years.  So dapper drake has been an excellent desktop/server combination.

---

### Post by jakslev on 2009-12-02
> **blueridgedog said:**
> There is nothing dramatically different between the two, and you will need the server process for file sharing.  You can either install Desktop, then install the server processes or Server, then install the Desktop.  Most go for the server then add a desktop.  It should not be overwhelming for one who changes laptops every six months, but take it one server process at a time, starting with samba as that will be the central file sharing tool.  Good luck!

Thanks! I will install the server as soon as I can.. woops - better start the download :o) 

You mention SAMBA. Is that something I will need in a pure Linux home? I was under the impression that it was mainly to interact with Windows? As soon as I write this post I will investigate the matter myself as well. 

Thanks, 

jakslev

---

### Post by jakslev on 2009-12-02
> **tgalati4 said:**
> The server edition doesn't have the sleep scripts or other hooks needed to put the machine in sleep/suspend mode.  Not a problem if you want to leave it on 24/7 like a real server.

For home use, desktop version runs just fine as a server.  I still have a dapper drake desktop machine running with several server daemons running 24/7 for over 3 years.  So dapper drake has been an excellent desktop/server combination.

Gotcha. I never used the sleep and suspend mode. Would imagine it would be left on pretty much all day as it will double as out TV / music set. Do you know if it still supports energy conservation features like turning off the harddisk and letting process'es sleep? In either case I think I will start with the server (basically because I am curious about it and a nerd) and then when I get the Dell Zino HD I will have done sufficient testing to know what to do :o)

---

### Post by munky99999 on 2009-12-02
**Does a normal home need a server edition?**

Define normal home? I'd think a normal home doesnt even know what a server is.

Realistically speaking. You can pretty easily covert server or desktop into the other. Or some hybrid that covers all your bases.

Your desktop edition can most likely act in all the manners you expect to need as a server. Rarely do you find yourself needing more.

---

### Post by some-what-Gnu-2-networks on 2009-12-02
A NORMAL home would start out using regular Ubuntu then upgrade it to do everything a server does over time. That's what I did anyway.

---

### Post by tgalati4 on 2009-12-03
There are tweaks regarding scheduling on the server edition.  Instead, set  up a mythtv server.

---

### Post by gspat on 2009-12-03
A "Normal Home Server" is one I would define as:

- sharing video, music and photo files to any other computer on the home network.
- remote storage of any other important files used by other programs such as openoffice and email.
- centralized access to printer, scanner, etc.

To do that, all one needs is the desktop version of ubuntu with sharing (samba) and cups (printing) turned on.

I've been doing that for a long time now (at least 3 years) with not only other ubuntu machines, but windows, macs (as the occasion arises) and a couple old xboxs running xbmc. 

The solution works fantastically.

The reason to use samba is because it is universal, if aunt Chloe comes over, she can connect to the network with her laptop and access everything she needs (wants), If uncle joe needs his computer fixed, I can connect his computer to the network, backup his important files to the server and fix away without worrying about him losing data... The list goes on.

Using gigabit ethernet, I can stream full 1080p files from the server to the HTPC perfectly.

I've never needed to install the server version.

---

### Post by mixmaster on 2009-12-03
I've got two always-on linux boxes.  One is running Ubuntu desktop but is used mainly as a music server for my squeezeboxes.  As such it runs a couple of server packages on top of the standard desktop.

The other is my video vault.  That was installed with the server edition because I wanted SAMBA, SSH and apache and because I was able to do a lot of RAID setup during installation.  For convenience I then added Ubuntu desktop since I found this more convenient while setting everything up.

Nowadays I tend to access both machines more via ssh than anything else, although both can be reached via XDMPC if I am desperate (neither have screen/keyboard normally connected).

---

### Post by derrick81787 on 2009-12-03
> **jakslev said:**
> Thanks! I will install the server as soon as I can.. woops - better start the download :o) 

You mention SAMBA. Is that something I will need in a pure Linux home? I was under the impression that it was mainly to interact with Windows? As soon as I write this post I will investigate the matter myself as well. 

Thanks, 

jakslev

In a pure Linux home, NFS might be the way to go.  I think it's the normal Unix file sharing utility.  I have it running at home. It works great and can be automounted on startup if you wish (although SAMBA probably can too).  I think it's faster than SAMBA, but I haven't used SAMBA in a long time, so my info might be outdated.

Here's the official Ubuntu Community documentation on NFS:
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

and here is the one for SAMBA:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

- Derrick

---

### Post by anselm on 2009-12-03
If you need samba I have found that it is easier to set up on the server edition.

---

### Post by M!K3_$ on 2009-12-03
I know my case may not be a common home server setup, but i like to have a server for web developement.

more on the home side of things, i like to ssh into my box from school/work and start torrents on rtorrent using screen.

---

### Post by jakslev on 2009-12-04
Well.. yes.. I installed server last night and will see if I can get heads and tails on it. First issue of course is that it does not seem that there is GUI. My experience is with Evil Empire products and not to say any positive about them; bt they seemed to be a "tat" more user friendly in the server management area... But then maybe I will find a nice user friendly GUI during the day and will then revert this malicious claim :o)

I would have wanted my home server to do (in prioritized order):

1) File server for Ubuntu laptops. 
2) Stream media to TV's and Popcorn Hour A 110. 
3) User Account Control (logging into the domain and authorizing against the server instead on each computer). Ideally this should work on LAN and via VPN from abroad :o)
4) Deploy new computers over LAN
5) Run webserver with Joomla!

Okay - I might have to switch to the desktop edition and settle for 1+2..

jakslev

---

### Post by blueridgedog on 2009-12-04
You will need to install the desktop on the server:

```
sudo apt-get install ubuntu-desktop
```

---

### Post by Toastie0815 on 2010-02-03
> **jakslev said:**
> Gotcha. I never used the sleep and suspend mode. Would imagine it would be left on pretty much all day as it will double as out TV / music set. Do you know if it still supports energy conservation features like turning off the harddisk and letting process'es sleep? In either case I think I will start with the server (basically because I am curious about it and a nerd) and then when I get the Dell Zino HD I will have done sufficient testing to know what to do :o)

Energy saving features should also work with the server edition. Probably you've to install some additional packages. But as you've mentioned the Dell Zino HD you may neglect energy saving for now, see my post:
[http://ubuntuforums.org/showthread.php?t=1389281&highlight=zino](http://ubuntuforums.org/showthread.php?t=1389281&highlight=zino)

About your initial question: My situation is similar as yours and I've decided for the server edition as the installer works better for me. E.g. setting up LVM was not working in the Desktop installer, but probably I've missed something. ;)

---

### Post by jakslev on 2010-02-03
> **Toastie0815 said:**
> Energy saving features should also work with the server edition. Probably you've to install some additional packages. But as you've mentioned the Dell Zino HD you may neglect energy saving for now, see my post:
[http://ubuntuforums.org/showthread.php?t=1389281&highlight=zino](http://ubuntuforums.org/showthread.php?t=1389281&highlight=zino)

About your initial question: My situation is similar as yours and I've decided for the server edition as the installer works better for me. E.g. setting up LVM was not working in the Desktop installer, but probably I've missed something. ;)

Okay! Well maybe I should take the jump on the Zino they have another one also.. the sleek rounded one.. (not sure what it is called..) that might be the way to go. As it is I have a normal Ubuntu Desktop installed as house server..

---

### Post by pirateghost on 2010-02-03
> **jakslev said:**
> Well.. yes.. I installed server last night and will see if I can get heads and tails on it. First issue of course is that it does not seem that there is GUI. My experience is with Evil Empire products and not to say any positive about them; bt they seemed to be a "tat" more user friendly in the server management area... But then maybe I will find a nice user friendly GUI during the day and will then revert this malicious claim :o)

I would have wanted my home server to do (in prioritized order):

1) File server for Ubuntu laptops. 
2) Stream media to TV's and Popcorn Hour A 110. 
3) User Account Control (logging into the domain and authorizing against the server instead on each computer). Ideally this should work on LAN and via VPN from abroad :o)
4) Deploy new computers over LAN
5) Run webserver with Joomla!

Okay - I might have to switch to the desktop edition and settle for 1+2..

jakslev

you can do all of those things with just about any version of linux you want to use, desktop or server it simply doesnt matter.

3) SAMBA can be configured to act as a domain controller
   a. you can even install openvpn on the box to allow your vpn connection into your home from afar

4) have a look at FOG - Free Opensource Ghost

5) apache....come to think of it there might be a joomla package in the repos...

---

### Post by Ordes on 2010-02-03
> **jakslev said:**
> SAMBA. Is that something I will need in a pure Linux home? 

When all your machines using Linux no need for samba. SSH or FTP will do it.

---

### Post by t4thfavor on 2010-02-03
I never hear people recommend FTP, that is probably not the best solution as it's somewhat difficult to setup, and you would have to transfer the entire file before you can play it. I do samba since it is relatively easy to setup, and can be accessed via the gui fairly easily without setting up exports and all that jazz.

---

### Post by Ordes on 2010-02-03
ssh is not harder to setup than samba. Install the ssh server and thats it.
and than u can login over terminal or nautilus ...

----
as ssh is much more than just file transfer, some people prefer to have ftp. e.g vsftp. install, allow users to login and here you go. thats all. 
no need to copy files first. you can directly interact with them over ftp.

----
for myself i only use ssh. i have however a ftpdaemon ready when someone needs some files from my home-server..

---

### Post by munky99999 on 2010-02-03
> **t4thfavor said:**
> I never hear people recommend FTP, that is probably not the best solution as it's somewhat difficult to setup, and you would have to transfer the entire file before you can play it. I do samba since it is relatively easy to setup, and can be accessed via the gui fairly easily without setting up exports and all that jazz.

I use samba or openssh server(sftp)

for linux you can create a launcher whose command is

nautilus smb://123.456.09.132/share
or
nautilus sftp://123.456.09.132/share

on any windows box

add network share to the location or map network drive or net use command.

pretty much compatible right across everything.


tftp and ftp have their places i guess... but shouldnt really be used.

---

### Post by ant2ne on 2010-02-03
server or client is a matter of perspective. Servers often, but not always, have more power and resources. A Workstation can also function as a print or file server. Any device offering a service to another device is a server. When a Domain Controller needs to do a name lookup, it queries a DNS server. In this instance a domain controller is the client.

My home is far from normal. But the computer I'm sitting at is 9.04 desktop edition but it is also a powerful server. It is a samba server that services all of the home computers. It hosts a media share with 40+ gigs of music and video that other boxes (including my xbmc) connect to. It is a VM server hosting 4 VMs. An apache werbserver VM, a Dansguardian Squid VM, and a WindowsXP VM. This box also is my primary workstation.

You can take the server edition of ubuntu and add gnome on it. You can take the desktop edition of ubuntu and configure it to NOT boot to a GUI. If you need to preserver resources don't install the GUI. If you have the resources, keep the GUI.

---

### Post by CAPLinux on 2010-02-04
Ant2ne

I am in the process of setting up a home Linux server, How do you have your VM's set up?  I want to set up a Firewall/Network Secuirty VM  How did you set your VM to work?  I normally use Sun VirturalBox.

---

### Post by Admiral_Payne on 2010-02-04
I've built a server to play http/ftp/smb/mail server in my house a while ago. After a while it also ended up running video/music streams (mostly locally), and downloading new stuff (torrent/nzb).

Nowadays I hardly use it though, I found that two simple devices - Media center (HDX) and NAS - in combination with a hosting package greatly outranked this machine.
Lower (power) costs, less maintenance, no worries about downtime or dataloss.

The thing is... running an entire system 24/7 to basically be eating out of its nose most of the time, is just a shame :)
Not only the power bill but also all that hardware you put into it is kind-of a waste of money. A hosting provider will be able to offer you more at less cost and guarantees regarding uptime and safety of your data (e.g. not loosing it).


Nevertheless, I hope your project will work the way you want it to. I've also learned that it can be a lot of fun and a nice learning experience :)
So, all the best of luck!

---

### Post by pirateghost on 2010-02-04
> **CAPLinux said:**
> Ant2ne

I am in the process of setting up a home Linux server, How do you have your VM's set up?  I want to set up a Firewall/Network Secuirty VM  How did you set your VM to work?  I normally use Sun VirturalBox.

how beefy is your server?

I was doing the ubuntu server + vmware server for a while, but i got tired of recompiling the friggin vmware server everytime a new kernel update came in.  i moved to a couple of esxi boxes... i absolutely love them.  esxi is free, just requires you to sign up with vmware.com for free to download.

one box is pretty weak.
opteron 165 with 2gb ram on an ASROCK motherboard, 2 intel gig pci-express nics, and one broadcom pci-express nic.  runs off a USB thumbdrive and all my vmstorage comes from an iscsi target on my ubuntu server filebox
modem to one nic (dedicated for the modem)
VM1 is pfsense running firewall/routing functions, maintains VLAN routing/firewalling, and my openvpn server
VM2 is vyatta running as a proxy for vpn connections and a few computers in my house
VM3 is a webserver running debian

the second box is a little beefier
intel e6300 overclocked to 2.1ghz
8gb ddr2 ram
4-36gb 10k rpm scsi drives + datastore connected to ubuntu iscsi
2 intel gig pci-express nics
a whole bunch of VMs to handle all kinds of functions for my home network
backups, download (torrent/newsgroup downloader), domain controller, secondary webserver (for testing), dedicated mysql server for all sorts of applications/php scripts, with room to spare for playing around with new distros, etc.

---

### Post by jakslev on 2010-02-04
Thank you everybody for your thoughts on the "problem". I have now been running a setup that seems to work for me and make sense. Basically it is a combination of a "normal" Desktop 9.10 connected to the tv and a Qnap NAS to work as the real file server. Can't wait to get my cat6 LAN installed :o)

I (as most people) come from Micraswoft and I have worked with Wangdows Server. I was therefore thinking that the Ubuntu Server would have an easy to use predefined graphical user interface; that would allow even a n00b to configure users, shares, etc. Obviously it doesn't - and there are probably good reasons for that. However I think it would be a nice step in shedding the remnants of being a "super-nerd system" if something along the lines of Small Business Server was introduced - at least as an add-on to the server install. 

I will mark this thread as solved - not sure what that will do :o)

---

### Post by pirateghost on 2010-02-04
> **jakslev said:**
> Thank you everybody for your thoughts on the "problem". I have now been running a setup that seems to work for me and make sense. Basically it is a combination of a "normal" Desktop 9.10 connected to the tv and a Qnap NAS to work as the real file server. Can't wait to get my cat6 LAN installed :o)

I (as most people) come from Micraswoft and I have worked with Wangdows Server. I was therefore thinking that the Ubuntu Server would have an easy to use predefined graphical user interface; that would allow even a n00b to configure users, shares, etc. Obviously it doesn't - and there are probably good reasons for that. However I think it would be a nice step in shedding the remnants of being a "super-nerd system" if something along the lines of Small Business Server was introduced - at least as an add-on to the server install. 

I will mark this thread as solved - not sure what that will do :o)


have a look at e-box.  it is available as a package in the repository or as a standalone OS.  They just released a new version today.

---

### Post by ant2ne on 2010-02-04
> **CAPLinux said:**
> Ant2ne

I am in the process of setting up a home Linux server, How do you have your VM's set up?  I want to set up a Firewall/Network Secuirty VM  How did you set your VM to work?  I normally use Sun VirturalBox.I guess I don't really understand what you are asking. Are you asking about my dans+squid filter? Or the VM operations in general? You can PM me and I'll be glad to share what I can.

---

### Post by jakslev on 2010-02-05
> **pirateghost said:**
> have a look at e-box.  it is available as a package in the repository or as a standalone OS.  They just released a new version today.

Yes.. Yes I tried that one. The right direction I guess. But still way too confusing and many things that you have to define in several places. But the good thing is - with GNU/Linux we will get there eventually :o)

---

