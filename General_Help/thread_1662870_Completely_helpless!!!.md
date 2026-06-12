---
title: "Completely helpless!!!"
date: 2011-01-08
forum: General Help
---

### Post by Linux_noob84 on 2011-01-08
Only 24 hours ago I fully installed Ubuntu Netbook Remix 10.10 on my Asus Eee PC, as in completely removing Windows and Linux is now my main operating system.
 
I was having a great time getting everything tweaked to the way I want it, and then we come to one of the main reasons why I wanted the ultimate performance Linux can provide, a game called Regnum Online.  Installation there went fine, but when I attempted to start the game, I got a message saying my video drivers needed to be updated and/or run DirectX.  OK, fine.  I searched for several hours to try and find a linux Intel Atom video driver, but could find none.  Then I found a command online that I can't relocate now (because my web history is in my non-functional laptop...), and decided to go ahead and enter it into my terminal.  A reboot was requested, I did so, and now I get ONLY the terminal.  I am able to login and my password works, the PC's name is the same, but when I try to start the gnome with "x-session-manager" (which in the help screen it says "Start the GNOME desktop environment", I get this message: WARNING **:  Cannot open display:
 
I would greatly appreciate it if someone could tell me what I should do, personally I would love to just completely reinstall netbook remix and start from the very beginning again, buuut that doesn't seem possible...

---

### Post by RedSingularity on 2011-01-08
Why does a reinstall seem impossible?

---

### Post by Linux_noob84 on 2011-01-08
I searched online for a command line to reinstall it but there doesn't seem to be one...

---

### Post by RedSingularity on 2011-01-08
You can reinstall it from a USB drive if you want.

Would you rather do a fresh install or try to fix the current one?  I will try and help either way.  :)

---

### Post by Linux_noob84 on 2011-01-08
I think at this point it would be easier for me, the Padawan, to start over from square one :D
 
Please walk me through the process of reinstalling if you would.
 
And also would you know how I could find the linux drivers for the intel video card?
 
Thanks in advance for your help, this is also part of the reason why I'm making the full-on switch, people helping people!

---

### Post by RedSingularity on 2011-01-08
We are all happy to help in the Ubuntu community!  Its one of MANY reasons people make the switch.

Anyway, on what OS are you posting from now?  Windows?  And do you have a USB drive at least 1 gig in size?

---

### Post by Linux_noob84 on 2011-01-08
I'm posting from a Windows XP desktop, but can't install anything on here.  I also have my 4GB flash drive that I originally installed Netbook Remix onto my laptop.

---

### Post by RedSingularity on 2011-01-08
Does the USB drive still have the install ISO on it?

---

### Post by Linux_noob84 on 2011-01-08
No, I formatted it after the install was complete.

---

### Post by mikewhatever on 2011-01-08
From Regnum FAQ:
> What do I need to play Regnum Online?
To play Regnum Online you need a PC with the following minimum requirements:

- Windows XP (or superior) or Linux kernel 2.6.13 (or superior) operating system.
- 3D accelerator video card listed here.
- 128kbps Internet access.
- AMD Athlon (or superior) or Intel Pentium 4 (or superior) processor.


I very much doubt that netbook will ever be able to run it.:P
Not meaning do discourage you or anything, but netbooks aren't made for 3d games.

---

### Post by Linux_noob84 on 2011-01-08
Ah, but Mike, here's the thing, I've been playing it on this netbook for about a year now, and from windows I would run the task manager and shut down all programs that weren't essential at the moment.
 
It wasn't fantastically amazing gameplay but I was able to play fairly well, and have been told from people in the game that switching to linux would greatly improve the performance of the machine!
 
Believe me, I would much rather use a strong desktop but funds being what they are and all...

---

