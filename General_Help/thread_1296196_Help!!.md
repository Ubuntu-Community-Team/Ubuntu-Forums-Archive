---
title: "Help!!"
date: 2009-10-20
forum: General Help
---

### Post by cmscott2 on 2009-10-20
I really know nothing about computers and a good friend of mine put ubuntu on my computer. I really do enjoy and have no complaints about ubuntu but that friend is sadly no longer around to help me with it and i do not know anyone else who can help me with ubuntu if need be. therefore, I have decided to move all of my important documents to an external harddrive and completely uninstall ubuntu and throw XP back on. I have the XP cd, now i just need to know how i go about doing all of this. Please help!!! Thank you!!

---

### Post by howefield on 2009-10-20
Have it from the horses mouth..

[http://support.microsoft.com/kb/316941](http://support.microsoft.com/kb/316941)

---

### Post by Giblet5 on 2009-10-20
> **cmscott2 said:**
> I really know nothing about computers and a good friend of mine put ubuntu on my computer. I really do enjoy and have no complaints about ubuntu but that friend is sadly no longer around to help me with it and i do not know anyone else who can help me with ubuntu if need be. therefore, I have decided to move all of my important documents to an external harddrive and completely uninstall ubuntu and throw XP back on. I have the XP cd, now i just need to know how i go about doing all of this. Please help!!! Thank you!!


**Step 1:** Save your data.

How much data do you have?

You can find out by opening a terminal window and typing the following: ```
du -sm .
```

That will report the number of "megabytes" that your home directory uses. You will need that much storage to save all of your data (it depends on what kind of data it is).

Get a USB pen drive, or some DVD-RWs, and start copying files by dragging them from your home directory to the pen drive or DVD-RW.

Pen drives usually come in 1G, 2G, 4G, 8G, and 16G. Multiply by 1000 to figure out how many megabytes that is.

DVD-RWs hold around 4,700 megabytes each.

Make sure you have enough pen drives or DVD-RWs to hold all of your data, as determined above.

(The more stuff you don't have to back up, the fewer pen drives and DVD-RWs you'll need...)

**Step #2:** Install Windows XP

Like **howefield** said, follow Microsoft's directions.

[http://support.microsoft.com/kb/316941](http://support.microsoft.com/kb/316941)

Good luck to you!

---

### Post by P4man on 2009-10-20
> **cmscott2 said:**
> i do not know anyone else who can help me with ubuntu if need be. 

You just met a few tens of thousands of those people here :p

Anyway, I understand why youd want to have windows back, just consider a dual boot. install windows first (see posts above) then install ubuntu and you'll be able to boot both. You can keep using ubuntu and have windows at hand in case you're in trouble. Or you can use windows and have ubuntu at hand the next tine you get bitten by a virus or some malware in windows, and no friend around to fix it ;)

---

### Post by mick222 on 2009-10-20
Probably easier to stick with Ubuntu as installing xp isn't as simple as it seems. You will need all the driver cd's that came with your computer need to install java flash and probably a lot more programs as it has almost no software installed . If you are really a newbie get some help.No5t to mention set up a firewall and antivirus antimalaware programs.

---

### Post by cmscott2 on 2009-10-20
thank you all very much for your replies... i will definetly try that... the reason why i am switching is because i recently moved and had a wired connection to my computer for the internet, however, the new place i am at has wireless and ubuntu wont connect to it, ive tried everything, im not sure the wireless card is being read, i know i have one because when i first got ubuntu i had a wireless connection, SO i would love to stick with ubuntu, but it just is not reading my wireless card..... if i can fix it i will stay.... any help with that??

---

### Post by howefield on 2009-10-20
> **cmscott2 said:**
> .... any help with that??

Have we to guess what wireless card you have ?

Help us to help you ;)

---

### Post by NightwishFan on 2009-10-20
Enjoy setting up drivers. You better find some ethernet ones while you still have a modern operating system installed. That way you can get the other drivers and service packs when you downgrade.

To Find Hardware, in a terminal on Ubuntu:
```
sudo lshw > Desktop/hardware
```

