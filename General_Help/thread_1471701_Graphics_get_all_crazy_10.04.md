---
title: "Graphics get all crazy 10.04"
date: 2010-05-03
forum: General Help
---

### Post by alexpwnsn00b2 on 2010-05-03
hi everyone I'm running Ubuntu 10.04 on my Gateway netbook and everything seemed to be fine until my graphics went crazy. at first i thought google chrome was the problem but it continued while saving a document and browsing the ubuntu forum using firefox. here are images to help.

---

### Post by WorMzy on 2010-05-03
That is crazy. I'm not sure what's causing that, but how hot does the netbook feel? It could be that the graphics chip overheated. Try switching to a different workspace to see if it forces the display to update. If that fails, press Ctrl+Alt+F1 to go to a tty, log in, and use:
```
sudo restart gdm
```

NOTE: This will restart Gnome and you will lose any unsaved documents.

---

### Post by florus on 2010-05-03
What graphics card are you using?

---

### Post by DomesDKG on 2010-05-03
You could also be having a graphics card driver issue. Try using the hardware drivers tool, and updating the machine.

---

### Post by alexpwnsn00b2 on 2010-05-03
here are my computers specifications. the Netbook doesn't feel like its over heating and I also used the update manager to make sure i wasn't missing a bug fix. When i use vista everything seems fine and thanks for the tip WorMzy that should come in handy its kinda tricky using memory to find the areas to click when the graphics get all cracked out.

Processor: AMD Athlon™ 64 L110 Single-Core Processor (1.2GHz, 800MHz FSB, 512KB L2 Cache)

Operating System: Genuine Windows Vista® Home Basic (32-bit) with SP1

Display: 11.6” HD WXGA Ultrabrigh LED-backlit Display (1366×768 resolution, 16:9 aspect ratio)

Video: ATI Radeon X1270 graphics with 256MB HyperMemory

Memory: 2048MB DDR2 533MHz SDRAM Single Channel Memory

Hard Drive: 250GB SATA hard drive

Wireless Network: 802.11b/g Wi-Fi

Battery: 6-Cell Lithium Ion

Chassis: Chassis with ATI Radeon X1270 Graphics and AMD RS690E Chipset8
External Ports: (3) USB 2.0, VGA Connector

Keyboard and Mouse: Keyboard with Multi-Gesture Touchpad

Media Card Reader: Multi-in-1 Digital Media Card Reader (Memory Stick®, Memory Stick Pro™, MultiMediaCard, Secure Digital™, xD-Picture Card™)

Network: 10/100 Ethernet LAN (RJ-45 port)

---

### Post by Tadgh on 2010-05-04
I myself have a toned down version of the same problem. On 10.04, I get random horizontal lines shooting through the screen. Nothing to the OP's degree however.

The only similarity between out systems is the X1270, so I assume that is what is causing the problem. Is 10.04 more graphically demanding then 9.10?

I looked around on ATI's site for any new drivers, but apparently they consider it legacy, and as such they do not provide drivers for it. Is there perhaps an OSS alternative?

---

### Post by dino99 on 2010-05-04
sadly you are not alone with this problem: i've had no issue for months, yesterday have packages have been updated and today no way to boot, even in recovery mode startx fail. but try:

sudo dpkg-reconfigure xserver-xorg-core
sudo dpkg --configure -a

i'm posting from karmic now :(

---

### Post by k1llm3kw1k on 2010-05-04
I have the same issue and reported it since 10.04b1. It seems to be an issue with the OSS Radeon driver...you can go to the radeonHD driver but any emu will and games are super slow...

I think we need to report it to the maintainer of the OSS radeon driver....

Went back to 9.10 for now....love 10.04 on my desktop though!!

---

### Post by alexpwnsn00b2 on 2010-05-05
well at least i'm not alone.

I've noticed that the screen only freaks out when i'm on sties like myspace or using google chrome. idk if they use more graphics or something. 

I've also tried to switch screens to see if it forces my graphics to fix but that doesn't work at all. It sucks i really like Ubuntu 10.04 and i don't want to install the previous version.

---

