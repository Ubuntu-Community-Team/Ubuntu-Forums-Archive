---
title: "ubuntu 10.04 extremely slow!"
date: 2010-05-02
forum: General Help
---

### Post by EasyGo on 2010-05-02
Hello. I just upgraded from ubuntu 9.10 to 10.04 yesterday through the update manager. I had no problems with 9.10 but with 10.04 just moving a window from one monitor to another is a hassle. My computer is barely usable. Even YouTube doesn't load correctly. I just started using ubuntu recently as my main operating system and don't know what to do. My Specs are as followed:

Motherboard: Asus P5vd2-x
Processor: Intel Celoron D 3.46 ghz
Ram: 1 gb
Video Card: Ati Radeon x700
Harddrive: Currently 40 gb ide with secondary 250 gb sata

---

### Post by dino99 on 2010-05-02
remove xorg.conf: sudo rm -f /etc/X11/xorg.conf

check: system admin hardware driver: is yours activated ?

which video driver is installed ?

what errors into .xsession-errors and logs (system admin log viewer) ?

sudo dpkg -configure -a

---

### Post by ajdelozey on 2010-05-02
I have just moved from Ubuntu 9.10 to 10.04 and found the same problem.  Opening ANYTHING takes from 5 to 10 seconds, and multi-tasking is worse.  If I have a song playing or video and I open another window the song or video is interrupted until the new window is open....I'm really disappointed considering the great experience I was having with Karmic.  I may just roll back if I can't get this performance issue solved.

Any ideas?

---

### Post by techunit on 2010-05-02
Strange Because Lucid is the fastest ever. What are your system specifications? You are using the ATI Restricted Drivers? If you are they are causing all kinds of problems. You did a update through the Update Manager? If all else fails and I mean all else a clean install with do the trick. (But When you do do the clean install manually partition the drive and create a /home partition) Update Manager Upgrades are always bad for me.

---

### Post by kaspar_silas on 2010-05-03
Hey ajdelozey your not alone. I just done a clean install of 10.04 on my Asus 900 and to put it bluntly, it's crippled. 

The internet is working at the speed of a 14.4k Modem. Some programs like Chromium are taking >2 minutes to start up and others like firefox don't seem to work at all. Plus I have an intermittent and variable lag on both the mouse and keyboard. 

Whilst this emulation of early 1990s performance and issues made me nostalgic, and the new purple terminal is nice, I am pretty disappointed. I realize these issues are all, no doubt, solvable but I don't really have time for that and I don't really think you should have to do that to get a working computer. 

The lovely 9.10 was working fine and has done since day one. Hence I think a quick retreat into the tested 9.10 is in order. I get the feeling that leaving 10.04 a few weeks is in order.

p.s. Firefox just loaded >6mins!

---

### Post by wojox on 2010-05-03
Try [Disabling IPv6]("http://wojox.homelinux.org/?p=46")

---

### Post by techunit on 2010-05-03
> **kaspar_silas said:**
> Hey ajdelozey your not alone. I just done a clean install of 10.04 on my Asus 900 and to put it bluntly, it's crippled. 

The internet is working at the speed of a 14.4k Modem. Some programs like Chromium are taking >2 minutes to start up and others like firefox don't seem to work at all. Plus I have an intermittent and variable lag on both the mouse and keyboard. 

Whilst this emulation of early 1990s performance and issues made me nostalgic, and the new purple terminal is nice, I am pretty disappointed. I realize these issues are all, no doubt, solvable but I don't really have time for that and I don't really think you should have to do that to get a working computer. 

The lovely 9.10 was working fine and has done since day one. Hence I think a quick retreat into the tested 9.10 is in order. I get the feeling that leaving 10.04 a few weeks is in order.

p.s. Firefox just loaded >6mins!

You had this problem after a clean install? That seems very unlikely, but I don't like arguing. I would recommend that you look at the system resources and see if your system is using to many or too few?

---

### Post by TBABill on 2010-05-03
Could any of these be related to the problem with Chromium and memory leakage? Apparently some users are having crippling issues if using the most current from the daily PPA. I do not know if this could be related, just throwing it out there just in case.

---

### Post by techunit on 2010-05-03
> **TBABill said:**
> Could any of these be related to the problem with Chromium and memory leakage? Apparently some users are having crippling issues if using the most current from the daily PPA. I do not know if this could be related, just throwing it out there just in case.

I doubt it but it is a possibility. I doubt that a problem lays with the operating system no longer properly utilizing the resources available to it.

---