Or use Hardinfo, which has a GUI
```
sudo apt-get install hardinfo && hardinfo
```

---

### Post by badger_fruit on 2009-10-20
Hmm, going back to XP eh?

It's really easy to do, the first reply gave you all you need to know.

Shame that you're "leaving" but, is there any reason in particular (other than "because I know how to use XP")?  

You see, the community here is something you won't find with XP; you've got thousands of users in one place that can help from the most novice problem to the hardest.  Windows XP, although nice and mature, is used on over 95% of the world's computers; that makes it a target for all kinds of nasty things you simply don't see here in Linux land.  A minefield for newbies such as yourself.

I reformatted a PC recently infected with many viri, within a week, even though they had anti-virus, anti-spyware, firewall etc, they still managed to get it re-infected!  If you don't know what you're doing then it's so easy to be misled by the "OMG YOUR PC HAS A VIRUS!!! CLICK HERE FOR FREE SCAN!!" nonsense that's on a heck of a lot of websites.  Problem, the "free scan" disables any REAL AV etc you may have, and installs a virus!

As an IT pro, I see all the time un-suspecting Windows users hacked, virus ridden and generally trashed computers.  It's a sad fact that an OS, no matter how secure you think you have it, there is always one easy way to break all that security.  The user.

Fool them and you're PC is owned.

Anyway, if you do go back to XP and you have installed Anti-virus (AVG), Firewall (Zonealarm), Anti-spyware (Spybot S&D), and you see on a webpage that "your pc is infected..." DON'T CLICK IT!!!

Good luck with Windows, seriously, it's a good OS but when you've re-installed it 10+ times due to malicious stuff getting onto it, Ubuntu (or any Linux distribution of course!) will welcome you back with open arms.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Have a lot of fun

---

### Post by P4man on 2009-10-20
> **cmscott2 said:**
> thank you all very much for your replies... i will definetly try that... the reason why i am switching is because i recently moved and had a wired connection to my computer for the internet, however, the new place i am at has wireless and ubuntu wont connect to it, ive tried everything, im not sure the wireless card is being read, i know i have one because when i first got ubuntu i had a wireless connection, SO i would love to stick with ubuntu, but it just is not reading my wireless card..... if i can fix it i will stay.... any help with that??

Im not sure I understood, did you have a wireless connection in ubuntu, or did you have one on that machine prior to installing ubuntu?

Either way, lets see which wireless network card you have, NightwishFan's post should help determine that. There are precious few, if any wifi cards that cant be made to work on ubuntu. But if you dont have a wired connection at the moment, it could be a bit tedious having to transfer stuff between machines.

---

### Post by howefield on 2009-10-20
> **badger_fruit said:**
> Shame that you're "leaving" but, is there any reason in particular (other than "because I know how to use XP")? ....[I]

snip the rest from the IT pro.[/I]

Why the rant ?

She has answered your questions before you even asked.

---

### Post by badger_fruit on 2009-10-20
> **howefield said:**
> Why the rant ?

He has answered your questions before you even asked.

Oh yeah, so he has, whoops - missed it on first read, doh.  Anyway, there was no "rant".  Just wanted to try to educate into the problems and 'dangers' faced by using XP, they guy said in the OP he's not familiar with computers and that's the kind of people these scams target.

---

### Post by cmscott2 on 2009-10-20
Once again, i really do not want to get rid of ubuntu but I need the internet for my graduate school. I had a wireless connection on my computer even after i put ubuntu on it,  then i went to a wired connection and now i am back to a wireless.

I will let you know what wireless card i have, Unfortunately since i do not have the internet, i do not know when i will be able to let you know, I am at work right now, hopefully i can let you know tomorrow.

This is so frustrating!

Thank you all again! 

