---
title: "Random Problems with Computer on Startup"
date: 2010-01-30
forum: General Help
---

### Post by Joseph Schwenker on 2010-01-30
This is a repost of another thread, which I marked as "solved" when it really wasn't.  This is the description of my last thread: 

> Hi everyone. For the last few weeks, I have been turning off my powerstrip after I turn off my computer, as my city is overbroadcasting their radio stations, making me listen to "Save Big Money at Menards" at night, unless I unplug the speakers. So, I just turn off the powerstrip, which my computer is also plugged into, as well as my printer. So, a few days ago, I started experiencing some problems in Ubuntu. I booted up, and no matter what I did, Compiz would not start. A run of compiz-check told me that everything was fine. I reinstalled Compiz, and everything worked fine. I still have no idea what caused this. The next day, I turned on my computer, and I booted into Ubuntu, but instead of my regular desktop, Nautilus was not running, my window border was changed to "Aging Gorilla", and Docky was asking for the default keyring. I tried to type it in, but neither my keyboard nor mouse would work. I manually shut of my computer, and when I restarted, things worked fine. On another day, I turned on my computer, and my graphics card fan would not stop screaming. Ubuntu would not start. I manually restarted the computer, and Ubuntu then worked fine. Today, I turned my computer on in the morning to print off a document for school. The first time, I just get to a blank screen. Nothing. I restart manually. Ubuntu starts up, but I get an error message about failing to initialize HAL. Keyboard nor mouse does not work. I manually restart, and then it works. This afternoon, I try getting into my computer. It got to the Ubuntu bootup screen, and the bar just kept bouncing back and forth, until I reached a black screen with a flashing cursor. Neither keyboard nor mouse worked. Upon a second manual restart, everything was fine again. I am completely confused as to why this is happening, especially when I had not turned my powerstrip off this morning, and yet still had problems in the afternoon. Does anyone know of a way to get a log file or terminal output or anything important for solving this? Is it something to do with the powerstrip? Thanks for your time. I am using an eMachines T5212, three or four years old, Ubuntu 9.04 32-bit. nVidia GeForce 8800GT with 512 MB of RAM, proprietary drivers enabled. Intel Pentium D 2.67 GHz. Can anyone help me? Thanks a bunch!

(The last thread's solution was for me to move the computer's power directly to the wall, which I did)

This morning when I turned on my computer, my graphics card fan would not stop spinning.  The next time, the Ubuntu loading screen froze at about 10%.  The next time, I just got a black screen after GRUB.  These problems repeated themselves several times.  After the second time, I got some compressed air, and blew out my computer's fans.  I expected things to work better now.  Nope!  I took about six to seven manual reboots for Ubuntu to work.  The last time, Ubuntu had a routine disk check, which took a while.  Ubuntu also took longer than usual to load.  Are there any files that I can get to to give here?  I am at a total loss as to what the problem is.  PLEASE HELP.

---

### Post by ajgreeny on 2010-01-30
Sounds rather like a hard disk problem.  At the very least i think you should make sure you are fully backed up, I would then boot to the Live CD and run ```
sudo fsck /dev/sdx#
``` where sdx# is the device name for your ubuntu partition, again.  If any errors are found, report them back here.  You could also use the Ultimate Boot CD, whch has many hard disk manufacturer's diagnosis applications on it.  Run the one appropriate to your hard disk make, if there is one available and see if that is all OK.  Karmic also has a program called Disk Tools or something similar, which will run palimpsest, which also does a disk check for you.

---

### Post by Joseph Schwenker on 2010-01-30
I am not sure of which hard drive I should scan, so I first tried sda0, which made it output:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda0
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: No such file or directory while trying to open /dev/sda0

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

I then tried sda1:

```
ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1: clean, 311025/11837440 files, 14399803/47331498 blocks

```

Also, I do not think that it is a hard drive problem, as sometimes when booting up my computer, my graphics card fan will scream, and never stop.  This is before anything ever appears on my monitor.  Do you think it has something to do with electricity or power?  Thanks for your reply!

---

### Post by pfranks on 2010-01-30
> **Joseph Schwenker said:**
> Also, I do not think that it is a hard drive pri oblem, as sometimes when booting up my computer, my graphics card fan will scream, and never stop.  This is before anything ever appears on my monitor.  Do you think it has something to do with electricity or power?  Thanks for your reply!

I suspect you have a problem with a noisy bearing on the graphics fan which is starting to wear and needs a few moments to warm up and rum smoothly. This is probably a secondary issue.

The big problem is startup failure. What you describe is typical for a hardware problem, with apparently random failures. This sounds like a failing hard disk which is having to make multiple reads to retrieve data (so slow). A software problem is usually reproducible if you can identify the steps to create it. In your problem the human step is very simple, "power on" so until you press something the startup software process should behave exactly the same every time. A hardware problem is often mechanical or heat moderated, so it is more random in occurrence.

---

### Post by Joseph Schwenker on 2010-01-30
So, from my last post where I put in my terminal output, do you think that my hard drive is failing?  My computer is a bit over three years old.  It is a Serial ATA in an eMachines T5212.

---

### Post by Joseph Schwenker on 2010-01-31
Today, I started up my computer.  First, my graphics card would not screaming.  The next two times, my computer froze at the eMachines splash screen.  The fourth time, I got past the eMachines screen, but got a blank terminal after the Ubuntu progress bar.  The sixth time, I got another blank terminal.  I was able to use ctrl+alt+f2 to get to a terminal, and then REISUBed out.  The seventh time was the first time the GUI was loaded successfully, but Compiz did not load.  I tried to get to a terminal to execute compiz --replace from, but when I clicked on Terminal, my whole system froze.  I then typed ctrl+alt+F1, but got to a blank screen with a blinking cursor.  I then reisubed out.  The eighth time logged me out twice, and when I was finally able to enter the GUI, there was no Compiz.  I was able to open the terminal, and ran compiz --replace, and got this output: 

