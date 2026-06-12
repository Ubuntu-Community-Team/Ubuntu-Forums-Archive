---
title: "Automatic Ethernet Activation"
date: 2006-02-27
forum: General Help
---

### Post by fatty_chris on 2006-02-27
I did a search and found nothing, so I figured I'd ask. 

Everytime I reboot, my ethernet card is deactivated.  Is there a way to automatically activate my ethernet card?

---

### Post by AndyCooll on 2006-02-27
In /etc/network/interfaces is there an entry somewhere that says "auto eth0"

If there isn't add it to the bottom of the page.

Also under System->Administration->Networking is eth0 selected as the default gateway?


:cool:

---

### Post by fatty_chris on 2006-02-27
I have the line that says auto eth0 but that still doesn't work.  In the networking section, it doesn't have anything selected for the default gateway.  I have to click on the location to get it to work.

---

### Post by darth_vector on 2006-02-27
if you have a static IP, then in /etc/network/interfaces you should have a set of lines kind of like this```
iface eth0 inet static
        address 192.168.0.187
        netmask 255.255.255.0
        gateway 192.168.0.1
```note the gateway entry.

if you are using DHCP then you will have to set the gateway on the DHCP server.

---

### Post by Postman on 2006-02-27
I've also learned that some Internet Providers (mine is locally used so it's not like the big time providers like AOL and so forth) doesn't support DHCP on Linux formats.  It's NW Minnesota so no very many people have Linux period so that's the reason.  I called there and they told me their servers can't pickup DHCP signals from Linux so I don't know if it's your problem but it's something to take note if you use a locally used IP.

---

### Post by fatty_chris on 2006-02-27
Thanks for the responses.  The connection works, but it just has to be activated everytime I turn the computer on.  I am using a DHCP server, but it's our own.  Basically, I'm testing a Linux box on a Windows network for my job.  It's kind of a side project, but I like the idea of the possibility to stick it to Microsoft if we can get the project to work.  One of the big problems is that we have to be able to shutdown and reboot the computer without having to manually activate the ethernet connection.

The gateway is set on the DHCP server, and it does connect to the internet through the server.  I don't have any problems with that, it's just the automatic activation that I can't seem to figure out.

---

### Post by jamesr on 2006-02-27
> Everytime I reboot, my ethernet card is deactivated. Is there a way to automatically activate my ethernet card?

Do you mean you have see it active and the boot deactivates or that you have never got to work?

---

### Post by fatty_chris on 2006-02-28
It works, when I go into the settings and activate it.  I think the first post I used to start this thread was on that machine, but I have to activate the card everytime it boots up.

---

### Post by jamesr on 2006-02-28
How do you activate it from the GUI or the console.

---

### Post by fatty_chris on 2006-02-28
I usually activate it from the GUI, since it's easier.  If there's a permanent fix through the terminal, I have no problem doing it that way.

---

### Post by jamesr on 2006-02-28
Could give me the route and commands that you use through the GUI.
Have you ever activated through to console?

---

### Post by fatty_chris on 2006-03-01
I go in through 
System>Administration>Networking
then I click on the eth0 connection and click Activate.  It works every time, but I have to do that every morning.

---

### Post by jamesr on 2006-03-01
At the cosole prompt have to tried
sudo ifup eth0

sudo ifconfig -a

---

### Post by fatty_chris on 2006-03-01
ifup eth0 works, but will that keep it activated when I reboot?

---

### Post by jamesr on 2006-03-01
Post the file
cat /etc/network/interfaces
cat /etc/modules

---

### Post by fatty_chris on 2006-03-02
ETC/NETWORK/INTERFACES:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
        network 172.16.96.37
        broadcast 172.16.103.255
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 172.16.92.4

#auto eth0

iface eth1 inet dhcp

iface eth0 inet dhcp



iface dsl-provider inet ppp
provider dsl-provider

auto eth0


ETC/MODULES:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse

---

### Post by DavidW2 on 2006-03-02
I have a couple of suggestions to make.

> # The primary network interface
iface eth0 inet dhcp
network 172.16.96.37
broadcast 172.16.103.255
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 172.16.92.4

#auto eth0

iface eth1 inet dhcp

iface eth0 inet dhcp

First, you can comment out the network and broadcast addresses.  DHCP will grab what info it needs for establishing the connection.
The "dns-nameservers 172.16.92.4" entry should be moved to /etc/resolv.conf as "nameserver 172.16.92.4" if you have a resolv.conf file. Otherwise comment it out.  That comes from the DHCP server as well, if configured.
Also, you can take out the second "iface eth0 inet dhcp" entry.
If that doesn't help you can look into installling Network-Manager.

> iface dsl-provider inet ppp
provider dsl-provider
For my own curiosity, I was wondering how these two lines come in to play?