if someone would be kind enough to send me a number via email i could reach them at that would be great, I am a helpless girl who is trying to learn all that she can so she can keep ubuntu :(

---

### Post by badger_fruit on 2009-10-20
> **cmscott2 said:**
> i do not have the internet at the moment

Hmm, the magical forum posting fairy is here, RUN! Protect your women and children!!
Seriously, how, with no internet, can you post on here?

[http://www.ubuntu.com/support](http://www.ubuntu.com/support)

May as well click the link above which will give you access to the official Ubuntu support pages and resources.

ps. Giving your email address on a public forum like this is BAAD thing to do!
LOLS @ all the ubuntu geeks "OMG, it's a girl", fires up evolution and then, doesn't know what to write :(

---

### Post by iTheBadGuy on 2009-10-20
> **badger_fruit said:**
> Hmm, the magical forum posting fairy is here, RUN! Protect your women and children!!
Seriously, how, with no internet, can you post on here?
Did you finish reading?, i believe somewhere in the post it said "I'm at work now". i think this is how she can post here..

---

### Post by howefield on 2009-10-20
> **cmscott2 said:**
> I had a wireless connection on my computer even after i put ubuntu on it,  then i went to a wired connection and now i am back to a wireless.

If you had the wireless working previously, but not now, could it be that you need to put the security key/passphrase to access the new wireless connection ?

Is there a network icon on the top right hand side of the panel, which when clicked shows available wireless networks ?

Apologies if you already knew to do that.

---

### Post by badger_fruit on 2009-10-20
> **iTheBadGuy said:**
> Did you finish reading?, i believe somewhere in the post it said "I'm at work now". i think this is how she can post here..

Oh man, I think I need my brain checking lol!
Ok, well, point being, if she can post on a forum then surely she can click the links to the support pages?

---

### Post by P4man on 2009-10-20
a few suggestions:
1) remove that email address from your post, unless you want to be spammed to death (and not just by linux geeks offering help heh). If over the phone help is inevitable arrange it through PM. Might also help to say what country you live in.

2) Doing this by phone is probably harder than doing it on a forum or irc or chat. I would suggest you bring the laptop to your work and try to solve it there using the forums (or some instant messenger, irc, skype whatever)

3) Can you borrow a usb wifi stick from someone? Most sticks just work, and it would be so much easier if you had an internet connection. Then we could help you get the builtin wifi working, and you return the stick.

---

### Post by cmscott2 on 2009-10-21
ok so now I am not sure how I was connected to wireless before, SO lets start from the begining, How can I tell if I have a wireless card or not? 

If ubuntu isnt reading my wireless card, what should i look for when i open the side of my computer? 

Maybe we should start with establishing that first because i really do want to keep ubuntu, i just need to get my internet working. 

Thank you!!

---

### Post by cmscott2 on 2009-10-21
[LIST=1]
[*]                     Ensure that your wireless device is turned on.
[*]                     Click the NetworkManager icon in the system notification area.
[*]                     Under *Wireless Network* click the radio button next to the 			network you want to connect to.
[/LIST]
I have done all three of these things, however, in the network manager, under wireless network, there is no radio button to click?? so perhaps i do not have an internet connection because there is no wireless card?

I just want the internet!! :)

---

### Post by NightwishFan on 2009-10-21
If you have a wireless card, you can use one the commands in my post to find out the name of it. If there is no driver for it, or not one in System -> Administration -> Hardware Drivers, you can use Ndiswrapper to install a windows driver for the card. I would advise to use a wired connection when possible (on any system) but most cards should likely work with wireless. If you can get me the exact model of your card, and if it works on another system currently, we can likely get it working. If I missed the name of the card in this thread somewhere, forgive me, I am due for a new pair of eyeglasses soon.

---

### Post by howefield on 2009-10-21
> **cmscott2 said:**
> ..there is no radio button to click??

There may not necessarily be a radio button, It may simply be the name of network to click on. Just getting the simple stuff out of the way :)

---

### Post by cmscott2 on 2009-10-21
Ok I think i tried getting ndiswrapper but i dont think I have it on my computer. I updated ubuntu and as soon as i did that, everything went haywire....

How can i find out the model of my wireless card for you?

---

### Post by NightwishFan on 2009-10-21
I will be happy to try to help.

