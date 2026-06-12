---
title: "ATI &amp; Gnome 3 problems on Ubuntu 11.10"
date: 2011-10-19
forum: General Help
---

### Post by emptycoder on 2011-10-19
Hello everyone, I wanted to switch from Unity to Gnome 3 shell, and no matter how hard I try it seems I can't get it to work!
I have installed my ATI graphic driver via Additional Drivers then installed Gnome 3 shell and when I rebooted I found my desktop broken, strange fonts with blur color on Gnome bar, I tried to install Gnome 3 first then graphic driver and I got the same thing.
I also tried amd catalyst 11.09 instead of Addinonal Drivers (Which ATI says they fixed Gnome 3 Problems) and yeah, Gnome worked but with Gnome 2 interface not 3?! (Gnome, Gnome Classic, Gnome Classic With No Effects are all the same interface!??)
When I installed Gnome 3 alone, with no drivers, it works with no problem at all, but I really need to install graphic driver, I use so many 3D apps.
I have heard that ATI open-source driver probably will work better, but I have no idea how to install it.
I'm sorry for my bad English, and yes... I'm still n00b.
Please help me, I really hate Unity!
Thanks.
By the way! My Graphic Driver is Radeon HD 5470

---

### Post by crdlb on 2011-10-19
The default driver that works with GNOME Shell is the "radeon" driver. Until ATI fixes their proprietary driver (aka "fglrx" or Catalyst), you can't have both GNOME Shell and full 3d performance.

---

### Post by emptycoder on 2011-10-19
Sorry. is there a difference between Radeon. ATI and fgkrx?
and what option do i have to have full 3d performance? using another shell?

---

### Post by foppeh on 2011-10-19
The ATI catalyst 11.09 driver from their website should be the same as the fglrx found in the Ubuntu repositories. This is the restricted proprietary driver. 
If you do not install this driver (or uninstall it) your desktop will fall back to the built in Radeon driver. This is the free software reverse engeneered driver built into the kernel.

Unfortunately ATI is always slow to update their (fglrx) drivers. That may take several weeks (a couple of month) after a new kernel arrives or X11 has had some changes.

I'm happy with the Radeon drivers since I switched to Gnome 3. I've had several unfortunate tries with the proprietary drivers. It will al work some day.

Hope this helps you understanding the situation better.

have fun,

---

### Post by emptycoder on 2011-10-20
I got it, so right now I have no other choice but waiting for ATI to release an update to fix this problem.
But I'm wondering, is Radeon good enough for 3D graphics? Or do I have to give up on Gnome 3 and choose another Desktop Environment?
Thanks again!

---

### Post by kaldor on 2011-10-20
> **emptycoder said:**
> I got it, so right now I have no other choice but waiting for ATI to release an update to fix this problem.
But I'm wondering, is Radeon good enough for 3D graphics? Or do I have to give up on Gnome 3 and choose another Desktop Environment?
Thanks again!

Depending on your needs, the Radeon driver might be just fine. What sorts of things do you need?

In Ubuntu 11.04 I got about 50-60 FPS on average with Urban Terror. With the proprietary driver I get about 120. Catalyst is much ahead of Radeon in terms of performance, but I recommend against its use unless it's actually needed.

The open source drivers tend to be much more stable, albeit with less features.

---

### Post by emptycoder on 2011-10-20
If Catalyst is much better than Radeon then I'm afraid that I will abandon Gnome 3, because I use Blender, and playing video games.
I guess that I will stick with Gnome 2 classic until ATI fix the problem, I just hope they won't take so long.
Thanks everyone for your help.

---

### Post by ubupirate on 2011-10-20
I've also experienced massive problems when I tested 11.10 with Gnome-shell. 11.9 drivers fixed the rainbow colors, but the graphical corruption of gnome-shell is still there.

Hope 11.10 drivers fix the graphical corruptions that so many AMD/ATI people have been experiencing. Sent AMD an email asking if 11.10 would fix it, but they weren't at liberty to tell me and said I had to wait until changelog was posted. lol