```
joseph@joseph:~$ compiz --replace
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Segmentation fault
Window manager warning: "" found in configuration database is not a valid value for keybinding "activate_window_menu"
Window manager warning: "" found in configuration database is not a valid value for keybinding "unmaximize"
```

I then opened Chrome to paste the output into a notes application, and my desktop theme was changed, and system sounds were suddenly enabled.  I reisubed out again.  The ninth time, the system logged me out once, but I was not able to use my mouse or keyboard to type into the login field.  I was, however, able to reisub out.  The tenth time was the first perfect time.  This is the boot from which I am writing this now.  Interestingly, when I boot up successfully, there are no problems within the OS.  The problems are confined to the boot process.  Should I reset my BIOS?

Edit: At about the sixth time, I got the terminal screen that is attached.

---

### Post by audiomick on 2010-01-31
Hi. I also suspect a hardware problem for your startup issue. I do not believe that it has anything to do with using a power strip ( meaning a power board with a swicht on it, I presume).

I am using one for everything that has to do with the computer, and have no problems. As long as everything is shut down properly before you pull the pin, you shouldn't have a problem.

---

### Post by Joseph Schwenker on 2010-01-31
Does anyone have any ideas as to which piece of hardware is causing this problem, or how to tell?  Does anyone have any solutions?

---

### Post by audiomick on 2010-01-31
> **Joseph Schwenker said:**
> Does anyone have any ideas as to which piece of hardware is causing this problem, or how to tell?  Does anyone have any solutions?

First guess would be the HD. Testing tool here
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by pfranks on 2010-01-31
> **Joseph Schwenker said:**
> Does anyone have any ideas as to which piece of hardware is causing this problem, or how to tell?  Does anyone have any solutions?

Prime suspect is the hard disk. I don't consider the BIOS is na contender - it is very unlikely to make random changes in it's content and then revert back to normal. What you are describing is typical for read failures on a hdd which is about to demonstrate catastrophic failure. Remember the hdd is at least 3 years old, which is about the stage where bad things start to happen.

The simple test is to boot a few times from a live cd or USB, and ignore the hard disk. If the OS comes up consistently from CD you have pretty much proved there is a problem in the hard disk.

Once again I suggest the noisy fan issue is simply a failing bearing, not related to the boot problem. You are lucky it has made 3 years, most of my fans seem to fail before that. Replacement should be simple and not too costly - either new graphics card, or if you are lucky a new fan and a few minutes with a screwdriver. Deal with the boot problem first.

---

### Post by Joseph Schwenker on 2010-01-31
My 9.04 installation is now buried with its last application, Banshee.  I had installed Banshee, and had it running in the background, when suddenly my system froze.  I couldn't move my move, I could do anything.  Only REISUB worked.  This happened several times, and after about the fifth time, I decided to reinstall Ubuntu.  I grabbed my 9.10 live CD, and hit install.  At about 80%, the install failed, with a crash indicator on the panel, saying that Ubiquity had crashed.  I then got a whole bunch of errors about a kernel problem, about "install.py", or something like that.  Then the whole screen froze.  Restart.  Same thing.  Restart again.  Same thing.  At this point, I had pretty much given up hope, and I am now no longer able to even boot from a live CD.  I just get a whole bunch of random errors while in the OS.  Also, to the user who told me that my graphics card's screaming was trivial, I have this to say.  When I start up my computer, my graphics card normally screams for a few seconds, then stops.  I have to wait for it to stop screaming before anything comes up on my screen.  If it doesn't stop screaming, then nothing comes up on my screen, and I have to manually restart my computer.  It is a PNY nVidia GeForce 8800 GT with 512 MB of graphical memory.  It isn't even a year old, and has a multi-year warranty.  

At this point, I am unsure of what to do, as I am no longer able to even boot my computer into anything.  Does anyone have any ideas or questions?  Thanks for all of your time on this.

---

### Post by audiomick on 2010-02-01
Get the graphics card replaced under warranty.

It sounds like you can boot into the live CD, but it doesn't run without lots of errors.
In that case, I would run the "memtest86" option from the live CD (or is it called "check memory"?)

That checks your RAM for problems. If things are normal, you should not see any errors. If you have errors, the first thing is to take out the RAM chips, taking care not to touch any of the connectors, and plug them back in. It may be that the connections have collected a bit of crap and need to be re-seated.

The other thing to run would be "Smartmontools"
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
to check your HD, but you will have to get it to a point where the live CD will run to do that.

---

### Post by coldraven on 2010-02-01
Take out your memory cards, give the contacts a wipe with some tissue paper, brush any dust out of the slots with a soft paint brush and replace them.
Sorted!:p

---

### Post by Joseph Schwenker on 2010-02-01
Thanks for all of your suggestions!  At this point, I am unable to boot into even the BIOS.  My CPU and graphics card fans just scream infinitely.  I guess I could always take a walk and see if it really was infinite, though...

Anyway, thanks for your suggestions about the memory.  I will be sure to try cleaning them, then I will post what happens.

---

