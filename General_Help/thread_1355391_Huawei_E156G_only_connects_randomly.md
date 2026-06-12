---
title: "Huawei E156G only connects randomly?"
date: 2009-12-14
forum: General Help
---

### Post by mahela007 on 2009-12-14
[workaround found on page 2.. post #17)

I have a huawei E156G modem to access mobile broadband networks. In ubuntu, it connects randomly. On such occasions, I see the blue connectivity indicator light light up but none of my applications can access the web.

---

### Post by mahela007 on 2009-12-15
anybody? Why does it connect randomly? If linux doesn't know how to use it, why does it work at all?

---

### Post by nanni on 2009-12-17
I have the same problem with a Huawei E1550. It's driving me crazy.
a solution anyone?

---

### Post by alexfish on 2009-12-17
> **nanni said:**
> I have the same problem with a Huawei E1550. It's driving me crazy.
a solution anyone?

Hi

 Which Version Of Ubuntu 

This May Help While The Browser Is Still Open / From the Network Manger  / Disconnect / then reconnect  

Then Click the " Retry Button" On The Browser  

Some Times The Main Servers Are Busy / The blue Light  shows when Connected Local

---

### Post by mahela007 on 2009-12-17
No.. that's not it. A lot of googling lead to the discovery that this is in fact a BUG. One bug report on launchpad  said it was a bug in the firmware of the dongle. Two other bug reports said it was a bug in the kernel. they are working on a fix. It seems this issue affects several Huawei dongles. I'll post the links to bht bug reports when I manage to find them.

---

### Post by alexfish on 2009-12-18
> **mahela007 said:**
> No.. that's not it. A lot of googling lead to the discovery that this is in fact a BUG. One bug report on launchpad  said it was a bug in the firmware of the dongle. Two other bug reports said it was a bug in the kernel. they are working on a fix. It seems this issue affects several Huawei dongles. I'll post the links to bht bug reports when I manage to find them.

Hi 

I am aware of This . For Reasons that Are Explained Here

It is Worth A read // Please just read ,if visiting the site

[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

But The Disconnect And Reconnect as Mentioned does Help At Present little

Question // With The Live /CD Ubuntu 9.10  it works out of the Box /as root

Re ubuntu @

Regards 

alexfish

---

### Post by mahela007 on 2009-12-18
If you can confirm that it works with the live CD you should post something on these bug reports.
[https://bugs.launchpad.net/ubuntu/+bug/446146?comments=all](https://bugs.launchpad.net/ubuntu/+bug/446146?comments=all)
make sure you post your kernel version over there.

---

### Post by alexfish on 2009-12-18
> **mahela007 said:**
> If you can confirm that it works with the live CD you should post something on these bug reports.
[https://bugs.launchpad.net/ubuntu/+bug/446146?comments=all](https://bugs.launchpad.net/ubuntu/+bug/446146?comments=all)
make sure you post your kernel version over there.

 Hi

Been Working on this one // trying to Narrow the field

---

### Post by 3rdalbum on 2009-12-18
It often helps if you wait until the desktop has loaded before inserting the stick. Before attempting to connect, you should eject the virtual CD-ROM. And after it has connected, you should try just pinging Google before you open your web browser.

When I do those things, it always works.

Probably doesn't hurt that I've run the system updates as well.

---

### Post by alexfish on 2009-12-18
> **3rdalbum said:**
> It often helps if you wait until the desktop has loaded before inserting the stick. Before attempting to connect, you should eject the virtual CD-ROM. And after it has connected, you should try just pinging Google before you open your web browser.

When I do those things, it always works.

Probably doesn't hurt that I've run the system updates as well.

Hi

No It Don't I am connected Write Now with The Situation Which One Would You Choose ? Forgot to add "The Two devices" randomly connect in a combination  on  "ttyUSB0, ttyUSB1 And tty USB2 ": So Hence the Reasons for / " From the Network Manger / Disconnect / then reconnect " /also you can be connected locally but not to the main server /

---

### Post by alexfish on 2009-12-18
I Think It's in the Qualcomm Configuration 



This Is What I Have Done  From The Boot Menu Screen

So I Select  Kernel Linux 2.6.31-14-Generic 

 Up and running first Boot

   Worth a try  // But Don't Know about rest of System settings / etc /etc

   Weee The video works  And Sound to

---

### Post by mahela007 on 2009-12-19
> **3rdalbum said:**
> It often helps if you wait until the desktop has loaded before inserting the stick. Before attempting to connect, you should eject the virtual CD-ROM. And after it has connected, you should try just pinging Google before you open your web browser.

When I do those things, it always works.

Probably doesn't hurt that I've run the system updates as well.
I'll try this out

---

### Post by alexfish on 2009-12-19
Hi All

I have narrowed the problem down to this /I Think

Having examined the  Device Manger and some of the error codes I think it comes down to this

as mentioned in the above posts / Trying to narrow the Field

Well

Look at The above Screen shots ,the one with two sets of devices showing

yes TWO set of devices on one Dongle

My USB Dongle Has an On board Storage Facility For a Micro SD slot altough I don't have a card inserted

To Try And NARROW THE FIELD 

This or What Led me To do these actions , and don't Think I am crazy either?!, may be

Having Looked visually at what was happening to the device , then trying to examine the error code !!!

My Dongle is a New Vodafone / 

I decide to open up The Dongle / Please Don't Try This Unless You Know What you are doing

This is What I discovered /Having taken all the bits apart /?  Don't try this /

Inside the case There is a Connection Like the Type on a Slide Switch , except this one does not slide

The Solution ??????

[SIZE=2][SIZE=3]I place a piece of paper over the connection  and re assemble the device [/SIZE]
[/SIZE] 
GUESS WHAT , THE DONGLE NOW WORKS ///   

I have looked at the / at Both sets of configuration files /  and Think I Have Spotted Some thing but not 
 not 100% on it

Hope There is A cure To this one Soon Other Than A PIECE of PAPER ' Can't /

 Perhaps The MANUFACTURES CAN MAKE THE DEVICE SO THE CONNECTION  IS ONLY MADE WHEN THE SD CARD IS INSERTED

PS HOW DO DO YOU REPORT A BUG / ABOUT  PIECES OF PAPER !

---

### Post by mahela007 on 2009-12-19
Wow.. impressive fix.. (although not for the faint of heart... ;-).
BTW why do you use so many slashes? '/'? No offence, but it's a bit confusing to read your posts.

---

### Post by alexfish on 2009-12-19
> **mahela007 said:**
> Wow.. impressive fix.. (although not for the faint of heart... ;-).
BTW why do you use so many slashes? '/'? No offence, but it's a bit confusing to read your posts.

Hi

Confusing for me to !

Been try to solve this one 247 for Two Week /so it is a long Story / 

the "/" cut out some of the reasons out of the post

it was the logic at trying to solve the problem 

at the foot of the post are the TWO easy solutions 

1 :at least you Know a piece  of paper can have many uses in electronics simple but effective 
2 :  this should not be a Linux problem ,but it is a problem for Linux through Manufacturers not not understanding HOW LINUX WORKS 

 TAKE NOTE MANUFACTURERS . THESES ARE SIMPLE SOLUTIONS TO LINUX  . HOPE YOU ARE READING ALL THESE POSTS

---

### Post by mahela007 on 2009-12-19
yeah... I hope huawei gets this..

---

### Post by mahela007 on 2009-12-19
Just found a workaround... worked 3 out of 3 times which is a much better record than before.
Here's what I did.
 Booted Ubuntu with the modem plugged in.
Right Clicked the icon representing my modem on the desktop (because nautilius mounted it as a storage device) and clicked eject.
 Then, I unplugged and re plugged the modem.
 Waited for a few seconds (approx 15-30) and then clicked connects in the network manager applet.
applet version is 0.7.996
Kernel is default Karmic  kernel (no updates)

---

### Post by alexfish on 2009-12-19
> **mahela007 said:**
> Just found a workaround... worked 3 out of 3 times which is a much better record than before.
Here's what I did.
 Booted Ubuntu with the modem plugged in.
Right Clicked the icon representing my modem on the desktop (because nautilius mounted it as a storage device) and clicked eject.
 Then, I unplugged and re plugged the modem.
 Waited for a few seconds (approx 15-30) and then clicked connects in the network manager applet.
applet version is 0.7.996
Kernel is default Karmic  kernel (no updates)

Hi 

Now You Now The MY comment   RE :"" Live CD ""

   Now We Know Two Fixes

  But I am Leaving my Dongle as It Is , Cos "I opened  the case" and the "Guarantee" will be "Defunct" But I don't " CARE " IT WORKS

---

### Post by alexfish on 2009-12-21
Hi 

Can You Try This


**Add in /etc/modprobe.conf:**           

**[B]options usb-storage delay_use=1               (or 10, or other)   5 is a good bench mark**[/B] To start

 From The log file Viewer You Can Check If There is A connection to The Secondary Server Which is The one to look for , if only see primary then your only connected locally
 

Adjust the Value Till it Looks Like This
  	 	 	 	 	 	  
kernel: [ 294.723705] usb 1-5: configuration #1 chosen from 1 choice

[COLOR=#000080]kernel: [ 294.746196] option 1-5:1.0: GSM modem (1-port) converter detected
kernel: [ 294.746512] usb 1-5: GSM modem (1-port) converter now attached to [/COLOR][COLOR=#000000][SIZE=2]**ttyUSB0**[/SIZE][/COLOR][COLOR=#000080]
[/COLOR]
[COLOR=#000080]kernel: [ 294.748622] option 1-5:1.1: GSM modem (1-port) converter detected
kernel: [ 294.748902] usb 1-5: GSM modem (1-port) converter now attached to [/COLOR][COLOR=#000000][SIZE=2]**ttyUSB1**[/SIZE][/COLOR]

kernel: [ 294.752541] scsi8 : SCSI emulation for USB Mass Storage devices
kernel: [ 294.754201] scsi9 : SCSI emulation for USB Mass Storage devices

[COLOR=#000080]kernel: [ 299.755772] scsi 8:0:0:0: [/COLOR][COLOR=#000000][SIZE=2]CD-ROM [/SIZE][/COLOR][COLOR=#000080]HUAWEI Mass Storage 2.31 PQ: 0 ANSI: 2
kernel: [ 299.757881] scsi 9:0:0:0:[/COLOR][COLOR=#000000][SIZE=2]Direct-Access [/SIZE][/COLOR][COLOR=#000080]HUAWEI MMC Storage 2.31 PQ: 0 ANSI: 2[/COLOR]

[COLOR=#000080]kernel: [ 299.781429] sr2: scsi-1 drive
kernel: [ 299.781995] sr 8:0:0:0: Attached scsi generic sg4 type 5
kernel: [ 299.782669] sd 9:0:0:0: Attached scsi generic sg5 type 0
kernel: [ 299.802756] sd 9:0:0:0: [sdc] Attached SCSI removable dis[/COLOR]k

pppd[8879]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
pppd[8879]: pppd 2.4.5 started by root, uid 0
pppd[8879]: Using interface ppp0

pppd[8879]: Connect: ppp0 <--> [COLOR=#000000][SIZE=2]**/dev/ttyUSB0**[/SIZE][/COLOR]

[COLOR=#000080]kernel: [ 324.448138] PPP BSD Compression module registered
kernel: [ 324.475252] PPP Deflate Compression module registered[/COLOR]

pppd[8879]: Could not determine remote IP address: defaulting to 10.64.64.64

pppd[8879]: local IP address 10.91.124.131
pppd[8879]: remote IP address 10.64.64.64
[COLOR=#000080]
pppd[8879]: [/COLOR][COLOR=#000000][SIZE=2]**primary.. **[/SIZE][/COLOR][COLOR=#000080]DNS address 10.206.65.68
pppd[8879]: [/COLOR][COLOR=#000000][SIZE=2]**secondary**[/SIZE][/COLOR][COLOR=#000080] DNS address 10.206.65.68[/COLOR]
 


 [COLOR=Navy]
...................................................................................................................................
[/COLOR]Also you could try the usb_modeswitch look here  ( Do Not use This With [ icon 5x5 {Orange}

 [SOLVED] [Ubuntu 9.10 mobile broadband can't connect]("http://ubuntuforums.org/showthread.php?t=1331660")             ([IMG]http://ubuntuforums.org/images/misc/multipage.gif[/IMG]  [1]("http://ubuntuforums.org/showthread.php?t=1331660") [2]("http://ubuntuforums.org/showthread.php?t=1331660&page=2"))

[COLOR=Navy]
[/COLOR]

---

### Post by mahela007 on 2009-12-22
I'm afraid that's a bit too complicated for me to understand...

---

### Post by n2sins on 2009-12-22
my huawei worked perfect in jaunty.. i just plug it in and go.. 9.10 even on live cd had to unplug and replug many times.. even though the modem light was on and according to network manager it was on .. i had no transfer.. so my solution is to boot with no usb devices except for the huawei.. under live cd i discovered if my chiller and usb mouse was plugged in my internet wouldnt work..so now i have to boot with those disconnected,, turn my internet on then plug in the external usb devices.. i think the kernel is getting confused with high spped usb and the slow spped usb ports on my chiller and the usb mouse.. just the mouse being plugged in gives me a 65% chance of not getting on the net.. so someone try that.. most ppl i know use the external usb mouse.. so let me know if it works for u

---

### Post by alexfish on 2009-12-22
> **mahela007 said:**
> I'm afraid that's a bit too complicated for me to understand...


Try This  From the Terminal

Code:

sudo gedit /etc/modprobe.conf

Add the line or or edit the value (0 to 10)  

[COLOR=Blue]options usb-storage delay_use= 2[/COLOR]

My setting is 2

---

### Post by hadysuliman on 2010-07-05
Hello All

I'm Installing Huawei E156G But it asks me the password, by showing the following message

password is required 
Huawei Techology Huawei Mobile 

Please help
 
Thanks

---

### Post by mahela007 on 2010-07-05
Hmm.. I wasn't asked for a password. How did you 'install' you modem? did you use the network manager applet from the desktop?

---

### Post by brufferman on 2011-06-02
I have the same problem on a eeepc netbook 1001ha
The dongle worked with no problems on 10.04, but now - trouble

I have noticed that when it does connect it gets fairly hot (morethan I remember from before)

Some times after plugging it in and I wait about 2 minutes or so - I get a promt to enter the PIN code for the sim card - I get all excited, but only to find I still do not have the Mobile Internet listed in the network manager - and no connection.

It seems if you plug in and unplug a bit ( a few times - some sort of confusion "accidentally" alows a connection

Some people here have suggested ejecting the icon for the stick from the desktop, but i do not have an icon apear on this machine - not sure why, it is there when running winedoze microbrain.

---

### Post by brufferman on 2011-06-02
> **alexfish said:**
> Try This  From the Terminal

Code:

sudo gedit /etc/modprobe.conf

Add the line or or edit the value (0 to 10)  

[COLOR=Blue]options usb-storage delay_use= 2[/COLOR]

My setting is 2


I have tried this and the reliability of connection is much better, will keep you all posted how this progresses :)

---