Radeon HD4200 here.

---

### Post by kaldor on 2011-10-20
> **emptycoder said:**
> If Catalyst is much better than Radeon then I'm afraid that I will abandon Gnome 3, because I use Blender, and playing video games.
I guess that I will stick with Gnome 2 classic until ATI fix the problem, I just hope they won't take so long.
Thanks everyone for your help.

Well there you go. I'm in the same situation as you are :(

In the future I'll probably just dual boot two separate Ubuntus. Catalyst installed for gaming on one partition, and a default Radeon for everything else.

Someday the Radeon drivers will catch up, though. Can't wait for the day that I will never have to use a proprietary driver.

---

### Post by emptycoder on 2011-10-20
It seems that Windows has priority over Linux, and that's totally unfair! ATI drivers work fine on Windows, but on Linux... we have to wait for updates and fixes.

---

### Post by masgeeks on 2011-10-22
Free drivers work fine with gnome shell for most things I have found - I had issues with fglrx drivers.  Interestingly, free driver works better in 11.10 than fglrx did when this machine was on 11.04.

Go figure.

---

### Post by Lumsdoni on 2011-10-25
Woud someone me able to help me?

I too have this problem, but I only use my netbook for internet apps, WP, spreadsheets and video watching. No games.

I have an MSI wind u230, 2gb  RAM, single core 1.6ghz.

I use the hdmi out to watch avi files on my HDTV. DO I need the 3d drivers?

I prefer gnome to untiy I think but am havng the same corruption at present. How do I make sure all the right drivers are uninstalled, and the right ones are installed?

I am familiar with uing terminal but not on the actual files required themselves.

Many thanks in advance.

Pete

---

### Post by Lumsdoni on 2011-10-25
Woud someone me able to help me?

I too have this problem, but I only use my netbook for internet apps, WP, spreadsheets and video watching. No games.

I have an MSI wind u230, 2gb  RAM, single core 1.6ghz.

I use the hdmi out to watch avi files on my HDTV. DO I need the 3d drivers?

I prefer gnome to untiy I think but am havng the same corruption at present. How do I make sure all the right drivers are uninstalled, and the right ones are installed?

I am familiar with uing terminal but not on the actual files required themselves.

Many thanks in advance.

Pete

---

### Post by Captain.Blubber on 2011-10-31
I had same problem with ATI fglrx driver, with Gnome 3 flashing and messing all the time.
I was following this solution from wiki.ubuntu.com and now its all working like it should.

