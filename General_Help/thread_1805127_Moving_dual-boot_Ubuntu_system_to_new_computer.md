---
title: "Moving dual-boot Ubuntu system to new computer"
date: 2011-07-15
forum: General Help
---

### Post by scott092707 on 2011-07-15
[This was posted at the end of another thread, but appears not to have been noticed so far.  Sorry to be repeating myself. ]

Hi.   I dual-boot Windows (XP) and Ubuntu (10.10 - 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 19:00:26 UTC 2011 i686 GNU/Linux).
I cloned an old hard drive to a new, after removing them from a computer  that became defunct as I was attempting to get it to recognize both  drives for the copy.
(I originally was planning to copy my old hard drive onto a new one and  use that, as the old one is as old as the computer was (2002), and I was  worried how long it would last.
First, I could not get the computer to recognize both the old drive AND  the new.  It was one OR the other.  Finally, it did recognized NEITHER  drive, NOR the cd/dvd drives.  I was advised that the IDE controller was  probably at least flaky, if not shot, and as that was on the  motherboard, that was basically it for my old computer...
I went to a computer place and had them assemble a new computer, sans  hard drive (as I had two already), and sans OS (as I had a dual-boot  Windows/Ubuntu).  I found a motherboard that had both IDE and SATA  controllers (new drive was SATA, with SATA->IDE adapter)).

I used an Ubuntu Live-CD to  "dd"  the old drive to the new.  OK,  although the progress reports (using the kill/watch commands found here  or elsewhere), seemed to indicate that most of the time, the Records Out  were one less than the Records In.  "diff"  was singularly unhelpful,  as after an hour or so it told me that the "files" (/dev/sda , /dev/sdb)  differed. Period.  I assumed that it would tell me individual files  that differed, so that I could deal with them individually.  No.
I took a chance and booted from the new drive.
Linux: no problems.  At all.  (New computer is nice and speedy, too.)
[Update: occasional "hangs" during boot.]
Windows: "Huh?!?!"    Either Windows (XP, SPIII?) is way less adaptable  to being placed in a new environment than Linux, or perhaps the  differing sections of the drives happened to coincide with really  important parts of Windows, as it will not boot Windows.  The first  time, it just re-booted.  Then, it put up a "Could not successfully boot  Windows the last time." message and gave me several options, all of  which lead, sooner or a bit later, to another reboot.

