---
title: "can't click in flash settings"
date: 2011-10-23
forum: General Help
---

### Post by ronniew on 2011-10-23
its doesn't matter if i'm on a 64 bit machine or 32 bit, I can not click buttons in flash. I can get to the settings but can't really change anything even if i could i couldn't not click the close button anyway.. . tab works to navigate but not everything is usable that way. the drop down menu for camera selection will not work by using tab and enter or any other combination.....  Im usually running ubuntu and various machines and its always the same problem... tried different browser with no luck.

case in point its also a problem on my windows machines running firefox, although chrome works there,, chrome on ubuntu although doesn't allow clicking in the settings area

i've been to adobes site and thats a partial workaround because you can not make selection of cameras there...

I have been searching for a way to change the default camera selection manually through some kind of local flash setting thats stored somewhere but i have not be able to find it

any help is appreciated

---

### Post by oldtimer7777 on 2011-10-24
> **ronniew said:**
> its doesn't matter if i'm on a 64 bit machine or 32 bit, I can not click buttons in flash. I can get to the settings but can't really change anything even if i could i couldn't not click the close button anyway.. . tab works to navigate but not everything is usable that way. the drop down menu for camera selection will not work by using tab and enter or any other combination.....  Im usually running ubuntu and various machines and its always the same problem... tried different browser with no luck.

case in point its also a problem on my windows machines running firefox, although chrome works there,, chrome on ubuntu although doesn't allow clicking in the settings area

i've been to adobes site and thats a partial workaround because you can not make selection of cameras there...

I have been searching for a way to change the default camera selection manually through some kind of local flash setting thats stored somewhere but i have not be able to find it

any help is appreciated

Try this really quick and see if it solves your problems:

[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by lincoln32 on 2011-10-24
I have the same issue here both 32 and 64 using 11.10 only and I even tried chrome to no avail also flash aid made no changes to the any of the 11.10 (3) that i have running atm all fail to allow me to configure flash settings

---

### Post by oldtimer7777 on 2011-10-24
> **lincoln32 said:**
> I have the same issue here both 32 and 64 using 11.10 only and I even tried chrome to no avail also flash aid made no changes to the any of the 11.10 (3) that i have running atm all fail to allow me to configure flash settings

How did you install Flash on 11.10? 

If you are running 32-bit Ubuntu:

 sudo apt-get install flashplugin-installer 

Or if you are running 64-bit Ubuntu:
 
sudo add-apt-repository ppa:sevenmachines/flash 
sudo apt-get update 
sudo apt-get install flashplugin64-installer

---

### Post by lincoln32 on 2011-10-24
on machine 1 ubuntu 11.10 I could not change flash settings for out Big BLue Button server and web meeting place voip video and chat (does work with stock 11.04 and puppy out of the box) install flash from software center and still failed and then tried adobe flash 64 from adobe version
11.0.1.152 all failed on all three machines I also tried chrome and it failed so not sure what to test next:)

---

### Post by oldtimer7777 on 2011-10-24
Have you tried using the PPA above? 

> **lincoln32 said:**
> on machine 1 ubuntu 11.10 I could not change flash settings for out Big BLue Button server and web meeting place voip video and chat (does work with stock 11.04 and puppy out of the box) install flash from software center and still failed and then tried adobe flash 64 from adobe version
11.0.1.152 all failed on all three machines I also tried chrome and it failed so not sure what to test next:)

---

### Post by lincoln32 on 2011-10-24
file not found so I will try later. but I am thinking it is not flash but os or web browser not allowing flash settings:confused:

---

### Post by oldtimer7777 on 2011-10-24
> **lincoln32 said:**
> file not found so I will try later. but I am thinking it is not flash but os or web browser not allowing flash settings:confused:

The best thing I have found to do in this situation is just go down the list step by step and make sure you have everything you need installed first to do what you want to do with Ubuntu:

