---
title: "Still Stuck in Screen Resolution 800x600"
date: 2010-01-12
forum: General Help
---

### Post by sarum on 2010-01-12
I upgraded to 9.10 some months ago and I have tried all the suggestions I can find on your forum to alter the resolution. I've done stuff on the consol I never thought I could, and inserted lines in xorg.conf via gedit. I've tried alsorts. But no luck. I've small Hp Compac and a flat screen Dell E151 FPb. Previously I had Hardy Heron and it all worked very well; I started off with 6.06 (years ago)and have been a keen Ubuntu type - till now.
Off topic; I spend (spent) a lot of time playing cards. 9.10 lacks Free Cell and FireFox>tools>[COLOR="Magenta"]cards[/COLOR] is nolonger there.
From the number of threads and answers 'Screen Resolution' has been, or in my case, still is a problem with 9.10. My question:- is this problem going to be fixed in the next issue. Which is April, I think. If it is then I shall wait. If not I suppose..........another computer or screen... but that rather defeats the aims of Ubuntu.
Grateful for any help or suggestions.....sarum

---

### Post by fancypiper on 2010-01-12
What is your graphics card?

[Getting the Best Help on Linux Forums](http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/)

---

### Post by kenaniah on 2010-01-12
Okay, well I solved the same problem with mine a couple of ways....


I found three possible drivers for m Nvidia GeForce card listed under "hardware drivers", and the second install solved the problem. But I had to run the update manager again first.

But there are some graphics hardware not fully supported yet (I had to remove my ATI Radeon for that reason...)

Hope this helps:D

---

### Post by Techsnap on 2010-01-12
> But there are some graphics hardware not fully supported yet (I had to remove my ATI Radeon for that reason...)

You most certainly did not! What issue were you having, it's likely we can fix it.

---

### Post by sarum on 2010-01-13
Thanks all for your replies. Via system>admin>system testing, I found that the answer is VGA1. I'm wondering if this is the correct way to find the info: required. Having boasted of my use of Ubuntu since mid'06, you may assume that I'm a slow learner, though I've not encountered this sort of problem before. I'll google VGA1 and see what I can find. If any of you would care to add further help as to how to proceed I shall be very grateful.
Fancypiper's link has been bookmarked and read..........thanks.

---

### Post by fancypiper on 2010-01-13
Open a terminal and command **lshw|less**. Scroll down until you find your video card.

---

### Post by sarum on 2010-01-13
Thanks for your reply, herewith the (part) result of lshw|less:-
    clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: 82945G/GZ Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e0400000-e047ffff ioport:10c0(size=8) memory:d0000000-dfffffff(prefetchable) memory:e0480000-e04bffff
        *-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
I look forward to hearing from you....cheers sarum

---

### Post by fancypiper on 2010-01-14
That video chip may not be supported. Check here:

[Ubuntu Hardware Support]("https://wiki.ubuntu.com/HardwareSupport")

---

### Post by sarum on 2010-01-15
Thanks fancypiper, I've had a quick look at that link and I'll go into it more this evening. I have also googled the 82945G/GZ, and there's plenty there to examine.
I'd be interested to know Techsnap's opinion - if he's still following this thread - he was well confident it could be sorted in a previous reply to my question.
Thanks for all the help so far..........sarum

---

### Post by fancypiper on 2010-01-15
He was replying to kenaniah who had an ATI Radeon video chipset. However, see the post below. You and the other poster have the same video card.

I got a notification that drivers were available for my nVidia card.  I wonder why you aren't notified for the intel card?

---

### Post by Jackzor on 2010-01-15
I found this through google. It seemed to help another guy with drivers

sudo apt-get update && sudo apt-get install xserver-xorg-video-intel

And

[http://newyork.ubuntuforums.org/showthread.php?t=1318856](http://newyork.ubuntuforums.org/showthread.php?t=1318856)

---

### Post by sarum on 2010-01-16
Hi Jackzor thanks for your reply. I'm a longtime newby and I'm old, so here's what I got:-
[sudo] password for cjf: 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic Release.gpg
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic/main Translation-en_NZ             
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic/restricted Translation-en_NZ        
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic/universe Translation-en_NZ          
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic/multiverse Translation-en_NZ        
Get:1 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic-updates Release.gpg [189B]        
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic-updates/main Translation-en_NZ      
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic-updates/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic-updates/universe Translation-en_NZ  
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic-updates/multiverse Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic Release                             
Get:2 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic-updates Release [44.1kB]          
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_NZ
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_NZ
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_NZ
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_NZ
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [44.1kB]
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic/main Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic/main Sources 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic/restricted Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic/universe Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic/universe Sources
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic/multiverse Sources
Get:5 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic-updates/main Packages [134kB]
Get:6 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic-updates/restricted Packages [14B]    
Get:7 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic-updates/main Sources [41.7kB]        
Get:8 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic-updates/restricted Sources [14B]     
Get:9 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic-updates/universe Packages [84.4kB]
Get:10 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic-updates/universe Sources [20.9kB]   
Get:11 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic-updates/multiverse Packages [6,942B]
Get:12 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) karmic-updates/multiverse Sources [3,831B] 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [46.4kB]       
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B]    
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [13.2kB]        
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]     
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [21.1kB]   
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources [3,944B]    
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [1,666B] 
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources [575B]    
Fetched 467kB in 19s (23.6kB/s)                                                
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg-video-intel is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
cjf@cjf-desktop:~$ 