### Post by Joseph Schwenker on 2010-02-01
I tried reseating the memory.  No luck.  I have been getting help from another guy, and he told me to look at the capacitors on the motherboard to see if they were leaking.  This would have caused the infinite fan screaming, as, at startup, the computer tells all of its fans to spin at maximum speed.  If they were leaking, they would have caused this process to go on infinite loop.  I could not see any leaking capacitors.  After re-seating the memory, trying to boot without the graphics card, and trying to boot without the hard drive, I am about at the end of my diagnostics.  Does anyone have any ideas?

---

### Post by Joseph Schwenker on 2010-02-01
Yay!  After I reseated the memory sticks, I did not try the hard drive again.  When I unplugged it this time, I was able to boot into the live CD, but it gave me a terminal that said something about a "kernel panic".  I rebooted the computer, and went into the memory test, which is about 50% done.  It looks like it will, in total amount, take an hour.  I will give you the results when I get them.  Any other comments, questions, or ideas?

---

### Post by sandkernel on 2010-02-01
Twice in the last 10 years I've had really weird problems with 2 different pc's. After troubleshooting up the ying-yang I discovered bad RAM. Let me tell you, bad RAM can do the damnedest things. It will cause problems that would drive you nuts. I would be highly suspicious of your RAM just because of these really strange issues. Consider going out and buying a stick of whatever RAM you are using. Worse case scenario, the RAM is not the problem and you've got extra RAM - never a bad thing.

---

### Post by Joseph Schwenker on 2010-02-01
> **sandkernel said:**
> Twice in the last 10 years I've had really weird problems with 2 different pc's. After troubleshooting up the ying-yang I discovered bad RAM. Let me tell you, bad RAM can do the damnedest things. It will cause problems that would drive you nuts. I would be highly suspicious of your RAM just because of these really strange issues. Consider going out and buying a stick of whatever RAM you are using. Worse case scenario, the RAM is not the problem and you've got extra RAM - never a bad thing.

The computer originally came with one GB of RAM, which I then upgraded to two GBs of RAM, bought DDR2 from Memory Ten.  I am now able to boot into a live CD, although it gives me errors about how there is a kernel error, and how my system is unstable.  Shortly after, the entire system freezes.  We're back to the random boot and error problem!  Can anyone solve it?  I will see if I can get the original RAM into the computer.

---

### Post by Joseph Schwenker on 2010-02-01
Also, the memory test passed.  Everything is a-ok according to the memory test.  If you want a picture of the results, I can attach it.

---

### Post by M1GEO on 2010-02-01
Do you have any details of what causes the kernel panic?  if you can get a console or terminal window, try running *dmesg*, and looking for anything untoward.  Especially text around the kernel panic/errors.

You have a few problems which may be causing you confusion.  Dismiss the fan as has been suggested.  The sceaming is just the bearings worn, and the fan-blades vibrate in the bearing-play.  When the computer crashes/fails to load, etc it is very common for the bios to put the fans up full - this is failsafe - it knows something has gone wrong, and doesnt know what - so keeping things cool is safe.  These are all secondary problems.  Something causes the machine to crash, and these things are a result, not the cause.  Sometimes you also note a high-pitch squeal (whine) - this can be switching noise.  The bus voltage is converted to a high current by an on-board (videocard) switching power supply.  It often makes squeaking/squealing/whining noises.  Dont worry.

If you can get a live cd to boot, try running *palimpsest* via System > Administration > Disk Utility or via the terminal (run palimpsest).  You can use that to look at hard-disks smart data.

If memtest86+ says your RAM is good then it is pretty safe to believe it.  What temperature does your CPU get to?  Also, remove any external peripherals you dont need.  Anything on the USB bus, or in card readers.  These can sometimes cause weird things/hanging if the kernel is trying to mount/enumerate hardware that wont respond.

Just a few ideas.
HTH. George.

---

### Post by M1GEO on 2010-02-01
Just another thought, is your computer stable if you boot the ubuntu live cd into recovery mode?  I.e. not into X (graphics), just leave it at a terminal screen.  I think there is a recovery menu (not sure off the top of my head) on the Ubuntu CDs...

Sometimes hardware will work with very standard (low performance) drivers (or none at all), and then when the driver tries to initialise faulty hardware, it all goes wrong...

Anyway, thats my 2 pence worth.

---

### Post by robert shearer on 2010-02-01
About now I would be checking the power supply unit.

Do you or your friend that's helping have a power supply that you can swap out to check ?

---

### Post by Joseph Schwenker on 2010-02-02
Thanks for all of your suggestions.  Again, my computer will sometimes boot up, and sometimes not.  It takes a few manual reboots before I can get the fans off of infinite loop.  Then, if I can get past the eMachines Splash screen, I should be able to use the recovery mode you spoke of.  I will also try the suggestion about the power supply.  I'll have to get a power supply first, though!

---

### Post by Joseph Schwenker on 2010-02-02
Although largely unsuccessful at booting into Ubuntu 9.10 (although I was able to get to a terminal and use Lynx), I have been extremely successful at booting into Crunchbang, a very lightweight distribution of Ubuntu.  I am currently typing this from Crunchbang 9.04.  I am unable, however, to find a disk utility tool yet.  When I find one (and when I plug in my hard drive) I will check my hard drive, which is currently unplugged.  Thanks for your help, although this problem is LONG from solved.  ;)

---

### Post by Joseph Schwenker on 2010-02-02
OK, Crunchbang just randomly froze, and I had to REISUB out.  Same problem as in my last Ubuntu 9.04 install!  I might try to install Crunchbang, if at all possible.  I will tell you what happens.

---