### Post by bobsp on 2010-05-03
I'm finding 10.04 to be much slower than 9.10 as well. I have it installed on a USB flash drive (clean full install - not live CD image), plugged into a Dell E6400 inspiron laptop. Worked beautifully for 6 months with 9.10, but 10.04 takes longer to start apps, greys out apps more often and for longer whenever I try to do something. I find myself opening apps twice sometimes, as the wait is so long for the first one to open that I double-click the file again! Also, gave up with the "broadcast" feature - was causing a pop-up window every minute or so, and system ran even slower.

---

### Post by techunit on 2010-05-03
It seems to me that Ubuntu 10.04 was designed to be used most effectively on new hardware but didn't eliminate support for older hardware. Lucids system requirwments will leave some unhappy but there minimums have icreased. Not that you hould be affected by such a change...

---

### Post by orthod0ks on 2010-05-08
I'm experiencing the same issues. No restricted drivers are being used. It seems to come and go. For 10 seconds, it will run great, then it just bogs down again. It's unusable. It's also affecting video streaming over minidlna.

Hmm... while it wasn't displayed in the restricted drivers manager, I did still have ATI drivers installed. I just searched in Synaptec for ATI and removed all driver-related entries, removed them, and restarted. It seems to be running 1000% better now.

---

### Post by petermck on 2010-05-08
I had the same problem. Searched in Synaptic for ATI and completely un-installed all xserver-xorg/ati related packages that came up. Installed fglrx. Rebooted and reconfigured X. This fixed it.
Then I did the same process in reverse, uninstalled fglrx and related packages and re-installed just xserver-xorg-video-radeon (the package may vary depending on the model of ATI card you have. Mine is a 9200GT).
Rebooted, reconfigured and things work OK.
I noted that 3D effects do not work with either configuration. They used to work although I don't generally have them turned on, so I'm not too concerned about that.
Things still seem a bit clunky with screen refreshes taking about 0.2 sec when I switch from desk 1 to 2. That's not really acceptable.

I just checked a LiveCD and on the basis of what is installed there I just reinstalled the following packages.In addition to xserver-xorg-video-radeon.
xserver-xorg-video-ati (with xserver-xorg-video-mach64 & xserver-xorg-video-r128 dependancies)
radeontool
fglrx-modaliases
Everything works fine now including 3D effects.

I can't be 100% sure, but I thought I saw xserver-xorg-video-mach64-dbg & xserver-xorg-video-r128-dbg previously after the upgrade.

---

### Post by dolson on 2010-05-09
I have the exact same problem on two completely different systems... And I do not have ATI GPUs, I have NVIDIA cards. The performance is the exact same with or without restricted drivers enabled. System load is insanely high - like around 1.0 at "idle" and 3-4+ while trying to play an MP3 and surf the web... It's ridiculous.

---

### Post by techunit on 2010-05-09
Well it seams like another problem caused by bad drivers? I had issues with the ATI  drivers for other reasons.

---

### Post by dolson on 2010-05-09
> **techunit said:**
> Well it seams like another problem caused by bad drivers? I had issues with the ATI  drivers for other reasons.

Well, as I said, I tried with the restricted drivers (both of the options available), as well as without, and the same high CPU load results no matter what, on two different systems, one with an AGP card, the other with a PCI card. I don't know what I'm supposed to do when I've tried all the drivers available. I guess just delete Ubuntu 10.04...

---

### Post by techunit on 2010-05-09
If you have high CPU usage make sure that cpu scalling is set up. Some systems don't support ubuntu's cpu scalling code. There are plenty of Articles on the net about enabling this.

---

### Post by jezza1972 on 2010-05-11
Sorry to say but it's the end of the road for ubuntu and me. I also have the same issues with my toshiba laptop. It's so slow that the software centre keeps crashing, updates fail, 100% cpu usage permanantly, internet was as slow as dial up, and forget any effects, anything other than 'none' in visual effects freezes the system and i have to hard crash the system. 

Yet when i was using 8.04 and 8.10, i had barely any issues at all. As a temporary measure i have gone back to 8.10. I know it's no longer supported, but as 9.04 and 9.10 also give me hassle, and the fact i hate windoze, i have ordered a new mac.

---

### Post by kaspar_silas on 2010-05-11
Actually I worked out some problems. I keep my home on a separate partition. It was various old config files in this not playing nicely with 10.04. Purging home of all config files solved this. Thou naturally this is not the most elegant solution. 

