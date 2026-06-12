---
title: "What has happened to ubuntu?"
date: 2010-01-31
forum: General Help
---

### Post by dgrafix on 2010-01-31
Seem to have had a lot of problems with the new one (Karmic). 
-Firstly the GDM login has gone so i seem to be stuck with all the super ugly looking user accounts as pretty pictures insted of a proper login and no options. 
-Apps seem to take ages (up to half a minute sometimes!) to load compared to the last version (9.04) and everything seems sluggish. 
-There was the issue of my camera which has just worked out of the box on the last few distros, fails to mount (although i fixed that in the end)
-I dunno what has happened to wine but it takes like 5 minutes for an app to appear.
-libstdc++5 seems to have just been dropped out of the repos and for some reason libstdc++6 doesnt seem to work. (how can i get the old one back, i have apps that need it)


(Dual core 64bit 1Gb ram)

On a positive note, it is nice to see proper screen maximisation on dual head.

---

### Post by bakegoodz on 2010-01-31
I think it is a problem with your setup, or maybe even your hardware. Sure Karmic is slower on older machines, I find it a little sluggish on P4 with 512 MB of RAM. It should run fine with your specs. If you have a older or motherboard video I recommending turning off the Desktop effects, you can get there by right clicking desktop, then properties. Also open a console and run: top   to see if there is a wayward app eating your computer alive. I sometimes find Adobe Flash (npviewer) running at 100% even without a browser running. You can run kill then the PID number of the process. example: (kill 9765) or uninstall the app if you don't need it.
 Finally check your hardware, see if anything is running too hot, you can install an app like lm-sensors or ksim, or most BIOS setups have a temperature and fan speed page. You also do the high tech "ouch" test, put finger on the hard drive case, processor heat sink, or back of power supply while the computer is running or immediately after turning it off. Running memtest on your RAM or manufacturers hard drive utility can find problems that cause slowness too.

---

### Post by dgrafix on 2010-02-03
> **bakegoodz said:**
> I think it is a problem with your setup, or maybe even your hardware. Sure Karmic is slower on older machines, I find it a little sluggish on P4 with 512 MB of RAM. It should run fine with your specs. If you have a older or motherboard video I recommending turning off the Desktop effects, you can get there by right clicking desktop, then properties. Also open a console and run: top   to see if there is a wayward app eating your computer alive. I sometimes find Adobe Flash (npviewer) running at 100% even without a browser running. You can run kill then the PID number of the process. example: (kill 9765) or uninstall the app if you don't need it.
 Finally check your hardware, see if anything is running too hot, you can install an app like lm-sensors or ksim, or most BIOS setups have a temperature and fan speed page. You also do the high tech "ouch" test, put finger on the hard drive case, processor heat sink, or back of power supply while the computer is running or immediately after turning it off. Running memtest on your RAM or manufacturers hard drive utility can find problems that cause slowness too.

Thx but have already done most o that. Its not my hardware because old ubuntu, windows and debian seem fine. Its defenitely something about karmic.

---

### Post by UKBB on 2010-02-03
> **bakegoodz said:**
>  I find it a little sluggish on P4 with 512 MB of RAM.

Yep, bumping my memory up by 1 gig helped a ton with that.

---

### Post by cjhabs on 2010-02-03
Sitting here with Firefox, Evolution and Truecrypt running - visual effects set to normal - and I am using 1.3gb of memory. Yours could well be a swapping issue.

---

### Post by Vaphell on 2010-02-03
GDM login is very unfortunate, but it's the gnome folks' fault. Apparently they rewrote bunch of code and old gdm functionality is no more - and ubuntu in fact didn't follow these changes in 3 releases.
It's weird though that configuability of the login screen is so neglected, current state of affairs causes obvious problems - exposing whole list of valid logins for anyone glancing at screen for 1 second, inconvenience of clicking to login when login[enter]password[enter] was so comfortable.
Customizability of linux is supposed to be one of its strong points. From the usability point of view it's a serious functional regression and there is nothing on horizon to make things better.
Sometimes i wonder if these guys have their priorities straight.

---

### Post by dgrafix on 2010-02-04
I agree, it is to pander to all the "book quick" fanboys, of which i am one (at least to the point of having a reasonably fast bootup), HOWEVER even with the GDM login Ubuntu would out boot any windows (perhaps not to login, but windows does not finish booting at the login and can take between 1 and 5 minutes to become useable after login - which many wind users fail to count when "racing" them) So tbh i dont see the point of this move.

If my problem is indeed a swapping issue i dont understand why the latest version of ubuntu is such a memory hog, when the last version ran fine.

---