'apt-get autoremove' on it's own sounds dangerous. Am I right in thinking that it should be followed by a space then "linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic"? Without the " ".
Then what's next.
After doing the terminal thing above, I was immediately advised to up date; which I have done. Now a restart is required - how nice it would be to get back to an acceptable resolution. This is a common problem with 9.10, and there seem to be solutions, but not one specific to my setup.
Thanks again.......sarum

---

### Post by Yellow Pasque on 2010-01-16
Post your /var/log/Xorg.0.log file so we can see **WHY** you're stuck in 800x600. Remember to use [ CODE ][ /CODE ] or pastebin when pasting all that text.

---

### Post by sarum on 2010-01-16
cjf@cjf-desktop:~$ sudo /var/log/Xorg.0.log file
[sudo] password for cjf: 
sudo: /var/log/Xorg.0.log: command not found
cjf@cjf-desktop:~$ 

Thanks for your reply. Above is the result - am I doing something wrong.
Sorry, I didn't understand what you meant by:-
Remember to use [ CODE ][ /CODE ] or pastebin when pasting all that text.
Cheers sarum..

---

### Post by sarum on 2010-01-16
I,ve been to file system and found the file;
            /var/log/Xorg.0.log
            /var/log/Xorg.0.log.old
            /var/log/Xorg.1.log
            /var/log/Xorg.1.log.old
The first one's the one you asked for and I see what you mean about all that text. I'll await your instructions as to how to post it.
Cheers,,,,,,,,,,,,,sarum

---

### Post by Yellow Pasque on 2010-01-16
Use pastebin... [http://ubuntu.pastebin.com](http://ubuntu.pastebin.com)

---

### Post by sarum on 2010-01-17
Posted...sarum

---

### Post by stoneage on 2010-01-17
[http://ubuntu.pastebin.com/m4e893965](http://ubuntu.pastebin.com/m4e893965)

It looks like you need to add a modeline with the correct horisync and vertrefresh rates to the xorg.conf?

---

### Post by sarum on 2010-01-18
Thanks; to obtain my correct settings, I did the following sometime ago.

cjf@cjf-desktop:~$ cvt 1024 768 60
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

The 1024x768 I got from Dell E151 FPb site - 'optimal resolution'
From another 'solved resolution' thread I, (in short), inserted new horz & vert: via gedit. But it didn't work. I assumed that the VertRefresh is 59.92 and the Horizsync is 47.82.
I printed the 'solved resolution' and looking at it now I see that s/he got horiz as 99.46
vert: as 59.99
But when it came to altering things in gedit HorizSync became 49.31 - 98.71 and VertRefresh 60.0
I think I may be guilty of having printed/read only the first thread and thought 'this is it' without reading follow-ups.
Anyway, with all the info I've posted, I hope some one can see where I've gone wrong,,,,,,,,,,,,,sarum

---

### Post by perspectoff on 2010-01-18
Onboard Intel graphics cards have had problems recently, since the switch to UXA graphics.

I have a similar Intel graphics card and had the same problems with resolution in both Jaunty and Karmic.

I had to revert to an old driver from Intrepid. I used the solution I found at 

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

Everything works fine with the 2.4 driver.

---

### Post by roharme on 2010-01-18
As everyone said , it must be driver problem.
 
Update the driver.
 
Use gksudo to invoke nvidia config gui with root access and change the settings and save it

---

### Post by stoneage on 2010-01-18
> **sarum said:**
> Thanks; to obtain my correct settings, I did the following sometime ago.

cjf@cjf-desktop:~$ cvt 1024 768 60
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync


Did you add the refresh rates and the modeline?
I had a similar problem and had to add the refresh rates as well.
Mine looks like this, though I use an nvidia card:-
```
Section "Monitor"
    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       31.0 - 80.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
    Modeline "1440x900_75.00" 136.49 1440 1536 1688 1936 900 901 904 940 -HSync +Vsync 
EndSection
```

You can get the optimal resolution and the refresh rates from the manufacturers specification.
- just an idea, I don't know if it is the cure - ;)


EDIT - You could(at your own risk) try this one, based on the information from [here]("http://support.dell.com/support/edocs/monitors/E151FPB/En/specs.htm") and a refresh rate of 75
```
Section "Monitor"
        Identifier   "Monitor0"
        HorizSync    30 - 61
        VertRefresh  56 - 76
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
	Modeline "1024x768_75.00"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync
EndSection
```

---

### Post by mk1w86 on 2010-01-18
If the OP is still having problems take a look at this:

[http://ubuntuforums.org/showthread.php?t=1324239](http://ubuntuforums.org/showthread.php?t=1324239)

---

### Post by sarum on 2010-01-18
Thanks for your reply; I'd tried that link some weeks ago, but noticed that you had added in the modeline. Modeline is not mentioned on that particular 'HowTo' and so I gave it a go - and have ended up with 
                 'Can not display this Video Mode'
The get-out-of in the howto wont work either (sudo rm -f /ect/X11/xorg.conf : followed by : sudo /etc/init.d/gdm restart ; exit).
I'm writing this from a live CD - no problems here.(PCOS)
Any ideas as to how to recover the screen. My thanks to all who have been so helpful.......sarum

---

### Post by stoneage on 2010-01-18
gksudo gedit /etc/X11/xorg.conf then edit and resave, reboot. Hopefully....

---

### Post by sarum on 2010-01-19
Cheers that worked so I gave it one more try..............same result.
I'm about to give up, either live with 800x600 or go back to the Hardy Heron. I'm sorry to have wasted so many good peoples' time. I think I've tried them all, some more than once. Driver update and going back to Jaunty driver 2.4.
Thanks to you all, I'm a regular lurker on this forum and I always scan the 'HowTo'/'Solved' threads. May be something will turn up...sarum

---