If you would rather use a graphical interface, and perhaps simplify things, you can install the package 'Hardinfo'. I have a command here to install and run hardinfo. Go to (Applications -> Accessories -> Terminal) and paste this command. If it asks for your password, then please type it, but it will not show up when you do so, but it is there.
```
sudo apt-get install hardinfo && hardinfo
```

For a command line way:

Run this in a terminal (Applications -> Accessories -> Terminal). It should save a file to the desktop. You can look through the file for the wireless card, or you can upload it here using "Attach Files" when you create a post, and I will find it for you.
```
sudo lshw > Desktop/hardware.txt
```

Please ask if you have any questions.

---

### Post by white-zilla on 2009-10-21
Hey CMscott2, the quickest and easiest fix would be to get a USB wifi dongle/adaptor/thingy that works on ubuntu strigt outta the box.

according to what i've read, this adaptor will work the instant you plug it in.  Hopefully you live in america so you can buy this exact item. 

[http://www.amazon.com/D-Link-Wireless-Adapter-802-11g-54Mbps/dp/B000FJJASO](http://www.amazon.com/D-Link-Wireless-Adapter-802-11g-54Mbps/dp/B000FJJASO)

Hopefully everyone else here can confirm wether or not it really works in ubuntu.

---

### Post by cmscott2 on 2009-10-21
Thank you nightwishfan... I am going to try this tonight and i will let you know how that goes tomorrow since i can not get back on the internet until tomorrow. I appreciate all the help!!

Whitezilla... thanks for the info! I will deifnetly look into that. I want to see if i have a wireless card first and then i will get that if i dont. Thanks!!! 

:):)

very confident this will be solved!

---

### Post by P4man on 2009-10-21
since no one else pointed it out yet afaik, let me state the obvious (well, obvious to some):  check if it is not already working. In the top right you have a network manager icon, if you right click it, you might see an option "enable wireless". If its there, then the card is already working. You wont need drivers. Just enable it and select the network from the list (left click on the icon)

