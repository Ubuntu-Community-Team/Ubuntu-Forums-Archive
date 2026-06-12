---
title: "&quot;out of range&quot;"
date: 2009-11-16
forum: General Help
---

### Post by Dusto on 2009-11-16
so, (new here) the other night we lost power and everything shut down. Including my computer. When I restarted it, I got a message on my monitor that simply said "out of range". I've tried a number of things to get my compy back up and running, but nothing seems to be working. I wonder if my video card was fried, though I have a more than capable surge protector. If anyone can help me out I'd surely appreciate it!

Dusto

---

### Post by audiomick on 2009-11-16
Out of range sounds like a message from the monitor, saying it is getting a signal it can't handle. Maybe you're right about your video card. But I'm guessing a bit...

---

### Post by Dusto on 2009-11-17
so, I am thinking the easiest form of fixing this problem is just to start all over again. However, how would I be able to recover some of the more important documents/pictures etc. that I have on my hard drive without being ablt to view it? Remember, I am totally new to Ubuntu and I am not current with most of the "lingo". So, I need detailed instructions. Please...

Thanks

Dusto

---

### Post by coffeecat on 2009-11-17
> **Dusto said:**
> so, I am thinking the easiest form of fixing this problem is just to start all over again.

Not yet!

If you think the video card might be fried, reinstalling won't help. Try booting up with the live CD, but **don't** do an installation - at least not yet. If the desktop displays OK, your video card is OK, if not it's probably fried. Let us know what happens

Next thing:

If the video card is OK, the next thing to try would be a 'fsck' of your root partition. You've had an unclean shutdown. There may be filesystem corruption. While you're in the live CD session, open a terminal and post the output of:

```
sudo fdisk -l
```That way we can tell which partition may need repairing and we can help you with the fsck command.

Third thing I can think of - if you can boot up into the recovery console, there are terminal commands you can run to reconfigure the xserver, but this depends on which release of Ubuntu you are running. Which is it: Hardy, Intrepid, Jaunty or Karmic?

Lastly - if all else fails and the video card is OK, you can copy off your personal data onto an external drive using the live CD. We can help you with this, but let's look at the other things first.

---

### Post by Dusto on 2009-11-17
GOOD NEWS.

So, I am posting from the "broken" computer using 9.04 in "view" mode. Though my current install is in 9.10 

The good part is, obviously, that my video card is indeed working and that perhaps it is not as bad as I had once thought. Though, I still dont know what is wrong, it appears that there might be a solution.

Coffecat: I tried the "sudo fdisk -l" in a terminal and I got,

Disk /dev/sda: 360.0 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       43073   345983841   83  Linux
/dev/sda2           43074       43777     5654880    5  Extended
/dev/sda5           43074       43777     5654848+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)


I have no idea what any of that means...

---

### Post by coffeecat on 2009-11-17
> **Dusto said:**
> So, I am posting from the "broken" computer using 9.04 in "view" mode. Though my current install is in 9.10

OK. I presume by view mode you mean that you were running the 9.04/Jaunty desktop CD live, but that it's Karmic/9.10 on your HD that's causing the monitor to put out the out or range message.

OK - fsck first. This stands for "filesystem check" and is sort-of/more-or-less/vaguely equivalent to a Windows "chkdsk". Slightly bad news I've just discovered: they've removed the fsck option from the recovery mode in Karmic, so that means you'll have to boot up with the live CD again. If you've got a Karmic live CD, it might be better to use that.

Boot up with the live CD, open a terminal and:

```
sudo fsck /dev/sda1
```Most likely it will give you a clean bill of health or at worst report a few minor problems which it can auto-repair. But if there is significant damage to the filesystem, things can get a bit incomprehensible. Let's hope not.

Once you've checked the filesystem, shut down from the live CD and reboot **while holding down the shift key**. The grub menu will appear. Choose the second option - recovery mode. Don't be alarmed at the text that scrolls by. When the rather retro blue menu appears, choose "drop to root shell prompt" and you'll be dumped into an even more retro environment with a # prompt.

Again - slightly bad news. I've been doing a bit of digging and it seems that the commands that used to be around for repairing the graphical server (xfix and dpkg-reconfigure xserver) are no longer used in Karmic. This is because the xserver autodetects hardware on bootup and configures itself these days. Which is why the out of range problem is puzzling. So - what I'm going to suggest may not help much if at all. At the # prompt, type 'Xorg -configure'. Once that's finished, type 'reboot' to get the system to reboot.

If none of that helps, the last option is to copy your data off the hard drive with the live CD and then reinstall. I'll post the foregoing up now so that you can digest it and then I'll post a quick howto for using the live CD for backup.