---

### Post by fatty_chris on 2006-03-02
Thanks for the suggestions.  I commented out the broadcast line, but the dns nameserver line is already in the resolv.conf file along with another nameserver line that is different.  Does that matter?

---

### Post by DavidW2 on 2006-03-02
> Thanks for the suggestions. I commented out the broadcast line, but the dns nameserver line is already in the resolv.conf file along with another nameserver line that is different. Does that matter?

Your welcome, hope it helps.
If your saying that there is another nameserver entry, no that doesn't matter.  The computer will try to use the first namerserver to resolve DNS names. If that doesn't work it will go to the second one and so on.

I'm using Network-Manager and it edited the resolv.conf file with the only entry being 127.0.0.1

---

### Post by fatty_chris on 2006-03-02
How do I install the Network Manager?  Does it just need to be unpacked from somewhere, or do I need to download something?

---

### Post by DavidW2 on 2006-03-02
I was just thinking... You don't need network manager unless you are setting up a laptop.  But if you want to try it you can install it from Synaptic.  Look for network-manager.

In the man page for resolv.conf is the following paragraph:
> On  a normally configured system this file should not be necessary.  The only name server to be queried will be on the local machine; the domain name is determined from  the  host name and the domain search path is constructed from the domain name.
 Which makes sense since you are going to get DNS server entries from DHCP.  Therefore, you should just add "nameserver 127.0.0.1"  at the top of the list in resolv.conf.

---

### Post by fatty_chris on 2006-03-02
Sweet.  Thanks, man.  Let me see if this thing stays connected when I reboot.

---

### Post by fatty_chris on 2006-03-02
Didn't work.  I had to re-activate my connection when the computer booted.  Buncha crap.  I have to be missing something really simple.  I have no idea what's going on.

---

### Post by DavidW2 on 2006-03-02
Sorry about that.  I'm not sure on the whole process myself.  In UNIX we used BIND, the resolv.conf file and the /etc/hosts file.  Here you have DHCP and dhclient3. I connected my laptop via cat5 and I'm trying a few things.

Did you install network-manager? Still don't think you need it.  But, if all else fails.

Immediately after reboot, if you type "ps -ef |  grep dhclient3" does it show any processes running?

---

### Post by fatty_chris on 2006-03-02
This is what I got from that command:

1000      7380  7369  0 16:40 pts/0    00:00:00 grep dhclient3

I didn't install network-manager yet.  I might try it.

---

### Post by DavidW2 on 2006-03-02
I'm sure you don't need Network Manager.  I uninstalled it on mine.  Then I de-activated eth0, rebooted, and when I log in it is already active.

When you start it manually, does dhclient3 show up when you do the "ps" command?

What you should install is sysv-rc-conf from synaptic.  Then we can easily see what process are started when.

---

### Post by fatty_chris on 2006-03-02
I tried to install the network manager, but it gave me this error.

network-manager:
 Depends: bind9  but it is not installable

---

### Post by DavidW2 on 2006-03-02
Well, I have been trying to reproduce the problem all day and the only way I have been able to do it is with the "ifupdown" process taken out of the equation.

If you type the following commands:
   cd /etc
   ls rc*.d | grep ifup

You should see 3 ifupdown processes.  Two are S36 and one is S39.  You should also see ifupdown-clean process as well.  Actually they are not processes but scripts.  Both ifupdown and ifupdown-clean should be set to run at init 0,6 and S.

---

### Post by jamesr on 2006-03-02
Hi
 I 2nd what DavidW2 said but I would the etc/network look as the following. You have a couple of double entries and commented out lines.

```
ETC/NETWORK/INTERFACES:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

# The primary network interface
auto eth0
iface eth0 inet dhcp
#network 172.16.96.37
#broadcast 172.16.103.255
# dns-* options are implemented by the resolvconf package, if installed
#dns-nameservers 172.16.92.4

iface eth1 inet dhcp

iface dsl-provider inet ppp
provider dsl-provider



```

---

### Post by simoncm on 2006-03-03
Fresh install of Breezy.  I am using a Cisco Aironet350 PCMCIA card.  
Login and under System > Administration > Networking.  I have eth1 and the other eth2.  eth2 is the connection I am using for wireless.  Upon each reboot I need to come here and select eth2 connection and activate the connection.  
I have checked all of my settings and compared to suggestions above.  As with the original post the suggestions are not working for me either.  

Any other suggestions?

---

### Post by fatty_chris on 2006-03-03
[QUOTE=DavidW2]Well, I have been trying to reproduce the problem all day and the only way I have been able to do it is with the "ifupdown" process taken out of the equation.

If you type the following commands:
   cd /etc
   ls rc*.d | grep ifup

