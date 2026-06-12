---
title: "help with drive partitioning"
date: 2011-07-28
forum: General Help
---

### Post by Arthur41 on 2011-07-28
Hello,!
 
I have a new HP 2000 notebook computer 240ca, 
the computer comes with Windows 7 and the ('500GB') HD comes factory default like this:
 
C: 451GB NTFS
 
HP_TOOLS (Hidden) FAT32
103MB
 
D: 14.29GB NTFS (Recovery Partition)
 
System (Hidden) NTFS
199MB 
 
Linux says, it can't install and to check Windows ('fs'), whatever that is.? 
 
any ideas.? thank you
 
Craig

---

### Post by Wim Sturkenboom on 2011-07-28
The problem is that HP has created 4 primary partitions which is the maximum that one can have on a single disk.

// rant
It's about the most user stupid setup that one can imagine. Any designer that comes up with those non-flexible and user-unfriendly ideas should be killed.
// rant end

You have to remove one and resize another one. Next create an extended partition (ubuntu will probably do that for you once it can create a partition) and place logical partitions inside it (again, probably ubuntu will do that for you).

Do a search here, the subject has come along a couple of times.

The probable solution is going to be to remove the second partition, resize the first one and let ubuntu use the free space. I'm however not 100% sure about that.

---

### Post by Arthur41 on 2011-07-28
Thank you.

---

### Post by Arthur41 on 2011-07-28
yae, I'm not 100% sure about these hidden drives or what to do with those.

---

### Post by Arthur41 on 2011-07-28
and the Recovery partition I was hoping to keep.

---

### Post by seawolf167 on 2011-07-28
You don't need any of the partitions aside from the primary C: partition. Rather than use the Recovery partition, I suggest you make full disk images using an imaging program like [Clonezilla]("http://www.clonezilla.org"). You can then make incremental backups of Windows with the Windows backup utility and of Ubuntu with rsync (or any number of [utilities]("https://help.ubuntu.com/community/BackupYourSystem"))

You can then resize your Windows partition with the built in Windows partition editor (right click "my computer" select "manage", then "disk management"). Once you have made Windows smaller, you can install Ubuntu to the freely unallocated space.

Here is a dual boot installation [guide]("https://help.ubuntu.com/community/WindowsDualBoot").

I suggest at least 3 partitions for Ubuntu on install (through manually partitioning the drive during installation):

/ (root), type ext4, mount point /
/home, type ext4, mount point /home
swap, type swap, mount point swap

---

### Post by Arthur41 on 2011-07-28
thank you.

---

### Post by oldfred on 2011-07-28
Some more info on partitions. Be sure not to delete the 100MB system boot/recovery as that is how windows boots. You should make the DVDs that are the recovery partition and the install DVDs that the vendor did not give you. But they are not an install but just an image of hard drive as purchased. You also should make a windows repair CD.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Arthur41 on 2011-07-28
I don't think the remainder from the shrunk partition as a "dynamic" F: at 50GB will work. it's just unallocated, but now ISOLinux 3.86 won't start from CD
 
it's a fubar partioning scheme set-up to illegally forstall any Linux ease-of-use
I think
 
it's just complicated
 
I'm not a lay user, but, it just gets [so] technical, that the ordinary user "can't be bothered"

---

### Post by Arthur41 on 2011-07-28
and I called HP, and they cited "compatibility issues" with dual-boot configurations,
 
but not "allowing" a dual-boot is another matter
 
I swear, people that don't know how to Rule a million people, shouldn't Rule a million people

---

### Post by Arthur41 on 2011-07-28
maybe I could use a LiveCD but that's too slow, and given, I don't want to throw Windows out and [only] use Linux as the sole operating system on the HD
 
it's these little 100MB hidden System partition and 200MB HP_TOOLS hidden partitions, that are causing the trouble here
 
if it was just one primary c: and one logical or extended d:, that would suffice anyway
 
there's only the recovery discs on the 15GB D: anyway, 
 
it's just cheezy

---

### Post by Arthur41 on 2011-07-28
I'm opposition to an illegal monopoly here, I'm telling you
 
Microsoft and HP have descended to the state of an illegal monopoly,

---

### Post by Arthur41 on 2011-07-28
I mean since when does Windows require a 100MB hidden System partition with an IBM Compatible PC.?

---

### Post by Arthur41 on 2011-07-28
Venda.!

---

