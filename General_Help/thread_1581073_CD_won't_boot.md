---
title: "CD won't boot"
date: 2010-09-24
forum: General Help
---

### Post by Clive Richardson on 2010-09-24
I have been using 8.04 for a year & it's been wonderful. Recently I saw the invitation on 'update manager' to upgrade to 10.04 & went ahead wih the download, but when the system tried to reboot the problems started &, I see from the forums, this seems to be a widespread problem. You get as far as UBUNTU & 5 dots then nothing. I have read as much as I can, understood a little but got nowhere so I thought I'd recover my files (hopefully) with the 8.04 CD using photorec & then reinstall my 8.04. Problem is the CD will not boot. I've used 'help' & installed the boot helper but I get the BusyBox message and don't know what command to put in. Could someone please help?

---

### Post by pricetech on 2010-09-24
I'm guessing your CD got damaged somehow.  Is this your only system, or can you test the disk elsewhere ??

---

### Post by Clive Richardson on 2010-09-24
It works in my other computer, just checked.

---

### Post by Rubi1200 on 2010-09-24
Also, could you elaborate on what you tried to make the CD boot?

What graphics card do you have etc.?

When the computer boots, hold down Shift and try to bring up the GRUB menu; what happens?

---

### Post by rgiles43 on 2010-09-24
Hello,

Are you trying to boot the CD from your local CDROM which is mounted in the computer or are you using a USB CD-ROM? 

We recently tried upgrading to 10.04 from a 9.10 desktop and it ended up crashing so we used a sysrescue cd to recover the files from our /home directories or what not. 

