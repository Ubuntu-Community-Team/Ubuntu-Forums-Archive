---
title: "Transmission Torrent client?"
date: 2010-01-15
forum: General Help
---

### Post by jfbooth on 2010-01-15
One of the updates (Karmic) this morning listed the following:

Update
transmission-common
lightweight BitTorrent client (common files)

Description

Transmission is a simple BitTorrent client. It features a very simple, intuitive interface (gui and command-line) on top on an efficient, cross-platform back-end.
This package contains the common files for the different transmission versions.

Changes

Changes for the versions:
1.75-0ubuntu2
1.75-0ubuntu2.2

Version 1.75-0ubuntu2.2: 

  * SECURITY UPDATE: fix arbitrary file overwrite via crafted torrent file
    - debian/patches/CVE-2010-0012.patch: adjust metainfo.c to check for '../'
    - CVE-2010-0012

So, I employed the update.  Problem is, I do not see this as an installed application.  TRANSMISSION is not listed in any submenu under the Applications menu OR Add/Remove.

Any and all comments are appreciated.

---

### Post by jward3010 on 2010-01-15
Odd, It should appear under "Applications > Internet" menu. 

OR open a terminal and type "transm", press TAB to complete it and see if anything appears. I think "transmission-gtk" should appear or maybe more than one option. If you like, hit enter to run it. If it does it's installed.

It's a default application as part of the Ubuntu set. In fact it might even be a meta-package where you can't get rid of it without destroying the whole desktop.

---

### Post by NFblaze on 2010-01-15
Well, I suppose it would entail what you have installed. I got that same message today, but being that I have installed transmission-gtk, transmission-cli, transmission-daemon, etc....

It seems like you only have transmission-common. 

It may be as simple as sudo apt-get install transmission

---

### Post by jfbooth on 2010-01-15
> **jward3010 said:**
> Odd, It should appear under "Applications > Internet" menu. 

OR open a terminal and type "transm", press TAB to complete it and see if anything appears. I think "transmission-gtk" should appear or maybe more than one option. If you like, hit enter to run it. If it does it's installed.

It's a default application as part of the Ubuntu set. In fact it might even be a meta-package where you can't get rid of it without destroying the whole desktop.

No 'Internet' under APPLICATIONS.  Using default install of Karmic.  transm TAB in terminal did nothing.  Here is results of terminal session:

jb@jb-desktop:~$ transmission
The program 'transmission' is currently not installed.  You can install it by typing:
sudo apt-get install transmission-gtk
transmission: command not found
jb@jb-desktop:~$ transmission-gtk
transmission-gtk: command not found
jb@jb-desktop:~$ 

So I conclude it is not installed.  That would leave the question If "It's a default application as part of the Ubuntu set. In fact it might even be a meta-package where you can't get rid of it without destroying the whole desktop.", then where is it?  I have never consciously installed it.

Seems like a 'minor' concern.  I am guessing Karmic uses/installs PART of it for some unknown reason, which would explain the update .. and it is not 'user installed'(?).  I would not want anyone investing 'too' much time on this.  More a curiosity to me than anything else, ..being a noob.


Wonder why no 'Internet' under Applications now.  Maybe that is the result of a different distro?

thank you both for the replies.

---

### Post by jward3010 on 2010-01-15
Oh, am I right in saying you use Xubuntu, I just noticed that at the side. I thought this was just normal Ubuntu.

---

### Post by jfbooth on 2010-01-15
> **jward3010 said:**
> Oh, am I right in saying you use Xubuntu, I just noticed that at the side. I thought this was just normal Ubuntu.

Yes Sir, .. Xubuntu (AKA Karmic Koala .. I think).

---

