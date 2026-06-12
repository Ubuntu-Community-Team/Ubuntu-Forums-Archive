---
title: "Cannot go beyond login page"
date: 2010-03-13
forum: General Help
---

### Post by milenixloerdi on 2010-03-13
Hello,

Something happened with my Ubuntu installation - when it reaches to the "login" "password" screen it gives the message in the upper corner that the** power management has not been installed properly**. So, when I try to login, it throws me back to the login screen. This happens with every prevous installation available from GRUB menu:

"! Install Problem.
The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact administrator."

The Recovery mode seems to work perfectly well, however it puts me in a dos prompt screen, from which I do not know how to operate.

I believe one possible reason for this to happen is that my Hard Disk where Ubuntu is installed, altogether with the SWAP disc which ubuntu uses, are completely full. I tried to free some space through my installation of Vista, but the program Ext2fsd does not enable me to see the content on my ext3 drives, only shows first level directory structure (the foldrs appear "empty" under Vista.

Could someone help me with a "magical" command line that I can type in recovery mode please...so that I free some space from my /user/videos directory (I dont mind it wiped out completely) and also all "wine" installations, that I can also wipe out. If the reason of Ubuntu not continuing beyond login screen is space, I do not mind anything that can free some space somehow and enable it to start...

Thanks a lot for the time and the probably very stupid question....

---

### Post by coffeecat on 2010-03-13
If you are uncomfortable at the command prompt, I would avoid deleting personal files just yet. One typo and you can do a lot of damage. Instead, let's clear out the package manager cache first. For every new app or update that you've installed, there's still the .deb installer sitting in the cache folder unused. You may have upwards of 500MB there - possibly more.

Boot into the recovery console and simply:

```
apt-get clean
```You don't need 'sudo' in the recovery console.

Now...

```
reboot
```... and see if you can get into the GUI from which you can delete stuff in your home folder and remove wine more safely.

If that doesn't clean out enough space I'll give you a command for removing your videos.

---

### Post by milenixloerdi on 2010-03-13
Thanks, but now it seems something else is wrong. When I reach the "Recovery Menu", now the following gets repeatedly written on top of it:


> Buffer I/O error on device sr0, logical block
End-request: I/O error, dev Sr0, logical block 179390and after logging and typing ```
apt-get clean
```, the following appears:

> E: Could not open lock file/var/cache/apt/archives/lock - open (13: Permission denied)I do not know exactly what might have happened - I tried to access the drives from vista...and a "$recycle bin" has now appeared on the ubuntu drive.

---

### Post by coffeecat on 2010-03-13
Oh dear.

Let's take those one at a time.

sr0 is your optical drive. That may simply be a spurious error because of the full filesystem, or something's wrong with the CD drive. Let's worry about that later.

The lock file problem is perhaps because a package manager was still open when you last shut down.

The $recycle.bin is a folder that Vista has put in your ext3/4 partition because it's used to seeing one in an NTFS partition. Despite that ext driver you added, it can't tell the difference. It won't do any harm - it can be removed later.  By the way, I'd avoid using that ext* driver if I were you.

OK - plan B

Let's remove that cache the brutal way - it won't do any damage.

Boot up into recovery console and...

```
rm /var/cache/apt/archives/*deb
```That will delete all the .deb package files which is what apt-get clean was meant to do. No you don't need "*.deb" instead of "*deb" - this is not Windows. And be very careful what you type in. Triple-check before you hit that enter key.

Then reboot and see if that has cleared enough room. If it hasn't, you can delete your personal video files with a live CD - that's easier. You'll be using the GUI. I'll tell you how if you need.

---

### Post by milenixloerdi on 2010-03-13
Thanks I double checked the spelling.

It said that No such directory or file exists...

Ill try again right away......

---

### Post by milenixloerdi on 2010-03-13
It definitely shows no such directory or file exists.

tried restarting in normal mode, same thing like the first post describes it - no "worse" there...

wondered if I can try erasing the harsh way the videos folder....or the .amule folder... If you could please help me with the syntaxis so I can try that too thank you so much!

Or I will try to do it with live cd...never done that before, thanks

---

### Post by coffeecat on 2010-03-13
> **milenixloerdi said:**
> It said that No such directory or file exists...

That could be because the apt-get clean worked despite the error message, or that the apt cache was empty anyway. But for the cache to be empty you would have had to run apt-get clean at some time.

Anyway....

Instructions for deleting personal files using live CD:

Boot up with live CD. Go to Places menu and find and mount the Ubuntu root partition on the hard drive. The Nautilus folder that opens will not help because the temporary live user "ubuntu" has a different UID from your own account and will not be able to delete your files. You need a root nautilus. So, close that windows and open a terminal and...

```
gksudo nautilus
```That will open in root's own folder. Click on the up button to go to the parent folder - in this case the 'root' of the live filesystem. Now double-click on /media. One of the folders in /media will be the folder in which your hard drive installation is mounted. Double-click on that and you will be able to see your installed filesystem. Now /home > yourusername and you will be in your home folder with root permissions. Delete what you will.

---

### Post by milenixloerdi on 2010-03-13
thanks Ill try that - was just about to say I was happy to see both useless and useful files are there when i loaded live cd, but I cannot do anything about deleting etc... Trying the way you described now, thank you!

---

### Post by coffeecat on 2010-03-13
Sorry - I realise that I got side-tracked with the apt-get clean problem and that if you are deleting system files from the console, you might as well delete your personal files. You may have been successful with the live CD by now, but I'll post this anyway for the record.

Here goes:

Recovery mode > root console.

Then cd to your home with..

```
cd /home/yourusername
```Now list all the folders to check their names - don't forget that Linux is case-sensitive.

```
ls
```Assuming your video folder is "videos" and not "Videos"..

```
cd videos
```Now again...

```
ls
```And now you delete with the 'rm' command. THERE IS NO GOING BACK ONCE YOU'VE DELETED. You can use the * wildcard, but unlike in Windows you don't have to type a point separately. In Windows deleting everything would be 'del *.*'. In Linux it's 'rm *'. So take care.

One hint. Say you want to do a selective delete, every file that starts with 'Charlie' for example. Do:

```
ls Charlie*
```... first to see what would be deleted. Then, if you are happy with that...

```
rm Charlie*
```Or - to remove all .mov Quicktime files, but to leave all the rest:

```
ls *mov
rm *mov
```

---

### Post by milenixloerdi on 2010-03-13
Thank you for that, but I was succesful with the CD. Typed ```
gksudo nautilus
``` and deleted many files.

Restarted and loaded normal Ubuntu - same "power manager issue" on login screen.

As a matter of fact, when I typed gksudo nautilus, it warned me about some things, amongst was the power manager again (quite a few times).

> ** (nautilus:3865): WARNING **: Could not inhibit power management: The name org.gnome.SessionManager was not provided by any .service files

Now, under vista, with the ext programme (wihtout mounting ext3 partitions, just looking at them), again shows that they are full - the swap one , too. I deleted a lot - gigabytes from my personal files, so I dont know why it doesnt "register" the change under vista...maybe driver problem.

But still, I have the first message when I try to log in in ubuntu on a normal (not recovery) mode...

---

### Post by coffeecat on 2010-03-13
OK - my guess is that some packages that were to do with power management were being updated when you were last able to log into the GUI and that before they were properly installed, you ran out of partition space. This would explain the apt cache lock problem we encountered. And, for whatever reason, this incomplete update is preventing the login process.

For the next you need to be able to connect your machine to your router with an ethernet cable. And I'm assuming you have broadband.

Boot up in recovery mode. When you get to the menu with various choices, go for the "drop to root shell with networking". We need an internet connection. If you get an error about a PID file, ignore it.

Once you're at the prompt, run two commands:

```
apt-get update
apt-get upgrade
```That will update the package data and do a full system update - all packages that need updating will be. I'm hoping that that will reinstall the broken packages because, at the moment, I can't work out how to determine which they would be. If you get a lock error, try this first:

```
rm /var/lib/dpkg/lock
```I can't guarantee this will fix the system. It could be very broken, but it's worth a try. When you run apt-get upgrade it will prompt you for the size of the download. If this is more than your bandwidth can tolerate, you can say no at this point.

---

### Post by milenixloerdi on 2010-03-13
> When you get to the menu with various choices, go for the "drop to root shell with networking".My only problem will be if once again the typings of the errors on sr0 cover completely the option "drop to root shell"(an all the rest of the recovery menu actually). So far, by pressing "enter" i was able to get to a prompt, but this is far beyond the "menu".

If I have to drop to the root shell with networking via prompt only, what command do i have to use please?
Thank you - I really hope this will fix it!

---

### Post by milenixloerdi on 2010-03-13
Did exactly as you said. didnt have problems dropping to root with network. Didnt have lock problems. Had the PID error and ignored.

Connected and updated succesfuly. Started upgrading with good speed and ran out of space again. Restarted and the Power manager issue was still there.

I do not understand how can i delete gigabytes from the harddrive and still run out of space in such a short time... When with LIVE cd, does everything I delete go in the recycle bin? I empty whatever is there before each reboot... From within the live CD it reports it has 15 gig filled from 144 gig. From vista it says its full, and tru the "root shell with network" recovery option it also says its full in a few mb downloaded.

Im focusing on saving important files and reinstalling ubuntu, of which the biggest dread is not erasing "vista" in the process (because re-installign vista is a terrible, terrible thing...(and i need it only for few applications....)

Thanks a lot though! Ive learned a lot and I hope it all is sorted soon with working new ubuntu and vista...

---

### Post by coffeecat on 2010-03-13
> **milenixloerdi said:**
> Im focusing on saving important files and reinstalling ubuntu,

I think you may be wise re-installing. I have a feeling that the filesystem is corrupted. My next suggestion was going to be to run a 'fsck' (that's a filesystem check which can also correct most errors) from the live CD. But we might end up chasing moonbeams for ever.

So... Some thoughts.

There are several reasons why the filesystem could have become corrupted, but I would really urge you not to use that ext2/3 driver in Vista. Drivers for reading Linux filesystems in Windows can be problematic. You mentioned earlier in the thread that you hadn't mounted the Ubuntu partition in Vista, but that you could see the file structure. Sorry - but that is mounted in my book. And then you have Vista creating a folder in the root of the filesystem - not a good idea.

Which leads me to my next thought. Before you do your partitioning, think about having a separate NTFS partition for personal data. It can be accessible from both OSs - Vista would see it as E: or F: or whatever and Ubuntu NTFS read-write is reliable. That way you don't have to mount your Vista partition from Ubuntu nor do you have to mount your Ubuntu partition from Vista. If you want the NTFS data partition mounted in Ubuntu at bootup, simply install the GUI configuration tool ntfs-config from the repositories.

By having a separate data partition, if you try to overfill it, you won't be able to and your Ubuntu partition won't get damaged.

You have a 144GB Ubuntu partition. That's huge if you don't take into account things like video files. I keep all my personal data on separate (NTFS) partitions on all my machines, and I've never got above about 6-7GB in the root partition. So between 10-20GB should be ample for your Ubuntu partition so long as you don't keep much in the way of personal files on it.

Some things to think about.

---

### Post by milenixloerdi on 2010-03-16
Its all reinstalled now. Thank you!

Ive learned a lot of things...

Take care!

---

### Post by coffeecat on 2010-03-16
Good luck! Happy Ubuntu-ing.

---

