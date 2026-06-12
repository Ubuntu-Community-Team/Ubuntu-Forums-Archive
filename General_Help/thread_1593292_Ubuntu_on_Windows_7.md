---
title: "Ubuntu on Windows 7"
date: 2010-10-11
forum: General Help
---

### Post by Turismo on 2010-10-11
Could i install ubuntu and whenever i boot my pc up, is it possible to boot up automatically into windows without any OS choosing screen appearing; and instead only boot into ubuntu when i have the livecd in my drive and boot from it?

Im the only one who knows about Ubuntu in my family and most would be quite confused if they didnt find thereselves booting into windows as they normally would. So to get around this and to have Ubuntu at the same time, i want to only be able to access ubuntu by putting in the live cd and booting it from that. Or is it possible for information that i download etc. to be stored onto the livecd itself?

And how much partition size should i give ubuntu?
Thanks for your help, im a newbie :D

---

### Post by yetiman64 on 2010-10-11
Grub2 if installed with a full dual boot can be hidden and in its settings your Windows install can be set as the default boot.

Then if your family use the machine, it boots to Windows and no grub screen will show at all.

However if you want to boot Ubuntu hold down the shift key during the machine boot to access the grub boot screen and choose an Ubuntu kernel to boot. No need to use the live-cd except for the initial install (and possibly partitioning prior to installing).

Using a live-cd is good to test if the OS will work OK with your hardware etc, however using a live-cd is very slow and you lose all system and program changes (installed apps etc) on each reboot. Not particularly practical for everyday use imo.

> And how much partition size should i give ubuntu? This is assuming you are going to install and not always use a live cd. I like to allow about 8 -10 GB for /, swap is 1.5 times RAM, and about 20 GB for a separate /home partition (allow more if you create and store a lot of big files :)). Note all 3 Linux partitions in the above figures can be in logical partitions, within an extended partition and Ubuntu will still boot and operate OK.

Also when planning your partitioning consider having an NTFS data only partition. It is possible to share a NTFS data partition with Windows and Ubuntu (common storage area). Having this will also avoid you mounting your Windows OS partition in Ubuntu (its not a good idea to access & write to a Windows OS from Ubuntu - but to separate data partitions is fine).

Remember when doing partitioning to do full backups (to external media) prior to altering your hard drive.:)

Edit: check link #2 and link #3 in my sig for general info on dual booting and grub2.

---

### Post by Cobracommand0 on 2010-10-11
Welcome to the forums and to Ubuntu!

It is possible to force the Windows partition to boot first, although you will need to edit the boot menu timeout settings to make it work.