### Post by robert shearer on 2010-02-02
You have tried 9,04, 9.10, and now Crunchbang all with the same troubles so that pretty much rules out a software problem.

I doubt that installing Crunchbang as you propose will make any difference.

You need to do some diagnostics of the hardware, replacing one at a time until the faulty item is found.

That you can sometimes get a working desktop would seem to rule out the graphics card, likewise as the troubles happen with both an install and a live cd then this would tend to dismiss problems with the hard-drive.

Leaves the motherboard, cpu, power supply and possibly the easiest fix the **cmos battery**.

When was the battery replaced last ?.

How about some specs of the machine.

---

### Post by Sylslay on 2010-02-02
I have really the same problem with my laptop with almost (8.04 was quite stable) every distro.
My first suspect is graphic chip 845 and intel drivers.
Nothing else.
First boot a day usualy  (more likly )fail, after reset works ok

Best solution for me will be get new laptop (non - intel graphic card)
, but not sun.

Some tweaking with grub mode setings for like vga=792 helps , from command line
but not always, and problem apear again now and than,

tan reset.

---

### Post by audiomick on 2010-02-02
> **robert shearer said:**
> You have tried 9,04, 9.10, and now Crunchbang all with the same troubles so that pretty much rules out a software problem.

Indeed.

> That you can sometimes get a working desktop would seem to rule out the graphics card, 

Unless it has an intermittent contact or is overheating??

---

### Post by Joseph Schwenker on 2010-02-02
> **robert shearer said:**
> You have tried 9,04, 9.10, and now Crunchbang all with the same troubles so that pretty much rules out a software problem.

I doubt that installing Crunchbang as you propose will make any difference.

You need to do some diagnostics of the hardware, replacing one at a time until the faulty item is found.

That you can sometimes get a working desktop would seem to rule out the graphics card, likewise as the troubles happen with both an install and a live cd then this would tend to dismiss problems with the hard-drive.

Leaves the motherboard, cpu, power supply and possibly the easiest fix the **cmos battery**.

When was the battery replaced last ?.

How about some specs of the machine.

Crunchbang is now working very well in Live CD mode.  I think I know what a CMOS battery is.  My dad said that it might go bad when I started turning off the power strip that my computer was on.  It has never been replaced.  My computer is an eMachines T5212.  It has a 2.67 GHz processor, came with 1 GB of DDR2 memory, which I later upgraded to two GBs.  It came with an integrated ATI Radeon XPress 200, which was replaced by me with an PNY nVidia GeForce 8800 GT.  I have a 200 GB ATA hard drive.  I do not know any other speculations.  You should Google my computer's model and see what else you can find.  Thanks for the response!  I will install Crunchbang now.

---

### Post by robert shearer on 2010-02-02
> Unless it has an intermittent contact or is overheating??

Agreed.  But lets eliminate the easily checked items first.

 entia non sunt multiplicander praeter neccesitatum methinks


> It came with an integrated ATI Radeon XPress 200, which was replaced by me with an PNY nVidia GeForce 8800 GT

For the purposes of testing you could remove the replacement card and try running with the integrated video.

The cmos battery is only a few dollars so is worth replacing to eliminate it as a possible cause. The manual for your eMachines T5212 should detail the steps. 

Just to be clear, are you posting from the problem machine ? does it or has it run any other os recently/.

---

### Post by audiomick on 2010-02-02
> **robert shearer said:**
> Agreed.  But lets eliminate the easily checked items first.

good plan. :)

---

### Post by Joseph Schwenker on 2010-02-02
I plugged in the hard drive, booted up, and the mouse would not work.  Random hardware not working again!  It appears that the "random" factor is coming into play again.  The thing is, everything seems perfect when it works, but when it doesn't work, it's completely random.  I am about to install Crunchbang 9.04.

---

### Post by robert shearer on 2010-02-02
> **Joseph Schwenker said:**
>    The thing is, everything seems perfect when it works, but when it doesn't work, it's completely random. 

That is because there is a hardware fault.

>  I am about to install Crunchbang 9.04.

Installing more software won't cure hardware faults.
Though I admire your persistence ;)

Once you have assured yourself that Crunchbang is not going to magically fix the faulty hardware then lets try some simple steps to find and fix it.

step 1)  replace the cmos battery. Then test with a live cd and report the results.

---

### Post by Joseph Schwenker on 2010-02-02
> **robert shearer said:**
> That is because there is a hardware fault.



Installing more software won't cure hardware faults.
Though I admire your persistence ;)

Once you have assured yourself that Crunchbang is not going to magically fix the faulty hardware then lets try some simple steps to find and fix it.

step 1)  replace the cmos battery. Then test with a live cd and report the results.

I tried to install Crunchbang, and although the live CD works better than the Ubuntu 9.10 one, many things will crash.  I am able to browse the web well with it, though.  The installer crashed, so I will not be installing it (obviously).  I will replace the CMOS battery, then try the Ubuntu live CD, as it will be a bit more obvious if it is working then.  Thanks!

---

### Post by Joseph Schwenker on 2010-02-03
I bought a new CMOS battery and put it in.  I had to remove my graphics card to get to it.  I noticed that two of the gold rectangles on my graphics card were missing their tips.  I put the CMOS battery in, and my computer immediately booted up when I plugged in the power cord.  It gave me an error about the "CMOS checksum".  I rebooted, and I had the infinite fan again several times.  When I was finally able to get to the eMachines screen, I reset my BIOS.  Then I was able to get to live CD screens.  I was unable to boot into Crunchbang and Ubuntu.

