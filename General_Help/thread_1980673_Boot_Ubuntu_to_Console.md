---
title: "Boot Ubuntu to Console"
date: 2012-05-15
forum: General Help
---

### Post by Jolladay on 2012-05-15
Hi there,

I'm trying to get Ubuntu 11.10 to boot automatically to console and then have a Python script run at boot.

I am having no luck booting to console.

I have tried the following:

> Step 1 First update your repository by running

sudo apt-get update

Step 2 There is some bug in old version of lightdm, so we need to upgrade the same. To do so run,

sudo apt-get install lightdm

Step 3 Now we have to modify grub config. Step 3a Open /etc/default/grub with your faviourite editor and change

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="text"

Step 3b Also comment GRUB_HIDDEN_TIMEOUT=0 This line is for unhiding the GRUB menu

Step 4 Now we will upgrade GRUB configuration

sudo update-grub

Found here: [http://askubuntu.com/questions/70188/how-do-i-boot-into-console-mode](http://askubuntu.com/questions/70188/how-do-i-boot-into-console-mode)

This only causes the system to go to a blank screen with a flashing cursor after GRUB. 

Any help is greatly appreciated!

-Jolladay

---

### Post by Jolladay on 2012-05-15
Does anyone know how to do this? :)

-Jolladay

---

### Post by oldfred on 2012-05-15
Did it boot before? That is like a typical video issue. 

there is now this line in /etc/default/grub. But the way you were doing it, was what used to work. I do not use it.

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

---

### Post by Jolladay on 2012-05-16
Thanks for the reply!

It's strange, if I run update-grub in the recovory console, it then shows GRUB menu (no countdown), if I select my ubuntu install it does boot to CLI. However, if I run update-grub in my normal ubuntu install, it then brings me to a blank screen with flashing cursor on the next reboot.

Here are the contents of my /etc/default/grub:

[PHP]GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10[/PHP]

...skipping

[PHP]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""[/PHP]

...continuing

[PHP]GRUB_TERMINAL=console[/PHP]

I'm trying to get it to boot directly to CLI w/out showing the GRUB menu.

Thanks for your help!

-Jolladay

---

### Post by oldfred on 2012-05-16
I have not paid attention, but there are some similar threads on servers. The issue  is grub wants to show menu after any boot error or recovery mode. I think it is in the scripts and ends up at the top of grub.cfg. But I do not know details of modifying script.

Found some reference:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

> Last Boot Failed or Boot into Recovery Mode

If the last boot failed or after a boot into Recovery Mode the menu will be displayed until the user makes a selection. The timeout setting in /etc/default/grub do not apply in this case. To change this behaviour, /etc/grub.d/00_header must be modified (if statement checking recordfail at the end of 00_header).


---

### Post by drs305 on 2012-05-16
*oldfred* is correct about the failure mode - if G2 doesn't get all the way to a normal boot it will stop at the Grub menu on the next boot.

The 'console' option refers to the Grub menu, vs displaying the grub graphics. It doesn't carry over after the kernel takes over.

Try adding "text" to the kernel options at the end of the 'linux' line in the menuentry. It's not a true kernel option, but in Ubuntu it is supposed to boot to the Ubuntu terminal, which is what you are looking for.

You can try it from the Grub menu for testing by pressing e and editing the menuentry. Cursor to the linux line, go to the end, remove 'quiet splash' and anything else (vt.handoff, etc) and add "text".

CTRL-x to boot and see what happens.

If it does what you want, make it permanent by adding it to /etc/default/grub on the line where 'quiet splash' currently exists (GRUB_CMDLINE_LINUX_DEFAULT=).

---

### Post by Jolladay on 2012-05-16
I pressed e in the grub menu, removed ro quiet splash vt.handoff=7 from the line beginning with linux, put text there and pressed ctrl+x. It then jumps to a screen that says "Booting a command list" with a blinking cursor. I cannot input anything with the keyboard. It stays on this screen.

I have previously put text in place of quiet splash in /etc/default/grub with no success.

-Jolladay

---

### Post by drs305 on 2012-05-16
When I responded I completely forgot you had already tried the 'text' option. I don't know how it would interfere with a boot to text, but try booting "text nomodeset".

The nomodeset kernel option often works for video problems before the user can install the correct driver. While using the 'text' option would seem to be enough, perhaps the combination will work.

---

### Post by Jolladay on 2012-05-16
I replaced quiet splash with text nomodeset and I still get the blank screen with flashing cursor.

Something interesting to note, when I then run fsck from recovery it boots into ubuntu (with GUI) just fine.

-Jolladay

---

### Post by Jolladay on 2012-05-17
Any other ideas? :)

-Jolladay

---

### Post by drs305 on 2012-05-17
> **Jolladay said:**
> Any other ideas? :)