[https://help.ubuntu.com/8.04/switching/dualboot-custom.html](https://help.ubuntu.com/8.04/switching/dualboot-custom.html)

That link is a good overview on creating a shorter boot sequence when the system is started. 

As far as multi-booting, hopefully someone else can step in and give you a better explanation. I always used a separate HDD when I was dual-booting XP and Ubuntu, simply because it is easy to mess up the dual-boot configuration setup and impact your existing Windows installation.  Make sure you back up your data before you proceed!

Cheers,
CC

---

### Post by Turismo on 2010-10-12
wow, thanks for your help you two!

yetiman64 im going to use your method

edit:
im kind of a newbie to ubuntu, i read your posts but im not sure what i should do to change Grub to hidden. Can you please write a mini tutorial here for me to follow. 
Thanks for your time and help

---

### Post by Schrute Farms on 2010-10-12
I will disagree with the rule of swap=1.5 times ram.  People have been stating that rule since Windows 3.1 days, and it's just not right.  Using that rule, the more ram you have, the bigger your swap is, but you need a bigger swap if you have less ram.

For instance, if you have 256Mb of ram, using that rule you would set your swap at 384Mb, giving you 640Mb total useable memory...not enough.  If you had 2GB you would set swap at 3Gb...overkill.

I've had no problems setting my swap drive at 1Gb.  I have an old laptop with 512Mb of ram and a 1GB swap partition.  I've had no problems with it at all.  If you have less ram & more hard drive space then it won't hurt to go more, like to 2Gb.

---

### Post by yetiman64 on 2010-10-12
> **Schrute Farms said:**
> I will disagree with the rule of swap=1.5 times ram.  People have been stating that rule since Windows 3.1 days, and it's just not right.  Using that rule, the more ram you have, the bigger your swap is, but you need a bigger swap if you have less ram.

For instance, if you have 256Mb of ram, using that rule you would set your swap at 384Mb, giving you 640Mb total useable memory...not enough.  If you had 2GB you would set swap at 3Gb...overkill.

I've had no problems setting my swap drive at 1Gb.  I have an old laptop with 512Mb of ram and a 1GB swap partition.  I've had no problems with it at all.  If you have less ram & more hard drive space then it won't hurt to go more, like to 2Gb.

True, the more RAM you have the less swap space you really need. 1.5 times RAM is a rough guide only and should be adjusted to suit the circumstances (note the OP doesn't state any amount for RAM - otherwise I would have suggested a specific amount).
Also if a setup with lots of RAM (for eg my 8 GB setup is allocated 10GB swap--a slight overkill, but I do use hibernation on a running system at times, and have multiple very large HDDs) is intended to be hibernated then the swap should at least equal the amount of RAM or be slightly larger.

**Edit**: just noticed your last post edit OP.  Section 5 in **link #2** in my sig has very detailed information and explanation of grub2 settings. Have a good read of the whole guide before trying any changes and if you still have questions feel free to ask them here. Also some good information on dual booting and how to set it up is in **link #3** in my sig (make sure to fully follow the links that pertain to your set-up needs within the page - easy to miss important info if you don't ;)).

---

### Post by Schrute Farms on 2010-10-12
Very true about hibernation...didn't think about that 'cause I don't use it.

Carry on...

---

### Post by Turismo on 2010-10-13
ok, so i've read through it all and a link was on section 5 to: [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

i should then just follow these instructions, and the menu would be hidden and will only appear if i click shift

> By design, Grub 2 allows hiding the menu only on single-OS systems. This is established in the /etc/grub.d/30_os-prober file. For users with multiple OS's on their machines, hiding the menu can be accomplished by eliminating one of the conditionals in this file.

For Grub 1.97~beta, found in Karmic, the lines to edit are approximately lines 27 and 62. Comment the first conditional (if) statement in the adjust_timeout section, and it's associated ending conditional (fi).

Shown are the applicable sections. Changes are highlighted in bold red. The lines between the altered lines have been omitted.

Quote:
adjust_timeout () {
[color=red]#[/color] if [ "x${found_other_os}" = "x" ] ; then
if [ "x${GRUB_HIDDEN_TIMEOUT}" != "x" ] ; then
if [ "x${GRUB_HIDDEN_TIMEOUT_QUIET}" = "xtrue" ] ; then
...
...
EOF
fi
fi
[color=red]# fi[/color]
}

if [ "x${GRUB_DISABLE_OS_PROBER}" = "xtrue" ]; then

i researched a little more and found about start-up manager, i saw on screenshots that it shows 'Show bootloader menu' if i uncheck this will the menu where i select the os dissapear and reactivate when pressing shift?

---

### Post by yetiman64 on 2010-10-13
Ah, it's good you read that, it seems I have made a blunder with regard to,> By design, Grub 2 allows hiding the menu only on single-OS systems.and your needs. Sorry about that. 

I don't advise a new user to touch os_prober scripting (though that info should be OK - I have never used it and don't know about SHIFT etc)- I didn't actually mean to go there :redface:. Even on a linux only install I actually force grub boot screen to show as I have background imaging set up - caused a bit of confusion for me (see attachment). 

If your family would tolerate the boot grub screen for say 2 or 3 seconds then it is easy to set Windows as the default entry to automatically boot **without user intervention**, while allowing you 2 or 3 seconds to get to Ubuntu if needed (up and down arrows on the keyboard).

Please don't set the timeout to 0 with Windows as the default though, has caused headaches for some (locked out of Ubuntu etc).

If you decide to install and need help in setting Windows as default or setting the timeouts (please don't use 0 !) it would be relatively easy editting /etc/default/grub. Let us know what you think about this new idea.

I'm glad you picked up on that thread info, as it will help stop any misunderstandings for other readers here, thanks.

Edit: I haven't used startup manager in quite a while, so can't advise you there. It went through a stage of causing me trouble around about when grub2 was first introduced (I installed grub2 in Jaunty first time). Maybe someone else can mention its status/usability (it seems from what I hear it's not as in depth as it used to be). Anyone?.

---

### Post by Turismo on 2010-10-15
ok, thanks alot for your help. im going to install ubuntu :D

---