If its not there, do as NightwishFan told you. Post back the results (or feel free to google the type of adapter you found and add "ubuntu jaunty" to the search string. Good chance you'll find a how to).

---

### Post by cmscott2 on 2009-10-22
Here is everything that I have done so far and the results

please see attachment

I hope this gives you enough information

---

### Post by P4man on 2009-10-22
Im afraid not :(
Well, it does tell us you have no working wireless, but the most important commands, you mistyped or ppl gave the wrong instructions.

```
lspci
```
is the most important one. Adding the -v was optional (gives a bit more info). Then someone  suggested adding ```
| less
```. that allows you to scroll back and forth but its a pipe symbol, or a vertical bar not  a slash. By typing a slash instead, the command failed to execute. But you really dont need to add that if you want to paste the output here.

then the ```
lshw
``` would have achieved about the same thing, but the person who gave you the command added "> Desktop/hardware.txt". That puts the output of the command in a file on the desktop. Provided you are not already in the desktop. It seems however your terminal opens in the desktop or you changed folders to the desktop so the relative path to ./Desktop became incorrect.  Hence it complains and displays nothing and saves nothing and we know nothing more then we did earlier :(

Long story short, I still have no idea what wireless card you have. Lets try again, and lets [KISS]("http://en.wikipedia.org/wiki/KISS_principle")

type these commands and copy paste the output like you did earlier:
```
lspci
```
```
lsusb
```
(should it be a USB device)

edit: and for the record, installing the hardinfo program also failed, because you have no internet connection...

---

### Post by RichardLinx on 2009-10-22
> **cmscott2 said:**
> Here is everything that I have done so far and the results

please see attachment

I hope this gives you enough information

Heh, a .doc file. A true Windows user. :)
I looked at the output you got from the iwconfig command and it doesn't look like your laptop has a built in wireless card. But my knowledge of Networking is pretty limited so I could be wrong.

> I had a wireless connection on my computer even after i put ubuntu on it, then i went to a wired connection and now i am back to a wireless.Can you confirm whether you had wireless working with some sort of external adapter or did it "just work" without the need for any attachments?

cmscott, have you tried the simple suggestion of just clicking the wireless connections icon in the top right corner of a default Ubuntu (GNOME) install? Although, since you don't seem to have any wireless functionality I guess it won't do you any good... (My bad :D )

Does your laptop have a wlan (wireless lan) switch or button of some sort on it? I have a Sony VAIO laptop that requires the wireless card to be turned on if I want connectivity (obviously), you might have something similar.

When I type the iwconfig I get this output:
```
richard@richard-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Ziski"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1B:11:FD:5D:3A   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=71/100  Signal level:-63 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```
You can see that you are missing wlan0 which would usually indicate your wireless connectivity. The output you got from ifconfig also confirms this. 

You're not able to connect either because you haven't set up your wireless router properly (ie. Even a properly set up laptop running Mac OSX, Windows, or Linux won't see wireless) or, your laptop has no wireless card/your laptops wireless card isn't being detected and doesn;t have a working driver installed.

For those of you that can;t be bothered to view the .doc file or don't have the extensions installed to view it from whatever strange reason, here it is:
```
christina@christina-desktop:~/Desktop$ iwconfig

lo        no wireless extensions.



eth1      no wireless extensions.



eth0      no wireless extensions.



vboxnet0  no wireless extensions.



pan0      no wireless extensions.



christina@christina-desktop:~/Desktop$ 




christina@christina-desktop:~/Desktop$ lspci -v / less

Usage: lspci [<switches>]



Basic display modes:

-mm		Produce machine-readable output (single -m for an obsolete format)

-t		Show bus tree



Display options:

-v		Be verbose (-vv for very verbose)

-k		Show kernel drivers handling each device

-x		Show hex-dump of the standard part of the config space

-xxx		Show hex-dump of the whole config space (dangerous; root only)

-xxxx		Show hex-dump of the 4096-byte extended config space (root only)

-b		Bus-centric view (addresses and IRQ's as seen by the bus)

-D		Always show domain numbers



Resolving of device ID's to names:

-n		Show numeric ID's

-nn		Show both textual and numeric ID's (names & numbers)

-q		Query the PCI ID database for unknown ID's via DNS

-qq		As above, but re-query locally cached entries

-Q		Query the PCI ID database for all ID's via DNS



Selection of devices:

-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots

-d [<vendor>]:[<device>]			Show only devices with specified ID's



Other options:

-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz

-p <file>	Look up kernel modules in a given file instead of default modules.pcimap

-M		Enable `bus mapping' mode (dangerous; root only)



PCI access options:

-A <method>	Use the specified PCI access method (see `-A help' for a list)

-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)

-G		Enable PCI access debugging

-H <mode>	Use direct hardware access (<mode> = 1 or 2)

-F <file>	Read PCI configuration dump from a given file

christina@christina-desktop:~/Desktop$ 


christina@christina-desktop:~/Desktop$ sudo lshw > Desktop/hardware.txt

bash: Desktop/hardware.txt: No such file or directory

christina@christina-desktop:~/Desktop$ 

christina@christina-desktop:~/Desktop$ 

christina@christina-desktop:~/Desktop$ sudo lshw > Desktop/hardware.txt

bash: Desktop/hardware.txt: No such file or directory

christina@christina-desktop:~/Desktop$ 

christina@christina-desktop:~/Desktop$ sudo apt-get install hardinfo && hardinfo[sudo] password for christina: 

Sorry, try again.

[sudo] password for christina: 

Reading package lists... Done

Building dependency tree       

Reading state information... Done

The following packages were automatically installed and are no longer required:

  kdelibs-data

Use 'apt-get autoremove' to remove them.

The following extra packages will be installed:

  libsoup2.2-8

The following NEW packages will be installed:

  hardinfo libsoup2.2-8

0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.

Need to get 316kB of archives.

After this operation, 918kB of additional disk space will be used.

Do you want to continue [Y/n]? y

Err http://us.archive.ubuntu.com jaunty/universe libsoup2.2-8 2.2.105-4build1

  Could not resolve 'us.archive.ubuntu.com'

Err http://archive.ubuntu.com jaunty/universe libsoup2.2-8 2.2.105-4build1

  Could not resolve 'archive.ubuntu.com'

Err http://archive.ubuntu.com jaunty/universe hardinfo 0.4.2.3-5ubuntu2

  Could not resolve 'archive.ubuntu.com'

Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/libs/libsoup/libsoup2.2-8_2.2.105-4build1_i386.deb  Could not resolve 'archive.ubuntu.com'

Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/h/hardinfo/hardinfo_0.4.2.3-5ubuntu2_i386.deb  Could not resolve 'archive.ubuntu.com'

E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

christina@christina-desktop:~/Desktop$ 


christina@christina-desktop:~/Desktop$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:15:f2:a1:67:86  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:23 Base address:0x6000 



eth1      Link encap:Ethernet  HWaddr 00:15:f2:a1:77:af  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:17 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:36 errors:0 dropped:0 overruns:0 frame:0

          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:2784 (2.7 KB)  TX bytes:2784 (2.7 KB)



christina@christina-desktop:~/Desktop$ 
```

cmscott, I take it you are some where with Internet access right now so we can help you in real-time? If you don't have your laptop with you currently then my honest opinion is that you follow Microsoft's instructions to the letter and reinstall Windows XP (Not easy for an average user, but with instructions you should be all right) or you get someone a little more tech savvy to install Windows or your preferred OS for you.

Otherwise, type this into a terminal please:
```
lsb_release -a
```
That will tell us which release you are running, which might be a little helpful. I'd also like to point out that a new milestone release (9.10) will be released in about a week and *might* fix all your problems with one install.

Cheers, Richard.

---

### Post by P4man on 2009-10-22
RichardLinx,

From the output its clear she needs a driver, provided the machine even has onboard wireless. She doesnt have internet on the machine right now.

I would wait to see until we find out which type of wireless card she has. It could be trivial to install. If its not, then keep in mind windows will likely also not pick up the wireless without drivers, and then comes all the trouble of sound drivers, display drivers, flash, java, .net, service packs, firewall, antivirus, office, acrobat, and what not. 

If it turns out the card is not (easily) supported by Linux, then I agree but at this point, switching to windows might prove a lot more problematic even than fixing the wifi.

---

### Post by renkinjutsu on 2009-10-22
Then you'd be asking for Windows help and support later... you don't like us here or something? :(


A good idea would be to dual boot, then you can switch around, and you can boot into the other when one fails ;)

---

### Post by RichardLinx on 2009-10-22
> **P4man said:**
> keep in mind windows will likely also not pick up the wireless without drivers, and then comes all the trouble of sound drivers, display drivers, flash, java, .net, service packs, firewall, antivirus, office, acrobat, and what not. 

If it turns out the card is not (easily) supported by Linux, then I agree but at this point, switching to windows might prove a lot more problematic even than fixing the wifi.
Good point. I guess I over estimated Windows XP hardware detection and Microsoft's installation instructions. If she knows anyone that's even a little tech savvy though, then she might be able to get someone to install Windows XP and all associated drivers for her. 

I guess what we should really ask:
cmscott, does you router have any external ports for an ethernet cable so you can just connect to the internet through a wired connection? 

It would make it a little easier for you and the people trying to help you if you were communicating with us through Ubuntu from a wired connection while we try to figure out what the problem with your wireless is.

---

### Post by P4man on 2009-10-22
> **RichardLinx said:**
> Good point. I guess I over estimated Windows XP hardware detection and Microsoft's installation instructions. If she knows anyone that's even a little tech savvy though, then she might be able to get someone to install Windows XP and all associated drivers for her. 

I guess what we should really ask:
cmscott, does you router have any external ports for an ethernet cable so you can just connect to the internet through a wired connection? 

It would make it a little easier for you and the people trying to help you if you were communicating with us through Ubuntu from a wired connection while we try to figure out what the problem with your wireless is.

If you read the whole thread, you'd have seen she only has wireless where she is now. If anything, Id suggest borrowing a wifi stick (or heck, buying one for $10).

As for windows, you're right she'd have more luck finding someone to help, but having done a fresh XP install recently, Ive rediscovered how incredibly much work it is. And how surprisingly few hardware works out of the box (none of three wireless adapters I tried, go figure). If she has a restore cd from the manufacturer, then its something else. She could do that in just an hour or so and be up and running.

---

### Post by RichardLinx on 2009-10-22
I did read the whole thread. :) Some wireless routers have the option to use a wired connection too (mine does), that's why I asked.

---

### Post by P4man on 2009-10-22
> **RichardLinx said:**
> I did read the whole thread. :) Some wireless routers have the option to use a wired connection too (mine does), that's why I asked.

fair point. Maybe all she needs is borrow or buy a network cable (even if only as temporary solution). Well, lets await the response...

---

### Post by ktmom on 2009-10-22
Woman to woman, just my two cents--

You indicated that you are a grad student. At most schools, there is an IT or electronics technical department somewhere on campus. Since linux is commonly used on campus for a variety of reasons (chemistry department probaly runs it on their instrumentation, the mathmatics department often uses linux based computers, physics folks also are likely to have computers running linux, you campus probably uses it to provide campus intranet, ect) I bet you could find a savy person to help you.  

It looks to me like everything is getting stuck because you just want the laptop to work and not become an "expert".  I bet all you're interested in right now is getting your dissertaion completed.  That's OK and very understandable, but some basic knowledge of how (any) operating system works will help you either resolve the wireless problem, or if you choose, re-install Windows.  

I bet, if you took your laptop to the electronics shop for the chemistry/physics department, or to a math grad student, and just explained that you need help determining if there is an internal wireless card or if you need an external adapter, they could sort it out for you.  I bet that would be some much less painful than the struggle to learn the jargon used to help you.  Come to think of it,it might cost you a dozen donuts.  But then you could get back to late nights studying in peace.

---

### Post by cmscott2 on 2009-10-22
Ok first of all, Im pretty tech savy when it comes to most things and pretty efficient when it comes to ubuntu when it comes to easier things. However, I seemed to have run into this problem.

second, i really do not want to switch to Xp AT ALL...but imfinding it hard to get the internet.

Third, ive realized that when i had wireless before it was through an external D-link usb adapter. 

I have found that adapter and tried to plug it in last night....to no luck, go figure....

I installed the d link disc and for some reason my computer/ubuntu will still not read the usb.

How do i go about setting d link up on ubuntu? since just installing the cd and plugging it in doesnt seem to be working.

also, I do not have a laptop, it is a desk top so i cant exactly take it anywhere to an internet connection. and yes....all im able to get at the place im at is wireless. There is a router upstairs but it would be a house full of wires if i tried to wire my computer to it. 

ANYways..... just seeing what else I can do......

SOOOO frustrating :)

one more thing, the grad school i am at does not have a "campus" that i can live at so im not even sure i would be able to get any help from them... and chances are.... they know nothing about ubuntu....

when will the world realize we all need ubuntu in our lives?:)

