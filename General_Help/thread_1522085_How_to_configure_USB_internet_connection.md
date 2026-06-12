---
title: "How to configure USB internet connection?"
date: 2010-07-01
forum: General Help
---

### Post by princerameses on 2010-07-01
In Damn Small Linux?

I have a dinosaur computer I need to use for something, and there's no ethernet port. But there is USB.

On the internet box my ISP provided there's a port for a usb cable. 

But I plug it in and there's no connection. Tried Vector too. 

Is there a terminal command to make it work?

---

### Post by princerameses on 2010-07-01
Can someone please help me? :)

The computer is waiting. :)

---

### Post by marshag63 on 2010-07-01
Which version of Damn Small Linux are you using?  Did you ISP also provide you with a USB cable?

If they did not give you a USB cable, you will need a USB to ethernet adapter (about $20) and an ethernet cable.  Plug the USB ethernet adapter into your USB port on the computer, plug the ethernet cable into the end of adapter and the other end into the box your ISP provided you.  I'll have to find my disk with Damn Small to remember if the network connection is automatic.

[http://www.officedepot.com/a/products/485170/TRENDnet-USB-to-10100Mbps-Fast-Ethernet/](http://www.officedepot.com/a/products/485170/TRENDnet-USB-to-10100Mbps-Fast-Ethernet/)

MarshaG.

---

### Post by princerameses on 2010-07-01
Yes the cable was supplied. Why would I need an adapter? Why can't I plug the usb cable into the box, then into the USB port on the computer? :confused:

If there is a way to do this, I would like to know. :)


But I did that and there is no connection. But this is Linux, so of course it's going to be more difficult. *sighs*

---

### Post by princerameses on 2010-07-01
There's one more option for getting me online- 
That's via my USB wireless adapter. But I would need to be walked through on EXACTLY how to do it. With NDISWrapper. :)

If someone was willing. 

Oh and the version of damn small linux? I'm not sure. It was from maybe a year (maybe a little more) ago. 

The latest version requires too much RAM. Though I do have it on disk.

---

### Post by marshag63 on 2010-07-01
One thing to try before moving on to wireless.

Plug in the USB cable from your ISP box to your computer and open a terminal and type "lsusb" and see what it lists as recognized and let me know.  Meanwhile, I redownloaded DSL and will boot into it to see if I can refresh my memory.  Checking back in a couple minutes.

MarshaG

---

### Post by marshag63 on 2010-07-01
Okay, rebooted into DSL 4.  

Make sure you plug your USB cable into the computer and the ISP's box before you boot DSL.  Once you are at the desktop, the program conky on the desktop (right upper corner of the screen) will show you if you have a connection by displaying an IP, i.e., Host:  box 192.168.1.100 or something.  If you see that, then you will be good to go.  I think the key is booting with the cable already plugged and seeing what happens.

If you get no IP showing, then go to a terminal window and type "lsusb" and see what comes up.

Keeping my fingers crossed for you :)

MarshaG.

---

### Post by princerameses on 2010-07-01
I was away, sorry. I will try this in a few minutes. :D

---

### Post by princerameses on 2010-07-01
Ok.

Bus 001 Device 1: ID 0000:0000
Device 2: ID 045e:0029 Microsoft corp. intellimouse optical
Device 3: ID 06a9:000b Westell

- The last one (device 3) is the router box.

But I have no connectivity. :o And Damn Small Linux is so basic I don't know where the network status is.

---

### Post by marshag63 on 2010-07-01
On the desktop, on the upper right side, is a bunch of text stuff -- it will show if you have an IP - look for "Host"

Another thing to try, in a terminal type "ifconfig" (without quotes) and see if eth0 shows up.

MarshaG.

P.S.  By the way, do you have to enter a user name and password before you can get on internet?

---

### Post by princerameses on 2010-07-01
Yes, I have that host box thing with the IP. :)
But the light on the internet box that says 'USB' is not lit up. When I was (like right now) connected through ethernet, the ethernet light lights up...


Do I connect to eth0? I thought it was usb0?

And no, no username/ password.

---

### Post by marshag63 on 2010-07-01
what does "ifconfig" show ?

---

### Post by princerameses on 2010-07-01
Ifconfig:

link encap: local loopback
inet addr: *My IP* Mask: 255.0.0.0
UP LOOPBACK RUNNING MTU:16436 metric:1
Rx packets:2 errors:0 Dropped:0 overruns:0 frame:0
Tx (all items say 0)
Rx bytes:100 (100.0 B) Tx bytes:100 (100.0B)

