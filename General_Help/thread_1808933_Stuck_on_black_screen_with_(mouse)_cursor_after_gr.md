---
title: "Stuck on black screen with (mouse) cursor after grub and a purple screen"
date: 2011-07-21
forum: General Help
---

### Post by Condenzationator on 2011-07-21
I installed Ubuntu 11.04 today as the main OS on my laptop.
I had deleted my XP partition, and repartitioned it according to a guide I had found. ([http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/)).
Basically it was setup like this:
500mb ext2 primary partition, has the grub folder, I believe this is either the '/' partition, or the '/boot' partition
2gb swap space logical partition
10gb ext4 logical partition -- this is either the '/' or the '/boot', it contains the 'bin,boot,cdrom,dev' etc folders
243gb (the rest of my hard drive, with the exception of a partition that contains documents and files from my XP OS, formatted to NTFS) ext4, this is the one that has all my desktop/documents/etc folders

Now, I know that may or may not have anything to do with the issue, but I'll keep going.

After Ubuntu was done installing, I had some message pop up about installing an ATI proprietary driver for my ATI graphics card (an ATI Radeon HD 4330, I believe, I may have messed that number up). I installed it and rebooted, no problem.

Next, I had another update window pop up with 198 items checked and ready to download and install. I went through all of this, and rebooted, again, no problem.

Next thing I did was install some apps that were essential for me to have to use for my work (an ide, chat programs, etc). No problem with any of that.

Last thing to install was the OSE Virtualbox, and then I installed WindowsXP Pro and Windows Vista Business, then installed the guest addition addon for VB. This all worked without any issues whatsoever.

Time goes on, and I notice my computer is heating up much more than (seemingly) normal. I begin to wonder if its my graphics card. So I shut down the computer and let it cool down. Reboot, and no problem, still working fine.

Then I opened a couple of apps and tried a simple game (can't remember the name) I believe it was a simple 3d topdown, as I wanted to test my graphics card. This is where things seemed to start to go wrong. My laptop began hanging, not even allowing me to access the terminal via ctrl+alt+f2. The screen flashed and I saw the blue/green/grey fuzz that I get when the graphics card is starting to heat up too much. Then everything hangs and I can't do anything at all, including move the mouse. I did a hard reboot (I believe this is what you call pulling the plug/pressing the power button, correct me if I'm wrong). I then rebooted, saw a chkdisk, then it booted seemingly normal, but it hung right after the purple screen after the grub screen.

This is pretty much where I'm at right now. I strongly suspect the fault is with the ATI drivers, but have been completely unsuccessful in my attempts to fix it. I've googled just about everything I could think of, along with searching these forums. I've tried just about everything listed in the forums, but to no avail.
I've tried the commands that are supposed to purge the ati drivers, but all I get are errors that say they can't remove the 'virtual drivers'.

Right now I'm booting off a live cd, so I know the computer still works fine, just not my actual installed OS. I'd really like to get the issue resolved without having to reinstall, as it took quite awhile just to get it usable in the first place, but this has already taken so much time, I may just resort to that if we can't solve it any other way. Got too much work to catch up on as it is.

As a re-instated note, perhaps if you have any tips, but not particularly about fixing the OS, my laptop (I'm strongly guessing my graphics card) is heating up much more than normal, compared to that when XP was installed. Is this more than likely just a driver issue, as is the rest of it?

Also, I did have Compiz installed, though I didn't choose for it to be installed, I believe it came pre-installed. I've heard it could cause some issues, though I have no idea as to the validity or relation to this particular issue.

Edit:
I just remembered while searching for a solution, I found a post somewhere that said something about the information not being sent to the monitor from the graphics card properly, thus no desktop. I'm guessing that'd still fall under the driver issues, but again, I'm unsure. I would think that wouldn't be entirely true anyway, since I can still see my mouse fine, just no desktop, only a black screen.

Edit #2:
Forgot my laptop specs.
HP ProBook 4710s
Intel Core 2 Duo T6570 2.1 GHz
3 GB DDR2 RAM
ATI Mobility Radeon HD 4330 (discrete)

---

### Post by Condenzationator on 2011-07-21
I now get a new error, and it refuses to bring up grub or anything else for that matter.

```
error: file not found.
grub rescue> (underscore cursor)
```

Any help/tips much appreciated. :)

---