---

### Post by steveneddy on 2009-10-22
Post the model number of the d-link adapter please? if it is available.....

---

### Post by cmscott2 on 2009-10-22
Judging on what I found online and what mine looks like (because it is at home and i am at work) 

I have either the DWA-130 wireless-N

OR

the DWA-125 wireless 150

Thank you!!

---

### Post by cmscott2 on 2009-10-22
also, another quick question....

is there anyway to reinstall Ubuntu without erasing anything on my computer?

OR I could put all of my things on a disk/eternal hardrive and reinstall ubuntu.... i just do not have the internet connection to reinstall it if that is needed.

please let me know. 

thank you!

---

### Post by P4man on 2009-10-22
> **cmscott2 said:**
> Judging on what I found online and what mine looks like (because it is at home and i am at work) 

I have either the DWA-130 wireless-N

OR

the DWA-125 wireless 150

Thank you!!

Oh God, Both are based on ralink chips. That means you'll have to download and compile your own drivers. Compiling means you have to install a truckload of dependencies first.

On the bright side, I think they are supported in Karmic out of the box. Perhaps that is your easiest ticket, download Ubuntu 9.10 beta at work, burn the iso to a cd (or usb stick). At home you can boot fron the cd/stick and see if it works. If it does, you can install it.

---

### Post by P4man on 2009-10-22
> **cmscott2 said:**
> also, another quick question....