### Post by Arthur41 on 2011-07-28
hm, 
proprietary hardware,
is that illegal.? 
 
it's sold as an IBM PC Compatible,
 
not closed source architecture

---

### Post by Arthur41 on 2011-07-28
oh well, I got it on sale, $400. 
HP laptop 2000 240ca
 
what can you do.
 
difficult to fight the man

---

### Post by Arthur41 on 2011-07-28
$400 is alot of money
it's like buying... a vacuum cleaner, for the next 5 years...

---

### Post by 23dornot23d on 2011-07-28
Buy a USB hard drive .... and you can set it to boot off of that ........

There are always more solutions ..... ;)

---

### Post by Arthur41 on 2011-07-28
I have 14days to return it, but it was on sale, and I'm not going to return it, so I'm stuck with it and Windoze

---

### Post by 23dornot23d on 2011-07-28
If in the BIOS you can set it to boot from an external USB Drive .... then all that needs setting in the
BIOS is the Boot order to look for a USB device first ....

Once it finds it it will use the USB MBR and boot whatever Linux system or systems up that you want ....

I use them all the time ..... just 30 Dollars for a WD 250 Gig from what someone posted in a earlier thread ...

and once you get used to Linux ... you will probably then remove everything to do with Windows .... at some point in the future,

I did ...... and no regrets ..... ;)

---

### Post by Arthur41 on 2011-07-28
I'm going to try a dynamic F: Drive anyway

---

### Post by Arthur41 on 2011-07-28
it says: "The operation you selected will convert the selected basic disk to "dynamic" disk. If you convert the disk to dynamic, you will not be able to start installed operating systems from any volume on the disk (except the current boot volume). Are you sure you want to continue.?"
 
hm.

---

### Post by Arthur41 on 2011-07-28
how am I going to convert my hardrive and keep Windows, and my recovery discs won't work, without all these fancy little hidden partitions

---

### Post by Arthur41 on 2011-07-28
it's just too much reading for me
 
give it to me straight
 
what.? do I use FDisk or something.?

---

### Post by Arthur41 on 2011-07-28
oh you (all) don't know who I am.
 
arthur-10forward.blogspot.com

---

### Post by Arthur41 on 2011-07-28
that's too large of a vendor to burn me,
that's Hewlett Packard.
 
I'm not done with this issue with this vendor quite yet I don't think
 
I didn't buy a Mac27 that needs special software and hardware from a closed source

---

### Post by Arthur41 on 2011-07-28
Made in China. I'm sick&tired of everything being made in china too.
 
it's HP Occidental, not Oriental.? that's what they market on the frontface.
 
"The Computer Is Personal Again" yea. I thought this was a good thing, it turned out to be a bad thing. they just don't know how to be good over there.

---

### Post by Arthur41 on 2011-07-28
I mean it's AMD too. it's all kinda standard non-proprietary stuff on the outside.

---

### Post by Arthur41 on 2011-07-28
I don't see any reason on the outside of the box, immediately or precisely or fairly, for this product to Proprietary Hardware or Oriental

---

### Post by Arthur41 on 2011-07-28
HP cannot mislead the general public. 
I'm going to fight this.

---

### Post by westie457 on 2011-07-28
> The problem is that HP has created 4 primary partitions which is the maximum that one can have on a single disk.

// rant
It's about the most user stupid setup that one can imagine. Any designer that comes up with those non-flexible and user-unfriendly ideas should be killed.
// rant end

You have to remove one and resize another one. Next create an extended partition (ubuntu will probably do that for you once it can create a partition) and place logical partitions inside it (again, probably ubuntu will do that for you).

Do a search here, the subject has come along a couple of times.

The probable solution is going to be to remove the second partition, resize the first one and let ubuntu use the free space. I'm however not 100% sure about that.
__________________
If you don't make backups of your important data, your data is obviously not important to you.
Last edited by Wim Sturkenboom; 5 Hours Ago at 05:20 PM..