---

### Post by robert shearer on 2010-02-03
Your bios has been reset to the defaults with the battery replacement.
Default boots the hard drive first.
This is why you cannot boot the live cd's.

You will have to access your bios and change the boot order to make the cd the first boot device.
Read your motherboard manual for the steps to do this.

---

### Post by Joseph Schwenker on 2010-02-04
> **robert shearer said:**
> Your bios has been reset to the defaults with the battery replacement.
Default boots the hard drive first.
This is why you cannot boot the live cd's.

You will have to access your bios and change the boot order to make the cd the first boot device.
Read your motherboard manual for the steps to do this.

No, that is not why.  By default, CD is the first boot setting, and it was after I reset my BIOS.  When I am able to get past the "infinite fans of doom", I am able to get to the starting screen for the live CDs, (where it says Try Ubuntu Without Changing Your Computer) but it usually freezes when loading the OS, or takes me to a black screen or terminal.

---

### Post by coldraven on 2010-02-04
Years ago I had a 486 powered laptop that developed a heat related fault.
it would work for half an hour from cold then freeze. Then a quarter hour, then five minutes. If I let it cool off the same symptoms started again.
 I took it to bits and cleaned every connector, scanned the mother board with a magnifying glass but never solved it. I gave it to a friend for parts.
Sometimes it's better to cut your losses :(

---

### Post by robert shearer on 2010-02-04
step 2) remove the graphics card and see if you can load and run with the onboard graphics.

---

### Post by Joseph Schwenker on 2010-02-04
> **robert shearer said:**
> step 2) remove the graphics card and see if you can load and run with the onboard graphics.

I was typing a reply to you from the Crunchbang live CD, but then it decided that it didn't like what I was typing, and decided to freeze the system.  I will try what you just suggested, as I was just thinking about doing it myself.  Also, there are some additional details I have found.  My DVD-ROM drive is making weird clicking noises, and after using my Crunchbang live CD once, I found that there were several deep gashes near the center of the disk.  And we're talking DEEP GASHES.  Also, when I tried to boot into the Ubuntu live CD once, I got a screen about a segmentation fault.  I have a picture of it, if anyone would like to see it.  
Thanks for not giving up on me!  ;)

---

### Post by robert shearer on 2010-02-05
> My DVD-ROM drive is making weird clicking noises, and after using my Crunchbang live CD once, I found that there were several deep gashes near the center of the disk

Well, step 3 was going to be 'try another disc reader' as 2nd hand ones are almost give-aways.
If you are **sure** that the gashes were caused by the dvd-rom and not any other way then swap it out and trying another would be a good move.
In fact it would be the only sensible thing to do now as symptoms of other possible faults will be swamped by this one, its a biggy!

A dying cd/dvd reader will account for inability to load, run, and install from the live cd .

You should also redownload,verify and burn new cds of the distros as we can't trust the scratched discs to not introduce further errors.

Starting to wonder if there is any part of your compy that isn't defective :).

---

### Post by Joseph Schwenker on 2010-02-06
> **robert shearer said:**
> 
Starting to wonder if there is any part of your compy that isn't defective :).

That's what you get when you buy eMachines!  I took out my graphics card and the computer would not start.  It did the "infinite graphics card fan" thing again, except this time, there was no loud graphics card.  After this, I unplugged the DVD-ROM, Hard Drive, and Modem.  The computer still would not start.  I think that if I tried manually rebooting enough, it would be able to boot.  That is what I usually have to do.  Should I try manually rebooting until it boots now?

---

### Post by robert shearer on 2010-02-06
> I took out my graphics card and the computer would not start. It did the "infinite graphics card fan" thing again, except this time, there was no loud graphics card. 

Sounds like it 'started' but you got no screen output ?.

You need to go into the bios and change  video to  internal.
You may have to put the card back now to get a screen so you can make the changes, then power down, remove the card, reboot and you should be good to go.

Other than that it **won't** 'start' as it has **nothing** to start !.
No dvd, hd, etc. 
So you at least need a **working** cd so you can boot something.

---

### Post by 23dornot23d on 2010-02-06
This one line says a lot to me .... 

{I think that if I tried manually rebooting enough, it would be able to boot. That is what I usually have to do. Should I try manually rebooting until it boots now?}

I have had a good read through this and see there may be more than one problem here.

after you replace the CD/DVD Drive ...

...... if you still get problems - 

Try it with one memory stick in the machine at a time only ......

Try booting the machine with each one ..... and see what happens .......

then if this does not work ..... check that the CPU is seated properly .....

seems that this has either happened after you moved the machine or after adding

the new Memory Stick ..... 

I usually buy memory sticks in matched pairs if possible ...... and by the same
manufacturer ........ ( I know you did a mem check by the way ) ......

and its obvious now that the DVD drive taking gouges out is Kaput .....

and it could be a problem with the graphics card as you said the contacts may be missing ?

but it will not harm to try the memory one at a time in the machine ..... 

to see if it works ..... thats presuming you have not fixed it already .... with the new drive ....

am writing this now as I may not be around for long tonight ,,,,

hope that this helps ..... a little ......

---

### Post by Joseph Schwenker on 2010-02-06
> **robert shearer said:**
> Sounds like it 'started' but you got no screen output ?.

You need to go into the bios and change  video to  internal.
You may have to put the card back now to get a screen so you can make the changes, then power down, remove the card, reboot and you should be good to go.

Other than that it **won't** 'start' as it has **nothing** to start !.
No dvd, hd, etc. 
So you at least need a **working** cd so you can boot something.