is there anyway to reinstall Ubuntu without erasing anything on my computer?

OR I could put all of my things on a disk/eternal hardrive and reinstall ubuntu.... i just do not have the internet connection to reinstall it if that is needed.

please let me know. 

thank you!

If you reinstall, you will probably wipe everything, unless you do some "complicated" things like partitioning and making a dual boot (so the old and new ubuntu can boot). Making a backup all of your documents is a good idea regardless :)

As I mentioned above though, you can try ubuntu from cd or usb stick wihtout installing it, and therefore without wiping anything. It would allow basic internet access provided your wifi is recognized (which i think is the case for Karmic aka ubuntu 9.10)

---

### Post by cmscott2 on 2009-10-22
OK so is there any wireless adapter you would recommend for ubuntu??

i am going to try to dl the iso for ubuntu 9.10 and see how that goes....

remind me again....

how can i run it without installing it??

Thank you!!

also....whats the command to see how much space i have used on my computer?

---

### Post by NightwishFan on 2009-10-22
You can run it without installing by using the live cd image, and burning it to a CD. The cd runs a system without installing, and can optionally install later. That is my recommendation on how to try and install Ubuntu. You can save the .iso and burn it to a cd/dvd on any machine with those capabilities.

Make sure you burn at the slowest possible speed.

