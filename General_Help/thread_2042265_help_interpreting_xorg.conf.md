---
title: "help interpreting xorg.conf"
date: 2012-08-14
forum: General Help
---

### Post by SteveHillier on 2012-08-14
I have been getting nowhere using AMD Catalyst Centre to configure 4 screens on my system.

Hardware set up
ASUS m/b with onboard graphics
2 x Sapphire HD5450 graphics cards - one in 16x PCIe slot, one in 4 x PCIe slot.
Have downloaded and installed fglrx drivers from reposititories.  I can get two monitors working together sometimes and whilst I can get the third monitor accepting the cursor it does not display any real output.

I am trying to configure my displays using the Cataylist Control Centre but it fails because I cannot seem to 'control' anything with it.  I can change settings but it then goes off and does it's own thing which is not what I want.

I feel the only resolution is to configure xorg directly through xorg.conf and even having read the 'man' pages I simply cannot understand what is going on.

In the above text I have used the words 'screen', 'monitors' and 'displays' very deliberately because you all know that I mean the physical piece of hardware that shows me output can be described using all these words, however for the life of me I cannot understand how monitor, screen and display are interpreted in xorg.conf

PLEASE NOTE: the config files beloew have been produced using amdcccle and have not been edited manually.

Let me add one of the config files I have got

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 1024 0
	Screen         "aticonfig-Screen[1]-0" 0 0
EndSection

Section "Module"
EndSection

Section "ServerFlags"
	Option	    "Xinerama" "off"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[1]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Monitor"
	Identifier   "0-CRT1"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1440x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "1440 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "0-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1440x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "1-Default monitor"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1440x900"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Monitor"
	Identifier   "1-CRT2"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
	Option	    "PreferredMode" "1024x768"
	Option	    "TargetRefresh" "60"
	Option	    "Position" "0 0"
	Option	    "Rotate" "normal"
	Option	    "Disable" "false"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "Monitor-CRT1" "0-CRT1"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[1]-0"
	Driver      "fglrx"
	Option	    "Monitor-CRT2" "1-CRT2"
	BusID       "PCI:2:0:0"
EndSection

Section "Device"
	Identifier  "amdcccle-Device[1]-1"
	Driver      "fglrx"
	Option	    "Monitor-CRT2" "0-CRT2"
	BusID       "PCI:1:0:0"
	Screen      1
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Virtual   2880 2880
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[1]-0"
	Device     "aticonfig-Device[1]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "amdcccle-Screen[1]-1"
	Device     "amdcccle-Device[1]-1"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection


```

OK back to some detail.

Lines 76 - 97 give me some devices.  I assume these are the graphics adapters.  Assuming the BIOS has diabled the onboard graphics.  I can see why I get two devices on bus PCI1 and PCI2. but why do I get one device identified as "amdcccle-Device[1]-1" and two others as "aticonfig-Device[0] -0" and "aticonfig-Device[1] -0".  Why is line 94 identical to line 80.  Surely that either confuses or overrides!

Lines 14 to 74 describe some monitors.  6 are described but at the moment I only have 3 on the system

The second config file I have got differs only in the server layout section

```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Screen         "aticonfig-Screen[1]-0" 2880 0
EndSection