### Post by jward3010 on 2010-01-15
> **jfbooth said:**
> Yes Sir, .. Xubuntu (AKA Karmic Koala .. I think).
Well, to be specific, Xubuntu is the operating system (well it's really Linux, but lets not make this more confusing) and Karmic Koala is it's current release name, so you're using:

Xubuntu 9.10 Karmic Koala

The previous one was Xubuntu 9.04 Jaunty Jackalope, before that 8.10 Hardy Heron blah, blah, McBlah. When the new one comes out it will be called Lucid Lynx (thats version 10.04).

---

### Post by jfbooth on 2010-01-15
Xubuntu 9.10 Karmic Koala ... right .. got it.  Thank you for all the clarification.

"Lucid Lynx (thats version 10.04)"  I will keep that in mind.  Thanks again.

---

### Post by warfacegod on 2010-01-15
I just got the same update with Ubuntu 9.10 NBR, after removing Transmission. I wouldn't worry about it.

---

### Post by jfbooth on 2010-01-15
> **warfacegod said:**
> I just got the same update with Ubuntu 9.10 NBR, after removing Transmission. I wouldn't worry about it.

Not worried .. just trying to 'manage' my system .. with a bad case of noob.  Just wonderin why the OS would update something I could not find on a menu .. and have determined is not installed.  Figured I needed to learn something.  Thanks for all the replies.

---

### Post by jfbooth on 2010-01-15
A "Catfish" search on TRANSMISSION shows 69 files found .. many with 'transmission' as part of the file/folder name and many with "transmission' nowhere in the file/folder name.  Could not guess on all the disk space taken.  I'm on a 10GB HD which is why I picked the 'leaner' XUBUNTU.  I'm sorta 'conscious' of disk space.

---

### Post by warfacegod on 2010-01-15
External drives are very cheap now. I bought an Iomega 1 TB drive at Radioshack for $106.00 US

---

### Post by jfbooth on 2010-01-15
Yep, and I have two USB drives that will work just fine .. I just can't figure out how to install programs to any of them.  They are great for DATA .. music, vids, pics .. but seems I have to install anything/everything to this 10G C: .. or dev0 or whatever Linux calls it.

---

### Post by warfacegod on 2010-01-15
> **jfbooth said:**
> Yep, and I have two USB drives that will work just fine .. I just can't figure out how to install programs to any of them.  They are great for DATA .. music, vids, pics .. but seems I have to install anything/everything to this 10G C: .. or dev0 or whatever Linux calls it.

10 GB should be fine if your cautious. I has 27 GB with 9.10 and files in one partition and I managed to get 9.10 Netbook Remix with installs, updates and such into the remaining 5 GB partition.

---

### Post by jfbooth on 2010-01-15
HAS to be a way to install programs on other drives .. other than the one the OS is on.  Has to be.  I'm figuring that would be another thread though.

---

### Post by warfacegod on 2010-01-15
I suppose it's possible although I imagine that your system would simply break if you turned it on without the external drives plugged in and on. My laptop can take as much as half an hour to boot up if my external is on. It ties to read something like 260 GB of data making sure there is nothing to boot from on it. If you really, really like your OS the way it is then you can tarball the entire thing, buy a bigger internal, do a fresh install on it, and unpack the tarball. Voila!, more drive space. Read this if that sounds like you might want to try it.

[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by jfbooth on 2010-01-15
I appreciate your tips.  I made the mistake of installing Ubuntu 9.04/64 on one of the USB drives with XP on C: (different machine .. laptop).  System would not boot to Windows without the ext. drive attached.  I guess Grub had to 'see' both OSses.  Not bad, but that ext. drive needed power from a wall plug .. so that did not work out (being a laptop).

I can install either 'USB' drive as the primary (internal) drive on this Xubuntu machine (desktop/tower).  One is a SATA with an IDE interface and the other is IDE, but ideally, I can leave Xubuntu on this 10G C: and install PROGRAMS on the ext. USB drive (either one).  With a 10GB C:, that just makes the most sense to me.  Fine if the ext. has to be 'present' to boot though not sure I would care for a 1/2-hour boot time.
Thanks for the tarball idea.  I will keep it in mind.

---

### Post by warfacegod on 2010-01-16
Programs wouldn't get to be 260 GB though. Personally, I think you might be worrying over very little, I've never had a Linux install grow much past 8 GB. I understand that 8 GB doesn't leave much room for files but you could keep your stuff on externals.

Here's a thread for getting rid of stuff:

[http://ubuntuforums.org/showthread.php?t=820804&highlight=cover+manager]("http://ubuntuforums.org/showthread.php?t=820804&highlight=cover+manager")

Here's a few question's:

How much RAM do you have?
Do you Suspend or Hibernate?
Do you burn CD's or DVD's?

---

### Post by jfbooth on 2010-01-16
> **warfacegod said:**
> I understand that 8 GB doesn't leave much room for files but you could keep your stuff on externals.

Here's a thread for getting rid of stuff:

[http://ubuntuforums.org/showthread.php?t=820804&highlight=cover+manager]("http://ubuntuforums.org/showthread.php?t=820804&highlight=cover+manager")

Here's a few question's:

How much RAM do you have?
Do you Suspend or Hibernate?
Do you burn CD's or DVD's?

Oh, sure, external drive(s) .. no problem for 'stuff'.  It's that 8GB drive with the OS that keeps me awake.  Thank you for the 'getting rid of stuff' link.  That is GREAT.

Xubuntu is on an old Windows ME machine:
512MB Ram (maxed out)  700MHZ CPU
Uh, . do I suspend or hibernate .. I actually do not know.  When I leave the machine for a while and come back, screen is blank (off) .. wiggle mouse and it fades to 'alive' .. but I think that is a screen saver .. not hibernate or Suspend.  Shutdown button DOES have OPTIONS to suspend/hibernate but I never use either.
Machine only has CD ROM on it .. but I could replace it with a 'burner' .. or add a USB burner.  Actually, even with Xubuntu the machine is slow ... I figure that is due to 512MB Ram and/or CPU.

Next thing I am going to do though is look at that link and get rid of what I can.  Thanks!!!!!

---

### Post by warfacegod on 2010-01-16
If you don't Suspend or Hibernate and it sounds like you don't then you can reduce the size of your swap to give you more room. If your not burning then reducing the System Reserve on your hard drive will get you another .5 GB or so. If you are interested let me know and I'll walk you through it.

---

### Post by jfbooth on 2010-01-16
> **warfacegod said:**
> If you don't Suspend or Hibernate and it sounds like you don't then you can reduce the size of your swap to give you more room. If your not burning then reducing the System Reserve on your hard drive will get you another .5 GB or so. If you are interested let me know and I'll walk you through it.

I do not plan to use suspend or hibernate.  Don't see any need for either on a desktop computer.  Gaining that disk space would be quite right, I think.  Yes, .. please instruct.

As I mentioned .. no burner on this machine ... but doesn't mean I would never burn.  There are external burners out there and burning MAY be something desirable 'one day'.  Since it is a 'possibility', let us reserve that capability.  Thank you immensely.

---

### Post by d3v1150m471c on 2010-01-16
It should already be installed as a default on ubuntu. Is it not on your system?

---

### Post by warfacegod on 2010-01-16
> **jfbooth said:**
> I do not plan to use suspend or hibernate.  Don't see any need for either on a desktop computer.  Gaining that disk space would be quite right, I think.  Yes, .. please instruct.

As I mentioned .. no burner on this machine ... but doesn't mean I would never burn.  There are external burners out there and burning MAY be something desirable 'one day'.  Since it is a 'possibility', let us reserve that capability.  Thank you immensely.

Fair Warning: This has the potential to be dangerous. Make a copy of all your files on another drive if possible.

Ok. First I will need to see a screen shot of Gparted. If it's not installed get it from Synaptic. It will look like this:

---

### Post by jfbooth on 2010-01-16
Tried to INSERT rather than attach .. but did not know how to enter the path.  screenshot.jpg on desktop.    

Anyway, here it is as an attachment (I hope).  

FWIW .. total size of physical HD is 10GB.  Looks to me like I am using all of it ... total of partition sizes = 9.77994GB.

---

### Post by jfbooth on 2010-01-16
> **d3v1150m471c said:**
> It should already be installed as a default on ubuntu. Is it not on your system?

Apparently it is NOT nor WAS installed.  that is why I was surprised at the update.  This is a 'default' install of Xubuntu, Karmic Koala 9.10.  No evidence of 'Transmission' being installed .. yet got an update for it.  I guess has to do with dependencies or something.

---

### Post by warfacegod on 2010-01-16
> **jfbooth said:**
> Tried to INSERT rather than attach .. but did not know how to enter the path.  screenshot.jpg on desktop.    

Anyway, here it is as an attachment (I hope).  

FWIW .. total size of physical HD is 10GB.  Looks to me like I am using all of it ... total of partition sizes = 9.77994GB.

I'll be with you soon. I'm a bit preoccupied at the moment, sorry. Be right back.

---

### Post by warfacegod on 2010-01-16
Step one turn off your swap file. Right click and click again where it says swap off.

---

### Post by jfbooth on 2010-01-16
OK .. done.

---

### Post by warfacegod on 2010-01-16
Step #2 resize the partition. I would say around 50 - 100 MB, your choice. Grab the  arrow where my pointer is well.. pointing and slide it >>>>>>> Now watch where it says "New Size MiB" and stop sliding when says the # of MB you want 50, 75, 86, whatever. Then uncheck round to cylinders and click Resize/Move. Being certain everything is the way you want it.

---

### Post by jfbooth on 2010-01-16
OK, .. using your screen shot instead of mine is a little confusing .. but with Linux Swap selected, R click, L click Resize/Move.  Starting on the LEFT, slid slider to the RIGHT until NEW SIZE says 60 (was 455) and Free Space Preceeding says 395 (was 0).  FREE SPACE FOLLOWING DID NOT CHANGE . SAYS 0.  Unchecked ROUND TO CYLINDERS.

Please confirm this is OK, continue instructions, and I will click Resize/Move button.

---

### Post by warfacegod on 2010-01-16
> **jfbooth said:**
> OK, .. using your screen shot instead of mine is a little confusing .. but with Linux Swap selected, R click, L click Resize/Move.  Starting on the LEFT, slid slider to the RIGHT until NEW SIZE says 60 (was 455) and Free Space Preceeding says 395 (was 0).  FREE SPACE FOLLOWING DID NOT CHANGE . SAYS 0.  Unchecked ROUND TO CYLINDERS.

Please confirm this is OK, continue instructions, and I will click Resize/Move button.

Yes. That looks correct. Confirmed.

---

### Post by jfbooth on 2010-01-16
OK, then.  Just clicked Resize/Move.  Comment at bottom of gparted window says "1 operation pending".

---

### Post by warfacegod on 2010-01-16
Sorry, there should be a green check mark at the top left. That is the apply button, hit it.

---

### Post by jfbooth on 2010-01-16
I hit it.  "All operations successfully completed (4 warnings)" with a close button at the bottom of the window.

---

### Post by warfacegod on 2010-01-16
Show me a screen shot.

---

### Post by jfbooth on 2010-01-16
ok

---

### Post by jfbooth on 2010-01-16
I (slightly) jumped the gun and hit the 'close' button.  that is a screen shot of gparted now.

---

### Post by warfacegod on 2010-01-16
Right click the Unknown Partition (the one with the red icon) Select Format to> choose Linuz-swap. Click apply.

---

### Post by jfbooth on 2010-01-16
ok

---

### Post by warfacegod on 2010-01-16
> **jfbooth said:**
> ok

You formatted as Linux-swap?

---

### Post by jfbooth on 2010-01-16
dunnno, .. something doesn't look right.  I selected FORMAT TO LINUX-SWAP ... I am almost SURE.

---

### Post by jfbooth on 2010-01-16
> **warfacegod said:**
> You formatted as Linux-swap?

I sure THOUGHT so!!!

---

### Post by jfbooth on 2010-01-16
try again???

---

### Post by warfacegod on 2010-01-16
Yup.

---

### Post by jfbooth on 2010-01-16
OK ... selected Format to // linux-swap and then APPLY.  Did a 'routine' and the satus BRIEFLY said it was a linux-swap file, .. then GPARTED 'updated' and the status changed back to UNKNOWN.  I knew I selected linux-swap the first time.

---

### Post by jfbooth on 2010-01-16
here is where gparted is right now.

---

### Post by warfacegod on 2010-01-16
Reboot.

---

### Post by jfbooth on 2010-01-16
ok, .. closed gparted and rebooted.  restarted gparted .. looks the same to me.  current gparted attached.

---

### Post by warfacegod on 2010-01-16
You're going to need to do this from your LiveCD. Reboot into your 'buntu install disc and select install without changes.

---

### Post by jfbooth on 2010-01-16
Ok

---

### Post by jfbooth on 2010-01-16
"select install without changes"

Don't see that on the XUBUNTU live CD boot screen.  I see RUN linux without changes, but not INSTALL without changes.  Looked at 'modes' and other options, but never found INSTALL w/o changes.  Any tips?

---

### Post by warfacegod on 2010-01-16
> **jfbooth said:**
> "select install without changes"

Don't see that on the XUBUNTU live CD boot screen.  I see RUN linux without changes, but not INSTALL without changes.  Looked at 'modes' and other options, but never found INSTALL w/o changes.  Any tips?

Run without changes. I "misspoke", my fault, I'm cooking dinner so my attention is split. I'll be more careful.

---

### Post by jfbooth on 2010-01-16
Oh .. OK, .. so I am running now off CD now.  Sorry to be intruding.  

1.  Tell me when I can 'bother' you with this ... when to check back or something so I am not intruding.  This is not a high priority with me ... (don't want it to get worse, but no hurry on recovering from all this either).

2.  What now?

---

### Post by jfbooth on 2010-01-16
I just tried to format that partition linux-swap after running off live CD and after a 'routine', now gparted looks more 'right.

screen shot attached

---

### Post by warfacegod on 2010-01-16
> **jfbooth said:**
> Oh .. OK, .. so I am running now off CD now.  Sorry to be intruding.  

1.  Tell me when I can 'bother' you with this ... when to check back or something so I am not intruding.  This is not a high priority with me ... (don't want it to get worse, but no hurry on recovering from all this either).

2.  What now?

No bother at all. Truly.

Open Gparted and format that same partition again assuming it is still "unknown".

---

### Post by jfbooth on 2010-01-16
Figured that would come next .. and I did that.  see last attachment.

---

### Post by warfacegod on 2010-01-16
Has your computer been behaving oddly in any way? (Aside from not recognizing its own format.)

---

### Post by jfbooth on 2010-01-16
NO,  it is a nice install with only a printer/scanner installed.  Ran great .. no problems at all.  Do we still have a mystery?  After booting live CD and gparted, looks like we accomplished what we wanted to ... no?  Just need to finish up ... no?  Did you look at that last attachment?  Looks like we are ready for the next step (to me).

---

### Post by warfacegod on 2010-01-16
I looked at the wrong attachment. I thought the partition was still unknown. Yes, we have accomplished what we needed to so far.

Step #whatever number I lost track.

Resize the unallocated space. Just like resizing the swap file, grab the left arrow and drag it as far over to the right as possible>>>>>>>>>>>. Uncheck Round to cylinders, click Resize/Move, apply.

---

### Post by jfbooth on 2010-01-16
looks like a problem.  I clicked on UNALLOCATED (highlighted it).  The box at the top where you 'drag'for size did NOT change.  The box is not sizeable.  Right click on UNALLOCATED and everything is grayed out except NEW and INFORMATION.  Of the greyed out choices .. one of them is RESIZE/MOVE.

---

### Post by warfacegod on 2010-01-16
Fair warning, my internet connection is starting to get a bit dodgy so don't panic if I don't respond.

---

### Post by jfbooth on 2010-01-16
maybe it is ext4 we want to resize??????????  (noob question).

---

### Post by jfbooth on 2010-01-16
nope .. could not resize it anyway, .. it is greyed out also and it says it is unmounted.  Maybe need to boot back off of HD??  (another noob question).

---

### Post by jfbooth on 2010-01-16
> **warfacegod said:**
> Fair warning, my internet connection is starting to get a bit dodgy so don't panic if I don't respond.

Story of my life ... HAH!!  I guess this machine can just sit .. booted off live CD w/ gparted sitting right where it is.

---

### Post by warfacegod on 2010-01-16
> **jfbooth said:**
> maybe it is ext4 we want to resize??????????  (noob question).

No, extended. What was I saying about paying more attention? And now I'm not cooking! Ok. You resize the EXTENDED partition (not unallocated because that's impossible) and I'll go make coffee.

---

### Post by jfbooth on 2010-01-16
> **warfacegod said:**
> I looked at the wrong attachment. I thought the partition was still unknown. Yes, we have accomplished what we needed to so far.

Step #whatever number I lost track.

Resize the unallocated space. Just like resizing the swap file, grab the left arrow and drag it as far over to the right as possible>>>>>>>>>>>. Uncheck Round to cylinders, click Resize/Move, apply.

OK ... did the above but with extended ... not unallocated.  I think we are making progress.

current gparted is attached.

---

### Post by warfacegod on 2010-01-16
Yes, we are. Good progress. And I've got coffee too, excellent progress.

Step #pi

Resize ext4 partition. This time grab the black arrow on the *right* and drag it right>>>>>>>>>> all the way. Still unchecking Round To Cylinders. Click, click, ...you get the idea by now.

I've reread these instructions several times. I promise they are correct.

---

### Post by jfbooth on 2010-01-16
OK .. done .. as instructed.  Got a window that popped up.  Says "Failed to mount '9G Volume'  The enclosing drive for the volume is locked".  I clicked close on that window.  Gparted said "successfully completed".  Screenshot attached.

---

### Post by jfbooth on 2010-01-16
have a feeling we are done .. just a feeling.

---

### Post by warfacegod on 2010-01-16
Very close. Right click the linux-swap partition and select Swap On.

I think that 9G thing was Linux protecting your GRUB.

---

### Post by jfbooth on 2010-01-16
> **warfacegod said:**
> Very close. Right click the linux-swap partition and select Swap On.

I think that 9G thing was Linux protecting your GRUB.

Oh yea .. swap on.  Wonder how many forget that.  Completed your instructions.  Got that window again re: locked volume.  Just clicked close on it.  Gparted says "successful'.

You don't have to answer this, but isn't grub ONLY for dual booting?  This machine does not dual boot .. nothing but Xubuntu on it.  Whatever .. just thought I would mention it.  Grub or whatever, I hope/assume the volume will mount when I boot from the HD.  Should I assume that is next and we are done?

---

### Post by warfacegod on 2010-01-16
> **jfbooth said:**
> Oh yea .. swap on.  Wonder how many forget that.  Completed your instructions.  Got that window again re: locked volume.  Just clicked close on it.  Gparted says "successful'.

You don't have to answer this, but isn't grub ONLY for dual booting?  This machine does not dual boot .. nothing but Xubuntu on it.  Whatever .. just thought I would mention it.  Grub or whatever, I hope/assume the volume will mount when I boot from the HD.  Should I assume that is next and we are done?

Yes, reboot is next. GRUB or GRUB2 is on all 'buntu installs. Its what is called a boot loader. With only one OS on your system you may never notice GRUB being there but it is. When you reboot go into Gparted again and look to make everything appears kosher.

---

### Post by jfbooth on 2010-01-16
I would say we have completed the task quite satisfactorily.  They are people like you who make Linux possible, and I cannot thank you enough.  Instead, I will thank you all I can, and wish you and yours a prosperous new year.

---

### Post by warfacegod on 2010-01-16
> **jfbooth said:**
> I would say we have completed the task quite satisfactorily.  They are people like you who make Linux possible, and I cannot thank you enough.  Instead, I will thank you all I can, and wish you and yours a prosperous new year.

Thank you and you are welcome. To you and yours as well. If you need any assistance with anything else I'm usually lurking about. Enjoy.

---