That is all that happened when I ran ifconfig.

---

### Post by marshag63 on 2010-07-01
So "*My IP*" means there is a number such as 192.168.?.??...

If so, open up firefox and google something.

MarshaG.

---

### Post by princerameses on 2010-07-01
Yes.

And I did that, it said: "www.google.com could not be found...."

:(

I just did it again with the USB cable unplugged from the box and got the same thing. The "host box" thing also still says the IP when not connected. By the way, I have never been connected on the internet on that computer.

And I'll just post the IP because it might matter. 127.0.0.1

---

### Post by marshag63 on 2010-07-01
Do you have a firewall or some other sort of network security like MAC address filtering setup?


MarshaG.

If you click on the DSL menu button (lower left of monitor) and look under "Apps" for DSL Control Panel, there will be a bunch of "buttons" on it and I believe one says "networking"

---

### Post by princerameses on 2010-07-01
See above message. edited.

I don't think I'm getting anywhere. :(

And no, no firewall.

Would you maybe want to try and get the adapter working if we can't get the USB connection to work? :roll:

---

### Post by marshag63 on 2010-07-01
Wifi is gonna be really tricky in DamnSmall because a lot of the newer wifi adapter drivers need "compiling."  What kind of wifi adapter/what kind of chipset?

If is usb, type "lsusb" with the adapter plugged in.

If its pcmcia, type "lspci" with the card plugged in

We need to get the info for the adapter to even see if it can be made to work in Damn Small.

Might have a better distro for you to try, depending on what you need this linux box to do and what your adapter is.

MarshaG.

What are the specs of this machine?

---

### Post by princerameses on 2010-07-01
I'm open to any distro.. but I usually have trouble installing linux. DSL was very easy though. (I had Vector before DSL and I didn't know what I was doing, but it installed) But DSL seems to work very nicely; so I might want to *try* to keep it- unless there's a distro that will work that will run the adapter straight away.

WUSB54G V.4 (from linksys) is the adapter. I also have an encore Enuwi-G2 and another that I don't know name of.

I'll run the terminal, one sec.

---

### Post by princerameses on 2010-07-01
Device ID: 13b1:000d is what it says for the adapter.

Also:
([https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54Gv4]("https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54Gv4"))

Oh, and I'm wanting the computer mostly just for web browsing. :)

And I did it for the adapter I didn't know the name of and got: 148f:3070 for the device ID.

---

### Post by marshag63 on 2010-07-01
Which adapter is this - the Encore Enuwi-g? 

According to DSL wiki, the encore Enuwi-G will work with ndiswrapper....

[http://www.damnsmalllinux.org/wiki/index.php/Verified_Wireless_Cards](http://www.damnsmalllinux.org/wiki/index.php/Verified_Wireless_Cards)

Encore enuwi-g works with the ndiswrapper of Suse 10.2 distros 

You will have to download from the "Mydsl browser" for the ndiswrapper app and transfer it via USB.  You will install via the mydsl install tool via the DSL menu.

MarshaG.

---

### Post by marshag63 on 2010-07-01
I found the info you showed before - thats a pcmcia card - if you have the CD with the drivers for windows XP, you are almost there.

Lets try the PCMCIA card first - hope you have the CD with the XP drivers (you need a RT2500.inf file)

---

### Post by princerameses on 2010-07-01
> **marshag63 said:**
> I found the info you showed before - thats a pcmcia card - if you have the CD with the drivers for windows XP, you are almost there.

Lets try the PCMCIA card first - hope you have the CD with the XP drivers (you need a *.inf file)

Do you mean the linksys one? (13b1:000d) or the second one? (I thinks it's ralink)

I did not post the device ID for the encore one.

If you want to get the encore one working, we can do that, though I might prefer the linksys wusb54g or the ralink? one. (I was planning on giving the encore one to a friend)

I have the disks for all adapters.

---

### Post by marshag63 on 2010-07-01
Do the WUSB54G -- its actually an RT73 and there are scripts and directions here:  [http://homepages.vype.de/Peter.Misch/wlan/wlan_drivers.html](http://homepages.vype.de/Peter.Misch/wlan/wlan_drivers.html)

You will want the one for 2.4.26 (you said you had an older version of DSL and that kernal is the older one) and RT73.0 > follow the directions in that link.

Good luck!  :)  

Let us know if it works for you.

MarshaG.

---

### Post by princerameses on 2010-07-02
Ya lost me. Where are you getting RT73? The Linksys adapter I have IS called WUSB54G v.4.

Or are you getting it confused with the second one I posted? It would help if I knew the name of the second one, but it doesn't say on the adapter.

[https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54Gv4]("https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB54Gv4") <that is the adapter I have. (and the one I would most prefer using)

Update. Yes you are getting them confused. :P OK, the RT73 is by ralink. That is one of the three I have.

So, what do I do now?

---

### Post by marshag63 on 2010-07-02
[http://www.damnsmalllinux.org/wiki/index.php/Verified_Wireless_Cards](http://www.damnsmalllinux.org/wiki/index.php/Verified_Wireless_Cards)

"Linksys WUSB54GC (driver & scripts => here, driver:rt73.o) "

This is the link to the driver and script:  [http://homepages.vype.de/Peter.Misch/wlan/wlan_drivers.html](http://homepages.vype.de/Peter.Misch/wlan/wlan_drivers.html)

Choose 2.4.26: rt73.0 (either the Dlink or Belkin one should work).

Follow directions as in that link  :)

MarshaG.

These were compiled specifically for DSL versions 3 and 4 - pretty sweet!

---

### Post by princerameses on 2010-07-02
I got the dlink one and the up and down scripts copied to my flash drive. But I'm not understanding what "Copy to "home/dsl/wlan" and adapt the UP_DOWN-scripts" means... Bear in mind I'm a linux noob. :P

Oh, and I'm not certain the flash drive works in damn small linux. I tried this before with another computer and I don't think it worked, but it did on other distros. But I will try once I know what to do.

---

### Post by marshag63 on 2010-07-02
You need to open the file manager (i think it auto mounts now).


The up/down scripts you will copy to /home/DSL/wlan - I think there is an option to run the file manager as root?

As for the RT73.o file, you need to find the "networking" setup option (try DSL menu button, Apps and then look for DSL Control Panel where there should be a networking or wireless button (since it is already compiled you don't need ndiswrapper).

Good luck!  You are very close to having wireless networking running.  If you need someone to talk you through, try irc #ubuntu channel on irc.freenode.com - they are pretty helpful.

Time for bed!  

Let us know how it goes.

MarshaG.

---

### Post by princerameses on 2010-07-02
Hmm.. I'm still not entirely sure I know what to do, but I will give it a quick try. I am also going to go to bed, so if I can't figure it out tonight, I'll seek help tomorrow. :)

Thank you by the way.


Ok, tried it- Didn't get very far as there's no DSL folder in the home folder. 
Are there terminal commands to do what I need? Because I also don't know anything about going into root if that is required.

But I'll be on tomorrow. ;)

---

### Post by marshag63 on 2010-07-02
Okay, just did a quick reboot into DSL Version 4.  At the bottom of the screen you will see the DSL menu button.

Next to that, continuing to the right you will see a button that says "Panel" that's the control panel where you will click on Wlanconfig (for wireless networking) and it will search for your wifi adapter.

Next,you may see a "mount" button (click on that to open the app and then click on floppy and continue until you see something like sda1 or sda2, then click unmount/mount and it will mount and unmount the flash drive)

The next button on the menu bar is "Term" for terminal.

The next one says "Files" and that is the file manager.

Don't forget to unmount the USB drive when you are done.

Good luck!

MarshaG.

---

### Post by marshag63 on 2010-07-02
PLEASE NOTE CORRECTIONS MADE IN THIS REPOST!

Morning!

The easiest way to get root file manager is, in a terminal type "sudo emelfm."  Emelfm is the file manager and sudo gives you root powers, so as soon as you get done copying files you need to get out of root because you can do some real damage as root if you are not sure what you are doing.

Set up the filemanager as so:  On the left side, navigate to /mnt/sda1 (or whatever your USB flash drive got mounted as).  

On the other side, navigate to /home/dsl.  Now click the "mkdir" button in the middle of the file manager and type "wlan" and then click "ok" otherwise it will ignore pressing the Enter key.  Now navigate into the "wlan" directory.

Now back on the /mnt/sda1 side left click, while holding down shift, on the files you want to copy.  Now, in the middle of the file manager there is a row of buttons down the center and one of them is "copy" so just click it and watch /etc/wlan for the files to show up.  Once you have done this, close the file manager so you are out of root.

Unmount your USB flash drive via the "mount" app.  

The WLAN_up.sh and WLAN_down.sh need to be edited from rt61.0 to rt73.o (I'm not sure you even need to use them at this point).

Open a root terminal and type "insmod rt73.o"  You wont' really see anything happen, just the prompt on the next line.  To verify you activated rt73.o type "lsmod" and look for rt73.o in the list.

Now I guess you reboot, choosing to boot without DHCP  - I could make my card light up, but it would not connect.... almost, but not quite working.

BTW, instead of wlan0 your wifi interface will be** rausb0.**
I think my connection is not working because I have wpa encryption and only saw spot to enter wep encryption, so depending on your wifi router setup, this may or may not work.


MarshaG.

---

### Post by princerameses on 2010-07-02
Oh, Ok, I guess I'll give this a try in a little while. (other computer is in use and I'll need it for referance. And the cords from this computer will be used for the dinosaur.)

When you say navgiate to /home/DSL/, how do you do that? 

If there's a terminal command to get me there I would appreciate it.

How do tell what version of the operating system you have? 


Also- "choosing to boot without DHCP" how do I do this?

---

### Post by princerameses on 2010-07-03
Ok I printed out your last two messages and tried it.

Nothing was as you said, but I managed to do everything you said except where you said wlan_up.sh and down need to be edited from rt61.0 to rt73.0 (are those zeros or o's? I tried both) 
It said no such file or directory, however you go to the wlan folder that was created, and it's there..

When you said to go to wlanconfig, all that comes up is "no wireless card found". There are no options except "ok" which closes it out.

When you said to mount the flash drive, I really don't know what you mean. I could not find "mount" anywhere. However, I went to myDSL or one of those folders on the desktop and right clicked and found mount, then clicked sda1.

Like I said I managed to copy the files to a new file called wlan, but you said on the left, it was on the right. 

So all that was really done was the files were copied into 'wlan' (the file that was created). 

Now what? you sounded like that was about it, but how are the files bridged to the adapter?

Also, does it matter if the adapter is plugged in at the time? I only have two USB ports; 1 for my mouse, 1 for the flash drive. I tried a regular non-usb mouse, but it doesn't work. (it works but not on that computer for some reason)

And when you say root terminal, what do you mean? I think I got to it, but not sure.

---

### Post by princerameses on 2010-07-03
I'll bump this.

And I think I'm off to bed. Hopefully you'll be on tomorrow. (marsha) :)

---

### Post by marshag63 on 2010-07-03
I guess I got a little ahead of things - sorry.

I found a link on using emelfm - these tips will help a lot on using the file manager:  [http://flusslinie.wordpress.com/2009/06/02/use-emelfm-like-a-pro/](http://flusslinie.wordpress.com/2009/06/02/use-emelfm-like-a-pro/)

Without making sure what version of DSL you are using, its hard to tell you where to look/how to do certain things.  On the Desktop, on the upper right corner of the screen you will see a bunch of text regarding how much memory you have, how much swap you are using, IP address, etc., and there should be an entry title "version" or something. 

Once we know what version of DSL you have, I can guide you better. 

BTW, my last post was the one to follow regarding steps needed - I edited to the correct steps after trying things while booted to a live cd.

MarshaG.

How fast does this computer run?  How much RAM?  How big is the hard drive?

---

### Post by princerameses on 2010-07-03
It has 96 MB RAM, not sure how big HD is. Like 7 GB if that.

It says 2.4.31, but that seems way older than it should have been.. 

Anyways, I want to thank you for all your help. I got this computer online. :D though not wirelessly. :( 

I forgot I had a spare ethernet port from an old scrap computer. I put it in and away I went. 

But one more issue- How do I install the flash player/ get sound? That was always a doozy with linux distros for me. 

Oh and do you know if I could get the chromium browser? (google chrome)this old FF isn't very good.

And for the partition, I'm not 100% sure, but I think I'm using the entire HD. I installed veector along time ago, then DSL over it using the partitions from the vector install I think. And it didn't tell me any specifics when I installed DSL.


And being online with damn small, well... It's a bit slow. So I was thinking about looking into antiX and see if that might work a bit better. Someone said it made their ancient laptop go quit fast. :D

---

### Post by marshag63 on 2010-07-03
2.4.31 is the latest kernal that DSL used - so you must have dsl4.4

You will need to find DSL's module for flash *currently version 7 flash* and install via the myDSL module installation system.

As for chrome - I doubt it.  You have a pretty old computer with low ram- that might be too much to expect.  You will have to compromise eye candy for functionality.  There is a lighter version of firefox - the name escapes me at the moment, but I just played with it in a live cd I was trying.  

AntiX needs 128 MB to run.  However, Slitaz has a low ram iso.  I was impressed with it when I tried it - flash and all.  Any idea what your processor speed is?  I'm guessing around 400 Mhz?

As for sound in DSL, you need to download alsautils from the myDSL modules - search the DSL forum for install sound.

Glad you found a network card to use -makes life a bit easier huh?

If you are interested in giving Slitaz a try, here are a couple of links:

[http://www.slitaz.org/en/about/index.html](http://www.slitaz.org/en/about/index.html)

[http://www.slitaz.org/en/get/flavors.html](http://www.slitaz.org/en/get/flavors.html)  --I recommend the lowram.iso if you decide to install

Once you understand how to install the myDSL modules, its pretty easy.

Let me know your processor speed as I may have other suggestions.

MarshaG.

Ooo- just found Absolute linux - looks like it will run on you machine and uses Chrome!

[http://www.absolutelinux.org/index.shtml](http://www.absolutelinux.org/index.shtml)

---

### Post by princerameses on 2010-07-03
I think I installed swiftfox, but I can't find the program to access it.

Oh. :( 
I've tried slitaz before, and wasn't extremely impressed, but it was a long time ago. :)

I think the processor is 333. Computer is a compaq presario 5050.

I'll look at modules, I'm sure I will have difficulties. =x

---

### Post by princerameses on 2010-07-03
Ok, I couldn't find anything on modules but I did find apps. But I didn't see anything on flash...

While browsing I came to a page that said "install missing plugins" and I did that, and it said it was successful, but no flash. ;.;

Tried twice. 

UGH. I hate linux sometimes.

---

### Post by marshag63 on 2010-07-03
you found a myDSL module for swiftfox?

there are a lot of modules, but you won't be getting the newest latest greatest because the kernel is 2.4.X based and not 2.6.X.  Like I said, you will have to comprose flash looks and eyecandy for functionality.

Let me go reboot my DSL cd and see if I can find swiftfox in the mydsl modules.  For DSL, you download from the DSL repository of modules as they are compiled specifically to work in DSL.

Check back in 10 minutes or so.  :)


MarshaG.

---

### Post by princerameses on 2010-07-03
How do I get to the module repository again? 

And can it be updated? This is the first time connected to the internet, bear in mind.


So, what do I do for getting flash?  I am really confused. o.o;

---

### Post by marshag63 on 2010-07-03
Can you get on irc?  Go to the damnsmalllinux forum and we can walk through this.

MarhsaG.

---

### Post by princerameses on 2010-07-03
Irc?


I suppose I could try DSL forums, it's just I'm sure it's dead which is why I came here. ;)

I'll make an account.

---

### Post by marshag63 on 2010-07-03
Yeah, its pretty quiet here.  Just start up nIRC and it will bring you to the forum.

marshag.

---

### Post by princerameses on 2010-07-03
Went there and made an account. (rameses)

Wow. O.O It's REALLY dead on those foums... I think my best bet is to stay here.. What topic? I'm not seeing much if any activity on all of them.

---

### Post by marshag63 on 2010-07-03
I'm in the IRC channel #damnsmalllinux

Click on the DSL menu button (lower left corner of your screen)
Then Apps > Net > AIM/IRC/ICQ > nIRC 

I will also start making instructions here for myDSL repository.

Be back in 5 minutes or so.

MarshaG.

---

### Post by marshag63 on 2010-07-03
To get to the myDSL Browser (how you install apps for DSL).

Click on DSL menu (lower left of screen - says "DSL"

Go to entry "MyDSL" (second from top of that pop-up menu)

Slide mouse pointer to the right to "My DSL Browser"

You should now have a window open titled "MyDSL Browser" and the first button on the left hand top of the diaglog box says "Update Database" so go ahead and click on that and let it do its thing - may take 5 to 10 minutes for your machine.


As an aside note, I use Firefox with a plug-in called "Video Downloadhelper" which downloads flash videos for you into a folder "DWHelper" which you can then play back with mplayer or vlc or whatever, but that's just my opinion.

I'm trying to work through flash for DSL - I'm not having much luck so far.

Let me know when you have found the MyDSL Browser and updated it.

MarshaG.

---

### Post by princerameses on 2010-07-03
I'm sorry, it messed up. I was typing 27, but num lock was on and it started talking about nickserver..

---

### Post by marshag63 on 2010-07-04
[http://i49.tinypic.com/rm5t03.png](http://i49.tinypic.com/rm5t03.png)


[http://i50.tinypic.com/2n19649.png](http://i50.tinypic.com/2n19649.png)

---

### Post by marshag63 on 2010-07-04
[http://i47.tinypic.com/2wh03vd.png](http://i47.tinypic.com/2wh03vd.png)

---

### Post by princerameses on 2010-07-04
[http://i47.tinypic.com/2qtl1xg.jpg](http://i47.tinypic.com/2qtl1xg.jpg)

---

### Post by marshag63 on 2010-07-04
I did find some instructions for flash in DSL:

How do you install adobe flash player in Damn Small Linux?

The version of Firefox bundled with Adobe Flash Player is too old to support newer versions of Adobe Flash Player. The last version that will work with it is version 7. You can use it by downloading the .tar.gz file, extracting it (tar xvvf nameoffile.tar.gz), and copying the plugin (a .so file) to /usr/lib/mozilla/plugins.  

You could also install minimal ubuntu, but I'm not sure you are ready for that yet.

MarshaG.

Addendum:  I had to putthe resulting *.so file in /usr/local/firefox/plugins (I had to be root to do this) , but still not working - maybe you will have better luck.


Max out your ram to 256 MB and you could possibly get Absolute linux (with chrome) or Dreamlinux to go.

---

### Post by princerameses on 2010-07-05
DANGIT.
I had a message all typed up and my computer all of a sudden restarted. o.o Right before I was going to send it.

Anyway- 

Why wouldn't I be ready for Ubuntu? ^-^ I've had it before, and it was of the easiest distros I've used.

And tried to upgrade RAM, but I got the wrong one, so that wasted me money, now I kindof don't want to spend any more on it. XD

Hmm.. I wonder why it's so hard to get flash? :x Any other options that require little RAM? What about those floppy distros? Or are those complicated to install?

'Cause I really need flash and a better browser.

---

### Post by marshag63 on 2010-07-05
Princerameses, I think your best option is Slitaz for a "ready to go" install - you should be able to get flash working easily, plus it works great on older hardware like your Compaq Presario with 96 MB ram.

I'm not sure I could walk you totally through starting with a minimal/base ubuntu install and get you to working flash.  What kind of desktop environment/window manager would you want to use?  Gnome and KDE would be way too heavy?

If you can get slitaz and give it a try, we will see what you think and go from there.

lucyisssi, why did you sign my name to your post?

MarshaG.

---

### Post by princerameses on 2010-07-05
lol.

And, sorry, I forgot about my 4th of July plans. ;_;

Do you think ubuntu would work as good or better as damn small?

I got slitaz (low ram). I tried it on one of my good computers and couldn't quite get the wireless to work. I tried twice. Yesterday it said it was connected and it should have been working but today I couldn't even get it to say that. (I was using linksys adapter) Any idea how to configure the wireless? Again, it's not necessary, but I *would* like wireless so I don't have to keep unplugging and moving my monitor/ mouse/ keyboard to another room.

And about graphical environments- Which do you think would be best? I don't like the one slitaz uses; I find it a bit clunky. 
I like the one puppy uses. But which ever you think would be best. then how do I change it on slitaz? Is it possible?

After I give it a try on the old computer to see if it even works, I'll try ubuntu on it. (if slitaz isn't gonna do it)

---

### Post by marshag63 on 2010-07-05
princerameses, slitaz will work well for you, with flash (easy to install - see links)  :)

Slitaz install flash:  [http://www.youtube.com/watch?v=-IHj9UDok_0&feature=PlayList&p=208CA99ED2E18645&playnext_from=PL&index=4](http://www.youtube.com/watch?v=-IHj9UDok_0&feature=PlayList&p=208CA99ED2E18645&playnext_from=PL&index=4)


other tutorials for slitaz:  [http://www.youtube.com/view_play_list?p=208CA99ED2E18645&annotation_id=annotation_935636&feature=iv](http://www.youtube.com/view_play_list?p=208CA99ED2E18645&annotation_id=annotation_935636&feature=iv)

marshag

will be haning out in slitaz IRC forum for a little while

---