There are however still two outstanding problems.  
A: Firefox locks up all the time (I use chromium mostly but it annoys me that firefox doesn't work) 
B: I can not "unlock" any gui. For example the log in screen settings menu. I can do the equivalent sudo command just not get privileges via unlock.

As for the fixs suggested:
System resources are normally totally fine at the time.
IPv6 is disabled.
Removing Chromium didn't help
It's not the minimum requirement thing as I also tested the netbook edition and it still happens. If 2g of Ram and 900MHz isn't enough to run one browser on the stripped version then something is wrong.

> **techunit said:**
> You had this problem after a clean install? That seems very unlikely, but I don't like arguing. I would recommend that you look at the system resources and see if your system is using to many or too few?

A: happens on a totally clean install. By totally clean I mean loading from a usb and accepting all the defaults and not changing any settings  
don't know about B: 

As for arguing why would I do that? The original post wasn't anti Ubuntu. 9.10 was close to perfect in my opinion. I am only giving my experience with 10.04 and I am not exactly alone.

---

### Post by techunit on 2010-05-16
Hey we all find ubuntu to our taste differently and sometimes we don't always agree on things but that should never stop us from helping each other.

---

### Post by abdusamed on 2010-05-16
same here..but the common prob thread sticky solved it

---

### Post by techunit on 2010-05-17
apps such as dropbox swolve such problems for me. just log in and my files get synced... I believe that the same sould be true of ubuntu one.

---

### Post by irvotheturbo on 2010-05-18
> **kaspar_silas said:**
> Actually I worked out some problems. I keep my home on a separate partition. It was various old config files in this not playing nicely with 10.04. Purging home of all config files solved this. Thou naturally this is not the most elegant solution. 

This could be the same problem I'm having. Did you simply delete all the hidden folders starting with . in your home directory? 

I've got the feeling the CPU is throttling too much though, even though it wasn't doing this prior to the clean install (AMD Turion64).

---

### Post by techunit on 2010-05-18
Actually He is right deleting folders with a "."befordre there name (hidden) should do it. With linux I have to do this occasionally with gnome if I was messing with the panels or the dock.

---

### Post by kaspar_silas on 2010-05-24
> **irvotheturbo said:**
> This could be the same problem I'm having. Did you simply delete all the hidden folders starting with . in your home directory? 

I've got the feeling the CPU is throttling too much though, even though it wasn't doing this prior to the clean install (AMD Turion64).

Sorry didn't notice your reply. Yeah I did basically deleted all the hidden files but I copied them first. So if a program lost settings I needed I then copied the specific files back. So far the copied back files haven't messed it up so deleting them all is definitely overkill.

Incidentally I also later found out by reinstalling gdm you solve the being unable to click unlock (to go into admin mode from a user gui thing) problem.

> **techunit said:**
> Hey we all find ubuntu to our taste differently and sometimes we don't always agree on things but that should never stop us from helping each other.

Totally agree.

---

### Post by keayz on 2010-05-26
I too have these problems with my Toshiba Tecra. I found the drivers in Synaptic but am concerned about removing them. If I do so will my display screen and touchpad still work?

---

### Post by slovy88 on 2010-05-28
hi guys i had these problems before too but somehow i fixed no idea how though...but now i have a different problem whenever i try to update or run synaptics it tries to uninstall fglrx and after a restart puts me back to the same problems and then again i have to install ati driver from ati site and run sudo aticonfig --initial
but then again synaptic...so i not to update...

---

### Post by kaspar_silas on 2010-06-02
> **keayz said:**
> I too have these problems with my Toshiba Tecra. I found the drivers in Synaptic but am concerned about removing them. If I do so will my display screen and touchpad still work?

Why do you want to remove the drivers. Do you think the problems lies with them? Just to clarify I didn't remove any programs or drivers only the program settings. I guess it's actually just the gnome settings but I haven't tested it. This stopped the freezing issue thou firefox is still very prone to freezing. 

If you are sure it's the drivers. 

You could test removing the touch pad one easily by opening a terminal and removing it with:

$ sudo apt-get remove [the-driver-name]

then try the touch pad. If the touch pad is now broke just reverse this by reinstalling. So from the same terminal: 

$ sudo apt-get install [the-driver-name]

I think their is also a safe graphics mode Ubuntu fails back to if you mess up the display. But I would definitely check up on this first.

---

### Post by efflandt on 2010-06-02
I wonder if any of your issues are related to the new kernel mode setting (KMS) video driver.  That resulted in slow moving things around in X (like card trails in Solitaire) and broke suspend/hibernate on my desktop with ATI X1300 using default drivers/modeules.  The **nomodeset** kernel boot parameter restored video to as snappy as 9.10 and fixed suspend/hibernate.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

The nomodeset (or radeon.modeset=0 on a USB drive) likewise fixed in issue with sometimes scrambled graphics boot hang (colored graphic pattern at top of screen) with a Dell Inspiron 6400 laptop with Radeon Mobility X1300 graphics.

I also have a old Compaq Presario V2000 laptop w/ATI 200M graphics that was unable to suspend or hibernate in 9.10.  The nomodeset made 10.04 more responsive, and it is now able to suspend.  The keyboard is more responsive in 10.04 (dropped keys very rare now), and mousepad is now just occasionally laggy and jumpy.  In 9.10 it was difficult to even type in a password without dropped keys.

---

### Post by jt1 on 2010-06-02
I'm also experiencing troubles with 10.04. After i did the upgrade from 9.10 to 10.04 my system is worse then Vista (didn't know this was possible). Latest issue: when i try to shut it down, it just logs out. The shut down button in the login screen doesn't work at all. All I can do is just switching the power off :(