If any other dual-booters who have had to migrate to a new system have  any ideas how to bring back Windows (for the few things we need it for  (like MagicJack, and sites that don't work with GNash), PLEASE give me  some hints.

ALSO:

I used   "e2fsck -fvC 0"   to check out the two Linux partitions (/,  /home), and almost instantly (why so fast? - I thought fsck took some  time to work...) received lots of info (but curiously, apparently no  numeric return code...), buried within which was the fact that NO bad  blocks were found.  It looks as if it will be safe to continue using  Ubuntu (which seemed likely, as I have been able to repeatedly boot  successfully).

Does anyone think that perhaps I should do the copy again, perhaps with a different program?  Gddrescue, perhaps...
(I have made minimal changes, thinking that a 2nd copy might turn out to be advisable.)

Would  "fsck"  be able to successfully examine or better yet repair the ntsc Windows partition? 
It is not, of course, guaranteed that copy errors are causing the  Windows non-boot.  It may well be that the new environment is the issue.   IF I have the Windows disks that came with the computer in 2002, I  suppose I COULD dig them out (45 minutes away, in a storage facility)  and re-install.  But with close to 10 years of updates, it would take  forever to install, I would think...

Ideas?

-Scott

---

### Post by szal on 2011-07-15
Hi Scott,

Somehow your post is very hard to read&#8212;can you please sum up the main points of your argumentation? Thanks in advance. :)

Some general thoughts on moving OSes across different hardware: You&#8217;ll most assuredly need to reinstall Windows. Getting Linux to run on different hardware is a bit easier; if it refuses to boot, get a live CD, chroot into the installation and rebuild the initramdisk&#8212;reinstalling the kernel should take care of that.

Skipping through your post I haven&#8217;t seen you mention how the old and new hardware differ. But my take is that you might also want to reinstall Ubuntu, and while you&#8217;re at it, choose to install 11.04. If the new hardware is 64bit, then you might even want to install the 64bit variant. You can keep your /home partition and create the same user(s) as on the old system, so you won&#8217;t lose your personal settings and data.

HTH

szal

---

### Post by scott092707 on 2011-07-26
Well...  I used Gddrescue to have another go at copying the old drive to the new.
It reported no errors.  However, diff reported that the drives differed...
 
Ubuntu still has no problems.
I do not know if Windows will boot this time or not, as I am now somewhere else, house-sitting
(I am writing this on their computer, having booted with a Live-CD of Ubuntu 10.10, so I can use
Ubuntu).

1. How worried should I be that diff reported differences, even though all SEEMS well?

I just thought of how I could re-install Windows (if necessary, and IF I can find the disk(s) that
came with my Dell 8200).
LET Windows have the old drive for the installation, since I believe it will insist on taking it all anyway, wiping it "clean" in the process.
Since I have Ubuntu successfully copied onto the new disk, it should be safe.
Then, after installing Windows to the old drive, copy my old Windows data to the old drive from the new.
Making sure it takes up no more room than the size I had allotted for it previously, use GParted to reduce the partition size to that size, and dd or Gddrescue the new Windows installation on the old drive to the partition for Windows on the new.

2.  Does this seem like a reasonable way to proceed?
(or will Windows not like the fact that it is now on a different drive, even though it is in the same system?)  

3. Since the entire drive was originally dd'd/Gddrescue'd (including, therefore the boot blocks), then the booting for Windows shouldn't be an issue, for when I dd/Gddrescue the new installation of Windows to the partition on the new drive where Windows was before, presumably the location to which the boot program jumps in order to boot Windows would be in exactly the same place as before.
Does this seem correct?

[I could of course just let Windows have the old drive, and only use the new one with Ubuntu...
Problem is, the reason for getting the new drive in the first place, was that the old one is from 2002, and presumably will fail soon, and then I will have no place to store my Ubuntu installation while installing Windows on the new drive (since it would wipe out everything else on the drive, including Ubuntu).]

4. Anyone have any comments on this situation?

-Scott

---

### Post by Mark Phelps on 2011-07-27
My own experience has been that MS Windows products are best at cloning/migrating MS Windows OS's from one PC to another.

You can obtain Macrium Reflect from their website for free, and it can be used to migrate an MS Windows installation from one PC to another. But, you have to have a working MS Windows PC to start with.  Once you install that, use the option to create the Linux Restore CD.

Their paid version also provides direct disk cloning capability (don't know if the free version also does this, or not) in which you can have both drives connected and simply clone one drive to another.

---

### Post by Waterman1000 on 2011-12-15
I'm having a slight simular problem.
I obtained a new 2TB Hitachi Sata Hardrive. I was running ubuntu 10.10 on the older drive with VB installed to run windows 7 Primium. I wanted to create a dual boot on the new drive. I Did that, here's what I did.
Installed windows 7.
Repartioned four area's.
1.Window own reserve
2. 300gb's for windows
3. 1.7TB's for ubuntu
4. 16gb's for swap. (There will be two 16gb's swap when done with everything. one
for windows and one for ubuntu).
Windows running fine on new partioned drive.
Used windows transferr to new computer to created VB backup and installed into
new Windows partsion. Reinstalled some programs and a few items and running like
the original with no problem.
Now I launched the ubuntu 10.10 live CD. Went thrue the install and
mounted the \ in main ubuntu and setup the swap. I didn't use the install
alongside other OS. Here's a point for other's. If you don't partition the drive
via window's into the above, then the alongside will not show in the ubuntu install
area.
Now I have a fresh install of ubuntu 10.10 and windows on a dual boot drive running fine. Now the hard part. I wanted to do the same with my ubuntu on my old drive. Migrate it to the new drive. I wound up using Clonezilla. This works very well at what It dose. I cloned the ubuntu off the older drive and install it into the newer area for ubuntu. It would write over the boot section and partition and wound up just booting ubuntu only. I noticed the windows partition's where still there. So... after looking around I found Boot Repair. Download it. It will install into ubuntu as well as burn a cd. I did both. Ran Boot Repair and now have a dual boot drive back. Not done yet, here's the problem. Clonezilla keeps overwriting the partion's I've set up. I copied the 300gb's from the old drive and installed that into the 1.7tb partition I set up. Is there a way to expand the partition colonezilla setup inside the newer one. Gpartion and disk managament will show the 1.7tb and the one clonezilla did inside, but won't let me modify It to use the whole area for ubuntu.

I guess in short. Is there software that would do the same for migrating your system to a newer one and still keep all the hard work you did to setup just the way you like it?:confused:

---

### Post by cptrohn on 2011-12-15
I've never had a problem with moving a HD with Ubuntu on it from 1 machine to the other... (have done it quite a few times actually)  Always ran without a hitch...

The Windows partition may be a different story, For Windows activation keys windows will record certain hardware from the machine that the license is used on and this is reported back to MS to discourage piracy.

As far cloning the HD I always have used Clonezilla for both MS and Windows partitions and have never had a problem with the image from either (clonezilla is available at sourceforge)

Creating images is usually done for the same hardware... Say like a mass deployment of machines that have the exact same specs.. in the case of a MS deployment all the machines would have the same specs you would either push or pull the image off of the network and then use sysprep to set it up for each individual host.

Your best bet here might be to reformat the MS partition as a fresh install and see if the activation key will get past MS that way, and if not call them and see if it will activate that way.

But neither here nor there, I don't think that a cloned partition of XP will run on a system with different hardware than what was activated.

---