```
but I don't understand the meaning of the differences. 

Can someone please give me the idiots guide to xorg.conf or at least give me some pointers as to how to correct these files and get it doing what I want it to do.

I shall be ditching the Catalyst Control Centre if I can get this to work.

Many thanks in advance to anyone who can help.

---

### Post by QIII on 2012-08-14
When you initialized your adapters after installing, did you do

```
sudo aticonfig --adapter=all --initial
```?

If you didn't, only the first enumerated adapter would have been initialized.

It appears as though you may have, but I just want to be sure.

---

### Post by SteveHillier on 2012-08-14
Hi QIII,
Yes I did do the initialise as you suggest.
Both adapters are in xorg.conf as you can see the PCI bus addresses.
Just to give you some comfort, I have had several attempts at this and this last attempt was a clean install of 12.04, immediate updates, the driver installation as in the wiki you promote in your signature - being very careful to not make any silly mistakes.  
The rest I have tried to do through andcccle with the results above.

Many thanks for you response.

There are so many threads on this and similar subjects and I am just wondering if amdcccle is doing what it should do in the background of not.
Steve

---

### Post by QIII on 2012-08-14
OK.  Please don't take these first few questions as indictments of your experience or intellect.  Just ruling out the "face-palm" things we all do from time to time.

You are using the administrative mode in CCC?

---

### Post by SteveHillier on 2012-08-14
QIII,
I did not take any offence at your question but just to make sure and for the benefit of others who might look at this thread I laid out chapter and verse.
Yes I did use administrative mode.

---

### Post by SteveHillier on 2012-08-14
QIII
Warming to my theme I have done enough programming to realise how easy it could be for amdcccle not to overwrite or delete segments but simply added new ones in areas it knows about.  The "I know about this one because I put it there" type of thing.  And the "don't mess with things I now nothing about" cautionary tale.
I recall way back in MS-DOS days someone coming up pleased as punch saying how he had now written a routine the change the system clock - and how crestfallen he was when I asked whether he had reset the real time clock or just the software clock.
As I have just put in a different post - I am not saying it is but 
maybe, just maybe.  And I don't have the expertise or understanding to know if this is the case.

---

### Post by QIII on 2012-08-14
That's why I like to ask one question at a time.  Easier to follow for someone else later!

In the Catalyst Control center, under "Pages", "Display Manager" on the "Multi-Display" tab, do you have "Multi-display desktop with displays(s) x" selected?  (In your case x should be 4).

---

### Post by SteveHillier on 2012-08-14
Hi,
Sorry, I have had to come into the garage to check.
In the display manager at the moment becuase I have yet to connect up the last monitor I have the following

If I highlight:-
the first display it reports "Multi display desktop with display(s) 2"
the second display it reports "multi display desktop with display(s) 1"
the third display it reports "Single display desktop (Multi-desktop)" and there is no option in the drop down box to select "Multi display desktop" for this display.

I have read this as "Display 1 knows it is sharing space with display 2 but not display 3; Display 2 knows it is sharing space with display 1 but not display 3; and display 3 knows he is "Billy no mates".

I did not get the "Multi display desktop" option on any monitors until I plugged a monitor into both ports on a single card.

---

### Post by QIII on 2012-08-14
Come to think of it, you are right.  I'm on a cell phone right now doing this from memory.  I have multiple cards on two machines, but I run them for GPGPU and don't currently have monitors attached to any but the first card.

I didn't pay enough attention to you xorg.conf or I'd have noticed only three monitors.

Now is the point where I ask if you have Xinerama enabled, since I don't see it in your xorg.conf.  Don't change anything.  Just a question.

This is also the point at which I tell you that you are going to make me have to add more to the wiki.

---

### Post by SteveHillier on 2012-08-14
Hi QIII
hope I am not running up your cell phone bill too much.

Ok, So I found another monitor and plugged it so now
On card 0 I have monitor 1 & 2 which are sharing the same space.
On card 1 I have monitor 3 & 4 which are sharing the same space, but they do not share the same space as monitors 1 & 2
by enabling Xinerama I can now see and move across all monitors.

So at the moment I have what I need to have.

So it appears that you cannot share across adapters unless Xinerama is enabled and the use Xinerama is deprecated.  In fact your wiki from memory explicitly says to disable Xinerama.

Because of the groupings of the monitors you have to use monitors attached to adpaters as a single entity not what I really wanted but I will have to live with it.

It does beg the question What if I don't use multi display desktops but simply attach all four monitors and enable Xinerama.

QIII, many thanks for your input.  You might feel you will have to update your wiki.  I will experiment as per the last paragraph and post back.  I might even write - not a "How to", but a "how I did it" thread.

Steve

---

### Post by SteveHillier on 2012-08-14
Now I have got this far and for my next trick....
I am unfortunate enough to have to run a Windows machine - a lot of my clients still use it!
At the moment on my production machine I use my two monitors on both machines across a KVM switch.
When this machine become my production machine the aim is to use monitors 1 and 2 shared via the KVM and leave 3 and 4 solely for Ubuntu.
I must be crazy!!
Maybe I should tell people how I get on before I get locked away for public safety reasons!!

---

### Post by QIII on 2012-08-14
Is the suggestion not to use Xinerama in the text of the wiki itself or in one of the links?  I suggest turning it off in single card applications.  Xinerama isn't deprecated, exactly.  I don't think so, anyway.  The effort to make it a standardized API has been abandoned.

By the way...

How Tos are being eliminated in favor of the wikis.

If you do a How I Did It, either add it here or update the wiki directly. 

If you add it here let me know and I'll come by and find what you have to weave it into the wiki.  

The wikis are a community effort, not the work of one member!

---

### Post by SteveHillier on 2012-08-14
I may owe you an apology.  I have just done a text search for Xinerama in the wiki and it has not come up.  I must have picked it up from some other post.

---

### Post by QIII on 2012-08-14
Meh.  No apology needed!  I was just furrowing my eyebrows trying to remember if I had seen that.

In a recent post I did suggest to someone to turn it off.  But that was on a single card as I recall.

By the way, the only thing not unlimited about my cellphone service is battery life!  ;)

---

### Post by SteveHillier on 2012-08-15
Thanks to QIII for all his help is sorting this out

This is a &#8220;How I did it&#8221; post.

What I was trying to produce.  A system with 4 monitors across two graphics cards.

Before you start make sure you have referenced ['The Community ATI Driver Wiki']("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

Also remember that on each graphics card the monitor attached to the DVI port will be monitor 1 and the one attached to the VGA port will be monitor 2.

I used the Alternate command line method taken from the wiki but amended for my needs

**Process**

Clean install of 12.04
Ran system updates
Opened terminal and ran the following command
```
sudo apt-get install fglrx fglrx-amdcccle
```
When this completed I ran the following
```
sudo aticonfig --adapter=all --initial
```
I then rebooted
After reboot you may find that the monitors attached to the second graphics card are white &#8211; ie no desktop.  Do not get concerned about this at this stage.

Immediately after reboot I ran &#8220;settings->displays&#8221; from the menu bar.  By default the launcher is displayed on all displays.  Click on the drop down and change it so that the launcher appears on the screen you want (unless you want it on all displays).  You need to do this at this stage because once you have configured everything with Catalyst Control Centre this method of changing display settings with not be available to you.  Click 'Apply' to complete the settings.

I now used Catalyst Control Centre to make all other settings

In Catalyst Centre under &#8220;Pages&#8221; there is a tab &#8220;Display Manager&#8221;  Click on this and all attached monitors should be listed.  
Most likely each monitor with be listed as &#8220;Single Display (multi desktop)&#8221;

IMPORTANT.  You can set up monitors so that a desktop has a &#8220;multi display&#8221; status and you can set it so that monitor 1 shares with monitor 2 and so that monitor 3 shares with monitor 4 BUT YOU CANNOT get all 4 monitors to share the same desktop space.

OK now I have two arrangements.

**Arrangement 1 (4 monitors with two desktop spaces &#8211; monitors shared as multi display desktops)**

Using Catalyst Control Centre and the &#8220;Display Manager&#8221; click on monitor 1.  Use the drop down box to select &#8220;Multi Display desktop with display(s) 2&#8221;.  If you look at the display layout graphic you will see the two monitors joined with a dotted line.  These two monitors are a single desktop space extended across the width of the two monitors.

Repeat this procedure for monitors 3 and 4.
Configure the layout of the displays in the layout graphic to suit your needs but remember if the displays are linked they will travel together.  So you can move displays 1 and 2 as a single entity and displays 3 and 4 as a single entity.  This does rather restrict your options.

There is still no output on displays 3 and 4 but don't worry.  Click any &#8220;Apply&#8221; buttons to confirm these settings.  You will get a warning that a reboot is required but leave this at the moment.

Now on the &#8220;Pages&#8221; section of CCC click to expand the &#8220;Display Options&#8221; (note to self to confirm this title).  Select &#8220;Xinerama&#8221; and enable this option.  Again you will get a warning to reboot.

Reboot.  After reboot you should have all four displays working.  I noticed that I only had the BIOS splash screen on monitors 1 and 2 and during system load up displays 3 and 4 did not display a normal desktop until X is fully loaded and you are ready to log on.

**Arrangement 2 (4 monitors with four desktop spaces &#8211; monitors set as &#8220;Single display (multi desktops)&#8221;**

In this arrangement I have not used multi display desktops.

I used CCC to place the four monitors where I wanted them.  There is still no output on displays 3 and 4 but don't worry.  Click any &#8220;Apply&#8221; buttons to confirm these settings.  You will get a warning that a reboot is required but leave this at the moment.

Now on the &#8220;Pages&#8221; section of CCC click to expand the &#8220;Display Options&#8221; (note to self to confirm this title).  Select &#8220;Xinerama&#8221; and enable this option.  Again you will get a warning to reboot.

Reboot.  After reboot you should have all four displays working.  I noticed that I only had the BIOS splash screen on monitors 1 and 2 and during system load up displays 3 and 4 did not display a normal desktop until X is fully loaded and you are ready to log on..

**Final notes**

I have chosen to use arrangement 2.  I have done this because I want better control over the positioning of each monitor.

Using arrangement 1 I set up my monitors in CCC thus

|  3  |  4  |  1  |  2  |

(the fact that on the ground they were arranged  |  3  |  4  |  2  |  1  | did cause an awful lot of confusion.)

However in this linear arrangement there is a lot of mouse travel to go from one side to the other.

Now you could use &#8220;Settings -> Displays&#8221;  to change the order of displays 1 and 2 so that 2 is on the left and 1 is on the right but you cannot use this method to switch displays 3 and 4.

I don't know at this moment  what final arrangement the displays will be on the ground.  I could use 

|  3  |  4  |
|  1  |  2  |

This arrangement probably works with multi display desktops but I have not tried it but it does work OK with single display desktops.

I think however, that the final arrangement of my displays will be

|  3  |  1  |  2  |  4  |

This should allow me to use displays 1 and 2 (which are my 22&#8221; screens) as my main work space but shift other pages to the wings (19&#8221; screens) without having excessive mouse travel.

This final layout cannot be configured using multi screen desktops because it separates displays 3 and 4.  You will have to arrange your displays as single displays.

REMEMBER that in order to use the displays on the second graphics card you MUST enable Xinerama.

I don&#8217;t think this has helped my understanding of xorg.conf but at least I can configure all my displays as I want them.

Good luck.

---