My system also runs and boots very slow, which is remarkable considering the specs:

Intel Core 2 Quad CPU    Q6600  @ 2.40GHz
4 GB of ram
nVidia GeForce 9600 GT

If no one finds an answer to the problem I'll have to downgrade to 9.10 again (which is very inconvinient cause I'm studying for my exams and really don't have the time to do this)

---

### Post by jt1 on 2010-06-02
I've just used some off the hints in the sticky post of this forum, and now my system works again (well at least better than before :)).

---

### Post by pauln60 on 2010-06-03
I also used

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

and eliminated ati packages (as per #13) to bring my bogged Dell latitude back to life - works better than ever.

---

### Post by Johnny_Lifeson on 2010-06-03
Applications

Now for the current applications. Basically we just need to make a full list of the installed apps.

sudo dpkg --get-selections > /home/user/package.selections

Of course don’t forget to backup package.selections on the external hard-drive. Also you should backup your /etc/apt/sources.list file since you probably have some extra sources listed over there. Now you can go about your business and do a fresh install.

Restore

Once your done with the fresh install, copy the file package.selections into your home. Then copy your sources.list file into /etc/apt/ and update it to match your current distro (e.g Gutsy –> Intrepid) you can use CTRL + H in gedit for that. Then do a “sudo apt-get update” ,and finally invoke:

sudo dpkg --set-selections /home/package.selections && apt-get dselect-upgrade

apt-get will now start downloading all your apps, this will take some time depending on the number of apps you have installed.

Once that’s done, just copy your backup-ed /home over the current /home (again don’t forget hidden folders).

Log out and log back in to your shiny new fresh install!

Edit: As the commentators below also mentioned, it would also be wise to have your /home in a seperate partition (thanks Boo Radley), backÂ  up /etc (thanks Bartek), and use the tar command to back up home (it will preserve your structure and permissions)

---

### Post by kaspar_silas on 2010-06-21
Just a quick note of the fix I used on my final (firefox being slow and locking up) problem. 

Firstly if you google "firefox slow ubuntu 10.04" you get loads of pages saying to mess about with variables in the about:config. This had no effect for me.

However removing the firefox add-ons "Bindwood" fixed the freezing during use issue. 

It was still being very slow to start firefox. This in turn was fixed by removing the "Ubuntu Firefox Modification" add on. Strangely I reinstalled this after and all seems well now.

---

### Post by squeakerz on 2010-09-20
[SIZE=2] New to Ubuntu10.04 but have been using it for several months everything worked great and fast, loved it!   Formatted drive, installed winxp for no good reason, formatted again reinstalled Ubuntu 10.04:  worked great for a bit. Did same terminal install of Java 6 u21, and vlc 1.1.4 with necessary extras same as previous install.  But this time VLC  doesnt stream smooth, choppy play.  restarted and now whole system scrolls like waves and is slower than dialup 10 years ago.   Any step by step solutions??

Appears it may be nVidia driver.  Any help fixing or getting a working driver would be appreciated!!!
[/SIZE]

---

### Post by kaspar_silas on 2010-09-27
Have you tried disabling the nvidia driver to see if that actually does "fix" your problem. You can test this by removing them by pressing: 

Ctrl Alt F2
which should drop you to a text only terminal

Typing:
sudo apt-get stop gdm

sudo apt-get --purge remove nvidia-*

Finally:
sudo shutdown -r now

If that works you can then follow any how to for installing nvidia drivers.

---