### Post by LOCKPICK on 2010-05-05
just wanted to chime in, I picked up a netbook today and I'm having the same issue.
so far the changing of workspaces is a good temp fix.  
but if anyone comes up with something permanent I'm all ears.   

everything else is running great :KS I'm new to linux (10.04 is my first) and I'm already a total convert.

---

### Post by alexpwnsn00b2 on 2010-05-06
> **LOCKPICK said:**
> just wanted to chime in, I picked up a netbook today and I'm having the same issue.
so far the changing of workspaces is a good temp fix.  
but if anyone comes up with something permanent I'm all ears.   

everything else is running great :KS I'm new to linux (10.04 is my first) and I'm already a total convert.

what type of netbook did you get? Are any of the specifications the same as my netbook?

---

### Post by LOCKPICK on 2010-05-06
sorry ..... same same .... Gateway LT3112H
[B]
[/B]

---

### Post by k1llm3kw1k on 2010-05-07
I posted to the mailing list for xorg. They are trying some bug fixes and hopefully they will have a final fix and update the radeon driver soon. It seems to be an issue with KMS which is new in the kernel. This is more then just a Ubuntu issue. Stick with 9.10 for the time being.

---

### Post by TheHollowDeity on 2010-05-17
Im just curious if this issue has been resolved. Im running 10.04 on a Gateway LT3103u it contains the same ATI Radeon graphics card and is doing the exact same as the OP's.

Any help or advice would be awesome. As this issue is becoming quite annoying.

---

### Post by bluelamp999 on 2010-05-17
I'm no expert so treat the following with caution...

I had my display(s) go bananas similarly and I'm using an old-skool ATI card.

What worked for me was adding the line ```
GRUB_CMDLINE_LINUX="nomodeset"
``` to this file ```
/etc/default/grub
```

YMMV

Edit: you must run ```
sudo update grub
``` after editing your grub file

---

### Post by rodspi on 2010-05-23
I have a gateway LT3103u with a x1270 graphic chip. I may have found a fix.  Mint 9 is my OS.  I had the same graphic issues as the others have discussed in this thread and others. I tried reinstalling twice. The problem persisted.  In those three attempts when would select recovery mode (Failsafe X Session)on boot screen, the OS would boot to the maximum resolution 1366x768 (weird) not the scaled down 1024x768 resolution.  I then did another reinstall.  After the reinstall, I booted to recovery first.  Inserted the <GRUB_CMDLINE_LINUX="nomodeset"> in the grub config file as other in this thread suggested. Issued the grub update command then rebooted.  I selected normal OS selection.  I then open programs to try to see if the glitch would occur.  It didn't.  I rebooted to recovery mode(Failsafe X Session) and the typical 1024x768 resolution was now present. No issues in the last two days I hope the glicth does come back.  Also I have been install and update my system in the failsafe X session of recovery mode.

---

### Post by TieSKey on 2010-05-27
Same problem here with the same hardware.

Any update on the issue?

---

### Post by 5ampl3 on 2010-06-01
i have much the same issue with my instal of 10.04 amd64. im not sure what my servers hardware is but.....

if i start up lets say Tetris, or gnometris or w/e then the screen kicks to that funky screen covering pattern once i exit the game. seems to happen with any seemingly accelerated graphics program.

i was able to get back to a usable screen by pressing ctrl+alt+f1 to a virtual console and then back to ctrl+alt+f7 to a GUI desktop.

that seems to temporarily rectify the graphics bug. im guessing its a driver issue or some sort.

any thoughts? i am not sure where to start.

---

### Post by jjzone on 2010-06-01
> **5ampl3 said:**
> i have much the same issue with my instal of 10.04 amd64. im not sure what my servers hardware is but.....

if i start up lets say Tetris, or gnometris or w/e then the screen kicks to that funky screen covering pattern once i exit the game. seems to happen with any seemingly accelerated graphics program.

i was able to get back to a usable screen by pressing ctrl+alt+f1 to a virtual console and then back to ctrl+alt+f7 to a GUI desktop.

that seems to temporarily rectify the graphics bug. im guessing its a driver issue or some sort.