---

### Post by Dusto on 2009-11-17
ok, looks like a clean bill of health...

fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda1: clean, 255259/21626880 files, 80756752/86495960 blocks


I assume "clean" means good. Going to reboot in recovery mode and cross fingers... but not while typing.

Thanks.

---

### Post by coffeecat on 2009-11-17
OK. How to get personal data off the hard drive with the live CD. This assumes, of course, that the filesystem is not hopelessly damaged.

You didn't say whether the documents and pictures you wanted to salvage are on your Ubuntu root partition in /home (on sda1) or in your FAT32 partition (sdb1) on the second drive.

I'm going to assume that you are going to copy the files onto an external USB drive. It would be wise to do so, rather than just from internal drive 1 to drive 2 or vice versa.

OK - the FAT32 sdb1 partition first, if only because it's easier. No permissions problems to trip you up. Boot up with the live CD and go to the main Places menu. See if you can identify your FAT32 partition - it will show either with the partition label (if there is one) or the partition size. Simply click on it to mount it and a file browser window will open. Now plug in your USB drive and once it has mounted and another browser window has opened, just do a drag and drop of everything you want to copy.

**Your home folder on sda1**. Mount the sda1 partition from the Places menu as before and navigate to /home/*yourusername*. Try dragging and dropping to the USB drive, but you'll more than likely get a permission denied error. This is because your (UID) user identity number in the live session is different from your account UID on the hard disc. If that happens, open a root browser window with:

```
gksudo nautilus
```Now navigate to the root of the (live CD) filesystem. Open the /media folder and you should be able to find the folder in which sda1 has been mounted. Open that and from there open /home and then /*yourusername* and you should be in your home folder. Now simply drag and drop as before to a USB drive.

---

### Post by Dusto on 2009-11-17
ubuntu@ubuntu:~$ gksudo nautilus
(nautilus:4849): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed


This cant be good.

---

### Post by coffeecat on 2009-11-18
> **Dusto said:**
> ubuntu@ubuntu:~$ gksudo nautilus
(nautilus:4849): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed


This cant be good.

I get:

```
ubuntu@ubuntu:~$ gksudo nautilus
(nautilus:3822): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:3822): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3822): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3822): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```That's with the 64-bit Karmic desktop CD running in live mode. Despite all the panic-stricken messages, I still get a perfectly usable root Nautilus. You get a similar worried comment about eels if you invoke Nautilus from the terminal without root powers. I seem to remember Nautilus has been doing something similar since the age of the Dinosaurs. I always ignore all this and plough on regardless. :-s

---

### Post by nerdy_kid on 2009-11-18
why not just delete the xorg.conf file? or run dexconf?


try this from recovery mode on the 'broken' pc:
```

dexconf

```

then reboot.

---

### Post by sudoer541 on 2009-11-18
try this it works: 

dont touch your computer until it boots up to the login screen press the tab button and it will take you to your username. press enter and enter your password. with your mouse assume that its slightly in the corner of the screen on applications menu. press the right arrow on your keyboard (>) twice go down once (V) then right arrow once (>) then press the letter D on your keyboard twice, the press the enter key. press the tab key 3 times and press enter. go down twice and press enter and voila you got your monitor working. I know you wont be able to see anything but assume that you are able to see and you will do it. if you want to practice this you can use the live CD and then you can follow the directions I posted above without the live CD. try it! bon chance

---

### Post by Dusto on 2009-12-08
> **sudoer541 said:**
> try this it works: 

dont touch your computer until it boots up to the login screen press the tab button and it will take you to your username. press enter and enter your password. with your mouse assume that its slightly in the corner of the screen on applications menu. press the right arrow on your keyboard (>) twice go down once (V) then right arrow once (>) then press the letter D on your keyboard twice, the press the enter key. press the tab key 3 times and press enter. go down twice and press enter and voila you got your monitor working. I know you wont be able to see anything but assume that you are able to see and you will do it. if you want to practice this you can use the live CD and then you can follow the directions I posted above without the live CD. try it! bon chance


didn't work...

neither did "dexconf"

---

### Post by Dusto on 2009-12-08
the only thing that has worked is "sending" all my pertinent stuff (pictures, docs, etc) to an external hard drive and saving it there. Now I am going to reinstall 9.01.

I'm gonna go get a bigger external hard drive (1 TB) and just start saving everything there instead of on my fixed hard drive. Its just pointless to have if you can't keep things on it without being able to get them off without having to jump through flaming hoops and balancing a glass of water on your nose.

---