I believe that there is no such option in my BIOS.  Also, if I restart my computer enough with those components unplugged, it will start.  It will be able, eventually to boot to the eMachines screen, and allow me into the BIOS, as that does not require a hard drive nor a DVD drive.

---

### Post by Joseph Schwenker on 2010-02-06
> **23dornot23d said:**
> This one line says a lot to me .... 

{I think that if I tried manually rebooting enough, it would be able to boot. That is what I usually have to do. Should I try manually rebooting until it boots now?}

I have had a good read through this and see there may be more than one problem here.

after you replace the CD/DVD Drive ...

...... if you still get problems - 

Try it with one memory stick in the machine at a time only ......

Try booting the machine with each one ..... and see what happens .......

then if this does not work ..... check that the CPU is seated properly .....

seems that this has either happened after you moved the machine or after adding

the new Memory Stick ..... 

I usually buy memory sticks in matched pairs if possible ...... and by the same
manufacturer ........ ( I know you did a mem check by the way ) ......

and its obvious now that the DVD drive taking gouges out is Kaput .....

and it could be a problem with the graphics card as you said the contacts may be missing ?

but it will not harm to try the memory one at a time in the machine ..... 

to see if it works ..... thats presuming you have not fixed it already .... with the new drive ....

am writing this now as I may not be around for long tonight ,,,,

hope that this helps ..... a little ......

I... have... not... bought... anything... yet...  
You can stop overusing the ellipsis now!  Thanks for your response, though.  I have DDR2 memory, so I do not think that I will be able to boot with only one memory stick.  The problem started randomly, not immediately after I bought any component.  I bought the two 1 GB memory sticks (DDR2) from memory ten over a year ago.  I have had my graphics card for about a year, maybe more.  The only things that could have caused the problem in the first place are the old age of my computer, or the fact that I had turned off my power strip at night.  Also, how do I check if the CPU is seated properly?  When in the live CDs, I sometimes got terminal errors about the CPU being frozen for 61 seconds, and it was not booting because of that.  I will probably not be buying anything until I definitely know what is the problem.  I am thinking that it could be the power supply now.  What does everyone think?

---

### Post by Joseph Schwenker on 2010-02-06
I just found out that my graphics card, which has been in my computer for about a year, required a power supply that has 400 Watts, and my power supply had less than that.  I think that it was 250 or 300.  Should I try to replace the power supply?

---

### Post by 23dornot23d on 2010-02-07
> **Joseph Schwenker said:**
> I just found out that my graphics card, which has been in my computer for about a year, required a power supply that has 400 Watts, and my power supply had less than that.  I think that it was 250 or 300.  Should I try to replace the power supply?

That could be the problem ,,,, 

If I was in your situation ..... that is a definite ...... yes ..... 

Power supply should be relatively cheap to pick up too ...... 

looking at this .... 

{20$ for a 400 watt .. for... 25$ a 500 watt  ....} 

( If it was me I would get the 500 or bigger to be safe - could always come in handy if you ever need to build  another machine )