any thoughts? i am not sure where to start.

I enabled the Radeon HD drivers on my Gateway netbook with 10.04 and I have been running it for 2 days without a problem with graphics. It has even been suspended during this time without issue. I believe that the HD drivers (available via Synaptic) do not allow for 3d, but I am not sure about this as I do not use any 3d apps on the machine. I use the standard desktop, which is ok as long as there is no corruption with it.

Hope that helps.

---

### Post by cstorvold on 2010-07-04
I also have a LT3108h Gateway Netbook and since installing 10.04 Netbook Remix, I am having the very same graphics corruption as in the OP screenshots.  

I did not have this problem with 9.10, but I did have a problem with my wireless networking which is why I upgraded ASAP to 10.04, which fixed the networking problem but introduced the display corruption.

I will keep looking for a solution and post any findings.  Thanks.

---

### Post by cubicsilver on 2010-07-19
I have an LT31 with the same issue.  This is the closest I have seen to a fix so far.  It involves a 2.6.34 kernel changing some lines in the driver file and recompiling.

[https://bugs.freedesktop.org/show_bug.cgi?id=27529](https://bugs.freedesktop.org/show_bug.cgi?id=27529)

Look towards the bottom, there are 2 options: a patch or a mod of the driver file and recompiling.  

I haven't had the time to try either of these options out yet as my netbook is in pieces right now.

---

### Post by ELoXL on 2010-07-20
Well it appears in GRUB I'm still on 2.6.32, hence this may not be my cup of tea at the moment.  I'll wait until they release the kernals in their own time to implement the proper fixes.  This is really a pain in the ***.  I've never been more frustrated at software as I am with Ubuntu right now.

---

### Post by cubicsilver on 2010-07-21
You can always revert to 9.10 or 8.04.  Those versions do not have that issue.

I know that 9.10 works nearly flawlessly.

---

### Post by brumorino on 2010-07-22
> **bluelamp999 said:**
> I'm no expert so treat the following with caution...

I had my display(s) go bananas similarly and I'm using an old-skool ATI card.

What worked for me was adding the line ```
GRUB_CMDLINE_LINUX="nomodeset"
``` to this file ```
/etc/default/grub
```YMMV

Edit: you must run ```
sudo update grub
``` after editing your grub file


Wowwwwww this solve my problem in my gateway Lt31!
First time I tryed to do this, but my ubuntu didn't have the /etc/default/grub file! I don' t know why, maybe because i upgrade from 9.10 and something going wrong.
I reinstall today 10.04, and add the line ```
GRUB_CMDLINE_LINUX="nomodeset"
```, to the file that now i have (uhull) and solve my problem. Thank' s mann!!
Hugs from Brazil!
:D

---

### Post by ELoXL on 2010-07-25
@BRUMORINO 

Your slight insert into the GRUB file worked like a charm!  I suffer no more from the issues of tiling and scrambled screens!  I notice I run into the issue when I maximize any application window.  I opened my Tweetdeck, FireFox, Chrome, and Thunderbird client all to maximum as far as screen real-estate goes.  I suffered not one glitch or shutter in my UI experience.  

This truly is a fix guys and just so you know I am also running the 31xx series of the Gateway Netbook line.  I will also note that I am not running the netbook edition, but the full desktop OS on this little puppy (funny how I'm typing this in FF under Vista).  

Someone, anybody, everybody - get the word out for this fix.  If anyone knows of this issue being presented in LP please post this remedy on there as well - great find this one!

---

### Post by ELoXL on 2010-07-25
> **bluelamp999 said:**
> I'm no expert so treat the following with caution...

I had my display(s) go bananas similarly and I'm using an old-skool ATI card.

What worked for me was adding the line ```
GRUB_CMDLINE_LINUX="nomodeset"
``` to this file ```
/etc/default/grub
```YMMV

Edit: you must run ```
sudo update grub
``` after editing your grub file

> **brumorino said:**
> Wowwwwww this solve my problem in my gateway Lt31!
First time I tryed to do this, but my ubuntu didn't have the /etc/default/grub file! I don' t know why, maybe because i upgrade from 9.10 and something going wrong.
I reinstall today 10.04, and add the line ```
GRUB_CMDLINE_LINUX="nomodeset"
```, to the file that now i have (uhull) and solve my problem. Thank' s mann!!
Hugs from Brazil!
:D

The fix is here!  It works and I'm using the desktop version of 10.04 on my Gateway LT 31xx!!!!!

---

### Post by Saint Nick on 2010-07-26
I've had a similar issue trying to play Doom3 on Ubuntu 8.10 with a X1270 ATI Radeon.

[http://ubuntuforums.org/showthread.php?t=1526446](http://ubuntuforums.org/showthread.php?t=1526446)

---

### Post by lsutiger on 2010-07-26
I have a similar issue, but it is only in a web browser (FF/Opera/Chrome - all bad).
I am running an ATI Xpress 200M video card on my laptop.

Here's my previous post.
[http://ubuntuforums.org/showthread.php?t=1538742](http://ubuntuforums.org/showthread.php?t=1538742)

I will try this fix when I get home and report back

---

### Post by Saint Nick on 2010-07-26
> **lsutiger said:**
> I have a similar issue, but it is only in a web browser (FF/Opera/Chrome - all bad).
I am running an ATI Xpress 200M video card on my laptop.

Here's my previous post.
[http://ubuntuforums.org/showthread.php?t=1538742](http://ubuntuforums.org/showthread.php?t=1538742)

I will try this fix when I get home and report back
---
Actually, your video is not too bad.  With my video I have strips of uniform color but no discernible images. I haven't even been able to get a successful screen shot otherwise I would show you.

---

### Post by lsutiger on 2010-07-26
> **Saint Nick said:**
> ---
Actually, your video is not too bad.  With my video I have strips of uniform color but no discernible images. I haven't even been able to get a successful screen shot otherwise I would show you.

WOW! Yes, mine is not as bad, but sometimes I get get what you are talking about...again, only in a web browser.

---

### Post by Saint Nick on 2010-07-26
That's the thing.  My browser is fine but for some reason doom3 and quake4 go crazy.

---

### Post by lsutiger on 2010-07-26
Attached is a better representation of what happens

---

### Post by phatpig on 2010-07-26
Hi,

I just tried this, but am getting the error:

sudo: update: command not found


Can anybody help?

---

### Post by aidenscool09 on 2010-07-26
You need to do ```
 sudo apt-get update 
```

---

### Post by aidenscool09 on 2010-07-26
And i also had the same problem when i tried overclocking my graphics card and it does that because the power supply isn't strong enough. So it may be the processor adjusting itself (laptops and netbooks do this) and not getting enough power. Or it may be the same thing with the graphics CHIP. This is usually the case with OEM PCs. And i said graphics chip because netbooks and laptops have graphics chips and not cards.

---

### Post by phatpig on 2010-07-26
thanks aidenscool09,

Will that also update the grub?

I keep getting the command not found error when I am trying the 

"update grub"

---

### Post by aidenscool09 on 2010-07-26
What are you trying to update GRUB for? It won't make any difference to the performance. It's only the Bootloader. I think you are thinking of updating your kernel. But i wouldn't go compiling it yourself. It takes about 2 hours to configure it and at least 2 hours to compile. And you probably have the latest kernel version anyway.

---

### Post by aidenscool09 on 2010-07-26
And if you do want to update your GRUB then do 
```
sudo update-grub
```

---

### Post by phatpig on 2010-07-26
ahh, thank you so much.  :) 

Worked like a charm.

---

### Post by aidenscool09 on 2010-07-26
I still don't see how updating you GRUB configuration has to do with your graphics problems.

---

### Post by aidenscool09 on 2010-07-26
Or did you sort the problem?

---

### Post by phatpig on 2010-07-26
You were so right about the grub.  Hasn't fixed any of my graphic issues.
 
I have no clue where to start. What would cause graphic problems before is ok, but my graphics are hit and miss.

---

### Post by ELoXL on 2010-07-27
First of all no one said that updating the kernal would fix anything.  I  was just letting you know what I was hoping for with an updated kernal  ready for download, 2.6.32-24-generic, that my system recognized.  I  said that IT DIDN'T WORK.  Since that is cleared up I will proceed to  reiterate what it was brumorino suggested.

I will admit brumorino wasn't too clear in  his instructions, but I reckon it was understandable if you're willing and patient to give it a shot.

Within terminal just type the following:

sudo gedit /etc/default/grub
It will then ask you for your password, so do the obvious

You should see window pop up, GRUB file, that will allow you to edit the contents.

GRUB_DEFAULT=10
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=15
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="[COLOR=Red]nomodeset[/COLOR]"

You will notice the red text is what you need to insert in-between the quotes that will originally have not nothing in-between the quotes on the GRUB_CMDLINE_LINUX= line.

Be sure to select the "Save" button within that window and you will be good to close it from there, BUT....

You must update it within terminal for it to take effect.  Within terminal type the following:

sudo update-grub
 
From there you will see some stuff going on; I reckon applying the changes to the file.  Once you see you "done" and your typical terminal prompt appear you should be good to go.  Reset your netbook and godspeed.  This worked for me and I hope it does for you.  I'm more than glad to help out, but I will claim I am no genius; each one teach one. :p

---

### Post by mansourk on 2010-07-27
Hi,
I have some similar problem, when i move a window in the screen some with lines and dots appears on the dark boarder of the windows (i  use the default 10.04 theme). my graphics is also not an ATI it's intel.

---

### Post by cloyd on 2010-07-27
I have a Gateway LT3103u. At fist, I thought 10.04 was just not going to work for me. The graphic problem almost blocked installation, it ran hot, what fixed heat problem would result in poor wireless. Eventually I used the 2.6.34 kernel and modified boot. I really don't understand what is going on there, but it helped. Now, 9.10 is gone, and 10.04 is the only os on my machine. Every thing I had to do is here:

[http://ubuntuforums.org/showthread.php?t=1518658](http://ubuntuforums.org/showthread.php?t=1518658)

My only concern is that if my wife eventually wants me to install it on her machine, the problem with the graphics really makes installation a hassle. I was just lucky to finish the installation, because I couldn't really tell if I was clicking on the correct option on a garbled screen. But these screenshots are exactly what I got.

---

### Post by Saint Nick on 2010-07-28
Hi, I have a X1200 series driver.  I've had graphics issues with Doom3 and Quake4.  These issues were resolved however.  It wasn't a driver issue but a screen resolution issue.  This may not be applicable to web browsing but to gamers, this is important.  By playing in window instead of full screen, I was able to have perfect graphics where before there was nothing recognizable except pixels.  If this applies to you, contact me or check "Doom 3 issues".

---

### Post by lsutiger on 2010-07-28
> **aidenscool09 said:**
> I still don't see how updating you GRUB configuration has to do with your graphics problems.

I also do not see how GRUB affects anything other than your hard drive and partition tables. 
But I tried it and so far so good. I just rebooted about 10 minutes ago...so time will tell.

But someone tell me this. What does the nomodset command do?


Also I lost my splash screen somewhat...it loads but not in the correct resolution and only shows for a second or so.

Keep this thread going!! This needs to be addressed!

---

### Post by ELoXL on 2010-08-03
I'm going through the same Ubuntu Splash screen resolution issue as well, but I honestly will have that be my only issue if it take away the "screen madness" that we've all been dealing with here; especially on Gateway LT31xx series of netbooks.

---

### Post by cubicsilver on 2010-08-14
nomodeset doesn't work for me.

added nomodeset to grub config, updated grub. 

Fail.

Am I missing something?

---

### Post by naujokas on 2010-09-24
had same problem with default instal of 10.10 beta on lt3103u but then did alernate install with nomodeset this effect is gone for good, it was showing up on adobe.com

---

### Post by brumorino on 2011-02-09
Same problem in 10.10

---

### Post by zohano on 2011-02-25
funny thing is i have the exact same things happen on screen but i have a desktop pc with nvidia geforce 8300 onboard graphics

i had the exact same thing happen to screen in win 7 and i kno0w that was nvidias new drivers

i have spent weeks working on this and other errors caused by the drivers for onboard nvidia win 7 drivers even killed one of my ram sticks as the ram controllers well all the controllers are actually nvidia driven

the difference with my screen doing the mad lines is the fact m,y system locks up at the same time and i mean totally locked up

i have tried the grub fix as mentioned and am about 25 mins into the reboot but i never get any problems untill i play either flash games online or any other graphics heavy activity

any updates on whats happening with these problems??

---

### Post by cubicsilver on 2011-03-06
The reason for the glitches is that the ati kms doesn't implement sideport memory very well.  I was using nomodeset for sometime as a work around and it seemed to be doing the trick, but it wasn't perfect and I still had issues. 

Eventually I stumbled onto a modified bios in the notebook review forums that solved pretty much every issue I ever had.

This bios adds a bunch of options that were previously hidden, and allowed me to shut the side port memory off and switch to uma.  This solved the problem.  No more graphics glitches.  No more entering kernel parameters to boot properly.

I highly recommend installing this bios for the many added benefits.
-AHCI (Faster HD speed + hackintosh support)
-VT   (Speeds up virtual machines)
-DDST (so the cpu throttles properly in linux)
-Video voltage and clocking options (for those that want to OC the graphics)
-And many more . ( I haven't played with them all yet )

Just google "Gateway LT31xx_MOD.rar" and you will find it.
Use at your own risk.

---

### Post by fenofonts on 2011-03-15
> **cubicsilver said:**
> The reason for the glitches is that the ati kms doesn't implement sideport memory very well.  I was using nomodeset for sometime as a work around and it seemed to be doing the trick, but it wasn't perfect and I still had issues. 

Eventually I stumbled onto a modified bios in the notebook review forums that solved pretty much every issue I ever had.

This bios adds a bunch of options that were previously hidden, and allowed me to shut the side port memory off and switch to uma.  This solved the problem.  No more graphics glitches.  No more entering kernel parameters to boot properly.

I highly recommend installing this bios for the many added benefits.
-AHCI (Faster HD speed + hackintosh support)
-VT   (Speeds up virtual machines)
-DDST (so the cpu throttles properly in linux)
-Video voltage and clocking options (for those that want to OC the graphics)
-And many more . ( I haven't played with them all yet )

Just google "Gateway LT31xx_MOD.rar" and you will find it.
Use at your own risk.

Cubicsilver, may I say that you have provided me with the solution I have desperately been looking for! This worked perfectly on my DOT M/A (same as Gateway LT31xx), and has allowed scaling and finished sorting the graphics bug. As an additional bonus, it lets me set the amount of shared RAM with GPU, so now I give the GPU only 128mb, leaving more to the system. 

Absolutely brilliant!!! Thanks!!!:KS

---

### Post by lsutiger on 2011-04-09
Just wanted to keep this thread alive in order to get a fix from the distro.
Any updates on launchpad?

---

### Post by Iateabee on 2011-04-11
> **lsutiger said:**
> Just wanted to keep this thread alive in order to get a fix from the distro.
Any updates on launchpad?
I am using an IBM R51 with a Mobility Radeon 7500.  I turned off KMS for a while but couldn't stand the slow graphics.  Here is what I ended up doing:

added a file /etc/modprobe.d/radeon.conf
added the following option:

'Option "EXAVSync" "on"'

went to the modprobe.d dir and used sudo nano radeon.conf to do this.

I picked this tweak from the list of options on man radeon.

Using radeon.conf was an educated guess. the ATI ubuntu site listed 'options radeon modeset=0'  line in the radeon.conf file as an opt method of turning off KMS.  The options weren't working in xorg.conf but for some reason they work in radeon.conf.

There are other options to eliminate tearing listed in man radeon.  This worked for my build but you may be able to tweak for yours.

cheers.

---

### Post by alexpwnsn00b2 on 2011-05-06
The only thing I have done in 10.04 to fix the problem is turn off all visual effects.

In 11.04 to fix the problem is using classic GNOME or using 2D Unity

I need my netbook for school so I don't have time to mess around too much with it

---

