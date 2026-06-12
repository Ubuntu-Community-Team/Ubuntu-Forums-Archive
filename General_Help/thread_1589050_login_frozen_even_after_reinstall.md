---
title: "login frozen even after reinstall"
date: 2010-10-05
forum: General Help
---

### Post by peacebliz on 2010-10-05
my login window and mouse freezes after boot up. 
 
i reinstalled 10.04 (without formating my home folder) and the same freezing happens just the same. it makes 3 drum sounds, u know the start up music, then freezo.
 
i compiled my first kernal maybe that the problem dunno followed some instructions compiling the kernal is over my head.
 
i know i can wipe the the drive down and everything will come out new but i don't have anywhere to back up my home partion.
 
Can i fix the login widow somehow? It must be a config file or something in my home partion thats causing this?

---

### Post by ridgeland on 2010-10-05
sometimes it can refuse to load a user if the user does not own it's /home/user   Try chmod
Also if you've been reinstalling and moving is the user number the same every time.

---

### Post by peacebliz on 2010-10-06
I reinstalled 10.04 with the setting turned off that shows the login window. When i start up ubuntu goes straight to the desktop and frezzes on the splash screen.
 
I think its the 10.04 frezze bug that people have posted about but i don't know.
 
I've reinstalled 10.04 over and over again and it allways frezes at the splash screen.
 
I have a compaq c61 notebook.
 
Its wierd because i've been running 10.04 for months now with no probs.
 
Anyone have any ideas whats going on?

---

### Post by peacebliz on 2010-10-07
I dont think permistions is the problem because i reinstalled 10.04 in another home folder and have the same problem.

10.04 just freezes on boot. the live usb frezzes on boot as well 



> Also if you've been reinstalling and moving is the user number the same every time.what do u mean by user number?

the owner and permitions of the home folder are owned by user1000#.

should the owner be my login name?

how can i change the owner of my home folder when the system wont boot?

---

### Post by ridgeland on 2010-10-07
Can you install fresh without using the old home partition and it boots OK?
My choice is I always use a partition that is /Data.  
/home/me only has system settings.  Any photos, music etc. are in /Data.  Why are you concerned about /home?  Data (music etc) or just settings?
UserID is 1000 by default.  So that looks right.
I'm only guessing what you're doing.  Are you using a LiveCD to see your home partition?  You might try
$ sudo chown -R me /home/me/*
That would set the ownership of all /home/me and all sub-directories to owner=me.
If none of this helps my next try would be to delete /home/me/.gnome and /home/me/.gnome2   Gnome should rebuild them after it boots but it erases all your settings, like screen size for nautilus etc.
Before deleting things though I would want a backup.

---

### Post by peacebliz on 2010-10-09
you were right on it ridgeland.... it was the permisions on my /home dir. dunno what they were but i changed the permitions of owner back to the user name.

i did a fresh install of 10.04 not formating my /home partition and bam i'm back up and getting things done again.

thank u for your help i owe ya :)

I was down for 5 days running off a live usb stick but hey i learned a lot trying to figure it out, thank u for putting an end to my missery.

i ran
sudo chown -R amber /home/amber

from a separate /home install

---

### Post by MyD0j0 on 2010-10-22
Ridgeland,

I was hoping I could solicit your assistance.  I'm having a similar problem as the OP, but I don't seem to have the rights necessary from my LiveUSB to do the work (or I'm just plain going about it the wrong way).

I initially installed Ubuntu 10.04 on a cleanly formatted disk from the LiveUSB (it's currently the system I'm using, usable because when I used the universal installer at pendrive.com I had the option of using a loop file).  When I rebooted after the install, everything froze at the login screen.  I've tried re-installing and even set the option to allow automatic login and all that did was allow the desktop to be displayed before everything froze (I've even installed from cd a couple times just to make sure it wasn't a bad Live ISO).

When I use the LiveUSB to chown the home directory as you suggested, the response is that there is no valid user.  I can change (and did) the owner to root; but after doing so realized I was never prompted for nor do I know the root password--or how to boot to a command line rather than the window system login.

Any thoughts on what I need to do?

thnks!

---

### Post by ridgeland on 2010-10-22
I don't have a LiveUSB so I just tested with a U10.10 CD.
Boot off CD - select [Try Ubuntu]
gets to desktop
System -> Administration -> Gparted
check the partition I need --- sda7 in this example
Applications -> Accessories -> Terminal
$ sudo su
gives you root privileges without asking for a password
# mkdir /mnt/sda7 (the partition to edit)
# mount /dev/sda7 /mnt/sda7
# ls -al /mnt/sda7/home
you should see yourname
# ls -al /mnt/sda7/home/yourname
Is yourname the owner of all the items? (except "..")
Now it could be tricky.  I'm not sure from a liveCD but looks like you might need to create the owner here first.
Just go to the System -> Administration -> Users&Groups and create yourname.
Now it should be able to 
# chown -R yourname /mnt/sda7/home/yourname/
(I made an assumption that on sda7 yourname is user 1000 and that the liveCD will create yourname with user 1000)

Of course you could be up against some other problem...

---

### Post by MyD0j0 on 2010-10-22
Thanks for the quick reply!

What you provided did work (using LiveUSB at that) for changing the user of my home folder to my login name, but unfortunately the login screen still freezes.  I wound up using the LiveUSB because my cd, after booting up, ends up blanking out with a cursor at the top left and then the video signal just stops (my monitor has dual video input that will switch over to what ever input is getting signal). One other thing I did do was change my keyboard/mouse.  I had been using a wireless setup (non-Bluetooth) and just to make sure that wasn't the issue, I am now using a wired usb keyboard/mouse with the same end result.

What I find so strange, is that on the exact same box, I have had no problems whatsoever using the LiveUSB--even in adding a couple programs, editing users, etc. and those setting even get retained--i didn't even have to make any system changes to get it to work.  But when I comes to booting from the hard disk, it just doesn't want to let me in the system.  

If you have any other ideas on what could be causing the problem, I'd sure love to hear them!

Thanks again!

---

### Post by ridgeland on 2010-10-22
I had an old Dell monitor that would not display - it gave a message though - out of range.  That was Ubuntu 7.04 and X-windows has changed so I cannot suggest that thread.
Like using a different keyboard see if you have an old monitor to try to get the installation done.
Are there switches on the monitor to toggle source?
I would search for posts about monitors, video drivers and X-windows.
The video driver used by the LiveCD is not the same as it installs I've noticed.

---