[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by Erlander on 2011-10-24
Have you tried Flash_Aid?  It is a Firefox plugin.

---

### Post by lincoln32 on 2011-10-24
yes I have tried flash aid and since the site will not work in chrome I am thinking OS issue 

 [http://azlocobbb.banditti.com/](http://azlocobbb.banditti.com/) to add a camera or audio you must enable Flash access to camera and audio. Our site does work with 11.04 chrome and Firefox and windows only 11.10 has this issue.:)

---

### Post by ronniew on 2011-10-29
flash aid does not help at all.. this problem is on all browsers on 11.10  you can not click anything in flash settings

---

### Post by oldtimer7777 on 2011-10-29
> **ronniew said:**
> flash aid does not help at all.. this problem is on all browsers on 11.10  you can not click anything in flash settings

Did this happen in 11.04?

---

### Post by lincoln32 on 2011-10-29
not for me:(

---

### Post by oldtimer7777 on 2011-10-29
> **lincoln32 said:**
> not for me:('

Try this...  Create a USB flash thumb drive stick of 10.10 Ubuntu with Startup Disc Creator (set persistance to a few hundred Mb)..  use a 32-bit version of Ubuntu 10.10.. Boot from that stick of Ubuntu 10.10 and see if Flash will install and work on your thumb drive booted system..  It could be your video driver, that would be my best guess. Test your hardware.

---

### Post by lincoln32 on 2011-10-29
hmmm.. same failure on on all six machines that have 11.10 so it fails on
Nvidia GMA intel and ATI that all fail only since 11.10 and tested one with live mode and it failed. Puppy 5.28 works on the same machine (live) 11.04 worked on all of them but currently have none with 11.04 right now. I may have more time to test other distros tomorrow. our local Ubuntu team has a installfest so I may have more info or a fix Thanks:)

---

### Post by ronniew on 2011-10-29
i doubt it has anything to do with a graphics driver.... my guess is its either flash itself or something to do with compiz

---

### Post by no2498 on 2011-10-29
if you have a working flash installed
you can change the settings at/on the adobe site in the settings manager

---

### Post by ronniew on 2011-10-29
Been there done that, which is really not an option or real fix for this issue. Sure you can change privileges there for the most part, but no real options.

In other words you can not select your mic, or camera or whether hardware acceleration is on or off there.

Those settings are only available through the settings menu after right clicking on flash.

This issue sucks. Between no click in flash and the stupid random Udev naming of components like webcams and video card its truly a big giant open sore on the face of a great OS..

In other words it friggin sucks.

---

### Post by ronniew on 2011-10-30
just installed the newest version of flash and still no joy... this bug still remains... you can not click in the settings area in flash. It does not recognize the clicks.

---

### Post by ronniew on 2011-10-30
JUST AS A REMINDER

This problem friggin sucks,,,, and why the H*** is no one working on this pain in the a** problem?

can't click on flash setting and Udev is absolutely STUPID with its bullsh** random naming of tv cards, webcams, etc etc, making it impossible to configure your webcam and tv card permanently, or at all for that matter... 

Seriously and you expect us to help to push this OS further and promote it to our friends and family... how the he** do I explain these inabilities and the apparent lack of regard for fixing them??

Just to get it straight, this happens on numerous different machines, both 64 and 32 bit with 11.10. Grrrrrrrrrrrrrrrrrrrr..........

---

### Post by ronniew on 2011-11-01
sigh ,,,, pity that this bug is getting to NO support or time to be fixed... this is a MAJOR bug for MANY people!

---

### Post by ronniew on 2011-11-02
OK here is a tip, a clue and a semi work around for some people.

Before you click on settings make it full screen first then go into settings and it will work. Did ya hear that? Make it full screen first then right click and go to settings and it will work.

Unfortunately for me this does not help me because of the absolutely stupid stupid stupid stupid Udev random renaming of components like tv cards, and webcams, from video0 to video1 back and forth back and forth its so unbelievably DUMB that this trick really doesn't help me.

Oh and I looked at creating symlinks for Udev components, that crap doesn't work either. Why? because flash doesn't give a crap about some symlink rule it simply looks for video0 or video1 etc etc. Besides if you can't make what your working with full screen because the option isn't there then you can't get the stupid flash settings to recognize clips.

I read the reason they made and switched to Udev was because it made the system scalable. That may be true and great for servers but for regular users its just simply a pain in the a** and totally friggin stupid

---

### Post by gbear14275 on 2011-12-02
Any resolution?  I'm getting the fun intermittently

---

### Post by rahduke on 2011-12-24
I've been running into the same issue since 10.04 and flash 10 beta.... any bug support?

---

### Post by ronniew on 2012-02-20
yea switch to lubuntu ,,,, i did and everything works fine now.... something to do with compiz and flash.... totally blows... but lubuntu doesn't use compiz at all so everything works

---

### Post by lincoln32 on 2012-02-20
I did some reading and found that if you install ubuntu restricted Extras it will in stall windows flash with wrappers and flash settings will fail
but if you install adobe flash first then add the restriced extras it works correctly. on another install I removed ubuntu restricted extras and flash
then cleaned the machine with Ubuntu tweak then installed flash then installed Ubuntu restricted extras all works correct. tested on Ubuntu 11.10
64 bit and 12.04 alpha 2 64 bit and I will be testing  ubuntu 11.10 32 bit and Ubuntu 12.04 32 ASAP:popcorn:

I hope this helps others

---

### Post by jonolambert on 2012-05-15
There was a smiler problem with flash displaying incorrect colours with YouTube based flash videos as a solution it was possible to logout of the current session and log back in as an "Ubuntu 2D" session, which allowed the flash settings to be edited in this case disabling hardware acceleration. This worked on 11.10 64 bit machine and I am able to edit any flash settings this way in Ubuntu 12.04 32 bit laptop. After all that I logged back into normal Ubuntu session and the previously changed settings still applying in the normal Ubuntu session.

---

