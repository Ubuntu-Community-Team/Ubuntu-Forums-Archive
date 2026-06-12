---
title: "How to edit or remove grub 1.98 boot choice?"
date: 2011-03-15
forum: General Help
---

### Post by oldefoxx on 2011-03-15
I replaced 250 GB laptop drive with a WD 750 GB one.  That takes three perpendicular recording disks and seems to be maximum for laptops that only allow 9.5 mm clearance.  A fourth disk, to 1 TB, requires 12 mm externally height and that only a few large laptops or notebooks can fit internally.  Externally is no problem.

That all said, I've divided the 750 GB into three 250 GB partitions, and being careful to avoid overlaps with some tricks I worked out, got different Ubuntu installs on each.  Then of course we have kernel upgrades  from time to time.  Some of the resulting boot options under grub are no longer wanted.

Now with the older versions of grub, you edit the /boot/grub/menu.lst text file directly to make changes.  An easy initial change is uncomment (remove #) where it can show white and cyan on blue, then see if the colors show up when you reboot.  It takes some study and care when modifying the menu.lst file, and if you mess up, it's good to have a backup file and you may need to boot the LiveCD to have some control.  I won't go into that much, except to say you will have to add folders to /media, one for each partition, then use the mount -t command to get the partitions mounted.  The command for each will look something like this:

mount -t ext3 /dev/sda1 /media/a1

where /media/a1 is the added folder for this partition.

But as Ubuntu worms its way towards grub 2 (a product still under development and not really legacy supporting with earlier grub versions),
the idea of making manual changes has become disjointed.  I'm looking at grub 1.98, and I can't even find info on to clean up the boot process now.  All you read about is install_grub followed by grub_update.

What grub wants to do is group entries by installs, so that you have a generic boot, a recovery boot, and one choice for testing memory and other hardware.  What I want to do is group the generic options together, then group the recovery options together, then one entry for the hardware testing.  That means my preferences are possible before grub 1.98, but now I can't even figure out how to rid myself of the oldest and no longer desireable entries.  In place of a straight forward text file that you can do cut and paste with, you have a scripting process with no clear understanding of what references are being made.

Now that is just to explain the awkwardness of my present situation.  I've gone down the list of boot options that come up when booting and marked a list of the options displayed as to which ones still work and which ones to get rid of, and I want to cut out about 50% of the entries I find there.  But I don't know how to do it now, and I don't even know if there is a tool ready for this purpose.  What I would have in mind is a tool that listed all, and give me these choices per entry:

1.  Comment out a whole entry
2.  Uncomment out a whole entry
3.  Show which partition by name relates to an entry
4.  Show which entry no longer is matched to a given Linux kernel
5.  Delete a commented out entry
6.  Shift a given entry up in the sequence one place
7.  Shift a given entry down in the sequence one place
8.  Re-option a given entry as to what it does while booting
9.  Set any uncommented entry as the boot default
10. Save Changes and exit
11. Exit without saving changes
12. Revert to a backup made before last changes

That is pretty much what I think a suitable tool should do.  Right now though, I would just like some guidance on eliminating some of the existing entries.

---

### Post by oldfred on 2011-03-15
The newer semi auto ways.
HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
A easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)


Link with several of links below:
How to edit bootloader? Feb 2011
[http://ubuntuforums.org/showthread.php?t=1694681](http://ubuntuforums.org/showthread.php?t=1694681)

How to: Create a Customized GRUB2 Screen that is Maintenance Free.
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom menu:
I used drs305's command to limit ubuntu entries to two, turned off os-prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit only titles:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

---

### Post by oldefoxx on 2011-03-16
Thanks for your many tips.  I will look at them tomorrow.

Tonight, Fox News is reporting the possible pullout of the last 50 workers at the out of control nuclear reactors in Japan.  I hit on a possible solution and I've been trying to go public with it.

It is simple in concept.  Pull out everybody in area, then have the U.S. Navy fly strikes against the failing reactors.  If the blow the cores apart, the rods will become litter to be cleaned up in the years ahead.  Still, that buys us time and we are runnning out of that as things stand now.

The real question is, what happens in the millisecond when the bomb explodes?  Either way we go, there is great risk involved.  But six out of control reactors would make one heck of a meltdown.

I've been trying to communicate this idea up the line, but I've found from earlier experience that news outlets like TV and radio are really non-responsive to call ins or emails.  They only listeen when they run one of their foolish public polls to gauge audience reaction to the news that has already been reported.

Speaking of which, if any of you Ubuntu followers out there know how to pass this suggestion along, it might be a good thing to do.

---

### Post by stinkeye on 2011-03-16
> Speaking of which, if any of you Ubuntu followers out there know how to pass this suggestion along, it might be a good thing to do.
Call up the FBI and tell them you want to bomb something,
and let them know you can only do it during Ramadan. ;)

---