[QUOTESome more info on partitions. Be sure not to delete the 100MB system boot/recovery as that is how windows boots. You should make the DVDs that are the recovery partition and the install DVDs that the vendor did not give you. But they are not an install but just an image of hard drive as purchased. You also should make a windows repair CD.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Noteboo...on/td-p/228360](http://h30434.www3.hp.com/t5/Noteboo...on/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windo...windows-vista/](http://www.howtogeek.com/howto/windo...windows-vista/)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-re...tion-dvd-disc/](http://www.intowindows.com/how-to-re...tion-dvd-disc/)
[http://www.webupd8.org/2010/10/creat...usb-drive.html](http://www.webupd8.org/2010/10/creat...usb-drive.html)
__________________][/QUOTE]

Follow the advice posted by Wim Sturkenboom and oldfred.

They were and are spot-on with their advice. I have re-posted them as quotes to refresh your memory. What they have suggested can and does work. FYI oldfred is regarded very highly about his advice with partitioning as is Wim Sturkenboom.

Both have unknowingly helped me when I have had various issues and followed advice and tips found in various threads without the need to ask any questions.

And the idea that you can install to an external drive is a good one.

---

### Post by Arthur41 on 2011-07-28
thanks for re-iterating, 
 
the idea to use an external USB Drive is a good one, but I already 500GB...
 
any other expedient, easy for the Linux newbie solutions to this problem.?

---

### Post by Arthur41 on 2011-07-28
the solution, is not immediately clear, even to HP and IBM and Microsoft.
 
now I could wipe the existing drive clear and just install Linux, OR I could buy an external HD, but then I've got this external harddrive sitting there cluttering up things.
 
is there any way to keep Windows.?

---

### Post by Arthur41 on 2011-07-28
I've got a feeling that if one knows how to use FDisk, 
one could get Linux running in dual-boot configuration on this proprietary HP laptop
 
that may be the only easily readily viable possible 3rd solution.

---

### Post by Arthur41 on 2011-07-28
let's say I can get FDisk running. how would I do this.? 
 
I'd have to re-boot the machine from a start-up CD with FDisk on it

---

### Post by Arthur41 on 2011-07-28
you can move and re-order partitions with FDisk, I think
 
it doesn't just re-format

---

### Post by Arthur41 on 2011-07-28
maybe a program like Partition Magic would work, 
but I don't have a copy of that, and it's old

---

### Post by westie457 on 2011-07-28
Your situation is very similar to this one. [http://ubuntuforums.org/showthread.php?t=1808742&page=2](http://ubuntuforums.org/showthread.php?t=1808742&page=2)

Read the through my posts in this thread. The advice does work as I had to do it myself. 

This link [http://ubuntuforums.org/showthread.php?t=1798827](http://ubuntuforums.org/showthread.php?t=1798827)

explains in detail what I did as an experiment to prove to myself that it could be done.

Enjoy and good luck.

---

### Post by Arthur41 on 2011-07-28
it's a matter of getting the logical and extended drive(s) clear and in the free, [on the end]
 
you see, the hidden partitions are impedeing Linux' view, to tack itself on to the end of the drive

---

### Post by Arthur41 on 2011-07-28
I should put the two(2) Hidden partitions in between C: and D:. 
 
perhaps System 1st and HP_TOOLS 2nd
 
this may allow Linux to fire up

---

### Post by Arthur41 on 2011-07-28
so I can't dual-boot. tell me why HP.

---

### Post by Arthur41 on 2011-07-28
even if I could re-order the hidden partitions and stuff them in between C: and D:, I don't know if Windows would start anymore, and restoring Windows from the Recovery CD's, even re-ordered back, may not work. 
 
furthermore, I may only be allowed to extend a 3rd logical drive from the apportionment D: being 15GB as it stands

---

### Post by Arthur41 on 2011-07-28
oh well, 
external USB Drive (possibly)
thanks for reading
thanks for the solution(s)

---

### Post by oldfred on 2011-07-28
You still have to MBR(msdos) four partition limit. To be able to create an extended partition that can hold many Linux partitions, you have to delete one of the current ones. Some say after making the DVD's the vendor recovery is worthless. And others say the HP tools can easily be copied or redownloaded if necessary.

---

### Post by oldfred on 2011-07-28
A third option, not often used on preinstalled systems. You can delete the 100MB boot/recovery partition. Windows 7 added this to let you encrypt the main partition. But some users have accidentally deleted it and we have successfully repaired the main partition with the missing files. Do not do it before asking for more info, if you are thinking about this as moving a couple of files & a boot flag may greatly simplify the repair.

---

### Post by Arthur41 on 2011-07-28
They left me 1.73GB on the tail end of D:, and that's it, AND they put the hidden partition System AFTER D:.! Imagine.! in fact, you can't even tell.

---

### Post by Arthur41 on 2011-07-28
Thank you. 
 
the solution is just not readily apparent to me, except using an external USB Drive or reformatting with solely Linux installed on the whole 500GB

---

### Post by Arthur41 on 2011-07-28
even the external USB Hardrive is a little tricky because it depends on the BIOS, and the Linux setup

---

### Post by westie457 on 2011-07-28
> **oldfred said:**
> You still have to MBR(msdos) four partition limit. To be able to create an extended partition that can hold many Linux partitions, you have to delete one of the current ones. Some say after making the DVD's the vendor recovery is worthless. And others say the HP tools can easily be copied or redownloaded if necessary.

+1

The HPTools partition is basically a library of installed software and drivers for Windows to operate. They can be downloaded any time you need them. The recovery partition on the other hand cannot be downloaded at all. Sometimes it really can be better to leave this on the hard drive as DVDs can and do get lost and or damaged. If ever you need to get a replacement of this the charge in the UK is about 40 GBP I think.

---

### Post by Arthur41 on 2011-07-28
running the whole system thru a USB Cable might bottleneck it. it might be a little slow

---

### Post by Arthur41 on 2011-07-28
unless I delete Recovery and HP_Tools and Re-size C:
 
but I'm not sure how to get sda1 sda5 and sda6 out of that one sole D: logical extended chunk

---

### Post by Arthur41 on 2011-07-28
but the HD layout is not clear, if you check the .png screenshot I posted earlier

---

### Post by westie457 on 2011-07-28
> **Arthur41 said:**
> but the HD layout is not clear, if you check the .png screenshot I posted earlier

Slow down and please look at the links posted a little earlier.

The information is there to help you.

---

### Post by Arthur41 on 2011-07-28
That little hidden 100MB System partition IS the MBR, which defeats Linux, I'm pretty sure

---

### Post by Arthur41 on 2011-07-28
you see, where does Linux normally write the GRUB Bootloader.?
 
it won't be able to write it in the hidden secret 100MB HP unnecessary System partition

---

### Post by Arthur41 on 2011-07-28
HP Doesn't want service calls that they can't understand, because a copy of Linux is loaded on the back end of the drive causing compatibility issues or stability issues, due to this GRUB Bootloader
 
but then I have to "throw out" Windows, so give me a Windows install CD with the battery powered desktop computer laptop then

---

### Post by Arthur41 on 2011-07-28
I'm going as slow as I can partner, but I don't have 40hours of reading time,

---

### Post by Arthur41 on 2011-07-28
Z to the 4 from the A to the 3, and I was in.!

---

### Post by Arthur41 on 2011-07-28
I think the MBR is in the 100MB, and it can't be done. That's what I think.!

---

### Post by Arthur41 on 2011-07-28
Imagine.! 40hours of reading later,! if you can actually Get it to work after the 40hours of reading, I would really commend the guy. even 10m of reading for this stuff.

---

### Post by oldfred on 2011-07-28
You do not install grub2's boot loader to a partition like sda1 but the the drive sda which is one sector at the beginning of the drive before the first partition.

The extended partition can hold many logicals. They all will be sda5, sda6 etc depending on how many you want to create. The minimum is / (root) and swap. But we often suggest /home as another partition and if dual booting with windows make the windows system partition smaller and store all its data into a d: drive that you mount in Ubuntu as a shared NTFS drive. Then you are not trying to write directly into the windows system partition which windows often does not like.

---

### Post by Arthur41 on 2011-07-28
bought the $400 vacuum cleaner, 
got burned
now I would say, who cares,
except for the fact that it's a really large vendor, 
that can't be a disappearing act or a fly by night

---

### Post by Arthur41 on 2011-07-28
I bought it at Staples Office Depot in Vancouver, BC, Canada

---

### Post by Arthur41 on 2011-07-28
so C: is sda4
I understand. I didn't know that.
 
so Linux works it's magic before A: in with the MBR of DOS and GrubBootloader.(?)
 
thank you

---

### Post by Arthur41 on 2011-07-28
[Solved] What this H.P. 2000 laptop model 240ca is is defeat of Linux so they don't have to take service calls concerning said 'compatibility' 'stability' issues to do with the GRUB BootLoader, BUT, they have to give me a Windows install Disc then, if they want to do that.
 
I can install Windows on this (generic) hardware, minus all the HP rigermarole

---

### Post by Arthur41 on 2011-07-28
we're pretty sure the IBM PC 1981 is [open source] hardware architecture, aren't we.? clones or compatibables are allowed, right.?

---

### Post by Arthur41 on 2011-07-28
1st of all, if anyone is going to claim that the PC is proprietary closed source architecture, it should IBM, Not HP for 1
 
and even then, only IF that were the case, which it's not, is IBM saying that "you can only install Microsoft O.S. on the official (PC)".?

---

### Post by Arthur41 on 2011-07-28
the hardware could even be re-visited
the IBM PC open source, hardware architecture, design, is frankly not precisely the best, 
 
but we need another open source, hardware architecture, design that Large enough, 
 
frankly, it would take the whole english government department to perhaps change the conventional PC to something we call the standard PC

---

### Post by Arthur41 on 2011-07-28
in fact, 
come to think of it
the IBM PC is like the English Government
 
it's not up for control
 
is it closed source proprietary.? 
or open source.?

---

### Post by Arthur41 on 2011-07-28
[IBM] is the Ruler of the (PC)
 
if an English government exception department were to (improve) upon the conventional PC to the world-standard PC, it would not gain any further control or right

---

### Post by Arthur41 on 2011-07-29
it's such a Large undertaking or concept, that we would have to proceed carefully. "What is the PC",? if we're going to improve it, we can't throw out "what currently makes it a PC"

---

### Post by Arthur41 on 2011-07-29
if ever a computer left something to be desired it was the H.ewlett  P.ackard netbook 2000 240ca. Man,! they just don't understand "intuity".  I mean, I know to put my umbrella up when it rains, 

let's presume some premises, 

right,? was I born yesterday.?

do I go up to my Government superior(s) and flex my 24"guns or do you think "firing up a couple of brain cells 'afore" is more impressive

the privacy, the security and esp. the [functionality], "are just not there",
which drops the "performance" right off,

HP just doesn't know what they're doing with Computers or a PC 

there are two extremes in life, of Pirate and Law 

I mean its recovery from discs process, what a mind  bogglingly convoluted restore from disc image.! hours.!

and the restore Is Not The Same as the factory default settings that came with the wizmo

---

### Post by Arthur41 on 2011-07-29
this computer here is a classic example of 24"guns. first of all, it's  very quirky or proprietary. it just has to be different.  the esc key is the F2 key, the pause key is down with the shift key,  which doesn't even work when used. the cursor keys are are not properly aligned. the  enter key to too far to the right. I have to stop what I'm doing, each time, to hit Enter.

so "Smart", that they miss the point.

24cycles later, the task was complete, and we didn't miss a single point, "but we missed the point"

---

### Post by Arthur41 on 2011-07-29
needless to say, I couldn't instill Linux. HP is way out of line.

1. it's not a PC, don't market it as such.

2. it's proprietary and I'm only allowed to install DOS, not UNIX. which is even more bogus.

3. you market it as an Occidental product, and it turns out to be an oriental product. this is bogus.

the list could go on

you want to market a 'wizmo', H.P. then do it. do whatever you want, but don't mislead and misguide the general public. market it as such.

the screen, which is a simple matter, relatively, is particularily  non-amenible to Linux. it's proprietary, so that Linux won't recognize  it. I mean the monitor.? the screen.? I think

it's an AMD processor too
right outside in big letters, on the box. 
which tells me, the consumer, that it's a PC Compatible

in fact, it's a Wizmo, and I got burned

---

### Post by Arthur41 on 2011-07-29
I could sort of cajole or rangle Linux onto it, if I just did a totally clean wipe and formatted the whole 500GB just for Linux, but then I don't have a Windows install disk

---

### Post by Arthur41 on 2011-07-29
the thing is, I don't wish to be out of luck with Windows. How will my recovery discs work.? they won't. this is not a solution. there is no practicable feasable way to dual-boot this Computer with Windows 7 and Linux.

---

### Post by Arthur41 on 2011-07-29
and I know that H.P. is so fly by night, they're so non- stand up

---

### Post by Arthur41 on 2011-07-30
I should raise a flag on this one, just one more time, before it goes down in history, as the last fly-by- night wizmo or Mac27

---

### Post by Arthur41 on 2011-10-21
furthernote:
 
as it turns out, this machine won't even let me root install Linux, as a stand-alone Linux machine, [because], the switch for the wireless internet card, is auto-off, and the F12 function keys only worked under the Windows environment,
 
a real [illegal] Wizmo

---