[http://goo.gl/Ogmbj](http://goo.gl/Ogmbj)

---

### Post by atulkakrana on 2011-11-02
Dont take captain.Blubber advice as that link isi too old and filenames are obsolete.

Perfect Fix:
Download latest drivers from 
[http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html](http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html)

Right click and select run as program

Go to terminal

$./whatever_name_of_driver

Just press ok and yes during installation questions

After it finishes, issue command

$sudo aticonfig --initial

Enjoy

---

### Post by JoZ3 on 2011-11-02
> **atulkakrana said:**
> Dont take captain.Blubber advice as that link isi too old and filenames are obsolete.

Perfect Fix:
Download latest drivers from 
[http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html](http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html)

Right click and select run as program

Go to terminal

$./whatever_name_of_driver

Just press ok and yes during installation questions

After it finishes, issue command

$sudo aticonfig --initial

Enjoy

OMG tnx for the news, fast update from ATI, I hope that this work gnome 3

---

### Post by JoZ3 on 2011-11-02
I just install and run as usual and unfortunately, I see no solution with 11.10 drivers :(

---

### Post by atulkakrana on 2011-11-02
> **JoZ3 said:**
> I just install and run as usual and unfortunately, I see no solution with 11.10 drivers :(

Whats the problem you are facing now? Did you installed the drivers from the same link I mentioned?

Try disabling

Tear free from Catalyst
and

Sync to VBLANk from compiz settings manager<OPENGL

Restart

---

### Post by JoZ3 on 2011-11-03
> **atulkakrana said:**
> Whats the problem you are facing now? Did you installed the drivers from the same link I mentioned?

Try disabling

Tear free from Catalyst
and

Sync to VBLANk from compiz settings manager<OPENGL

Restart

Yes I have disable the tear free and sync to blank since I upgraded the ubuntu, the problem is flickering and tearing in the gnome-shell, I never had problems with Unity but with the gnome-shell is other history, I thought that with the new drivers the problems were going to solve it but nothing happend... the only change is if I enable tear free from Catalyst, the flickering in gnome-shell was reduced a little... :(

---

### Post by viperdvman on 2011-11-03
This is why I intend to stick with NVidia when I upgrade my desktop's graphics setup to a single dual-head card. I've never had problems running anything in my Ubuntu 11.04 with the proprietary drivers *(they are tons better than the open-source nouveau drivers, which suck compared to the ATI open-source drivers)*. However, they don't seem to run very well in Ubuntu 11.10 for me (I blame my odd-ball setup).

My netbook runs an ATI Radeon HD 4250 (part of the AMD "Nile" V105 platform). I run Ubuntu 11.04 on it as well. Using "Additional Drivers", I find that compiz tends to run with a slightly but noticeably lower FPS than the OSS driver, and that pretty much any Adobe Flash video (YouTube, Hulu, etc.) runs at an astoundingly low FPS. I haven't tried the later versions of said Catalyst driver than what "Additional Software" provides, though. I do love the OSS "Radeon" driver. It runs Compiz, Adobe Flash, and even Ubuntu 11.10's Unity very very well. :)

So yeah, I plan to stick with NVidia on my desktop if ATI is still having problems with their proprietary Linux drivers.

---

### Post by arkeo on 2011-11-09
On a 5570 the radeon driver works flawlessly (Flash @ 1080p??? :shock: ) for my very unprofessional needs--I don't think I'll touch a Catalyst driver ever again!
I find GNOME3 a bit weird, as with all these new tablet-inspired GUIs (Unity, Windows 8, etc) but I think I *might* get used to it in time...

Once I figure out how to migrate my RAW photo workflow (Rawtherapee? UFraw? Darktable?) I might actually wipe Windows (and get a second HD for free! ;) )...except maybe for some light gaming... We'll see, but things don't look so bad on my desktop PC as they do on my netbook (see here: [http://ubuntuforums.org/showthread.php?t=1680348]("http://ubuntuforums.org/showthread.php?t=1680348") )

Cheers!

---

### Post by BillyBoa on 2011-11-10
> **JoZ3 said:**
> OMG tnx for the news, fast update from ATI, I hope that this work gnome 3

It works much better, but the flickering insists.
The solution is good but not perfect, why they pushed the SOLVED button?

---

### Post by Lumsdoni on 2011-11-12
Not working for me. 

I had 11.10 installed with Gnome 3, but did not install the ATI Radeon drivers.

I then read (stupidly)  that te 11.10 ATI driver fixed the gnome 3 problem.  So I duly installed it.

Tada! The Menu bar was fine, no crazy colours, but the some weird tearing occured inpop up boxes.

I managed to get the Control Centre up to change the Tearing option, but no change.

I then followed the instructions below to remove ATI Radeon and revert to the open source drivers (please correct if wrong) From [here]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx")

$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
$ sudo apt-get install xserver-xorg-video-ati
$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
$ sudo rm -rf /etc/ati

Unity was fine but now even if I select Gnome3, it loads up Gnome Classic.

I then uninstalled Gnome3, and reinstalled it but no change, I can still only get Gnome Classic, despite the Gnome3 option being selected.

I would greatly appreciate any help in getting my Gnome3 access back, I really like it (each to their own) and as a linux newbie, have finally got my laptop dual booting with Win7 and a shared data drive, and shared dropbox folders all working superbly well, and I really cannot face yet another re-install of Ubuntu.

Please advise if you need any command outputs for help.

Laptop is an MSI-U230 single core 1.6ghz, 2MB ram. 1st partition Win7 (32bit), 2nd partition (extended) Ubuntu 11.10 (32bit) and Swap, 3rd partition FAT32 Shared Data drive.

Chip is AMD MV-40, Graphics Card is ATI Radeon 5200 HD.

Thank you

---

### Post by arkeo on 2011-11-12
Lumsdoni,
try this: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

It worked for me...

Also, I think that "radeon" stands for the open source driver... Some might misinterpret what you mean if you simply write "ATI Radeon driver"... :)

I had a fine working Gnome Shell on Ubuntu Oneiric using the open source drivers, but after a couple of days it got messed up (though I'm sure I didn't touch anything)... I don't think Ubuntu is the right distro at this moment for a smooth Gnome Shell experience... Stick with Unity if you can, I know it's ugly (now you see the menus now you don't, are you kidding me?? :confused: ) and I understand perfectly why you prefer Gnome Shell, but after so many reinstalls and fglrx purges it's either this or a switch to Fedora, which has a very smooth Gnome Shell: I simply can't wrap my head around its package management system... (Stuck with apt-get for life?? :o )

Hope the link above helps...

Cheers

---

### Post by Lumsdoni on 2011-11-13
Thank you for the response. After a number of attempts at various solutions I think the system got so messed up I decided to go for a full re-install, which is not so bad as most of my docs are on the cloud.

Think I will have one go at installing the new drivers (11.10) and THEN installing Gnome3, and if that doesn't work I will just reinstall and forget the 3D drivers.

To clarify, are you saying that the link you provided, allowed you to install the Additional Drivers for 3D accelleration AND use GNOME3? OR just to remove the FGLRX ones after a failed attempt to run Gnome3?

---

### Post by arkeo on 2011-11-13
> **Lumsdoni said:**
> To clarify, are you saying that the link you provided, allowed you to install the Additional Drivers for 3D accelleration AND use GNOME3? OR just to remove the FGLRX ones after a failed attempt to run Gnome3?

The link I posted provided instructions on how to completely remove the proprietary fglrx driver and reinstall the open source radeon driver.
Even the latest version (Catalyst 11.10) **does not** work properly with Gnome Shell! If you want to run Gnome Shell you are stuck with the open source driver right now (i.e.: do nothing, it's the driver installed by default).
Whichever order you follow installing gnome-shell and fglrx it's **very** likely that you'll end up with a messed up system once again.

To clarify, if you want or need the proprietary drivers, at the moment you're far better off using a desktop environment **other** than Gnome Shell! Yeah, I know... :(

---

### Post by Lumsdoni on 2011-11-13
Once again thank you. GLad I posted to clarify. Not sure I actually need the accelerated graphics as I am not playing any games.

Video playback seems fine so I think I will leave it as is until someone confirms a new, working Catalyst driver with Gnome3.

Thank you for your patience and explanations, slowly finding my way with Ubuntu and you are all helping.

---

### Post by arkeo on 2011-11-13
> **Lumsdoni said:**
> Not sure I actually need the accelerated graphics as I am not playing any games. Video playback seems fine(...)

I'm glad I can help! I know a bit about these things because I have an AMD C-50 APU based netbook which sorely needs the proprietary drivers (otherwise its performance and battery life suck!), but on my desktop (Radeon HD 5750) I'm happy to use the open source drivers (I can even watch smooth 1080p Flash content! Amazing...), but I don't do anything 3D neither. It's capable enough for my needs, let's just say :D

You might want to take a look at these threads as well, (all regarding APU-based systems, in which driver optimization is important if not essential) for a deeper perspective into how much of a mess fglrx drivers are at the moment (and have been for many months now!):

11.10 Oneiric (AMD 64) AMD E-450, ATI HD 6320 AMD Catalyst 11.8: [http://ubuntuforums.org/showthread.php?t=1857911](http://ubuntuforums.org/showthread.php?t=1857911)

Acer Aspire One 522 - Smiles and Frowns: [http://ubuntuforums.org/showthread.php?t=1680348](http://ubuntuforums.org/showthread.php?t=1680348)

---

### Post by keithspg on 2011-11-19
Arrrrgh. I will not buy another ATI graphics card. What a runaround. 

None of the video drivers will not work with Gnome3. The closed source version in the repo is 11.8 (current ATI version is 11.11). If I try to install the 'post release' fglrx driver (11.11?) from jockey, it fails. If I install the release fglrx driver, Gnome 3 will not display correctly (tearing, missing letters, laggy, etc). If I use the open source driver, Gnome 3 reverts to the 'faulty graphics driver' 2D version. 

Unity seems to work with the open source radeon driver. Prob is I do not like Unity and want Gnome 3. With my laptop and even in a vbox install, Gnome 3 works fine. Just not with a full install on a desktop with an ATI radeon video card:

01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4250]

Frustrated trying to get all my computers all on the same GUI and same release...

I see this bug was resolved for the nvidia drivers, just not the ati drivers.

edit: Grabbed the latest 11.11 drivers. Compiled and installed. Still tearing on the popups and graphics garbage when refreshing. Awful. Went back to the open source driver and Unity. Please someone come up with a fix. I hate unity and want to see if I can live with Gnome 3. Gnome 3 in compatiblity mode is pretty ugly

---

### Post by Harry66 on 2011-11-26
I have the same problem on Radeon, but on the other hand Fedora 15 & 16 live CD's (with Gnome 3) are just fine on the same hardware.

( [http://ubuntuforums.org/showthread.php?p=11491282#post11491282](http://ubuntuforums.org/showthread.php?p=11491282#post11491282) )

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/870569](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/870569)

---

### Post by Harry66 on 2011-11-26
Ah... Looks like it *is* the ATI drivers...

I tried the Additional drivers, and was activating the ATI proprietary  FGLRX driver (post-release updates) when I changed my mind, and I had to re-boot to stop it.

It came back fine, and when I looked, neither of the ATI FGLRX drivers were activated.

---

### Post by ArcherB on 2012-01-05
> **atulkakrana said:**
> Dont take captain.Blubber advice as that link isi too old and filenames are obsolete.

Perfect Fix:
Download latest drivers from 
[http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html](http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html)

Right click and select run as program

Go to terminal

$./whatever_name_of_driver

Just press ok and yes during installation questions

After it finishes, issue command

$sudo aticonfig --initial

Enjoy

This worked for me.  Of course, I removed all the Radeon drivers, rebooted, then removed the FGLRX drivers, rebooted, installed the 11.12 version of the drivers I downloaded earlier from either SoftPedia or AMD.  I must note that after the second reboot, the screen was flickery, even at the console and difficult to follow.

also, I didn't run the aticonfig --initial.

After that third reboot, everything seems to be working fine.  I'm typing this message from Gnome3.  We'll see how long this lasts.

---

### Post by BlinkinCat on 2012-01-06
> **ArcherB said:**
> This worked for me.  Of course, I removed all the Radeon drivers, rebooted, then removed the FGLRX drivers, rebooted, installed the 11.12 version of the drivers I downloaded earlier from either SoftPedia or AMD.  I must note that after the second reboot, the screen was flickery, even at the console and difficult to follow.

also, I didn't run the aticonfig --initial.

After that third reboot, everything seems to be working fine.  I'm typing this message from Gnome3.  We'll see how long this lasts.

What is the situation with your graphics now?

Are you having any problem with a glitch in the top bar?

---

### Post by nowerries on 2012-01-25
Just updated to the 11.12 catalyst drivers, almost all the glitches are gone in gnome 3 except drop down menus are sometime distorted. But the one that really bugs me and makes gnome 3 unbearable is that gnome-terminal displays all buggy unless window is fully expanded. For now i have mint 12 installed on separate partition running with the open source drivers. It works just fine and movie players are still able to run 1080p movies with no problem on a radeon HD4200. Anyone who wants to use gnome 3 without drivers and still wants a separate ubuntu partition should download mint 12 just because gnome 3 comes as a more complete package ie. shell extensions and what not.

---

### Post by JoZ3 on 2012-01-25
New version catalyst private drivers (version: 12.1 - Release date 01/25/2012) 

Download - [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

Oneiric Installation guide - [http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide")

---

### Post by Nardon on 2012-01-26
I saw that the drivers (At least from 11.12) seem to work a lot better with Gnome Shell. You still have a few minor glitches occasionally but it's a lot better! Only when you have a dual videocard setup things might not work out too well.

---

### Post by ratcheer on 2012-01-26
I just installed Catalyst 12.1 on Oneiric and am running gnome-shell. Things are looking pretty good, so far.

Tim

---

### Post by nintendojet on 2012-01-27
It is now working with G3:
[http://ati.cchtml.com/show_bug.cgi?id=99](http://ati.cchtml.com/show_bug.cgi?id=99)

Performance issues exist, but it is definitely usable.

---

### Post by Shadow Death on 2012-02-04
> **Nardon said:**
> I saw that the drivers (At least from 11.12) seem to work a lot better with Gnome Shell. You still have a few minor glitches occasionally but it's a lot better! **[COLOR=Red]Only when you have a dual videocard setup things might not work out too well.[/COLOR]**

That's the catch.  I'm sporting a Radeon HD 4250m and a Radeon HD 5650m.  Linux will see my 5650 but the drivers won't.  Aside from that everything works great.

---

### Post by JayKay3OOO on 2012-02-07
I had same problem so first ran and update command from another thread which made it work, but it was really laggy.

So I first used this help to purge xorg (I meant to purge fxglr first :o.

> **Lumsdoni said:**
> Not working for me. 

I had 11.10 installed with Gnome 3, but did not install the ATI Radeon drivers.

I then read (stupidly)  that te 11.10 ATI driver fixed the gnome 3 problem.  So I duly installed it.

Tada! The Menu bar was fine, no crazy colours, but the some weird tearing occured inpop up boxes.

I managed to get the Control Centre up to change the Tearing option, but no change.

I then followed the instructions below to remove ATI Radeon and revert to the open source drivers (please correct if wrong) From [here]("http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide#Removing_Catalyst.2Ffglrx")

$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
$ sudo apt-get install xserver-xorg-video-ati
$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
$ sudo rm -rf /etc/ati

Unity was fine but now even if I select Gnome3, it loads up Gnome Classic.

I then uninstalled Gnome3, and reinstalled it but no change, I can still only get Gnome Classic, despite the Gnome3 option being selected.

I would greatly appreciate any help in getting my Gnome3 access back, I really like it (each to their own) and as a linux newbie, have finally got my laptop dual booting with Win7 and a shared data drive, and shared dropbox folders all working superbly well, and I really cannot face yet another re-install of Ubuntu.

Please advise if you need any command outputs for help.

Laptop is an MSI-U230 single core 1.6ghz, 2MB ram. 1st partition Win7 (32bit), 2nd partition (extended) Ubuntu 11.10 (32bit) and Swap, 3rd partition FAT32 Shared Data drive.

Chip is AMD MV-40, Graphics Card is ATI Radeon 5200 HD.

Thank you

Then I used this link:

> **Captain.Blubber said:**
> I had same problem with ATI fglrx driver, with Gnome 3 flashing and messing all the time.
I was following this solution from wiki.ubuntu.com and now its all working like it should.

[http://goo.gl/Ogmbj](http://goo.gl/Ogmbj)

to purge the fxglr before using these drivers:

> **atulkakrana said:**
> Dont take captain.Blubber advice as that link isi too old and filenames are obsolete.

Perfect Fix:
Download latest drivers from 
[http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html](http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html)

Right click and select run as program

Go to terminal

$./whatever_name_of_driver

Just press ok and yes during installation questions

After it finishes, issue command

$sudo aticonfig --initial

Enjoy

Used a force overwrite. It's also worth noting that I forced deletion of fxglr. You may not need to go through all these steps as the driver might just work, but I started out with bad text. I compromised with some funny coloured flashes, lag and text screw ups and finished 1h later with a system that seems to finally work under gnome 3.

A task I had put off for 3 months. What a pain in the a%%.

---

### Post by emptycoder on 2012-02-17
The latest ATI Catalyst dirver 12.1 is better the old ones, GNOME 3 is usable but I'm facing two problems.
The first problem (Which is not very important but little bit annoying) is that GNOME Shell is a little bit slow, and the second one (Which is very serious problem) that GNOME sometimes falshes and disappears for a few seconds then returns back, but sometimes it disappears and somehow it falls back to Classic mode, the panel disappears and there's no available function except ctrl+alt+del to logout and then login again.
Does anyone have any clues?

---

### Post by arkeo on 2012-02-17
> **emptycoder said:**
> Does anyone have any clues?

Yeah, two:

1) next time I'm gettin' an Nvidia card, that's for sure, as much as I love AMD

2) I tried Fedora 16, Debian Wheezy, Precise Pangolin, and the result is always the same: the user experience on gnome-shell (or Unity) is horrible, horrendous, it gets me so frustrated I'd like to bang my head on my LCD screen... well, almost...

GNOME3 (GTK3?) has serious stability issues: software update crashes regularly on F16, I seem to remember something very similar on PP12.04 (it's either apt-get or yum updates, the GUI would always crash), aside from the fact that you still have to hunt down every bloody Unity customization and get rid of it any way you can just to have menus that don't disappear or force you to move your mouse pointer from the corner (where the menu gets activated) to the middle (where the actual menu is located).

AMD/ATI drivers are possibly in an even worse condition: I have a great C-50 netbook, still waiting for a decent kernel or a truly accelerated driver for video playback. Gee, thanks AMD!
On a quad core desktop with a 5570 I frankly don't see much of a difference: when I manage to get smooth 1080p video playback (not that often, catch my drift?) I always suppose I have the CPU to thank...

Sorry for the angry post, but this is truly the way I feel, and I've been stuck in this situation ever since I bought those two systems almost 6 months ago...

And I'd hate to be stuck with Windoze... :(

ADMINS: could someone please oh please REMOVE the "SOLVED" tag from this thread? It really feels like a bad joke...

---

### Post by njrob on 2012-02-17
Hi,
I'm using Ubuntu 11.10 on a Dell Latitude D810 with an ATI MOBILITY RADEON X600 graphics card.

Must an ATI graphics card have an AMD driver, or can I use a NVIDIA driver for my current hardware?

Other contextual information that might be helpful:

I have some kind of opensource AMD driver installed through the Software Center that keeps my everyday display running smoothly.

I need to upgrade my driver to obtain full OpenGL support for a game I'm trying to run using Wine.

The game is DDO, and uses the program pylotro as a surrogate launcher to run the game.  One or both of these programs requires the OpenGL support.

Any and all assistance would be appreciated; Thank you.

---

### Post by emptycoder on 2012-02-22
You're right [arkeo]("http://ubuntuforums.org/member.php?u=287766"), I have marked the thread as unsolved, my bad sorry.
And yes, you're tottaly right! buying a laptop with ATI driver was one of my biggest mistake that I have ever done, next time when I'm gonna buy new laptop I will stick wtih Nividia, those ATI developers are so lazy, I thought that they will fix all GNOME 3 Shell's problems on the next Driver release, I sent a mail to them and they told me they're still working on it, duh!
Right now I'm trying so hard to find any possible fix 'cos I'm stuck with this horrible driver and have no choice.
The Open Source Driver doing very well, GNOME is so smooth but there's an overheating problem that I couldn't fix it!

---