[http://distrowatch.com/table.php?distribution=systemrescue](http://distrowatch.com/table.php?distribution=systemrescue)


You may also want to check your bios to make sure that it is telling it to boot from the CD-ROM. 


Please let me know if you need some help using the sysrescue cd to get the files you need.

Thanks,

---

### Post by Clive Richardson on 2010-09-24
The short answer is it has booted! Held down shift got message --Press esc to enter menu 3.......then it booted up. Many thanks, I'll try the recovery job now.

---

### Post by coffeecat on 2010-09-24
> **Clive Richardson said:**
> I thought I'd recover my files (hopefully) with the 8.04 CD using photorec & then reinstall my 8.04.

A few comments. Don't use photorec unless you really have to. Photorec is for retrieving files from a damaged filesystem, not a damaged installed system. Something probably went wrong with the upgrade without necessarily damaging the filesystem. Almost certainly your files will still be there.

Once you can get the live CD booting, all you need do is to mount your hard drive partition from the Places menu in the live session and copy whatever you need to an external USB drive. If you use photorec, **all** the filenames will be changed and it is quite unnecessary if you can see the files from the Places menu.

Also - the reason you cannot boot into the upgraded system is either that the upgrade went wrong or that your hardware is not compatible with the 10.04 version. Either way, this is not a "widespread" problem. You get a skewed idea of the incidence of issues from the forum. People don't post complaining when everything works or goes OK. :wink:

May I suggest that you download the 10.04 ISO and burn a CD from that? Since you are having to make a fresh install you might as well see if 10.04 works on your machine. If it runs from the CD then it was the upgrade that was the problem. Then you could install 10.04 rather than 8.04 which will be supported for so much longer.

---

### Post by Clive Richardson on 2010-09-24
I'm booting from the local CD Rom. Will have a look at that website and get back if I have trouble(almost inevitable with me)
Many thanks

---

### Post by Clive Richardson on 2010-09-24
coffeecat
Right, thank you for that timely advice and it sounds much easier for me. Once I have recovered everything I'll certainly try 10.04 again and see how it goes though I'll probably buy the CD this time.
Many thanks

---

### Post by coffeecat on 2010-09-24
> **Clive Richardson said:**
> coffeecat
Right, thank you for that timely advice and it sounds much easier for me. Once I have recovered everything I'll certainly try 10.04 again and see how it goes though I'll probably buy the CD this time.
Many thanks

Just a word of warning about copying off your personal files with the live CD. Your UID in the hard drive will probably be 1000. Iirc the account 'ubuntu' has an odd UID of 99 - or perhaps 500/1. Certainly different from yours. If you get an access denied or permission error when trying to copy the files, just force things with a 'gksudo nautilus' root nautilus file browser.

If you are going to buy a CD, make sure they send you the updated 10.04.1 version, not the original 10.04. Any reason for buying rather than downloading and burning yourself?

---

### Post by rgiles43 on 2010-09-24
Hello,

Do not buy the CD just go to ubuntu's website and download it from there. It sure beats the hell outta spending money out of your pocket when its open source.

---

### Post by Clive Richardson on 2010-09-24
coffeecat
One other question now I've had a look - How do I 'mount my hard drive partition from the Places menu?
Thanks

---

### Post by coffeecat on 2010-09-24
> **Clive Richardson said:**
> One other question now I've had a look - How do I 'mount my hard drive partition from the Places menu?

If you go to the Places menu it should list all the hard drive partitions (except swap). Sometimes this is in 'Removable media', sometimes not. Sorry to be vague about this - it seems to vary from version to version. Anyway, if the partitions do not have labels, they should be identified by size in GiB.

You need to find your root partition if you installed Ubuntu to a single partition, or the /home partition if you set up a separate home, or a data partition if that's what you had. Simply click on the partition in the Places menu and a nautilus file browser will open. If it was the root partition, you will see the complete filesystem: bin, boot, cdrom, dev and so. Double-click on the home folder and you will see a folder named with your account name. Double-click on that and you are in your home folder.

If you have to open a root nautilus browser because of permissions problems, it will open in the root directory (not to be confused with root filesystem) of the live session and your home folder is a bit more difficult to find. This is what you do. Click on the up button in the toolbar. This will take you to the root of the live CD flesystem **which looks just like the root filesystem of your hard drive**. So, don't go into /home just yet. Double-click on the /media folder and in that you should find the mountpoint for your hard drive partition. Double-click on that and you will see the root filesystem of your hard drive. See how you can confuse the two? Now double-click on the home folder and you should be OK from there.

---

### Post by Clive Richardson on 2010-09-24
hello rgiles43,
I know it's nice to have it free but last time I tried the download for my first ubuntu, it didn't work. I'm out in the country and the speeds were very slow then but I think they may have improved so I'll give it another try.
Thanks

---

### Post by Clive Richardson on 2010-09-24
Hello coffeecat,
I have done it! Your last message very helpful as most files were blocked but now I have them all and can breathe again! Many thanks to all and I hope it helps someone else.
Thanks again

---

### Post by coffeecat on 2010-09-24
I'm glad you've got your files off safely without having to use photorec. Another reason why you wanted to avoid that in this situation is that it would have found and backed up virtually every single system file. You would have ended up with thousands of unsorted files with impenetrable names in folders with equally impenetrable names.

Anyway, let us know how you get on with 10.04 when you finally get the CD. Another reason to insist on the 10.04.1 disc if you are buying it because of slow download speeds is that if you install the original April version of 10.04, by now there will be hundreds of megabytes of updates to apply.

By the way. When you copied your files did you copy them to a drive formatted with a Microsoft filesystem FAT32 or NTFS, or to a Linux filesystem such as ext3? If FAT32 or NTFS there won't be a problem, but if you used a Linux filesystem with a root nautilus they may now all be owned by root. Easily fixed but I forewarn you in case you get another permissions error when you try to copy them from the external drive.

---

### Post by Clive Richardson on 2010-10-26
Coffeecat, It's taken me a long time but here is where I am now:
Downloaded 10.04.1 (3 hours about) and then burnt it onto a CD but it didn't work - the packages didn't show up- I tried again but now have two more bird scarers for the fruit trees!
So then I made sure I had retrieved all the files plus my emails etc. I then used the rescue discs that came with the Toshiba Tecra A1 which did a quick format and reloaded Windows Vista. However Windows won't boot. message
PXE-E61:Media test failure, check cable.
PXE-MOF: Exiting Intel Boot Agent
GRUB Loading stage 1.5.
GRUB Loading, please wait........
Error 2 {sign with vertical line and two horizontal cross bars}

I have tried re-installing windows 3 times but always with the same result.

I have tried to install the 10.04.1 ubuntu. The disc runs and the ubuntu logo appears-the five dots change colour many times then stay on orange for a while. Then the screen changes, there's a flash of colours followed by a blank screen.
Perhaps my Toshiba isn't compatible?
I would be grateful for any ideas.
Thank you
Clive Richardson

---

### Post by coffeecat on 2010-10-26
As far as 10.04 on that laptop is concerned, I found this thread:

[http://ubuntuforums.org/showthread.php?t=1518655](http://ubuntuforums.org/showthread.php?t=1518655)

Try the 'i915.modeset=1' in post #2 to see if that gets you booting with the live CD. Just to clarify - boot with the CD and when you get the purple screen with the two icons at the bottom, tap the space bar to get the main menu. Then press F6 and add the modeset argument to the kernel boot parameter.

If that gets the CD booting then it is not difficult to add that option to your HD install. It's just a pity that no one explained how in that thread, which is probably why the OP went back to 9.10.

Turning to the Vista and non-booting issue, it looks as though the rescue discs took out the old Ubuntu root partition when it restored Vista but failed to repair the MBR for Windows. You are getting grub stage 1 and 1.5 which are looking for grub stage 2 and the menu which used to be in the Ubuntu root partition.

If you can boot up with the 10.04 with the nomodeset option (or failing that with the 8.04 live CD), boot into the live desktop, make sure you are connected to the internet and go here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Run the script and post the contents of the RESULTS.txt file. Please enclose this in [noparse]```

```[/noparse] tage by clicking on the # icon jsut above the message field.

As far as booting Vista again, you have two options:

1 - Repair the Windows mbr so that you can boot into Windows only. I can tell you how to do that with an Ubuntu CD if you don't have a Windows install DVD.

2 - Install Ubuntu so that grub is set up for a dual-boot. If we can solve the 10.04 booting issue with the nomodeset option, then you can do that with 10.04.

Post the RESULTS file and what you want to do and we can take it from there.

Also:

> **Clive Richardson said:**
> PXE-E61:Media test failure, check cable.
PXE-MOF: Exiting Intel Boot Agent

That doesn't sound healthy. That's not a problem with either grub/Ubuntu or Windows. That sounds like a message from your BIOS about the hardware.

---

### Post by Clive Richardson on 2010-10-27
coffecat-have got the Boot Options  file=/cdrom/preseed/ubuntu.seed boot/casper initrd=/casper/initrird.1z quiet splash --
I inserted as follows ...initrird.1z i915.modeset=1 quiet splash -- but the boot up failed as before. Is my insertion in the correct place, spacing etc?

---

### Post by coffeecat on 2010-10-27
Normally you would put extra options at the end of the line when using the live CD. If you were editing grub's kernel line it wouldn't matter to put the modeset option before 'quiet splash', but the two dashes at the end of the line may have a functionality - I don't know. Try it again but with the placing thus:

```
..... quiet splash -- i915.modeset=1
```That is, you don't have to move the cursor after you press F6. Just type the option in. And I can't remember whether the two dashes were together or with a space between. Whichever, leave them as they are.

---

### Post by Clive Richardson on 2010-10-27
It worked and I have the results.txt but I don't understand how to send it. I have started a new thread as there aren't any # signs in the quick reply.
I won't post the new thread because I don't know how you'll find it. Sorry.
It also appears I have windows XP. I rarely use it so I think I might overwrite it with ubuntu. I just need to know how to make the boot up work every time.

---

### Post by coffeecat on 2010-10-27
> **Clive Richardson said:**
> I have started a new thread as there aren't any # signs in the quick reply.

Use the new reply button, not the quick reply button. I never use quick reply, even if I want to reply quickly. :wink:

Instead of the #icon, you can wrap the text in [noparse]```

```[/noparse] tags. But it's easier and quicker with the # icon. Just highlight the text that needs code-enclosing and click on #.

Anyway, I'm glad the modeset option worked. It is possible to get that into the hard drive install, but it needs a little work. When you've decided whether to continue this thread or start a new one, I can see if i can help.

---

### Post by Clive Richardson on 2010-10-27
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,140,159    78,140,097   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        2C581FB5581F7CB0                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=0

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
```

---

### Post by coffeecat on 2010-10-27
First - when you used the rescue discs to reload Windows, it didn't just reload Windows. It reformatted the whole drive and installed Windows to one big partition. Except it did a half-hearted job. It has wiped out your Ubuntu, but it left  grub stage 1 which is still sitting in the mbr, and that's why Windows won't boot.

If you want to get Windows booting as a single boot before you install Ubuntu, this is how you do it. Boot up with the Ubuntu 8.04 disc or the 10.04 disc using the boot option. Once you are in the desktop, connect to the internet however you can do that. Then from a terminal:

```
sudo apt-get install lilo
sudo sudo lilo -M  /dev/sda mbr
```I'm not sure whether you need to...

```
sudo apt-get update
```... first, so if you get an error message after the 'install lilo', do so.

This will get you booting into Windows which I think would be a good idea to see if it is a viable installation, so that you could have the option of a dual boot.

Now boot into the 10.04 CD using the added modeset option. Start the installer and choose whichever option you want depending whether you want a Windows/Ubuntu dual-boot or an Ubuntu single boot.

Once installed, reboot. For the first boot into Ubuntu, you will have to add the modeset option manually. If you have created a single-boot, you need to press the SHIFT key immediately after the POST screen to get the grub menu, otherwise it will boot automatically and will, of course, fail. Once you get the grub menu, which you will get anyway if you have made a dual-boot, highlight the first Ubuntu entry and press 'e' to edit the boot command. In the editor find the 'linux' line at the end of which you'll find 'quiet splash', but no dashes. Simply add 'i915.modeset=1' (no quotes) after 'splash' as before, making sure there is a space between 'splash' and 'i915.modeset=1'. Now press ctrl-X to boot.

To make this permanent, once you are booted into a desktop, open a terminal, and...

```
gksudo gedit /etc/default/grub
```Find the line that says...

```
GRUB_CMDLINE_LINUX=""
```Change this to...

```
GRUB_CMDLINE_LINUX="i915.modeset=1"
```Now save the edited file and exit gedit. Now from the terminal...

```
sudo update-grub
```And you *should* find that 'i915.modeset=1' has been added to the boot options and that you can boot reliably.

---

### Post by Clive Richardson on 2010-10-28
well I got XP to boot and then tried to install 10.04. It seemed to do everything and install, but gave the message that Ubuntu was working in low-graphics mode and I needed to configure screen, graphics and input device settings. When I tried to re-boot I could only get XP - no dual boot option screen came up. I tried the suggestions on 'How to restore the ununtu grub loader' and got in a real mess. I think I'll have to start again. Re-install everything; but first I think I need to know what to do about the 'low-graphics' business bacause I think that may be causing a problem. Any ideas?
Just when I thought I'd got there too!

---

### Post by coffeecat on 2010-10-28
> **Clive Richardson said:**
> It seemed to do everything and install, but gave the message that Ubuntu was working in low-graphics mode and I needed to configure screen, graphics and input device settings.

I would guess - and this is a guess only - that this is related to the need to insert the modeset option into the boot options. The problem seems to be that the version of xserver and intel driver that comes with 10.04 doesn't play so nicely as 8.04 did with your graphics card.

> **Clive Richardson said:**
>  When I tried to re-boot I could only get XP - no dual boot option screen came up.

That sounds as though the grub configuration had not finished - perhaps the installer hadn't finished its job. Did you get the low-graphics message before the installer finished? Normally you get, "Installation finished. You may reboot now." Or words to that effect.

> **Clive Richardson said:**
>  I tried the suggestions on 'How to restore the ununtu grub loader' and got in a real mess. I think I'll have to start again. Re-install everything; but first I think I need to know what to do about the 'low-graphics' business bacause I think that may be causing a problem. Any ideas?

Apart from what I said above, not really. When the low-graphics message came up, did it offer you any way of configuring screen, etc?

You could persevere with this modeset option and make sure the installer finishes before you reboot, but this does sound very frustrating. The only other suggestion I can make is to try some other distros. The latest releases of others may have the same xserver and version of Intel driver so you may run into the same problem, but you may be lucky. Ones to think about are openSUSE, Fedora and PCLinuxOS, all of which have gnome or KDE versions and all distribute live CDs. Fedora 14 is due for release in a few days so perhaps worth waiting for that rather than 13. Try the live CDs. If they allow you to boot up, chances are that a HD install will.

Don't bother with Linux Mint. As that's really Ubuntu with a green theme and some tweaking, it will fail where Ubuntu fails.

---