You should see 3 ifupdown processes.  Two are S36 and one is S39.  You should also see ifupdown-clean process as well.  Actually they are not processes but scripts.  Both ifupdown and ifupdown-clean should be set to run at init 0,6 and S.[/QUOTE]

I did see 4 processes, but what do you mean they should be set to run at init 0,6 and S?  

By the way, does it matter if I'm using Edubuntu?

---

### Post by DavidW2 on 2006-03-03
simoncm,
   I have to press a button to turn on my wireless after I am logged in.  Therefore, I couldn't get straighforward interface setup to do the trick.  That is why I installed Network Manager.

 Some are able to do it by just tweaking the interface file like here.
[http://www.ubuntuforums.org/showthread.php?t=138510](http://www.ubuntuforums.org/showthread.php?t=138510)

The respondent in this post used ifplugd to get his interfaces to come up.
[http://hardware.mcse.ms/archive42-2005-5-191123.html](http://hardware.mcse.ms/archive42-2005-5-191123.html)

Note: I stand corrected. I added the extra lines into my wireless connection (eth1) from the first link above and I was able to connect to the internet.  But only after trying three times to access the internet with XMMS.  Then the connection came up.
Tried again and waited 15 seconds after pressing the button.  Works. No Network Manager installed.

fatty_chris, 

   If you change directory to /etc and type "find . -name \*ifupdown\* -print" you should get the following:
> ./default/ifupdown
./init.d/ifupdown-clean
./init.d/ifupdown
./rc0.d/S36ifupdown
./rc0.d/S18ifupdown-clean
./rc6.d/S36ifupdown
./rc6.d/S18ifupdown-clean
./rcS.d/S39ifupdown
./rcS.d/S18ifupdown-clean
find: ./lvm/archive: Permission denied
find: ./lvm/backup: Permission denied


---

### Post by fatty_chris on 2006-03-03
./default/ifupdown
./init.d/ifupdown-clean
./init.d/ifupdown
./rc0.d/S36ifupdown
./rc6.d/S36ifupdown
./rcS.d/S39ifupdown
./rcS.d/S18ifupdown-clean
find: ./lvm/archive: Permission denied
find: ./lvm/backup: Permission denied
find: ./ssl/private: Permission denied


It looks like I'm missing 
./rc0.d/S18ifupdown-clean
./rc6.d/S18ifupdown-clean
and I have 
find: ./ssl/private: Permission denied

---

### Post by DavidW2 on 2006-03-04
Actually, you are ok.  Mine was setup wrong. 

What kernel are you using when you start Linux.
  You can also find it by typing "uname -r".

Is there anything in your syslog or kernel log that talks about dhclient or eth0?  Look around the timeframe that you restart the computer.

Your logs are easiest to read by going to Applications->System Tools->System log.  Then click on the log in the list to the left that you want to read.

If all else fails we can bring it up using a dirty hack.
But before that I would say, update your repositories and do:
apt-get update
apt-get dist-upgrade

The correct repositories can be found at:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)
Just look under the Breezy heading.  You can copy and paste those into a new sources.list file in /etc/apt/.

---

### Post by fatty_chris on 2006-03-06
I'm using kernel 2.6.12-9-386

There is something about eth0, but it's just the identification for the chip.
I didn't see anything about dhclient, but there are things about dhcpd, but it's all stuff that you'd find in the "about" section on the help tab.

I ran update and dist-upgrade and that didn't work.  This whole thing doesn't make any sense.  I would think there would be a way to keep the active connection active upon a reboot.

---

### Post by laplatakid on 2006-03-06
Don't know if you saw it or not, but I believe you have the auto eth0 commented out in post #16.

Change ```
#auto eth0
``` to ```
auto eth0
```I think it should work then.

---

### Post by fatty_chris on 2006-03-06
I have it changed, so now it looks like post #29.  It still isn't working.

---

### Post by DavidW2 on 2006-03-08
Here is the hack you can try.

Open a terminal window and type the following:
```
cd /usr/local/bin
sudo gedit start_eth0
```
add the following to this file: 
```
ifup eth0
```
save and quit.
Then type: ```
chmod 755 start_eth0
```
Now go to System-> Preferences-> Sessions
Pick on the Startup Programs tab and Add.  
Browse for the /usr/local/bin/start_eth0 file, select Open
Then change the order number to 99 and press OK, then close.
This will execute the "ifup eth0" command for you during startup.

After you have upgraded or dist-upgraded your software you can try disabling this and see if you get a proper network connection.

[I think ifplugd may be a good program to use in an office environment because it would protect for the situation of a user booting their PC with the internet down.  But it took, in my computer, 3-5 minutes to connect after I plugged in the RJ45 jack.  That is partly because it was trying to get the wireless connection up first even though it was disabled.  If you don't have a wireless connection the delay should be minimal.  But this is all future planning]

---

### Post by fatty_chris on 2006-03-08
I tried that, and it didn't work, but when I checked my networking application under System>Administration, I noticed that the window doesn't show any "location" selected.  When I click on the location I had already created, the eth0 connection shows active, but the "activate" button is showing.  I clicked on that and it opened the connection.

---

### Post by simoncm on 2006-03-08
Still having to "Activate" Eth2.  Read all replies up to this point.  I could be mistaken but I find that the eth2 is up and running but somewhere is not the default network device.  Almost like upon boot whatever the config is trying to establish as the default connection is not available.  When I go in and "Activate" eth2, it works as it should.

When reading the log files I find that the system is trying to set eth1 as my default and eth2 should be the default "Active".  The /ect/network/interfaces is set as recommended in the posts.  

Where else is there settings in the system that dictates default devices?  This has only been a problem in Breezy.  I have been using Hoary since release and had no problem with networking.

---

### Post by threethirty on 2006-03-08
I know this sounds kinda dumb, but did you try shutting down with save current setup checked?  I do that on my laptop and I dont have a problem with it.  And if you have certain programs/files that you need right as soon asap you can open those before you shutdown of a night.  

I hope that will solve your problem

---

### Post by DavidW2 on 2006-03-08
simoncm,

    Are you using a pcmcia card or builtin networking?  Your problem sounds something like this other thread.
    [http://www.ubuntuforums.org/showthread.php?t=88926](http://www.ubuntuforums.org/showthread.php?t=88926)

fatty_chris,

  I don't use the location box.  But, I did read about someone trying to use it in another post for a home and work setup and not getting good results.  Trying to find the post.  If you only have one internet connection and you stay at one location it shouldn't be needed.  Regardless it does change the issue/problem a bit.  We may have to add that location manually into your interfaces file to get it to be the default setup.
  Using threethirty's suggestion, check the box to save the setup during logout and see what that does.

---

### Post by fatty_chris on 2006-03-09
Checking that box didn't work either.  This is kind of annoying.  5 pages into this thread and nothing works.  Everything you guys have said should be working, but for some reason it's not.  I just don't get it.

---

### Post by DavidW2 on 2006-03-10
So your interfaces file looks something like this...


```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

gateway <your gateway ip>


auto eth0
```

---

### Post by fatty_chris on 2006-03-10
It worked.  Awesome.  Thanks.  I don't know why it didn't work in the first place, but now it is.  David, you rock, man!!  Thanks.

---

### Post by DavidW2 on 2006-03-10
Hahaha! That worked.  I can't believe it.  I am almost as happy as you are. Woohoo!!!  Happy Trails.

[Makes me think having you put "nameserver 127.0.0.1" in /etc/resolv.conf was a bad idea.]

---

### Post by fatty_chris on 2006-03-10
You're probably right about the nameserver thing.  Crazy.  Who knows what the deal was.  Thanks for the help again.

---

### Post by DavidW2 on 2006-03-10
Your welcome.  Whew!  What a load off.  That was stressing me.

I think I'll lay off the networking questions for a while.

---

### Post by fatty_chris on 2006-03-10
Yeah, I don't know what the deal was.  You persevered though.  Good job.

---

### Post by simoncm on 2006-03-16
The following paste has been the best fix I could locate to keep the system as dynamic as possible.  Several suggestions were to set the IP static and problem would go away.  With a laptop that connects to several wireless netowks the configuration changes are too much trouble.  
------------------------
 1.  Make a file called /etc/init.d/local with a text editor. This file is a script so it should always start with the following line:

  #! /bin/sh

   2. Next, for example I have an always on cable modem and I want to use rdate to update the system time to atomic clock time at startup, so I add the following command to the file:

  rdate -s clock-1.cs.cmu.edu && hwclock --systohc

(The rdate command updates your system time, then the hwclock command updates the bios clock)

   1. Make this file executable with:

  chmod +x /etc/init.d/local

   2. Next, link the new local file by running:

  update-rc.d local defaults 80
-----------------------------------------

I have changed the above process in two places to better suit my use.
1. the local file contains the following:
   #! /bin/sh
   ifup eth2

2. when I ran the update-rc.d line my execution was as follows:
   update-rc.d local defaults 50

I read in several locations that enough of the system is available around 40 and above.  Several locations seemed to suggest 50 so I just followed their lead.  
My system is now turning the network on as I boot the machine.  No longer need to manually start the interface.

Thanks for all the suggestions.  As always the research for solving a problem is an educational adventure.

---

### Post by fatty_chris on 2006-03-17
Awesome.  Congratulations.  This was definitely a learning experience.

---