-Jolladay

Do you have a lot of entries in your /etc/fstab file? You might try disabling anything other than system partitions.

Is it possible your system isn't fully ready to boot during a normal start but that by going to recovery mode things are then ready?

When it's running the fsck check in recovery mode can you see repeating errors that might be fixable? You might boot a LiveCD, run an fsck check from the LiveCD and then try a regular boot to see if the problem occurs. If it doesn't, then it would appear you are getting some sort of filesystem problem while running or exiting a normal session that has to be repaired before the system will boot.

---

### Post by sjuranic on 2012-05-17
Maybe I misunderstood what you're trying to do, but as I understand it, you just want the machine to go into a text console login after running some custom Python script at boot?

All you need to do is fiddle with your runlevel(7) scripts.  The default set of these reside in /etc/rc2.d.  This is where you can disable your graphical login manager (kdm, gdm, lightdm, whatever).  Ubuntu has some custom scripts for managing these links, but I always just do them by hand.

Then to run your Python scripts, just edit /etc/rc.local.

Then the next time you boot, everything should come up the way you like (if I understood you correctly).

---

### Post by Jolladay on 2012-05-17
Here is the contents of my fstab file:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb6 during installation
UUID=07c865b6-a9a9-414a-80c0-515f77230bda /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb1 during installation
UUID=28f1ae60-50a3-49d6-95e8-ed3118fac4d0 /boot           ext2    defaults        0       2
# /home was on /dev/sdb7 during installation
UUID=8b546d1a-be95-44ea-a8e3-0d49a220d987 /home           ext4    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=016e3f2f-67da-4857-872b-1cd417b16396 none            swap    sw              0       0
```

I can't seem to find fsck's log file (I checked in /var/log/fsck* and neither file contains anything)

But while watching it I noticed it says several times "superblock last write status in future..." 

After I run fsck, it boots into ubuntu w/ GUI even though I only have 'text' in the grub file.

sjuranic: Yep, just trying to boot to console and then automatically run a python script. What I am building is a utility that resides on an external drive. The user plugs it in, boots to it and it brings up my script right away.

---

### Post by drs305 on 2012-05-17
I think we are working on resolving 2 different issues. A couple of us have focused on your normal boot problems, while *sjuranic* focused more on your real objective.

I'll let *sjuranic* take the credit and explain the rc settings, which should be able to direct you to the terminal. Don't really know if the other issue will affect this or not.

Once you mentioned the error message, I believe the problem is the system clock isn't agreeing with BIOS and is generating the error. Years ago I recall one of Ubuntu the installations was hanging up because of a 'future date' issue. The issue was the difference between UTC and local time, and the system getting confused over datetimes in the future (UTC time was 5 hours ahead of mine).

I searched the error message you posted and found some threads which shed some light. Neither of these are recent but should point you in the right direction:
[https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/268808]("https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/268808")

[https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/268808]("https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/268808")
Solutions start about mid-thread.

Search further with if the error message if they aren't quite right for more recent versions of Ubuntu.

---

### Post by Jolladay on 2012-05-18
Great! Thanks very much for the replies all. By tinkering with run levels I found that Ubuntu levels 2-5 or thereabouts are all GUI boots. I simply disabled lightdm with 

```
sudo dpkg-divert --rename --add /etc/init/lightdm.conf
```

And that seems to be working fine.

As far as the superblock-future-write issue, I still can't figure that one out. I checked into the threads you linked, drs305, and although very insightful, none of the solutions mentioned worked for me. 

The process goes like this:

I am in Ubuntu, shutdown, and must run fsck from recovery console (getting the future-superblock messages) or it will simply hang and not boot into ubuntu. Once I run fsck, it then boots fine if I select "continue boot" in recovery. At any point, if I restart or cut power, I have to run fsck again in order to boot.

If I cut power and then check BIOS, the clock is correct. I have tried both UTC=no and UTC=yes in /usr/share/initscripts/default.rcS

I have been scouring the web for hours and will keep searching. If anyone has any more ideas that'd be great!

-Jolladay

---

### Post by drs305 on 2012-05-18
> **Jolladay said:**
> I have been scouring the web for hours and will keep searching. If anyone has any more ideas that'd be great!

-Jolladay

Sorry I can't give you a more specific reference. I've erased my notes on the subject that affected my computer since it was so long ago. 

In case the Ubuntu files aren't the specific ones that need altering, is there a time selector in BIOS that can be changed? 

Also, these file changes might best be made at a specific time of day when the computer will be off for a long period. For me, living in Eastern US, I recall I made the changes at night because there was a 5 hour UTC difference. That way, any already-written files were no longer in the future when I turned on the machine in the morning and the new settings could take effect on newly-created files. (If this makes any sense.)

---