### Post by dgrafix on 2010-02-05
Found the problem, it seems to be opera!
I booted up and visited something on opera, left it running for a day and night when i came back the swap was 100%@2.9GB the ram was 100%@1GB! (figures obtained after waiting half an hour for the task mon to load) i found out it was Opera.

OPERA+UBUNTU64 = MEMORY LEAK BIG TIME

sudo apt-get remove opera!!!!!

Chrome for me from now on because FF seems to be loosing it these days too.

---

### Post by Swagman on 2010-02-05
You might want to try Epiphany too. It's blazingly fast.

---

### Post by llawwehttam on 2010-02-05
Hmm, I have had my fair share of problems with karmic but a lot of peeps have too. It was released a bit too early just like vista.
Lucid looks good though.

---

### Post by Roasted on 2010-02-05
If you need stability, use an LTS. They're there for a reason.

---

### Post by Objekt on 2010-02-09
I, too, have been wondering what the frack is going on w/Karmic.  Stuff just seems to break spontaneously, and there are some rather serious bugs.  I mostly have got around them because I don't mind tinkering, but some would be showstoppers for non-technical users.  

F'rinstance: A couple of days ago, I had a very tense hour when my video broke for no apparent reason.  It started with a game, Urban Terror 4.1, crashing on start with an OpenGL error message.  In trying to fix this, I went through all kinds of fun stuff like getting no GUI upon boot.  I eventually solved it with a combination of stopping the X server, dropping to the CLI at runlevel 3, and reinstalling the Nvidia 190.53 driver package (*.run file) that I just happened to have in my /home folder.  In short, a lot of tinkering that really shouldn't have been necessary, and I still have no idea why it happened. 

Another example: the ongoing saga of internet connection sharing.  I have a desktop with 2 NICs, one of which I would like to be able to share with another computer.  I have been struggling with it off and on for around a month, without success.  ICS is supposed to be "Simple" in 9.10, but so far I can only make it happen when running Windows XP on the same hardware.

9.10 has also had the ugly "entire system freezes, but you can still move the mouse pointer around" bug, again seemingly at random, on old and new hardware alike.  It hasn't happened to me on my computer, but that's just pure luck.  When I built an Ubuntu system for someone recently, I used Ubuntu 8.04.3 LTS instead of 9.10 because I did not want to become remote-control tech support, and did not want the (semi-technically literate) user to have a crappy experience.

There's also performance in general.  I can't put my finger on why, but some things just do not work optimally under Ubuntu 9.10.  Regardless of the desktop environment I use, whether Gnome or LXDE, the visual presentation of at least some 3D games - Urban Terror is the one I play most - is simply not as smooth as it is using the same hardware under Windows XP or 7.  While Urban Terror shows a framerate locked to my CRT refresh rate (75 frames/sec), it is perceptibly laggy compared to running with the same settings under Windows XP.  I don't know why.

(Yes, I have desktop effects turned off, and my hardware is plenty beefy (Nvidia GeForce 9800 GTX+ video card, Intel E8500 Core 2 DUO CPU, 4 GB DDR3 1333MHz RAM).  I can only conclude that there must be some "extra" stuff Ubuntu is doing in the background to slow things down just a little bit).

I'm tempted to start over with Ubuntu 8.04.3 LTS.  The only possible drawback, as far as I know, is that I would get older versions of some things from the repositories.  For the apps that matter to me, like Thunderbird and OpenOffice and Firefox, I can get the newer versions by installing another way (Ubuntuzilla for example).  I would not miss GRUB 2 terribly, as it is exhibiting some unfortunate bugs, being still in Beta stage (chiefly, a mysterious 20+ -second delay on startup).  The older GRUB had limitations, but in some ways was much easier to live with.

This has gotten way more long-winded that I intended, but I share the OP's general concerns about the direction of Ubuntu.

---

### Post by dgrafix on 2010-03-08
Yes i agree. I reinstalled it from scratch (last came from an upgrade) but it still seems to be problematic (little things like alt-tab to switch windows, while it switches it is not comming up with the switcher properly) and other little niggles.

I get some system freezing too alhough i traced that back to opera. But whereas ctrl alt f1 used to be instant, now it seems to take a while. I also wonder what happened to ctrl-alt-bs to restart X (this was useful too)

I cant quite put my finger on it either but i my Debian and windows on same machine run as expected (as did 8.10 ubuntu)

---

### Post by derrick81787 on 2010-03-08
I think that a lot of the memory issues and general sluggishness comes from having desktop effects on.  It could just be my video card, but I turned off the effects and I think it helped a lot.  I have an NVidia 6600GT using the NVidia drivers.  It was a nice card when I got it (several years ago now, though) but it seems strange that it would have a hard time handling the effects.

Either way, I think my performance got better when I turned the desktop effects off.

---