[http://www.tigerdirect.com/applications/category/category_tlc.asp?CatId=106&name=Power%20Supplies]("http://www.tigerdirect.com/applications/category/category_tlc.asp?CatId=106&name=Power%20Supplies")

and a CD/DVD ...... 

( these are just examples by the way ..... as I do not know where you get your computer bits from )

[http://www.tigerdirect.com/applications/Category/category_tlc.asp?CatId=4&name=CD-DVD-Burners](http://www.tigerdirect.com/applications/Category/category_tlc.asp?CatId=4&name=CD-DVD-Burners)

you almost know enough to rebuild a computer from scratch now ....

I hope the Power Supply sorts it ,,,,, there is a good chance it will .... 

as long as you get a CD/DVD reader/writer too to boot a live CD/DVD from .... 

{around $20}

Best of luck ..... this will become a success story soon ..... I hope ....

---

### Post by Joseph Schwenker on 2010-02-07
> **23dornot23d said:**
> That could be the problem ,,,, 

If I was in your situation ..... that is a definite ...... yes ..... 

Power supply should be relatively cheap to pick up too ...... 

looking at this .... 

{20$ for a 400 watt .. for... 25$ a 500 watt  ....} 

( If it was me I would get the 500 or bigger to be safe - could always come in handy if you ever need to build  another machine )

[http://www.tigerdirect.com/applications/category/category_tlc.asp?CatId=106&name=Power%20Supplies]("http://www.tigerdirect.com/applications/category/category_tlc.asp?CatId=106&name=Power%20Supplies")

and a CD/DVD ...... 

( these are just examples by the way ..... as I do not know where you get your computer bits from )

[http://www.tigerdirect.com/applications/Category/category_tlc.asp?CatId=4&name=CD-DVD-Burners](http://www.tigerdirect.com/applications/Category/category_tlc.asp?CatId=4&name=CD-DVD-Burners)

you almost know enough to rebuild a computer from scratch now ....

I hope the Power Supply sorts it ,,,,, there is a good chance it will .... 

as long as you get a CD/DVD reader/writer too to boot a live CD/DVD from .... 

{around $20}

Best of luck ..... this will become a success story soon ..... I hope ....

Thanks for your help!  I think that many of the clicking noises I have been hearing are due to one component, probably the power supply.  I notice that when my DVD drive and hard drive click, my ethernet light goes off at the same time.  Unfortunately, the only replacement power supplies that I can find are one with 480 Watts, and one that is 400 watts, the minimum of what my graphics card needs.  I have an eMachines T5212.  Unfortunately, I am not sure of the wattage of my power supply now.  I think that it was under 400, but I am not sure.  I will order a new power supply, and hopefully that will work!  (I'll get more fps now, too!)

---

### Post by Joseph Schwenker on 2010-02-07
I ended up buying a power supply from Best Buy, which had 400 Watts.  I am still having the same problems.  I tried booting into Damn Small Linux from a live CD, but it has a segmentation fault at one location, and then dumps out multiple screens of I/O errors.  Should I try to replace the DVD-ROM drive now?

---

### Post by Joseph Schwenker on 2010-02-07
I just replaced the DVD-ROM drive with a CD-ROM drive from another computer.  I have the same problems.  Live CDs still freeze in the middle of loading.  I am thinking, since I have tried every other component in the computer, that I will reseat the CPU next.  Does anyone have any further ideas?

---

### Post by pfranks on 2010-02-07
> **Joseph Schwenker said:**
> I believe that there is no such option in my BIOS.  Also, if I restart my computer enough with those components unplugged, it will start.  It will be able, eventually to boot to the eMachines screen, and allow me into the BIOS, as that does not require a hard drive nor a DVD drive.

Sorry you didn't like my suggestion that the fan noise is a result and not the primary fault. However, that is behind us.

Your system in absolute minimal configuration should be able to put the Power-On Self Test on screen and/or start the BIOS setup screens every time, without fail. As a quick guide the bare minimum is:

* Power supply
* Motherboard with CPU and cooler
* At least one "set" of RAM boards. (Check the docs for this, it could be single slots or paired)
* Some kind of display output.
* Keyboard - safest on PS/2, unless USB Kb is already enabled in the BIOS.

If there's no display, or no RAM detected you should get a beep code.  

If you can't get POST or BIOS with the bare minimum try different RAM. You've tried PSU and video already. If it still fails I think you're looking at a motherboard and/or CPU issue.

---

### Post by Joseph Schwenker on 2010-02-09
> **pfranks said:**
> Sorry you didn't like my suggestion that the fan noise is a result and not the primary fault. However, that is behind us.

Your system in absolute minimal configuration should be able to put the Power-On Self Test on screen and/or start the BIOS setup screens every time, without fail. As a quick guide the bare minimum is:

* Power supply
* Motherboard with CPU and cooler
* At least one "set" of RAM boards. (Check the docs for this, it could be single slots or paired)
* Some kind of display output.
* Keyboard - safest on PS/2, unless USB Kb is already enabled in the BIOS.

If there's no display, or no RAM detected you should get a beep code.  

If you can't get POST or BIOS with the bare minimum try different RAM. You've tried PSU and video already. If it still fails I think you're looking at a motherboard and/or CPU issue.

I am no longer having the infinite fan issue very much anymore.  I am almost always able to get into the BIOS on first boot.  However, when I try to boot into a live CD, the screen will either freeze or dump out a whole bunch of errors when I tell it to boot into the live CD from the screen.  I am going to try reseating the CPU next.

---

### Post by Joseph Schwenker on 2010-02-09
I just tried taking the hard drive from a working Linux machine out and putting it into mine to see if I could boot from the hard drive.  What I found proves the the problem is not with the hard drive nor the DVD-ROM or CD-ROM drives.  [Here]("http://www.youtube.com/watch?v=yHHw6QlbYPM") is a video with what happened when I tried to boot Crunchbang 9.04 from the hard drive formerly in a working Linux machine.

---

### Post by pfranks on 2010-02-09
> **Joseph Schwenker said:**
> I just tried taking the hard drive from a working Linux machine out and putting it into mine to see if I could boot from the hard drive.  What I found proves the the problem is not with the hard drive nor the DVD-ROM or CD-ROM drives.  [Here]("http://www.youtube.com/watch?v=yHHw6QlbYPM") is a video with what happened when I tried to boot Crunchbang 9.04 from the hard drive formerly in a working Linux machine.

Unfortunately I'm not sure that is a valid test unless the donor machine's hardware is identical. I admit it's something I have never tried with Linux, but there's a good chance some of the drivers you need may be different. It may be more helpful if you can confirm the error/crash messages are always the same, from hdd, from cd, etc.

Have you ever run this release of Crunchbang successfully on the failed PC? Are we even sure it is fully compatible?

---

### Post by pfranks on 2010-02-09
> **Joseph Schwenker said:**
> I am no longer having the infinite fan issue very much anymore.  I am almost always able to get into the BIOS on first boot.

Just to make it clear for us, do you *ever* get failures going into the BIOS? It should work 100% of the tries, zero failures you can't account for by human error. Even one failure here puts the problem somewhere around the motherboard and directly attached components. That's why I suggested the minimal system.

One thought prompted by a machine I was asked to repair yesterday, take a very close look at the motherboard and all the electrolytic capacitors. That's the cylindrical components usually stood on end. The upper end of the cylinder should be absolutely flat not domed in any way, and they should be a nice silver color without brown staining. If even one of them is bulged you are wasting your time on that motherboard because it is damaged. It's not so easy to see on the small capacitors but it seems to be the larger ones which fail.

---

### Post by 23dornot23d on 2010-02-09
I am pretty sure that you cannot just pull a hard drive out one machine and expect it to work in another ..... 

( unless the other machine is exactly the same as yours ) 

so this is not a 100% valid test ..... and it did get to the Grub loading ok ..... 

With no weird characters on the screen ..... can you still do a Memtest ok .....


It **does appear to work OK upto the point where the Grub takes over** ......
then falls over .......

comes up with something not syncing  ,,,,, has the other machine you pulled the HD out of got the same CPU in it ..... 
and is it the same motherboard in it as yours ? 
_________________________________________________________________

Moving on ......

[B]Can you do a video looking into your computer with 
the computer turned off and unplugged from the mains .....[/B]

just scan around it ...... show the connectors CPU ... Memory .... Graphics Card and 
the connectors on the back of the Hard drive and CD drive ...... plus as many other
connectors and components as you can ...... ( do the video movements slowly )

One more question ...... have you altered any of the jumpers on the motherboard ....

At least we know now you have one good component in there - a new power supply ....

( and you can or have put in another second hand CD drive that works ok ? )
_________________________________________________________________

Back to the CD drive do you just have the one good CD drive connected and is it still connected now ...... 
and you removed the other one or at least disconnected it .....

The next thing is the Live Boot CD ...... is it scratched or damaged at all ......
(do you know for sure that the disk is ok does it work ok in another machine .....)

[B]do you have more than one Live CD ? to try ......

I agree with everything Pfranks is saying too .... 

[COLOR=SeaGreen]Start with the minimum plugged in to get it working ...... where it works properly .... [/COLOR]

the way to work things out is to [COLOR=Red]add things one at time till it fails

[/COLOR]( and then you should know what is causing the problem ..... ) 
[/B]

---

### Post by Joseph Schwenker on 2010-02-10
I have multiple live CDs.  All of them work on another computer, and none of them work on mine.  I have tried using all of these discs with another CD-ROM drive, and had the same problems.  The computer I got the other hard drive from was from a completely different computer, nothing was the same as mine.  It had Crunchbang 9.04 installed on it.  I have already tried your suggestion of adding things until it fails (that's one of the first things I did) and it failed no matter how few components were in the machine.  I will make a video showing all of the connectors and will post it soon.  Thanks for your help!

---

### Post by 23dornot23d on 2010-02-10
Ok I have subscribed to your link on You tube .... 

I will watch out for the video ..... it should email me when you upload it .....

---

### Post by Joseph Schwenker on 2010-02-11
I took out the CPU, and everything was perfect.  I put it back in, and got the same results as usual.  I also made a video of my connectors, which is [here]("http://www.youtube.com/watch?v=zeUi0HLnFdg").

---

### Post by 23dornot23d on 2010-02-12
There were 2 thing's I noticed there ......

1 .... you did not unplug the computer or turn it off ..... as I asked ....

and

2 .... it was 90% of the time almost in darkness ......

[IMG]http://i46.tinypic.com/2q21iyv.jpg[/IMG]

( What is that green light - to me this looks switched on ..... )

please if you do it again ..... or take a few photos using a flash ......

**Turn it off** and [B]Disconnect it ......... from everything else .....
[/B] 
A) Its to stop you electrocuting yourself ........ 

and

B) to make it easy to put it in a position where light can get into the box so we can see inside at some of the components ......

I was hoping maybe to see a little of the Motherboard and the components on it .... and possibly the RAM ...... if possible ....
is there two sticks or one ..... and do any of the components on the mother board look as if they have any 
damage or brown colouring from possibly failing ...... 

what I saw was a machine switched on with the power lead in it and you must have been less than a inch away with the camera ...... and 90% black ......

[B]I worry !!! ........ 

[/B][B]
Always disconnect if the sides are going to be taken off ,,,, 

[/B] [B]
How have you worked on it and have you always made sure any static
has been discharged from you when touching both the CPU and the RAM
  
- always after you have it disconnected put in a place where you can work on it easily ......
and have some light possibly a torch or overhead light ... so you can see what you are doing .....

[/B]can it be done again with some .....  [B]light shining in it and it switched off  

PLEASE ..... 

*** if you do not discharge static from your body before touching 
components like the RAM ... you could possibly damage them .....


There are usually 2 to 4 slots ... and RAM has to be matched if its in 2 sticks .... on most computers ..... ram can cause problems ..... if not correctly seated too. 

__________________________________________

A better idea still .......

 I think you may be better off taking it to a shop and get them to sort it out for you ........ after all this is not a job most people would get involved in doing
without reading up and knowing exactly what they are doing ........

Even if we see a problem on the motherboard ..... someone will have to replace it and set it up ..... 

( but it could be any number of things if you have handled the components  .....   without getting rid of static ..... )

[/B]Sorry I would like to see this fixed here but after all of this I think the best possible solution is the shop .... if you are positive its nothing to
do with the operating system ..... as you say you have used a few Live CDs ...... so this appears to be hardware ....

and if its not the (Power Supply) not the (CD player) .... not the (Hard Drive) .... (CPU) should be ok to get as far as the boot screen ....
then we are narrowing it down to Motherboard...... RAM........ Graphics Card....... or possibly a bad data bus lead or connection or
to cover all options ..... Something Else ......( LAN ? ..... can cause lock ups sometimes - but it gets to the boot screen ? )

You have also removed the Network Card .....and The Graphics Card ....... 
( just running it from the onboard vga - then its not the network or Graphics card )

You ran it minimal configuration and it did not work .... I seem to recall you saying ...

[B]So Take it to A Computer repair Shop ......  
[/B]

---

### Post by Joseph Schwenker on 2010-05-01
Problem solved.  Replaced motherboard and power supply.  New motherboard was not compatible with old hard drive.  Acquired new 160 GB IDE one, set it to slave, and system is 100% operational.  I fixed it about a month or two ago.  Thanks for all of your help!

---