---

### Post by P4man on 2009-10-22
> **cmscott2 said:**
> OK so is there any wireless adapter you would recommend for ubuntu??

There are too many adapters. Chances of you finding one Id recommend are slim. Instead, go to the website of your pc shop and google on the product type adding "ubuntu jaunty" and youll probably quickly see if its supported or not. 
```

i am going to try to dl the iso for ubuntu 9.10 and see how that goes....

remind me again....

how can i run it without installing it??

```

First question should be: how do I burn it? Have a look here:
[https://help.ubuntu.com/8.04/switching/installing-burning.html](https://help.ubuntu.com/8.04/switching/installing-burning.html)

Then to boot the cd, have a look here:
[https://help.ubuntu.com/community/BootFromCD#BIOS%20is%20not%20set%20to%20boot%20from%20CD%20or%20DVD%20drive](https://help.ubuntu.com/community/BootFromCD#BIOS%20is%20not%20set%20to%20boot%20from%20CD%20or%20DVD%20drive)
(perhaps print it)

Booting the cd wont install it, just select the "try out ubuntu" option and off you go.

```
also....whats the command to see how much space i have used on my computer?
```

From a terminal 
```

df -h
```

Or have a look in applications > accessoiries > disk usage analyzer 
to get a nice overview of what is using your diskspace

---

### Post by steveneddy on 2009-10-22
The next time I need help I will say I'm a gurl, too.

There are people posting to this thread that I thought were gone from the forums.

**Just kidding.** :popcorn:

Looks like you are getting some great help from some really fine folks.

You're gonna be such a geek when you get this figured out.

I'm just gonna watch and see how this gets resolved.

---

### Post by NightwishFan on 2009-10-23
Obviously you do not mean me. From 11-2pm est I help everyone when I can. This should be easy to resolve though.

---

### Post by steveneddy on 2009-10-23
Personally I believe that the OP should purchase a well supported USB wireless modem or install a wireless LAN card, which IMHO, would be easier because I believe it would be detected and setup automatically upon next boot.

I wonder how she is making out on this issue?

---

### Post by cmscott2 on 2009-10-25
good news!! i finally was able to get my internet to work! yay! thanks everyone for your help!! i get to keep ubuntu!!  :D

soooo happy!

---

### Post by NightwishFan on 2009-10-26
Good work, glad you got it working. Fend off the beast of Redmond. ;)

---