### Post by RedSingularity on 2011-01-08
Ok no problem.  First of all you need to download an ISO file to your windows computer.  Make sure you download a 32Bit version since it will be going on the netbook.  Get it from the ubuntu web site.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Also on the windows computer download and install [unetbootin](http://unetbootin.sourceforge.net/)

---

### Post by Linux_noob84 on 2011-01-08
Beauty.
 
This will take some time, however, as I am on a 10MBps connection :(
 
I assume the process is pretty self-explanatory from here though?

---

### Post by mikewhatever on 2011-01-08
> **Linux_noob84 said:**
> Ah, but Mike, here's the thing, I've been playing it on this netbook for about a year now, and from windows I would run the task manager and shut down all programs that weren't essential at the moment.
 
It wasn't fantastically amazing gameplay but I was able to play fairly well, and have been told from people in the game that switching to linux would greatly improve the performance of the machine!
 
Believe me, I would much rather use a strong desktop but funds being what they are and all...

Who told you that?

---

### Post by LetsMugSanta on 2011-01-08
Did they mention that Linux isn't a primary operating system for gaming as well or did they leave that out? You have to jump through hoops to get some games to work ESPECIALLY on any systems that have low hardware specs. Did you try and find out what manufacturer of the video card in the motherboard is?  If you can there might be a linux driver available depending on the manufacturer from their website.

---

### Post by Linux_noob84 on 2011-01-08
Mike, do you mean which player in the game?

---

### Post by RedSingularity on 2011-01-08
> **Linux_noob84 said:**
> Beauty.
 
This will take some time, however, as I am on a 10MBps connection :(
 
I assume the process is pretty self-explanatory from here though?


Sure is!  Once you put the ISO on the USB drive make sure your BIOS in the netbook is set to boot from USB.  And of course come back here if you have any problems.

---

### Post by Linux_noob84 on 2011-01-08
Santa:
[http://www.regnumonline.com.ar/index.php?sec=6&l=1](http://www.regnumonline.com.ar/index.php?sec=6&l=1)

---

### Post by RedSingularity on 2011-01-08
> **LetsMugSanta said:**
> Did you try and find out what manufacturer of the video card in the motherboard is?  If you can there might be a linux driver available depending on the manufacturer from their website.


In regards to the video card model, you can run "lspci | grep VGA" from a terminal when ubuntu is set up and it will give you the proper info.  Then do a google search for any available drivers.  You may only have access to the ones built into the kernel.

---

### Post by LetsMugSanta on 2011-01-08
Oh wow a game that isn't proprietary with Windows or Mac. Never mind then. Try finding out the video info though. Look on the manufacturers website of the netbook to see if they have any linux drivers available (I doubt it but it's worth a shot). Otherwise find out the manufac info of the actual card/chip

---

### Post by Linux_noob84 on 2011-01-08
> **LetsMugSanta said:**
> Oh wow a game that isn't proprietary with Windows or Mac. Never mind then. Try finding out the video info though. Look on the manufacturers website of the netbook to see if they have any linux drivers available (I doubt it but it's worth a shot). Otherwise find out the manufac info of the actual card/chip
 
After a quick look, my model is the Asus Eee PC 1005HAB, and it appears there are only Windows drivers available.  Maybe there is some way for me to utilize WINE in this scheme, as far as the drivers are concerned?  Running the game through WINE is possible but would pretty much take me right back to where I started from...
 
At any rate, having Linux is definitely more preferable aside from probably not being able to run the game...

---

### Post by LetsMugSanta on 2011-01-08
You might have already done this but I just want to make it clear. Did you use the update manager and driver manager yet? Also on the site for the game you want to play it says you might need to update your driver at the bottom did you click on the Intel one?

Google isn't really helping me out right now so I might have to try the game for myself on my netbook and see what happens.

---

### Post by Linux_noob84 on 2011-01-08
Yeah I ran the update manager twice, and hit the check button a couple times and it said all drivers were up to date.
 
Also on the intel website they don't have my specific brand of netbook, or I wasn't looking in the right place....  I'll double check again but I remember hitting a dead end when looking in linux so in that moment I started looking for terminal commands (bad idea..)

---

### Post by LetsMugSanta on 2011-01-08
Yeah I checked Intel's website and ASUS was of no help at all. You would think they would make their website's retard proof but their still a pain in the *** sometimes. Give me a little bit I'm going to download the game and try it on my netbook as I research some more.

---

### Post by mikewhatever on 2011-01-08
> **Linux_noob84 said:**
> Mike, do you mean which player in the game?

A player in the game told you to switch to linux and you did? Are you serious?

---

### Post by Linux_noob84 on 2011-01-08
> **mikewhatever said:**
> A player in the game told you to switch to linux and you did? Are you serious?
 
Well he didn't tell me to switch to it and I did so immediately, but after listening to him talk about it's benefits, and advantages (aside from the lessened system drain from the OS), I decided to just go ahead and make the jump.  Was probably stupid and reckless but it was either do this and more than likely have an OS that at least works, as opposed to.... Windows....

---

### Post by LetsMugSanta on 2011-01-08
Well windows isn't that bad of an operating system. What OS did you have before you installed Ubuntu.

---

### Post by Linux_noob84 on 2011-01-08
It was Windows 7, and while the OS isn't that bad, it just seems that with each version of windows, no matter what antivirus I had, how good I was at regular system maintenance, there was always a slow but steady degradation of the performance of the system itself and anything else I ran, games or otherwise.  Several seconds from mouse click to actual button press on the screen is pretty ridiculous to me, and I just got tired of that and other similar things.
 
It was explained to me that viruses are written for operating systems that are used by many people, the more the better.  Aside from that, writing viruses for linux systems is pretty much null and void.
 
Even if all I end up being able to do with this computer is running videos or solitaire-esque games, I'm happy with this new OS.

---

### Post by LetsMugSanta on 2011-01-08
Well that's good that you like Ubuntu. One thing that may contribute to the issues is the fact that the version is 10.10. There have been several threads and questions as to why there are so many issues with it. I currently just converted mine to 10.04 LTS 32 bit today and it runs a lot better than the 10.10 version (on mine anyway). While viruses are less on Linux OSes they are entirely possible so I recommend checking these threads out for preventative action.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

I would *personally* recommend switching to the 10.04 edition, this may solve some issues but I will not guarantee that.

The windows 7 that is loaded with netbooks is the starter edition, which is complete garbage.

---

### Post by Linux_noob84 on 2011-01-08
> **LetsMugSanta said:**
> 
 
The windows 7 that is loaded with netbooks is the starter edition, which is complete garbage.
 
HAH!  I'm glad you agree, and I'm also glad I didn't shell out the 70-some dollars for an upgrade!
 
Thank you for the links as well, I'm close to installing the ISO Red recommended.  Will I be able to switch versions once it's installed?

---

### Post by LetsMugSanta on 2011-01-08
> **Linux_noob84 said:**
>   Will I be able to switch versions once it's installed?


Versions of what exactly? Ubuntu itself?

---

### Post by Linux_noob84 on 2011-01-08
> **LetsMugSanta said:**
> Versions of what exactly? Ubuntu itself?
 
Yeah versions of Ubuntu.  The person I spoke to said that installing the netbook version would allow me to switch between that and the desktop version, so I thought maybe a switch of desktop versions was possible..?

---

### Post by LetsMugSanta on 2011-01-08
> **Linux_noob84 said:**
> Yeah versions of Ubuntu.  The person I spoke to said that installing the netbook version would allow me to switch between that and the desktop version, so I thought maybe a switch of desktop versions was possible..?

I'm pretty sure that's not possible, maybe he meant workspaces but that's probably it. In order to actually upgrade or change versions seamlessly you have to use the .iso file and reinstall it.

---

### Post by Linux_noob84 on 2011-01-08
Alright well, the download has been frozen at 97% for the past half hour now, an hour and a half wasted. I will be trying this again tomorrow.
 
Thanks everyone!
 
---actually nevermind, older version of XP  :D

---

### Post by mikewhatever on 2011-01-08
> **Linux_noob84 said:**
> Well he didn't tell me to switch to it and I did so immediately, but after listening to him talk about it's benefits, and advantages (aside from the lessened system drain from the OS), I decided to just go ahead and make the jump.  Was probably stupid and reckless but it was either do this and more than likely have an OS that at least works, as opposed to.... Windows....

While Linux has many advantages, gaming is not one of them, no matter what you were told. Unfortunately, Intel's graphics is another disadvantage. Intel makes crappy drivers for Linux, so don't bother updating.

PS: Hope I am wrong, but that's unlikely. :P

> **Linux_noob84 said:**
> Yeah versions of Ubuntu.  The person I spoke to said that installing the netbook version would allow me to switch between that and the desktop version, so I thought maybe a switch of desktop versions was possible..?

That one happens to be true. You can select a session at the login screen. Just logout of the netbook session and select Gnome Desktop under sessions. The netbook edition is not a different version, it's just a different GUI.

---

### Post by Linux_noob84 on 2011-01-08
> **LetsMugSanta said:**
> Well that's good that you like Ubuntu. One thing that may contribute to the issues is the fact that the version is 10.10. There have been several threads and questions as to why there are so many issues with it. I currently just converted mine to 10.04 LTS 32 bit today and it runs a lot better than the 10.10 version (on mine anyway). 
 
What problems have you had with 10.10?

---

### Post by LetsMugSanta on 2011-01-08
> **Linux_noob84 said:**
> What problems have you had with 10.10?

While I like the interface I immediately had issues upon a fresh installation. Whereas the 10.04 version I didn't. The unity interface was slow to react and when clicking say something like firefox, it took forever to load. After I updated and activated my wireless driver I rebooted and the wired internet (ethernet) no longer worked. So I said %$@! it and went back to the LTS version.

---

### Post by Linux_noob84 on 2011-01-08
[QUOTE=mikewhatever;10333786]While Linux has many advantages, gaming is not one of them, no matter what you were told. Unfortunately, Intel's graphics is another disadvantage. Intel makes crappy drivers for Linux, so don't bother updating.
 
PS: Hope I am wrong, but that's unlikely. :P
 
 
QUOTE]
 
Party pooper :P
 
just kidding!

---

### Post by LetsMugSanta on 2011-01-08
Minimum 	 	 	 		Processor 	 	 	 		**Intel** Pentium 3 800 Mhz or **AMD** Duron 900 Mhz or superior 	  	 		Memory 	 	 	 		256 Megabytes of RAM or superior 	 	 	 		Video 	 	 	 		**ATI** Radeon 7500 or **nVIDIA** Geforce 2 and superior 	  	   	 		Recommended 	  	 		Processor 	 	 	 		**Intel** Pentium 4 2.4Ghz or **AMD** Athlon XP 2400  	  	 		Memory 	 	 	 		512 Megabytes of RAM 	 	 	 		Video 	  	 		**ATI** Radeon 9600 or **nVIDIA** Geforce FX5700 	  	 





I'm pretty sure that the linux drivers for the Intel Atom are not as good as the minimum video. So most likely the game will not work right either way in linux. BUT as I said before I would try going to 10.04 to see if it changes anything. If it doesn't oh well, Linux still has some great arcade games in the software center. Hope that helps.

---

### Post by Linux_noob84 on 2011-01-08
> **RedSingularity said:**
> Ok no problem. First of all you need to download an ISO file to your windows computer. Make sure you download a 32Bit version since it will be going on the netbook. Get it from the ubuntu web site.
 
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
 
Also on the windows computer download and install [unetbootin]("http://unetbootin.sourceforge.net/")
 
OK, the download completed and I loaded the ISO and also copied it directly to the flash drive.  After setting the BIOS to boot from the drive the install menu came up, and I selected Install Ubuntu.
 
This is the message I got:  (initramfs) mount:  mounting /dev/loop0 on //filesystem.squashfs failed:  Invalid argument  Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
 
That's the end of it.

---

### Post by RedSingularity on 2011-01-08
Before we try anything else try booting and select the option to "try" ubuntu.  If that works you can always install it from inside the "live cd" mode.

---

### Post by Linux_noob84 on 2011-01-09
> **RedSingularity said:**
> Before we try anything else try booting and select the option to "try" ubuntu. If that works you can always install it from inside the "live cd" mode.
 
Attempted try as well, with the same result.  Anything I try from 10.10 doesn't seem to work.  Maybe because the setup was for "install from Windows"?
 
I'm about to try 10.04 (the one available for download from the website)..

---

### Post by Linux_noob84 on 2011-01-09
It must have been the version!  I'm currently installing over 10.10 on the entire drive with 10.04, hopefully I'll be making the next post from my own laptop!

---

### Post by RedSingularity on 2011-01-09
You may have gotten a bad ISO.  You said the download came to a stop in the middle?  May have become corrupted.

---

