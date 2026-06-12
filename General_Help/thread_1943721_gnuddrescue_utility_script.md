---
title: "gnuddrescue utility script"
date: 2012-03-20
forum: General Help
---

### Post by maximus57 on 2012-03-20
Hopefully this is a good place to post this. I am working on a ddrescue utility script. My end goal was for it to be a menu driven frontend for ddrescue. However, right now it is a functional script that will take a ddrescue log and find all files on the entire drive that are corrupt, and I think that is all I will end up making it. It currently does pretty much what I want it to do, but I may make updates to fix bugs or tweak it. Read the text at the beginning of the file (or use the help function) for dependencies and info. I will update this periodically as I make new versions. Enjoy.

Features:
    Finds the files related to bad sectors
    Uses the logfile from gnuddrescue
    Can also use a file with a sector list    
    Works on a whole drive or single partition
    Works on a target device or image file
    Works on NTFS, EXT2/3/4, FAT16/32, and HFS+ partitions
Works on DOS, GPT, and APT partitioned drives
    Should be faster than other methods (md5sum and grep) in most cases
    Does not (knowingly) write to or alter the target
    File system of target does not have to be mounted
Uses command line arguments

Changelog:
version 1.3
    * Initial release

version 1.4
    * Added MAN page
        + Made improvements to --help output
    * Added support for HFS+ file system
    * Added support for GPT and APT partition tables
    * Improved some of the code
        + Improved how it handles loop devices
        + Improved handling of FAT partitions
        + Changed names of temp files so less likely to be existing file
        + Target, logfile, and output file names can now contain spaces
        + Added option to change sector size
        + Added option to include more info in long results
        + Changed command line arguments
    * Fixed bug so Linux partitions get correct block size
    * Major code reconstruction to make it more modular


It is now hosted in a PPA, here is the link:
[https://launchpad.net/~scott-dwyer/+archive/ddrutility]("https://launchpad.net/%7Escott-dwyer/+archive/ddrutility")

To install this on Ubuntu 9.10 and newer from the PPA:
sudo add-apt-repository ppa:scott-dwyer/ddrutility
sudo apt-get update
sudo apt-get install ddrutility

Version 1.3 is on Ubuntu Rescue Remix 12.04. To use the latest version with a live CD you will have to download the .sh file and put it on another media such a a USB flash drive and run it from there.

Download links for both .sh and .deb files

---

### Post by maximus57 on 2012-03-24
Here are previous versions, if the need should arise. 

Note that both 0.12b and 1.3 have a bug that Linux partitions only work properly if the block size of the filesystem is 4096.

---

### Post by bakegoodz on 2012-03-28
Awesome to find someone interested in what I've been working on. Check out my ddrescue front end at triagelinux.com

Script files are here
[http://triagelinux.com/downloads/scripts.zip](http://triagelinux.com/downloads/scripts.zip)

---

### Post by maximus57 on 2012-03-31
> **bakegoodz said:**
> Awesome to find someone interested in what I've been working on. Check out my ddrescue front end at triagelinux.com

Script files are here
[http://triagelinux.com/downloads/scripts.zip](http://triagelinux.com/downloads/scripts.zip)

Cool, thanks for the link to the scripts. If I do end up going farther with what I have, I may use some of your ideas in my script, hope you don't mind. If I do I will give credit where credit is due.

Edit: I just saw your reply on the ddrescue bugreport. If you use my script in your frontend, maybe I won't have to make one :)

---

### Post by maximus57 on 2012-03-31
My script is being considered to be put on the next version of Ubuntu Rescue Remix. But I need to turn it into a Debian package. Can someone help point me in the right direction for that?

Also, I am interested in anyone testing my script. I have put it through many tests, but the outside world needs to test it so I can get some feedback.

---

### Post by bakegoodz on 2012-04-04
Here is basics of deb files. A simple deb file is just a compressed folder with a yourproject/DEBIAN/control text file giving the package information and a binary in yourproject/usr/bin or where you want the files to end up. Other library files etc can be added in their appropriate relative path folders.
You compress up the folder into a deb file with 'dpkg -b' command
More information here: [http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/How-to-make-deb-packages/](http://www.linuxfordevices.com/c/a/Linux-For-Devices-Articles/How-to-make-deb-packages/)

Also you can easily make deb files out of source packages that you "make" with checkinstall
[http://www.falkotimme.com/howtos/checkinstall/](http://www.falkotimme.com/howtos/checkinstall/)

---

### Post by maximus57 on 2012-04-05
Ok, I have made a simple Debian control file and then made a .deb file. It would install on the system it was created on. But it won't install on a different system (fresh install of Ubuntu). By not install I mean when it opens with the Ubuntu software center, the install button cannot be clicked. No other messages are present. I think I am missing something.

---

### Post by bakegoodz on 2012-04-07
hum . . .post the deb file and I'll look at it

---

### Post by maximus57 on 2012-04-07
I think I found the issue that was preventing Ubuntu Software Center from installing my deb package. It seems that the software center must have an internet connection before it will install anything, even if it is local. I was trying it offline with no updates. I put it online and it installed (after a lengthy online negotiation of some sort). But dpkg -i will install it just fine, even with no internet connection.

I am going to make a few tweaks to my script before posting as a deb file. Mostly I want it to be able to inform the user if certain requirements are not met and which functions will not work because of that. Plus I am still wrestling around with a permanent name to call it.

And I still am not sure if that will be enough for it to end up on Ubuntu Rescue Remix. I might need to get it into a repository (even a personal one), and there might be more requirements from what I have read. It almost seems to me that the easy part was writing the script...

---

### Post by maximus57 on 2012-04-10
Update: Moved file to first post

Here is my first attempt at a .deb file.
Updated: made the owner root before creating package.

---

### Post by bakegoodz on 2012-04-10
It installs fine with dpkg. Software center complains because the ddrutility file is not owned by root. Its owned buy uid 1000 which is typically but not always the operator's user. The other files in /usr/local/bin/ are set to rwxr-xr-x too. So I would do a ```
sudo chown root:root ddrutility
``` and ```
sudo chmod 755 ddrutility
``` too

---

### Post by maximus57 on 2012-04-10
> **bakegoodz said:**
> It installs fine with dpkg. Software center complains because the ddrutility file is not owned by root. Its owned buy uid 1000 which is typically but not always the operator's user. The other files in /usr/local/bin/ are set to rwxr-xr-x too. 

I wondered about that. So now I ran chown and chmod recursively on the entire source folder before building the package. It still doesn't install with the software center not being online. It seems to me I have had similar problem in the past with packages I have downloaded. Like the software center feels the need to go online and (try to) check the package out before it will let you install it that way.

I updated the download in my previous post to reflect the latest changes. Maybe I still didn't do something right.

---

### Post by az on 2012-04-26
Ddrutility is included in the 12/04 version of Ubuntu-Rescue-Remix.

[http://ubuntu-rescue-remix.org/Version12-04](http://ubuntu-rescue-remix.org/Version12-04)

Thanks, Scott for rolling up your sleeves and packaging it in a PPA at the last minute!

"Ubuntu-Rescue-Remix features a full command-line environment with the newest versions of the most powerful free/libre open-source data recovery software including GNU ddrescue, Photorec, The Sleuth Kit, Gnu-fdisk and Clamav.

This release features ddrutility, a new tool written by Scott Dwyer to identify files affected by unrecoverable blocks on a disk image."


Anyone is encouraged to expand the Rescue Remix's capabilities and features, and join in its development. Any and all help is welcome!

Thanks!

Andrew

---

### Post by maximus57 on 2012-04-28
I am very happy that my program has made it onto the latest release of Ubuntu Rescue Remix! I never quite expected something like that would happen when I wrote it.

I quite honestly only have about 2 weeks into the writing of the core of the program, including research and much tedious testing. And then almost a month trying to figure out how to package it and doing a few tweaks to make it more presentable, trying to meet the deadline. So this program is almost a rough draft, considering that the whole thing was a learning experience. That and I also never got anyone else to test it and give feedback.

Now that I can relax some, I will be working more slowly on improving it and adding features. I rushed to get it out, but now I will be taking my time on it. I know there is not a big demand for what I created, but I am hoping that I will be able to get more feedback in time.

Next goals: Support for HFS/HFS+ filesystems, restructure some of the code, and make a MAN page.

---

### Post by maximus57 on 2012-05-11
Version 1.4 is released. New features include HFS+ support and the ability to change sector size.

Note that I do not own or have access to a Mac, so HFS+ support was tested using gparted to partition a drive, and a trial version of TransMac from a Windows computer to write data to it.

Also note that this has only been tested on drives with 512 byte sectors, as I don't have any drives with a different sector size.

Enjoy!

---

### Post by htbw on 2012-06-18
being an alarm guy, this is all french to me... and I don't speak french. :)
Basically, my system has been having problems for awhile. The screen would suddenly freeze then some random message about battery or driver utility would pop up. When I tried to re-boot it failed and came up with some system halted message. (Yes, I know not very specific) Usually I could re-boot if I let the system sit powered down for awhile or was persistant enough.

Now it seems unresponsive and I can only boot via the live disk.

When I go to the harddrive it shows a folder "system volume information"
inside that I have "MountPointManagerRemoteDatabase" and "Tracking.log"
mount point opens up as a blank page with a flashing curser as if I can enter something, whereas when I try to open tracking with a text editor it errors out saying it cannot read it using unicode. I tried the other two options and no go.

again, sorry for being such a newb, but the wife is bitching me out for installating Ubuntu because some dork *** told her it was not for home users. Now I am up the creek because some of her docs were lost. Luckily I did use UbuntuOne for most of them, but these were torrent downloads and they did not go into the backed up directory as they were usually moved to another PC for viewing. (useless info that may be of help)

Cheers

Heinz

---

### Post by maximus57 on 2012-08-09
Awhile back I had an email conversation with someone that had some suggestions and comments about ddrescue. Some of those ideas made it into this next release, so I figured it would be nice to post the conversation so others can see the thought process. It is kind of long, so I am putting it in a code box. You might have to select all in the code box, and then paste into your favorite text editor with word wrap turned on to be able to read it. Conversations are separated by long =======. Sorry I didn't show who sent what message, but I think you can figure it out...


```

========================================
Scott,

There is a typo in the ddrutility 1.4 bash script reference to ddrescuelog, missing last letter:

        (which ddrescuelo)

However, in the context of ub-r-r-12.04, it is somewhat moot since ddrescuelog seems to not be present in this distro?!

Thanks much for your work on this vital utility. It is a tough challenge, because every user's situation will be different -- both the tech issues, and the skill level; many users will be desperate but uncomfortable with the Linux command line...

ub-r-r-12.04 seems a far from ideal rescue LiveCD, but I was eventually forced to give it a try, partly because it was the only distro including your new tool.

I am struggling to rescue a failing 40GB WinXP NTFS hard drive.  Although I was able to ddrescue all but half a megabyte, and the NTFS structure seems mostly intact, things seem to still be messed up enough that I can't get the partition to mount, and I have not found any tools that can give me access to the as-is file structure -- just unstructured access like PhotoRec, and I am not ready to let go of hope of getting the file structure back.

Your tool quite confused me, when it ran but sort of did nothing.  So, I have been studying the internals, and learned a lot, though painfully/slowly...

I was quite confused when my image was described as a "whole XXX disk". This usage is clear within your script: "whole drive or single partition". But the use of the word "whole" by itself made me guess that the script thought I was supplying a non-partitioned data structure! I suggest changing the msgs the script generates, replacing "whole" with something along the lines of "whole multi-partiton" (or just "multi-partiton").

In my case, the script sees the partitons in my image, knows there is one labelled NTFS -- and then fails to process it, since it is corrupted. But what it says to the user is just that it can't recognize the partition type, as it goes through null motions. It would be good if function findpartitiontype specifically said that fsstat is what "Cannot determine partition type", and if the program more explicitly handled this condition.

In Main, after calling findpartitiontype, the returned valued is processed by a sequence of independent if-thens. Maybe more of a case structure that picks just one, and explicitly handles the none-of-above case?

Above that is the main gfdisk call. I'd generally recommend "cat tempddrfdisk" be inserted right after that, to show the user this key partition data.

When the script leaves the user puzzled, maybe the MOREINFO flag is what they need; I haven't used it enough to say. But I am wondering if studying the various temp**** files would be generally helpful. Maybe a flag for this, or a pause at the end before deleting them, so that the user could CTRL-C out and study them?

After weeks of this struggle, I still can't tell if I'll get any useful recovered data.  I just have to pretend I am learning useful things in any event.

-k/kethd
===

echo "ddrutility 1.4
Report bugs to scott.dwyer@yahoo.com
ddrutility home page: http://ubuntuforums.org/showthread.php?t=1943721

    ## get all bad and unread sectors from ddrescue log
    ## use ddrescuelog if available (more reliable)
    ## else parse logfile ourself
    DDRESCUELOGCHECK=$(which ddrescuelo)

========================================
Finally, some actual feedback from someone! And very informative. I greatly appreciate it.

I just thought I would give a quick reply for now, since it may take me a few days to get around to looking into all of it in any detail. All are very valid points. Luckily the bug doesn't harm the function as it will just always use the built in log parser, which as far as I can tell actually does the same thing as the ddrescuelog function.

I will reply with a more detailed email in the future when I have more spare time.

Scott 

========================================
I just had a couple quick thoughts about your situation.

First you might want to make a copy of your recovery to work with, a copy you can manipulate with different tools. It is always a good idea to have an original copy to go back to and another one you can play around with (and never mount, write to, or alter the original until you are sure you have recovered all possible data, just make another copy to work with). I say this because you may have to mount it on a windows computer and let windows try to repair it, if you haven't tried that already. If you are working with an image file you can use OFSmount in windows. I think I remember having luck with it by adding .dd to the end of the filename (image.dd). IF windows can repair it (or do what it thinks is repairing it), you might be able to run ddrutility on the repaired copy and get results, although I couldn't guarantee accurate results after windows touched it.

Also you might want to try my older version of ddrutilty version 0.12b. You have to edit your settings manually in the script before running it (no command line options). It uses fdisk to find the partition type. So if it shows up in fdisk as a ntfs partition it will try to process it. Then it is up to ntfscluster to decide if it can read the filesystem or not on a per sector basis. By the sound of it, it would probably still fail as your file system seems messed up.

Scott

========================================
Good to hear from you -- we have a lot to talk about here!

My resources are not super, but adequate, since this problem HDD is "only" 40GB. I am able to store copies (nice 2TB external drives). One of my limitations is that mostly I am at USB2.0, and generally get about 1GB/min copy throughput speeds, so the time factor restrains me... I have been making some late-night Linux CLI mistakes (copying in the wrong direction etc) and dealing with a variety of random hardware issues, so having a somewhat cautious sequence of stored snapshots of work progress has been essential.

It took about 24hrs+ to get a "finished" ddrescue result, with only about 500KB bad, and about 80 hunks. I restored this (after zero-filling the bad spots) to an HDD identical to the original failing one. (I ran into weird problems putting it on an 80GB drive, and had to learn about HPA removal to get the "same" model drive to be full sized -- every step of this weeks-long process has been full of such extraneous obstacles.)

I have a hacker LiveCD with a collection of old Win RE/PE systems. I was able to run ~2003 CHKDSK, but unable to save the msg output; it seemed to make about a thousand changes in the NTFS, which of course freaks me out; I have no idea how much it did to what, or if it moved things around so that ddrutility analysis will be invalid... (Is there a legit public version of CHKDSK on floppy or CD.iso?) (I don't currently have ready access to a good working lab Win NTFS system to add the problem hard drive to for processing.)

Thanks for the tip about using OFSmount in Windows to work with the image file -- hope to learn more about that if I have a future need.  I assume I should be doing a lot of this work in some kinds of virtual machines/emulators, but I am not current with that tech, and it seems like way too much to try to learn right now just to get this task done.

I did hack your ddru 1.4 script, to force it to think all partitions are NTFS. That just lead to the partition processing blowing up with lots of confusing msgs about NTFS being corrupt.

It is very, very hard to work with corrupt devices, in the real world. Almost all modern OSes, even the rescue/forensic LiveCDs, do all sorts of default unsuppressible undesireable interactions with the problem drive at both the hardware and contents levels during the boot process. The corrupt NTFS often delays or crashes the boot process.

This morning, I was finally able to really run your script against my "fixed" replica-copy HDD.

For the Greater Good, we should be having this dialog online for posterity etc? I'll try to get a launchpad/ub ID etc and move over there, but that is just another complication that I have not gotten around to yet... I wanted to give you my feedback from really running your script this am, before my life moves on to other things...

I started by running the standard ub-r-remix12.04 ddru-1.3. It started working away, showing line after line of sector numbers, but no results. It was working hard, grinding away audibly, taking about 3 sec per sector. Since I have a list of about a thousand sectors, this was going to take about an hour!

This is a definite issue with your script. Many users are going to have much larger data sets than mine, with much more than my measily 500KB of bad spots. It is hard to imagine why 3 sec of HDD head motion is required to follow out the references to one bad spot. But regardless, users need more real-time output. We need to see some real-time meaningful results. If it is going to take one hour or many hours, that could be OK, but we need to know that something useful is being done. Since I do have some understanding of the script, it was a simple matter to CTRL-C and browse the temp files. I found line after line of:
* Inode 2 /$LogFile/$DATA

And the four-line version:
Device Sector 6230552
Partition Sector 6230489
Searching for sector 6230489
Inode 2 /$LogFile/$DATA

Not very thrilling or helpful, but the first hint of actual bad-spot mapping into the file structure that I have achieved in this whole process. (Thank you!)

I suggest changing your script to produce one line per sector user msg output in real time:
* Searching for sector devsec#/partsec# Inode # /path/file

I concluded from this experience that a faster browse/skim mode is also needed.

Next, I tried ddru 1.4 (downloaded from the launchpad repository). It was a simliar experience, running at about 4 sec per sector-output line. The same suggestions as above apply.

Next, I hacked the script, to produce a quick-skim version. This is a very easy mod. In function processlogfile, comment out this line:
#   while [ $COUNT -gt 0  ]; do
and the "done" line four lines later. Now it just processes the first bad sector in each hunk, so in my case it runs over ten times faster. It finished in 7.6min, and produced a nice summary output at the end. This is my first truly interesting and useful output. But I'd be happier if when it rolls up a bunch of bad sectors into one summary line about Inode/filename, if the line was prefaced with a bad-sector-count for that file.

ddrutility output file - files that have bad sectors
.................................................................
.................................................................
Partition /dev/sda1 type NTFS is found to be ntfs
Inode 0 /$MFT/$DATA
Inode 10406 /WINDOWS/system32/drivers/pciide.sys/$DATA
Inode 10545 /Documents and Settings/user/Cookies/$INDEX_ALLOCATION($I30)
Inode 2 /$LogFile/$DATA
Inode 41413 /Documents and Settings/user/Application Data/Thunderbird/Profiles/1wsh4tk2.default/Mail/smtp.emailsrvr.com/Drafts/$DATA
Inode 43553 /Documents and Settings/user/Application Data/Thunderbird/Profiles/1wsh4tk2.default/Mail/smtp.emailsrvr.com/Sent/$DATA
Inode 50406 /WINDOWS/system32/speedfan.sys/$DATA
Inode 63395 /WINDOWS/system32/drivers/volsnap.sys/$DATA
Inode 63445 /WINDOWS/system32/drivers/partmgr.sys/$DATA
Inode 867 /Documents and Settings/user/Application Data/Thunderbird/Profiles/1wsh4tk2.default/Mail/smtp.emailsrvr.com/Trash/$DATA

(Proof-reading this later, I realize we really want to see a pretty GUI map of the bad sectors combined with a map of the files that they are in... and lacking that, a simple summary along the lines of: sectors aaa-bbb bad, contained within file GHJK which runs from xxxx-yyyy.)

Also, I'd like to have a count of the number of null-match bad spots. Ideally, these would be of no concern, references to unused blocks. But since my file structure is corrupt and untrustworthy, these are my worst nightmares.

Some general remarks on the script user interface. I invoked it by mistake with too few parameters. It just sat there doing nothing. I guess maybe it was waiting for console input to take the place of a missing parameter data stream?  If it is easy, maybe there could be more error checking of the invocation line? Also, I'd like to see the starting and ending date/time displayed both on console output and in the report files.

And the script version number. Invoking ddru bare gives a list of options. Please include the actual version number there, by default. And the version number in the report files.

So, then I tried the skim version with the MOREINFO flag. It started OK, but was very quickly grinding away, working hard, with no explanation or visible output. CTRL-C and browsing the temp files showed that it was walking the whole file tree! It was already about 6MB, so it was pretty efficient in the time domain. This is certainly a potentially useful/interesting thing to do, but the user needs to be clearly told that is what is happening when it starts this phase. Maybe MOREINFO needs more gradations? Your file system would have to be very small/simple for this to ever be appropriate to generate without very explicit desire/choice.

On the other hand, this sort of information:

/dev/sda1
########## fsstat output ##########
FILE SYSTEM INFORMATION
--------------------------------------------
File System Type: NTFS
Volume Serial Number: 9AC8060DC805E879
OEM Name: NTFS
Version: Windows XP

METADATA INFORMATION
--------------------------------------------
First Cluster of MFT: 786432
First Cluster of MFT Mirror: 5017296
Size of MFT Entries: 1024 bytes
Size of Index Records: 4096 bytes
Range: 0 - 112336
Root Directory: 5

CONTENT INFORMATION
--------------------------------------------
Sector Size: 512
Cluster Size: 4096
Total Cluster Range: 0 - 10034591
Total Sector Range: 0 - 80276740

is so essential/interesting/core that I think it should always be generated, at least in resultslong.

That was the end of my explorations of MOREINFO; I'd have to suppress the tree-walking phase to find out what else it might offer.

At this point, I was finally ready to run the full 1.4 script, and go do something else while it completed, in apparently somewhat over an hour. The most interesting thing about this is that the final useful output file list was exactly the same as from the quick-skim version! This is not a big surprise, but very relevant.

I suggest that by default the program first skim-process the minus hunks, just the first sector in each contig run. Then the same for the other non-plus hunks. Then do the full current standard processing. With some flags to enable/disable the full sector-list processing?

But we also have to ponder why the script is so time inefficient. If it is the fault of the external programs being used, and we have no ready fixes for that, we are faced with the basic dumbness of the current approach. A bunch of bad runs of various lengths is turned into a list of individual sectors which are processed singly (and then the results recombined)...

Well, before I continue that thought, I guess the place to start is that we have 512B sectors, but NTFS seems to use 4096B clusters as the allocation unit? So, we are losing a time factor of eight, by not avoiding re-mapping each sector within a cluster?

Anyway, I was going to say, once we look up a bad sector, and get the Inode etc (whatever that is) -- can't we now look up the Inode/filename, find out a range of sectors, and just speed through processing the following sector numbers, until we get to a sector that is out-of-range and have to do another real sector>filename map. This will be a substantial script programming challenge, but such a vast improvement in efficiency that it seems worth doing. (Just doing the 8x sector-cluster trick might be easier, and a big step forward, but might be more NTFS-specific. Doing the general case would automatically handle the 8x aspect too?)

Well, I am kind of running down, after going on at such length -- but I guess I'll throw in a couple more general thoughts, while I am here...

The format of ddresuce logfiles is wonderfully simple, as it should be, but quite unhelpful to human browsers, even with a comfort level reading hex numbers. There could be fancy GUI tools to graph the data to give the user a sense of how many bad spots there where, what progress was being made, etc. But since we are mostly stuck in the CLI space for now, it seems like there could be a pretty simple set of scripts that produced summaries and char-mode graphs of logfiles, that would be of general use.

Also, I am left very curious/nervous about all my bad spots. Isn't there some way to do a "READ LONG" and get the sector bits, some corrupt version, that could be browsed? Regardless, it seems like it would be pretty simple to have a tool to browse the sectors immediately before and after unreadable sectors (and especially any readable sectors in-between). The simple version would just facilitate looking at the hex/ascii of the adjoining readable sectors. A fancy version would also make filename mapping info available.

And now, I should try to catch some of this nice sunny day.

-k / kethd

PS: Those of us who know computers understand that any "simple" utility like ddru can only handle bad files; bad structure info (dir/indexes etc) make things potentially infinitely complex, and beyond the capabilities of the tools we have now. But many users, desperate to recover their data, will not come with this understanding, so the associated docs/discussions need to repeatedly acknowledge this fundamental obstacle.

PPS: To methodically approach rescuing hard drives, one needs an experiemental library of various problem hard drives. I have an absurd collection of drives (well over a hundred), but I was forced by space constraints to downsize a while back, and discarded the bad ones, so when I needed now to practice bad-drive processing I had a devil of a time finding appropriate experimental subjects. I was almost driven to try out the hdparm features for making bad spots!  I suspect one might readily get folk to give/ship one an "interesting" variety of failing drives, if you had nothing better to do with your life...

======================================
Wow, you have given me much to think about. I will look into everything you have pointed out. But I would like to make a few points myself...

1) The weather is getting nice, and the fish are biting. So my work on this project is not at the highest priority level right now. Hope you and everyone else will understand that.

2) I am really not a programmer. This is more or less my first fairly complex program, and totally my first linux bash script beyond the simple basics. The whole thing has been a learning experience. But I always like learning.

3) I actually DON'T currently have any bad hard drives to test with (they got discarded). I am using MHDD to make bad sectors on an old 20GB hard drive for testing. This method is good for testing accuracy, but maybe not so good for the real world.

4) Testing for an application like this is slow and painful even in ideal controlled conditions, and testing different scenarios is even more difficult. So I really do appreciate all your comments, suggestions and experiences, whether I can get to them or not.

5) Yes, this conversation should end up online somehow. I don't know about launchpad, but I could put the whole thing in a post on the ubuntu forum (what I call the home page for ddrutility).

Scott 

======================================
At 01:30 AM 5/20/12 , Scott Dwyer wrote:
> Wow, you have given me much to think about. I will look into everything you have pointed out. But I would like to make a few points myself...
>
> 1) The weather is getting nice, and the fish are biting. So my work on this project is not at the highest priority level right now. Hope you and everyone else will understand that.

Yes, please do put real life first! I think your work here has a good chance of being the foundation for a core important utility in the Linux world for decades to come. It could have been done any time over the last 10-30 years, but it wasn't -- until you came along, at just the right time for my current needs/interests.  How it evolves over the next years is much more important than how fast it evolves over the next days/weeks.

> 2) I am really not a programmer. This is more or less my first fairly complex program, and totally my first linux bash script beyond the simple basics. The whole thing has been a learning experience. But I always like learning.

Good to know -- makes me more impressed with your script -- quite clean and readable!  I started as a programmer in the 1960's. Haven't done too much programming since the 1980's. I've been experimenting with Linux for the last decade, but mostly just LiveCD/Linux/GUI. Have not been able to force myself to commit to Linux and the non-GUI aspects, as much as I hoped to.

So, I had a devil of a time just executing any version of your script other than the 1.3 built in to ub-rr12.04. A midnight session of absurd struggle with Linux security "features", execute permission bits, etc. Finally went to bed in defeat. Next day, finally found that I could bypass  all that nonsense, invoke bash explicitly.  I'd suggest you add tips about this to the top of your nice help text, something along the lines of:
# sudo bash ddrutility image logfile options

Once I conquered that basic hurdle, it was easy to use nano editor to make changes. And use the bash -xv flags to try to follow script execution. But I never figured out how to get that step-trace output into a file. Was stuck with hoary old CTRL-S/Q from the dawn of computers to pause the too-fast output. I cannot fathom how bash can be so dumb as to not have any single-step debugging features.

> 3) I actually DON'T currently have any bad hard drives to test with (they got discarded). I am using MHDD to make bad sectors on an old 20GB hard drive for testing. This method is good for testing accuracy, but maybe not so good for the real world.

(When discarding hard drives, you might offer them on craigslist: the internal neodymium magnets are of interest to experimenters.)

(My absurd inventory of HDDs is mostly <1GB, down to around 100MB. Crazy, but for some experiments smaller could be better/quicker?)

To the extent you are willing to ponder with me the larger context of rescueing failing hard drive info, not just how to process ddrescue output, the hardware aspects of problem HDDs are critical. We need tools much better than current ubuntu-rescue-remix-12.04 for a context, that can boot up without getting bogged down by the failing HDD.  And we ultimately need much smarter tools than ddrescue, that understand the file system from the start, and focus on reading the relevant/important info rather than blindly torturing the failing hardware trying to recover unimportant or irrelevant data.

> 4) Testing for an application like this is slow and painful even in ideal controlled conditions, and testing different scenarios is even more difficult. So I really do appreciate all your comments, suggestions and experiences, whether I can get to them or not.

Definitely, you need some test systems in a corner that can run for days without being in the way. Sadly, I don't have that at the moment -- mostly because my piles of junk tech have expanded to fill all available space, leaving very little space to actually work...

> 5) Yes, this conversation should end up online somehow. I don't know about launchpad, but I could put the whole thing in a post on the ubuntu forum (what I call the home page for ddrutility).

The reason I mentioned launchpad is, when I stumbled on your ub forum post, and then the launchpad repository, I first tried to get your updated scripts from the forum, but was blocked from downloading as a non-member. I looked into registering, but that is a major obstacle for us careful-methodical folk, when you aren't sure you'll be using the forum much in the future. I noticed that lanuchpad was sort of separate, but that a launchpad ID (whatever that is) was supposed to get you in also to the ub forum, and other places, so I figured that's what I should do. But then, I was able to get your script from launchpad (why does it seem to list the same thing about six times, for each different ub distro?) -- so the whole matter faded for the time being...

In any event, feel free to do whatever you think is appropriate with our dialog. If you have the energy for reposting to that or any forum etc, please do. My current vision is that some of this belongs in the thread you started, and some of my musings about the bigger "how to rescue failing hard drives" issue belong in some other new thread somewhere (where?).

(I am not much into "ownership", of ideas etc, just trying to be helpful, creative, contributing etc -- you are free to do whatever with any of this that is useful to you, acknowledged or not -- but I am rather into "privacy", particularly keeping my cyberspace world separate from the real world. This email dialog bridges the two somewhat; I am being "kethd" here, my cyberspace persona, so that you can re-post online pretty freely.)

If you haven't looked at the forensics wiki, they have some great material, about hidden changes to hard drives during boot and auto-probing, auto-swap-mounting, etc.

I messed with endless OS flavors before ending up with ub-r-r. My main alternatives were RIPLinux and grml.

I am assuming that a major way around my hardware complaints is to mount the failing HDD after the rescue system has booted, via a USB adapter. But that approach has it's own issues, and it always frustrates the hell out of me to not be able to get computers to do what I want (in this case, not to be able to boot an OS while completely ignoring the failing hard drive).

> Scott

Looks like another beautiful sunny day!

-k/kethd


========================================
This primary resource about ddrescue fill mode:

http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html#Fill-Mode

Fill mode can also help you to figure out, independently of the file system used, what files are partially or entirely in the bad areas of the disc. Just follow these steps:

1) Copy the damaged drive with ddrescue until finished. Do not use sparse writes. This yields a logfile with only finished (`+') and bad-sector (`-') blocks.

2) Fill the bad-sector blocks of the copied drive or image file with a string not present in any file, for example "DEADBEEF".

3) Mount the copied drive (or the image file, via loopback device).

4) Grep for the fill string in all the files. Those files containing the string reside (at least partially) in damaged disc areas.

5) Unmount the copied drive or image file.

6) Optionally fill the bad-sector blocks of the copied drive or image file with zeros to restore the disc image.
---

seems to me over-simplisticly nutty and dangerously misleading to the vulnerable.  It ignores the crucial distinction between bad spots in data areas and in index structures. You certainly don't want to inject random DEADBEEF nonsense into the index structures!

I have seen no discussion of the safest fill bits before doing CHKDSK on ntfs corrupted system, so I used zeroes. (Maybe all ones would be better?) Of course, what we really need is something CHKDSK-like that will accept our list of known missing data and try to repair corruption accordingly.

Back to the real world. I'd love to be able to examine my files, that ddrutility now tells me contain missing data, in hex/ascii browsing mode, with a way to easily browse the parts immediately adjoining the missing parts.

Until that is available, the challenge is, how to produce the intersection of one or more filenames output from ddrutility, and the badsector list in a logfile, and then use just that limited set for a DEADBEEF sort of safe data-domain fill, and then browse the questionable file. I wish I could figure out how to test those bad spots before filling, to see if they are still zeroes!  It is possible that CHKDSK was able to heal the file contents, using some kind of backup transaction logs?

Anyway, ddrutility could at least help facilitate these kinds of subsequent processing. We are stuck with dealing with both the hex and decimal worlds, so maybe at least reportlong could output both forms of any sector numbers. And maybe v2 could try to put at the end of reportlong a list of all the bad spots grouped by filename, in logfile format, that could be fed back to a ddrescue fill operation targeted at just one file contents.

Although by default ddrutility should certainly never try to read the bad spots, since you have to assume the target is the original failing hardware, you also hope that usually you are working with a completely readable copy. Seems like it might be easy to hack the script to check on the contents of each processed badblock, see if it reads as zero, at least -- might even be of enough general relevance to deserve an option flag in the standard version?

What is the source language of ddrescue? Don't suppose it is just a script... It would be nice to have a version of the fill function that instead of writing does a read-check against what would normally be written. So, fill with WHATEVER, CHKDSK, and then fill-check against WHATEVER, to see which bad spots CHKDSK might have changed.

Might be easy to gut-hack your script down to a derived version that did nothing but check all the bad sectors to see if they read zero...

-k

========================================

I woke up with swirling schemes for simple hacks/utilities to facilitate browsing the edges of rescued rad areas.

As the day wore on, making no actual progress at implementing these fantasies, I started focusing instead on the practical question of, what was the least-effort path to just get immediate access to such results.

Standard ddru 1.4 results.txt is too simple; resultslong is too un-compressed, over a hundred pages of printout. I wasted almost an hour just trying to manually edit out the duplicates within runs before trying to print, gave up -- too much data. So I wrote the simple BASIC program below, which just compresses resultslong into one line per sector (sector#, Inode, path/file) -- this is a vast practical improvement. It also clearly shows the gaps and their sizes. It is now much easier to manually delete the middles of big runs (it would be nice if that feature was automatic), so I did get down to a semi-feasible 26 page printout with a reasonable effort.

Fired up UBCD 5.0.3, chose a sector hex viewer somewhat at random (HDAT2), and was actually able to browse the contexts of my bad sector ranges.

It seems like at least half of my thousand bad sectors are in the MFT -- I am surprised the recovered file system appears so intact and functional! I am trying to keep to my intention to never get sucked in to trying to boot up such an untrustworthy can of worms...

Many of the zero-filled bad sectors, esp in the MFT, seem to have acquired contents as a result of CHKDSK. So, this experience is another vote for general access to a function that conveniently checks the logfile-tagged spots in an image to see which ones are still zero.

-k
===

' resultslong.bas (SmallBASIC FLTK 0.10.6 Windows XP)
' compress ddrutility resultslong output file
' kd 22 may 2012

NEWLINE$=CHR(13)
DOTS=".........."
OPEN "resultslong-wp.txt" FOR INPUT AS #1
OPEN "resultslongone.txt" FOR OUTPUT AS #2
? "STARTING"

WHILE NOT EOF(1) AND (IN$ <> DOTS)
LINEINPUT #1, IN$
PRINT #2, IN$;NEWLINE$
PRINT IN$
WEND

WHILE NOT EOF(1)

LINEINPUT #1, DS$
LINEINPUT #1, NULL$
LINEINPUT #1, NULL$
LINEINPUT #1, INODE$

SPLIT DS$," ",TOK$()
SECT=VAL(TOK$(2))
IF (SECT-OLDSEC)>1
   PRINT #2, NEWLINE$ : PRINT #2, NEWLINE$
   PRINT #2, (SECT-OLDSEC-1);NEWLINE$
   PRINT #2, NEWLINE$ : PRINT #2, NEWLINE$
   PRINT
   PRINT  (SECT-OLDSEC)
   PRINT
  FI

PRINT #2, DS$;"     ";INODE$;NEWLINE$
PRINT     DS$;"     ";INODE$
IF INODE$<>DOTS THEN LINEINPUT #1, NULL$

OLDSEC=SECT

WEND

? "ENDING"
STOP

========================================
I guess I never planned for large amounts of bad sectors, at least not making it easy to sort out. I think I could make one line long results, maybe with the option to sort by sector or by file name (or both if it didn't add too much time). I will try to process the simple parts of your suggestions first, the parts I think I can do fairly easy. I like the idea of a shorter more readable output. Grouping a run is a good idea for sure, but something like that requires a bit more time to work on (at least for me). I quite honestly have not had the time to work on it at all lately. Ubuntu 12.10 will be out in October, and I hoping I can have a much improved version ready for then so it can make its way on that version of rescue remix. But everything takes time...

You have been very helpful giving me ideas and suggestions. I have but one request. If possible can you keep a copy of your image and log around so you can run future versions of ddrutility against it so you could give more feedback at a later date?

As for the MFT being reconstructed... I believe windows keeps a backup copy of the MFT. If the same parts of both are not messed up at the same time, it is supposed to be able to reconstruct it from the two. Being able to check what parts of the original bad sectors are not zero is an interesting idea. I am thinking I will need to incorporate a menu into ddrutility to accommodate all the possible functions. I did want it to be a menu driven frontend when I started, but was too complicated for me at first...

On a side note, I just thought I would mention that when you pointed out the original bug, I realized another bug. I didn't allow for ddrescuelog to process a sector size other than its default of 512. But since ddrescuelog will never run anyway due to the first bug, the point is moot.

And I haven't seen or used BASIC since 1987, on an Apple IIe

========================================
At 12:42 AM 5/23/12 , Scott Dwyer wrote:
> I guess I never planned for large amounts of bad sectors, at least not making it easy to sort out.

Some users will have orders of magnitude more bad sectors and ranges than I do; they will need even more powerful summarize/compress/browse tools. Not too productive to think about those needs, without a real-world example to experience...

>  I think I could make one line long results, maybe with the option to sort by sector or by file name (or both if it didn't add too much time).

The vision  I just woke up with is, transforming the current logfile format:
* START LEN in hex bytes
to:
* START LEN = S+L-1/S+L in hex bytes, followed by the same four numbers in dec sectors

A seperate simple program could do that transformation. But I think it would also be handy for your program to do the same, and interleave those lines in the resultslong output. Combined with your current resultslong in single-line format, would have worked well for me. Adding a sector count for any gap also would be good.

My current experience is that sorting is not too relevant/desireable. Compressing a run of sameness is very relevant. All but one of my logfile badsector lines corresponds to only one inode (in some cases, combined with no-match sectors).

The sorting that results.txt currently displays is peculiar -- sorted by the first digit of the Inode number! This is the least relevant. Original sector order is most natural; a sort by inode should ideally be a numeric sort.

>  I will try to process the simple parts of your suggestions first, the parts I think I can do fairly easy. I like the idea of a shorter more readable output. Grouping a run is a good idea for sure, but something like that requires a bit more time to work on (at least for me). I quite honestly have not had the time to work on it at all lately. Ubuntu 12.10 will be out in October, and I hoping I can have a much improved version ready for then so it can make its way on that version of rescue remix. But everything takes time...
>
> You have been very helpful giving me ideas and suggestions. I have but one request. If possible can you keep a copy of your image and log around so you can run future versions of ddrutility against it so you could give more feedback at a later date?

I'll probably keep almost everything indefinitely; logfile is short, I'll attach it here. I actually have an earlier snapshot, of image and log, with about 1.5MB of bad+unfinished, that might be interesting to play with at some point...

> As for the MFT being reconstructed... I believe windows keeps a backup copy of the MFT. If the same parts of both are not messed up at the same time, it is supposed to be able to reconstruct it from the two. Being able to check what parts of the original bad sectors are not zero is an interesting idea. I am thinking I will need to incorporate a menu into ddrutility to accommodate all the possible functions. I did want it to be a menu driven frontend when I started, but was too complicated for me at first...

There is a $MFTmirror, but it only contains something like "the first 16 records of the MFT"; I am only beginning to understand MFT records... So, not at all a full copy!

A weird experience; I don't understand how the hard drive contents could get so messed up, how the MFT could be such a mess and keep sort of working, or how things could go so wrong so fast, without such total internal hardware failure that there would be much more messed up... My original presenting symptom was no-boot with a message about IO err reading the $MFTmirr. I thought at first that my only problem was, how to get some tool to just ignore the $MFTmirr, use the MFT and give me access to the files. But amazingly, ddrescue seems to have read all of the $MFTmirr OK, but has great problems with the MFT, starting from the very beginning...

It would be wonderful to have a smart tool to facilitate examining the $MFTand $MFTmirr. But I don't think I'll be trying to learn all of that from scratch right now!

For now, I suggest you do offer to check bad sectors for non-zero, but keep it very simple -- a simple option flag to enable, and a simple one-char zero/nonzero flag on all sector-by-sector output lines. (Maybe all-ones is an important alternative to all-zeros, and you could check for the three states in each sector: all zeros, all ones, other.)

> On a side note, I just thought I would mention that when you pointed out the original bug, I realized another bug. I didn't allow for ddrescuelog to process a sector size other than its default of 512. But since ddrescuelog will never run anyway due to the first bug, the point is moot.
>
> And I haven't seen or used BASIC since 1987, on an Apple IIe

I loved the Apple ][plus in the early 1980s. I know I should be doing handy little spiffy things with grep, awk, etc -- but I just can't escape the pull of BASIC convenience, the interactivity of an interpreter. Hope I'll manage to transition to python or ruby or something, but the way everything keeps changing, by the time I think something is the Right Choice, something Newer and Better will always have come along...

-k

========================================

I tried out TestDisk and PhotoRec on my recovered 40GB NTFS. I was not impressed. TestDisk can access/copy deleted NTFS files. But in my case that was a list of about 1000, with no option other than browsing the whole list hunting for "interesting" path/file names. PhotoRec was even less usable. It could scour all the raw bits trying to reconstruct possible file fragments -- but only based on some magic file-type filtering. No ability to selectively recover files based on contents. I would be forced to recover "everything", at least about 10GB, in probably much more than a thousand pieces, and then somehow filter all that with other tools.

But they offer an interesting list of LiveCDs. Which led me to:
===
http://www.caine-live.net/
CAINE (Computer Aided INvestigative Environment) is an Italian GNU/Linux live distribution created as a project of Digital Forensics

1) "rbfstab" is a utility that is activated during boot or when a device is plugged.  It writes read-only entries to /etc/fstab so devices are safely mounted for forensic imaging/examination.  It is self installing with 'rbfstab -i' and can be disabled with 'rbfstab -r'.  It contains many improvements over past rebuildfstab incarnations.  Rebuildfstab is a traditional means for read-only mounting in forensics-orient distributions.
2) "mounter" is a GUI mounting tool that sits in the system tray.  Left clicking the system tray drive icon activates a window where the user can select devices to mount or un-mount.  With rbfstab activated, all devices, except those with volume label "RBFSTAB", are mounted read-only.  Mounting of block devices in Nautilus (file browser) is not possible for a normal user with rbfstab activated making mounter a consistent interface for users.

CASPER PATCH
The patch changes the way how Casper searches for the boot media. By default, Casper will look at hard disk drives, CD/DVD-drives and some other devices while booting the system (during the stage when system tries to find the boot media with correct root file system image on it - because common bootloaders do not pass any data about media used for booting to an operating system in Live CD configurations). Our patch is implemented for CD/DVD versions of CAINE and enables CD/DVD-only checks in Casper. This solves the bug when Casper would select and boot fake root file system images on evidentiary media (hard disk drives, etc). ---
===

It sounds like they are trying to address my LiveCD failing-HDD boot concerns.

I have not had success finding tools that can give me a READ LONG of my bad sectors, the corrupted raw bits. I have dabbled with MHDD.

I like the sound of this:
http://hddguru.com/software/2005.10.02-MHDD/mhdd_manual.en.html
"The main difference: MHDD does not use BIOS functions and interrupts. So, you even do not need to detect your drive in BIOS. You can even turn on your drive after MSDOS boots. MHDD works directly with IDE or Serial ATA controller so it does not care about partitions, file systems, BIOS (motherboard) limitations, etc."

I am confused-curious-and-scared about messing with the IDE drive data/power connections "hot"...

I tried the version included with UBCD 5.0.3. MHDD is pretty quirky, can't tell if it might be abled to do some form of READ LONG.

This is entertaining:
http://blog.atola.com/restoring-factory-hard-drive-capacity/

Under new management?:
http://real-world-systems.com/docs/MHDD_en_manual.html

===

Most fascinating, qubit from 2002 (all following is quoted); these folk are *really* serious about recovering bad hard drives -- too bad their work doesn't seem to have led to any generally available utilities! :

(The whole fascinating qubit thread at http://forums.storagereview.com/index.php/topic/19869-deducing-75gxps-rll-an d-ecc-algorithms/ is worth browsing.)

http://mail.opensolaris.org/pipermail/zfs-discuss/2009-July/029577.html
---
A bad sector specific recovery technique is to instruct the disk to
return raw read data rather than trying to correct it.  The READ LONG
command can do this (though the specs say it only works on 28 bit LBA).
(READ LONG corresponds to writes done with WRITE LONG (28 bit) or WRITE
UNCORRECTABLE EXT (48 bit).  Linux HDPARM uses these write commands when
it is used to create bad sectors with the --make-bad-sector command.
The resulting sectors are low level logically bad where the sector's
data and ECC do not match; they are not physically bad).  With multiple
read attempts, a statistical distribution of the likely 'true' contents
of the sector can be found.  Spinrite claims to do this.  Linux 'HDPARM
--read-sector' can sometimes return data from nominally bad sectors too
but it doesn't have a built in statistical recovery method (a wrapper
script could probably solve that).  I don't know if HDPARM --read sector
uses READ LONG or not.
HDPARM man page: http://linuxreviews.org/man/hdparm/

Good description of IDE commands including READ LONG and WRITE LONG
(specs say they are 28 bit only)
http://www.repairfaq.org/filipg/LINK/F_IDE-tech.html
SCSI versions of READ LONG and WRITE LONG
http://en.wikipedia.org/wiki/SCSI_Read_Commands#Read_Long
http://en.wikipedia.org/wiki/SCSI_Write_Commands#Write_Long

Here is a report by forum member "qubit" modifying his Linux taskfile
driver to use READ LONG for data recovery purposes, and his subsequent
analysis:

http://forums.storagereview.net/index.php?showtopic=5910
http://www.tech-report.com/news_reply.x/3035
http://techreport.com/ja.zz?comments=3035&page=5

------ quote ------
318. Posted at 07:00 am on Jun 6th 2002 by qubit

My DTLA-307075 (75GB 75GXP) went bad 6 months ago. But I didn't write
off the data as being unrecoverable. I used WinHex to make a ghost image
of the drive onto my new larger one, zeroing out the bad sectors in the
target while logging each bad sector. (There were bad sectors in the FAT
so I combined the good parts from FATs 1 and 2.) At this point I had a
working mirror of the drive that went bad, with zeroed-out 512 byte
holes in files where the bad sectors were.

Then I set the 75GXP aside, because I knew it was possible to recover
some of the data *on* the bad sectors, but I didn't have the tools to do
it. So I decided to wait until then to RMA it.

I did write a program to parse the bad sector list along with the
partition's FAT, to create a list of files with bad sectors in them, so
at least I knew which files were effected. There are 8516 bad sectors,
and 722 files effected.

But this week, I got Linux working on my new computer (upgraded not too
long after the 75GXP went bad) and modified the IDE taskfile driver to
allow me to use READ LONG on the bad sectors -- thus allowing me to
salvage data from the bad sectors, while avoiding the nasty
click-click-click and delay of retrying (I can now repeat reads of a bad
sector about twice per second) and I can also get the 40 bytes of ECC
data. Each read of one sector turns up different data, and by comparing
them I can try to divine what the original was. That part I'm still
working on (it'd help a lot to know what encoding method the drive uses
- it's not RLL(2,7), which is the only one I've been able to get the
details on).

But today I did a different kind of analysis, with VERY interesting
results. I wrote a program to convert the list of bad sectors into a
graphics file, using the data on zones and sectors per track found in
IBM's specification. After some time and manipulation, I discovered that
all the bad sectors are in a line going from the outer edge 1/3 of the
way to the inner edge, on one platter surface! It's actually a spiral,
because of the platter rotation. But this explains why all the sectors
went bad at once. One of the heads must have executed a write cycle
while seeking! I could even measure the seek speed from my bad sector
data -- it's 4.475 ms/track! (assuming precisely 7200 rpm) And there are
evenly spaced nodes along the line where larger chunks were corrupted --
starting 300 ms apart, gradually fading to where they actually are
*less* corrupted than the line itself, at 750 ms apart.

I don't know if anyone else will find this interesting, but I found it
fascinating, and it explained a lot. If you'd like to talk to me about
the technical aspects of 75GXP failure, please email me at
quSPAMLESSbitATinorNOSPAMbitDOTcom (remove the chunks of spam, change AT
and DOT to their respective symbols).

For completeness, I should say that I had the drive for a year before it
developed the rash of bad sectors. It\'s made in Hungary, SEP-2000.

I wasn\'t using it too heavily until I got an HDTV card, then I was
recording HDTV onto the drive; this heavy usage might have helped it
along to failure. (2.4 MB/sec sustained writing -- and it was quite
noisy too.)

I updated the drive\'s firmware not too long after it developed the bad
sectors; of course this didn\'t let me read them any better -- I didn\'t
expect it to. I\'m not sure if the firmware update will make the drive
safe to use after a reformat, but I\'ll surely try it once I\'ve
recovered as much of the bad sectors as I can. Even if I still RMA the
drive, I\'d like to know.
------ end quote ------

===

http://forums.storagereview.com/index.php/topic/19869-deducing-75gxps-rll-an d-ecc-algorithms/page__st__20
 Posted 01 June 2005 - 07:53 PM
Truely, fasinating. Forthe life of me I cannot figure out what is so important in the any of the files you are trying to recover that you would want to spend even five minutes recovering the data. It must be the purely intellectual challenge of understanding how the drive operates.

The specifics of IBMs ECC I don't know, but there is sometimes the possibility of using what is called blind ECC correction. Some hdd manufacturers use this, some don't. WD used it in a recent drive I examined. Maxtor has not been using it. I don't know if Seagate or IBM have used it.

In blind ECC correction, the normal ECC correction has failed because more bits were damaged then the ECC was designed to correct. However, if the damaged bits are assumed to be continuous the drive can use that information to nearly double the number of bits that be corrected. The drive assumes it knows which bits are in error then solves the ECC equations to recover the data. It reserves a few of the ECC bits to check if the solution is consistant with those remaining bits. The bits assumed to be in error are moved through the data until a consistant solution is found. The wd drive I played with would take nearly 30 seconds to recover a sector purposly damaged ( using write long) beyond its normal ECC recovery range. Most drives don't use blind ECC because it takes too long.

www.eccpage.com

===

http://webcache.googleusercontent.com/search?q=cache:tGzooI3cfmUJ:http://www .pbase.com/qubit/image/45725145/original%2Bqubit+75GXP&hl=en&gbv=2&gs_l=hp.3 ..0l10.12272890.12275410.0.12276510.5.4.0.0.0.0.1810.3460.4-2j0j1j0j1.4.0... 0.0.OGXe-cuw_64&ct=clnk

75GXP multiple reads of a sector with corrupted sync.png

My data-recovery experiment with the 75GXP has progressed very far. I've reverse engineered its RLL algorithm (it is a simple 32/34 scheme with one parity bit), which means I can match up multiple differently-shifted reads of a sector whose sync mark has been corrupted.

The sector shown here one I am trying to fully recover. It is part of a ZIP file, so recovering it is an all-or-nothing proposition. I'm finding I have to throw every available technique at it: context (there happens to be some degree of order in it, even though it's part of a ZIP), RLL encoding, and ECC. If I can perfectly recover all but 40 of the bytes, then I will be able to apply the recovered ECC to correct the rest of it.

On the left is the RLL-coded version.

In the middle is the PR4-precoded version, corresponding directly to positive and negative magnetic polarity (not reversals).

On the right is what the drive's read head must have seen. Since the drive employs PRML, this is a blurred version of the flux reversals.

(To the left of each version is the correct data, for comparison.)

As you can see, without a proper sync mark, the drive just dives in at a random spot near the beginning of the sector. It takes a while for its sync to stabilize, as you can see by comparing the beginning (top) with what comes later. The single-bit errors (in the precoded version) still occuring after it has stabilized are mostly caused by miscorrected parity (the bits interpreted as parity in shifted reads are in fact data bits, not parity).

The reason there are so few reads matched up in this picture (only 64 of them) is that the drive goes through a grinding, clicking rigamarole trying to read a sector like this, taking an average of 40 seconds just to return a result. Furthermore, most of the time it just returns all zeroes or all ones; only about 1 out of 80 reads returns actual data. And even some of those have very bad sync.

You can also see the gap and sync mark of the following sector from the reads which started late (in a couple of the reads, you can even see the beginning of the next sector). As it turns out, the gap+sync adds up to 552 encoded bits, compared to the 4692 bits taken up by a sector.

P.S. I successfully recovered this sector! I had to call in an extra technique though — tracking backreferences in PKZIP's deflate format pointing to unknown data, filling in the unknowns one by one from context, recompressing the result with the same parameters with which it was originally compressed, and using that to fill in more of the remaining blanks in the original ZIP file so that ECC could be applied. I had wanted the extra technique to instead be modeling the Viterbi decoding of an out-of-phase unstable sync (since that'd be more universal) to create a reverse maximum-likelyhood algorithm, but that will have to wait...


========================================
I have finally had some time to sit down and go through all your suggestions and make a list with replies.


1) Fix the ddrescuelog bug... done, actually removed the use of ddrescuelog since it is leftover from before the built-in log parser was created. And using only the built-in one will give me more control over future changes.

2) Replace "whole XXX disk" with something like "whole XXX partitioned disk"... consider it done.

3) Specifically state that fsstat is what "Cannot determine partition type"... will do, and maybe look for other things that could give better info like that. As for handling it differently, not sure what you mean, if it can't tell the type there isn't much else it can to but move on to the next partition or quit if done. But I am thinking that if fsstat fails then use a backup (my original) method using the gfdisk output to try to find partition type. I do see what you mean about the if-thens, might change to a case statement later.

4) Wondering if studying the various temp**** files would be generally helpful... They are very helpful to me when debugging! Actually I am thinking of having more than the 2 current results files, having output results in different formats that could be useful for different purposes on different levels, including being able to be processed to extract specific data.

5) I suggest changing your script to produce one line per sector user msg output in real time:
* Searching for sector devsec#/partsec# Inode # /path/file ... good idea, will look into that...

6) Next, I hacked the script, to produce a quick-skim version. But I'd be happier if when it rolls up a bunch of bad sectors into one summary line about Inode/filename, if the line was prefaced with a bad-sector-count for that file... I was thinking of trying to add the number of bad sectors for each result in the short results. You think it would be better in one line? That would be better for processing, but not so much for user viewing. As for a quick-skim version, it would be faster, but I would worry that someone could misunderstand the results as they would be incomplete and might miss something important. I will look into the idea though.

7) Maybe MOREINFO needs more gradations?... yeah, it could use something for sure. I might add some of the more important info to one of the ouputs.

8) But we also have to ponder why the script is so time inefficient... While the script isn't as efficient as it could be (using temp files instead of memory for one, if I can ever find a way around that I will), most of time is taken by the 3rd party applications called upon. Some of them can be painfully slow (and NTFS is fast compared to processing a linux filesystem). Only doing one call per cluster/block instead of every sector could definitely speed it up, i will look into that.

9) Once we look up a bad sector, and get the Inode etc (whatever that is) -- can't we now look up the Inode/filename, find out a range of sectors, and just speed through processing the following sector numbers, until we get to a sector that is out-of-range and have to do another real sector>filename map... Yes, that should be possible. However, it is unclear at this time if that would speed it up or slow it down. That would require another call to a possibly slow tool, not to mention more processing in the script. I will look into the possibility later, after working on some of the other stuff.

10) Isn't there some way to do a "READ LONG" and get the sector bits, some corrupt version, that could be browsed, to have a tool to browse the sectors immediately before and after unreadable sectors (and especially any readable sectors in-between)?... Will probably never be a "READ LONG" ability in my script. Maybe a way to browse the sectors before and after could be done.

11) Those of us who know computers understand that any "simple" utility like ddru can only handle bad files; bad structure info (dir/indexes etc) make things potentially infinitely complex, and beyond the capabilities of the tools we have now. But many users, desperate to recover their data, will not come with this understanding, so the associated docs/discussions need to repeatedly acknowledge this fundamental obstacle... Very true. I added something in the help file, and will probably add a little something to the top of the results files. I will also try to add appropriate comments on certain failures if possible.

12) Show what bad sectors are no longer filled with zeros... Not a bad idea, could be very useful. I will look into that for sure.

13) We are stuck with dealing with both the hex and decimal worlds, so maybe at least reportlong could output both forms of any sector numbers... For what purpose would this be? Most all other utilities that I have seen use the decimal form for listing sectors (part of the reason ddrescuelog was created I believe). And the hex in a ddrescue logfile is in bytes, not sectors, so you can't directly feed a hex sector number back into it anyway. I will consider it (would help if I even knew how to do it, it must be simple), but not high on the priority list right now.

14) Although by default ddrutility should certainly never try to read the bad spots, since you have to assume the target is the original failing hardware, you also hope that usually you are working with a completely readable copy... ddrutility does not itself try to read the bad sectors, HOWEVER at least one of the tools (either ifind or ffind) does attempt to read the sector, and it will fail if it cannot read it. This only affects FAT and HFS+ filesystems as NTFS and Linux are processed differently. I thought for sure I had put some info in 1.4 about that, but can't find it now. 

========================================
At 01:48 AM 5/25/12 , Scott Dwyer wrote:
> I have finally had some time to sit down and go through all your suggestions and make a list with replies.
>
> 1) Fix the ddrescuelog bug... done, actually removed the use of ddrescuelog since it is leftover from before the built-in log parser was created. And using only the built-in one will give me more control over future changes.

That sounds reasonable. And I have no experience with ddrescuelog. However... We are trying to evolve a tool ecosystem, based on ddrescue, which already includes ddrescuelog. So, although you may not need it, it is desireable to retain compatibility with it, whatever that means. To be able to accept as input logfile, or ddrescuelog output, or manually edited bad spot lists.

> 2) Replace "whole XXX disk" with something like "whole XXX partitioned disk"... consider it done.
>
> 3) Specifically state that fsstat is what "Cannot determine partition type"... will do, and maybe look for other things that could give better info like that.

I'm just suggesting, maybe state that the partition table claims "ntfs", then say that fsstat is what "Cannot determine partition type", so apparently it is corrupt... -- and state that ddru cannot currently do anything more with the partition.

>  As for handling it differently, not sure what you mean, if it can't tell the type there isn't much else it can to but move on to the next partition or quit if done.

All I mean is, currently you call external functions to get the partition type, then you check for various expected valid types, and process them accordingly -- but if no valid expected type was returned, you just do nothing; it would be better for the code to explicitly catch that case and say something explicitly about no valid partition type -- it is confusing to try to understand the code, and finally realize that the no-good-partiton case just falls through.

>  But I am thinking that if fsstat fails then use a backup (my original) method using the gfdisk output to try to find partition type. I do see what you mean about the if-thens, might change to a case statement later.
>
> 4) Wondering if studying the various temp**** files would be generally helpful... They are very helpful to me when debugging! Actually I am thinking of having more than the 2 current results files, having output results in different formats that could be useful for different purposes on different levels, including being able to be processed to extract specific data.

I agree.

> 5) I suggest changing your script to produce one line per sector user msg output in real time:
> * Searching for sector devsec#/partsec# Inode # /path/file ... good idea, will look into that...
>
> 6) Next, I hacked the script, to produce a quick-skim version. But I'd be happier if when it rolls up a bunch of bad sectors into one summary line about Inode/filename, if the line was prefaced with a bad-sector-count for that file... I was thinking of trying to add the number of bad sectors for each result in the short results. You think it would be better in one line?

Not so important here for it to be just one line -- but possibly significant future advantages, in terms of subsequent processing by grep etc?

Actually, the full version of the inode/filename summary report cannot as a practical matter be just one line per inode, because what the user really needs is a list of all the sector ranges that make up that file, in file-mapped order, and which parts of each of those have bad spots...

> That would be better for processing, but not so much for user viewing. As for a quick-skim version, it would be faster, but I would worry that someone could misunderstand the results as they would be incomplete and might miss something important. I will look into the idea though.

I am not attached to a pure quick-skim mode, but I think it is highly advantageous to almost always quick-skim first, and then be more thorough. Otherwise, the ordinary first time user is very likely to be sitting watching very uninteresting repeated $MFT-type results, and quite possibly abort after a few minutes of that, and never find out that ddru really can come up with meaningful file matches, it you let it run long enough!

> 7) Maybe MOREINFO needs more gradations?... yeah, it could use something for sure. I might add some of the more important info to one of the ouputs.
>
> 8) But we also have to ponder why the script is so time inefficient... While the script isn't as efficient as it could be (using temp files instead of memory for one, if I can ever find a way around that I will), most of time is taken by the 3rd party applications called upon. Some of them can be painfully slow (and NTFS is fast compared to processing a linux filesystem). Only doing one call per cluster/block instead of every sector could definitely speed it up, i will look into that.
>
> 9) Once we look up a bad sector, and get the Inode etc (whatever that is) -- can't we now look up the Inode/filename, find out a range of sectors, and just speed through processing the following sector numbers, until we get to a sector that is out-of-range and have to do another real sector>filename map... Yes, that should be possible. However, it is unclear at this time if that would speed it up or slow it down. That would require another call to a possibly slow tool, not to mention more processing in the script. I will look into the possibility later, after working on some of the other stuff.
>
> 10) Isn't there some way to do a "READ LONG" and get the sector bits, some corrupt version, that could be browsed, to have a tool to browse the sectors immediately before and after unreadable sectors (and especially any readable sectors in-between)?... Will probably never be a "READ LONG" ability in my script. Maybe a way to browse the sectors before and after could be done.
>
> 11) Those of us who know computers understand that any "simple" utility like ddru can only handle bad files; bad structure info (dir/indexes etc) make things potentially infinitely complex, and beyond the capabilities of the tools we have now. But many users, desperate to recover their data, will not come with this understanding, so the associated docs/discussions need to repeatedly acknowledge this fundamental obstacle... Very true. I added something in the help file, and will probably add a little something to the top of the results files. I will also try to add appropriate comments on certain failures if possible.
>
> 12) Show what bad sectors are no longer filled with zeros... Not a bad idea, could be very useful. I will look into that for sure.
>
> 13) We are stuck with dealing with both the hex and decimal worlds, so maybe at least reportlong could output both forms of any sector numbers... For what purpose would this be? Most all other utilities that I have seen use the decimal form for listing sectors (part of the reason ddrescuelog was created I believe). And the hex in a ddrescue logfile is in bytes, not sectors, so you can't directly feed a hex sector number back into it anyway. I will consider it (would help if I even knew how to do it, it must be simple), but not high on the priority list right now.

The goal of the user is to Understand their data corruption. Our goal is to provide tools to facilitate that.  ddrescue gave me logfile output with badspot ranges. But that was pretty useless because I did not know what files the bad spots were in, or almost anything else useful.  You gave me inodes and file names, but disconnected to anything else; and a sector list that was so detailed that meaning was lost. It all added up to a cloud of relevant aspects that did not cohere into any picture.

The most ground truth I can get about my problems is to examine the boundaries of the bad spots with a sector viewer. If I can know the file mappings around those boundaries, that will be very helpful.

I have to use whatever units that various sectors viewers use.  For a very small number of boundaries, I can just do whatever conversions myself.  But for the dozens to thousands of spots I have to deal with, any help with this grunt work becomes very important.

Each range of bad has a start and an end.  Although this is entirely determined by a stated START and LEN in any units, as a convenience each range has five relevant numbers: S-1/S, L, S+L-1/S+L. In other words, before-and-after each boundary, and the length between. And each of those five quantities can be expressed four different ways: hex or dec, bytes or sectors. logfile is already hexbytes, so we are stuck with that. You have chosen to output decsectors, which is fine with me. But I am still stuck with reconciling everything subsequent back to logfile. You can help by quoting the logfile lines interleaved in your detailed sector mapping output, as a grouping header. And in general the more of the five numbers you give me, in both hexbytes and decsectors, the easier it will be for me to carry out whatever subsequent steps I may attempt...

(These differences of one and hex/dec stuff might sound trivial, but during this week plus of struggle with different hard drives, sizes expressed in many different units(dec vs. bin MB/GB!), hidden hard drive areas, the subtle tension between the number of the last sector on the hard drive vs. the total number of sectors -- the confusion and potential for error has been significant.)

> 14) Although by default ddrutility should certainly never try to read the bad spots, since you have to assume the target is the original failing hardware, you also hope that usually you are working with a completely readable copy... ddrutility does not itself try to read the bad sectors, HOWEVER at least one of the tools (either ifind or ffind) does attempt to read the sector, and it will fail if it cannot read it. This only affects FAT and HFS+ filesystems as NTFS and Linux are processed differently. I thought for sure I had put some info in 1.4 about that, but can't find it now.

If there are cases where ddru implicitly does try to read logfile-listed bad spots, however indirectly, it would be very good to try to very explicitly warn the user -- that could be very frustrating, if it was used with the original failing hardware!

-k

==============================
I was learning a little about grep recently... it might be a useful tool for condensing a reportlong list of bad sectors?

If reportlong were reformatted to one line per sector, and those lines contain something distinctive like "Inode" that does not otherwise appear, and something else is inserted between the runs of continguous sectors that map to the same inode (any kind of distinctive break-gap marker, ideally including a count of the number of sectors in the gap)...

grep has a feature that prints the match line and N lines surrounding. And a feature for selecting the not-matching lines instead. If those two features happen to work together the way we need, a simple grep filter might be able to take out the repetitious insides of long runs of sectors that map to the same inode. You could include this info as a tip in your help docs, and/or execute such at the end of a standard ddru run, producing an additional reportlng.txt from reportlong.

-k 

==============================
Actually "sort" is very efficient at this, at least for one liner outputs. It is used already to create the short results. But grep is very useful, used with awk to get specific results. I have not fully explored all of these.

If I make a consistent output with one line per sector, it can be easily manipulated and processed by these tools. Already in my though process. 

==============================
Just something I would like to point out... All this talk we are doing is about NTFS. Ddrutility also has to deal with other filesystem types, and they give different information back so they can't all be processed exactly the same. I have to make all of them give readable results. That complicates things a bit, but nothing that can't be overcome. 

==============================

At 12:51 AM 5/28/12 , Scott Dwyer wrote:
> Just something I would like to point out... All this talk we are doing is about NTFS. Ddrutility also has to deal with other filesystem types, and they give different information back so they can't all be processed exactly the same. I have to make all of them give readable results. That complicates things a bit, but nothing that can't be overcome.

Yes, indeed...  I happened to be trying to format-as-bootable a 2GB flash drive yesterday. The WinXP tool (Rufus) defaulted to FAT and a cluster size of 32KB as I recall; FAT32 defaulted to maybe 4KB, so I chose that... if you could smart-process such varying allocation units, there could be a big potential speed/efficiency gain.

If a term like "Inode" is "wrong" in the context of NTFS, but easy/natural/convenient for ddru to use for uniformity with other filesystem types, I think it's probably better to keep it and just provide a footnote in the help/docs/reports, than to change the report output formats to be more "correct" but less consistent (is my first thought on the subject).

(But, I assume you are facing bigger challenges between filesystem types than just terminology.)

-k

==============================

```

---

### Post by maximus57 on 2012-08-09
Version 1.5 released. Many improvements, the biggest being improved speed and reconstructed output files. Please report any bugs/errors/typos before Ubuntu 12.10 comes out in October so that I can have it fixed to make it on the next release of Ubuntu Rescue Remix.

Changelog
version 1.5
  * No longer uses ddrescuelog
  * Improved error handling
    + Improved some error and warning messages for easier understanding
    + Eliminated some conditions that caused errors
    + Most error messages go to the debug file
  * Uses single base name for output files
    + Reconstructed output files for different uses
  * Improved processing speed
    + Only checks once per cluster/block instead of every sector
  * Shows total run time when done
  * Sector file can contain ranges
  * Added option to produce extra types of output files
  * Fixed command input problem that caused infinite loop
  * Added quick processing option
  * Added special quick ntfs processing option
  * Added version number to output files
  * Many more small changes and improvements too numerous to list

version 1.4
  * Added MAN page
    + Made improvements to --help output
  * Added support for HFS+ file system
  * Added support for GPT and APT partition tables
  * Improved some of the code
    + Improved how it handles loop devices
    + Improved handling of FAT partitions
    + Changed names of temp files so less likely to be existing file
    + Target, logfile, and output file names can now contain spaces
    + Added option to change sector size
    + Added option to include more info in long results
    + Changed command line arguments
  * Fixed bug so Linux partitions get correct block size
  * Major code reconstruction to make it more modular

version 1.3
  * Initial release

Since I am unable to edit any of my earlier posts, the files are attached here.

---

### Post by maximus57 on 2012-09-20
Version 1.6 released.

This version fixes a bug where the logfile is not process correctly (or at all). This bug seems to only be with an incomplete rescue.


version 1.6
  * Fixed bug where ddrescue logfile was not processed

version 1.5
  * No longer uses ddrescuelog
  * Improved error handling
    + Improved some error and warning messages for easier understanding
    + Eliminated some conditions that caused errors
    + Most error messages go to the debug file
  * Uses single base name for output files
    + Reconstructed output files for different uses
  * Improved processing speed
    + Only checks once per cluster/block instead of every sector
  * Shows total run time when done
  * Sector file can contain ranges
  * Added option to produce extra types of output files
  * Fixed command input problem that caused infinite loop
  * Added quick processing option
  * Added special quick ntfs processing option
  * Added version number to output files
  * Many more small changes and improvements too numerous to list

version 1.4
  * Added MAN page
    + Made improvements to --help output
  * Added support for HFS+ file system
  * Added support for GPT and APT partition tables
  * Improved some of the code
    + Improved how it handles loop devices
    + Improved handling of FAT partitions
    + Changed names of temp files so less likely to be existing file
    + Target, logfile, and output file names can now contain spaces
    + Added option to change sector size
    + Added option to include more info in long results
    + Changed command line arguments
  * Fixed bug so Linux partitions get correct block size
  * Major code reconstruction to make it more modular

version 1.3
  * Initial release

---

### Post by maximus57 on 2012-10-21
I have been working on a new utility that could potentially use ddrescue to read only the used portion of a NTFS disk. It works by extracting the bitmap file and then creating a custom logfile to work from. (One of the neat things about this is that it has put me a few steps closer to actually being able to extract individual files from a failing NTFS disk, using raw reads with ddrescue and processing parts of the MFT.) I have a working test version right now that shows the concept can be done. However…

  I have hit a major road block. Actually I have come up to a deep ravine and there is a rope walking bridge, and I need to drive a semi truck across it. So I need to build a new bridge from scratch. Since I am not technically a programmer, I don’t know any good languages and have been doing everything in bash script. But bash is just way too slow to do what I need. I can see I need to teach myself C, which isn’t going to happen overnight.

  Until I can learn C, I could use a bit of help from someone. I have a small bash script that I need converted to something much faster. If that could be done then I could produce a working alpha version for the masses to try out. The script is commented fairly well, and there is a readme file with it.

  Any help is appreciated.

  Thanks

Updated to include a small sample bitmap file that was supposed to be there

---

### Post by shimavak on 2012-10-22
I don't know how clean or quick it is, but I have mocked up a quick program in C.  Very little error handling, okay security if run as an unprivileged user, etc.

Unfortunately, your attachment did not include a bitmap file to test it on, but I did a quick unit test with what you had in the readme.txt and an additional test where the last cluster is used also, to make sure it handled the edge case.

I am emailing you my test cases, the program, and the resulting outputs.

---

### Post by maximus57 on 2012-10-23
> **shimavak said:**
> I don't know how clean or quick it is, but I have mocked up a quick program in C.  Very little error handling, okay security if run as an unprivileged user, etc.

Unfortunately, your attachment did not include a bitmap file to test it on, but I did a quick unit test with what you had in the readme.txt and an additional test where the last cluster is used also, to make sure it handled the edge case.

I am emailing you my test cases, the program, and the resulting outputs.

Oops, I was supposed to include a small sample bitmap file that I was using. I have updated the attachment to include it. But I think you did what I needed already! As a matter of fact I think you fixed a bug that I didn't realize was affecting the length in the last line of output. And so much faster... my bash 3.589s, yours 0.004s. Awesome!

:guitar:

---

### Post by shimavak on 2012-10-23
Glad to help,

I was also thinking of a method which might improve the speed a bit more too, but it would heavily depend on if a typical bitmap file is completely random, or well ordered with large sections either filled or empty.  

The thought is that I am checking each bit, but the comparison could be done 4 times faster if we expect most bytes to either be FF or 00.  We could check the byte before beginning to process it and if it is FF or 00 handle it differently.  However, if it is a nearly random distribution, this will cause a slowdown, as we would have to do two extra comparisons every 8 loops which will nearly always fail.

I tried running it on a urandom generated 32MB bitmap (corresponding to a 1TiB HDD with 4096 byte blocks) and the result only took 1.5 minutes, and most of that was disk writing because it was good random data.  Actually, it may be a problem with large bitmaps which do have random data, because it was compiled without large file support, so my output file dies at 2GB.  I have recompiled with LFS and made some minor bug fixes to handle such large files.

In my test with a large random file, the change doesn't cost any time, and produces identical results, so it may be faster on real files.  Either way, I am sure noone will mind a minute.  I can add a status display if needed also (wouldn't take much effort to dump an update every few cycles).

---

### Post by maximus57 on 2012-10-24
> **shimavak said:**
> Glad to help,

I was also thinking of a method which might improve the speed a bit more too, but it would heavily depend on if a typical bitmap file is completely random, or well ordered with large sections either filled or empty.  

The thought is that I am checking each bit, but the comparison could be done 4 times faster if we expect most bytes to either be FF or 00.  We could check the byte before beginning to process it and if it is FF or 00 handle it differently.  However, if it is a nearly random distribution, this will cause a slowdown, as we would have to do two extra comparisons every 8 loops which will nearly always fail.

I tried running it on a urandom generated 32MB bitmap (corresponding to a 1TiB HDD with 4096 byte blocks) and the result only took 1.5 minutes, and most of that was disk writing because it was good random data.  Actually, it may be a problem with large bitmaps which do have random data, because it was compiled without large file support, so my output file dies at 2GB.  I have recompiled with LFS and made some minor bug fixes to handle such large files.

In my test with a large random file, the change doesn't cost any time, and produces identical results, so it may be faster on real files.  Either way, I am sure noone will mind a minute.  I can add a status display if needed also (wouldn't take much effort to dump an update every few cycles).

It would seem we think alike. I was actually going to do something like  that for my bash script. But when I realized how slow it really was I just decided to stick with the very basics to ask help for. I would think that a real hard drive would have many areas of data in the bitmap that were either FF or 00, especially if there is ever any sort of defrag happening. I will try some speed tests on a real bitmap file at some point in the future when I get some free time. If you find the time to add some sort of status display that lets the user know that something is happening, that would be great. Everyone likes to see progress and not a seemingly locked up program.

This utility is a concept that is based on the idea that many people have large hard drives in their computer of which they are using very little space. It is yet to be seen if this will end up creating very large ddrescue log files that are not efficient to process. I am sure it will not be the best for every scenario, but at what level it can work can only be found by testing in the real world.

---

### Post by shimavak on 2012-10-24
I just ran a couple of tests with real bitmaps from 40GB drives and 250GB drives in various states of fullness and found that my fear was correct.  With all of the extra conditionals to be checked each loop, it takes a statistically significant amount longer to run if we check for 0x00 and 0xFF.

But, I then ran it on a 1TB real partition bitmap and it completed in an average of 0.392 seconds (n=50, 95%CI 0.387s-0.398s) whereas the normal one completed in an average of 1.130 seconds (n=50, 95%CI 1.106s-1.155s).

Either way, for normal systems, it really doesn't seem to matter in any appreciable way, and adding a status indicator would just slow it down (has to do a comparison every loop to see if it is time to display an update) and you wouldn't even get to see it.  The file sizes, by the way, are still quite small for the logs, so it should really be helpful.  In the 1TB drive it ended up only being 3.3MiB, so nothing to worry about.  It occurs to me that there may be a problem with using 32bit integers to store the position, but that won't happen with drives less than 16TiB.

I did run a test switching them to unsigned long long but it does cost in time (0.542s [0.534s-0.552s] and 1.675s [1.662s-1.687s] respectively), so that is something to consider.  Then again, it would not cost anything when compiled for 64 bit...

Anyway, let me know if there are any other things you might like out of it.  Or, of course, you can play around with all of those things yourself.  As I mentioned, all you should need are gcc and libc6-dev packages and compile it with:

```
gcc -D_FILE_OFFSET_BITS=64 -O3 -Wall processbitmap.c -o processbitmap
```

---

### Post by maximus57 on 2012-10-25
I am sorry that I have not had time to do any tests, or anything else for that matter. I have been sick all week, and work decided that since I am sick it is a good time to make me work crazy overtime and try to kill me. If i am lucky I might be able to spend some time on it this Sunday.

I do have one question about compiling. A few days ago I did play around with making and compiling a simple C program. I know what the -Wall switch does, but what is the -D_FILE_OFFSET_BITS=64 -O3

---

### Post by shimavak on 2012-10-25
The -D option [D]efines a macro, in this case _FILE_OFFSET_BITS to be 64.  Macros in C allow one to define bits of branching code that is branched at compile time instead of run time.  In this case the _FILE_OFFSET_BITS lets us use 64 bit file addressing on a 32 bit system, allowing us to make files larger than 2GiB.

The -O3 tells the compiler to be very aggressive in optimizing the code for speed during run.  It makes it very difficult to debug if there are memory leaks, etc. but as this is a very simple program, there will not be any issues like that.  You could compile without -O3 and it would work just fine, but it may make it ever so slightly faster to use the optimization.  It can introduce some really strange errors though, but usually only if you aren't writing standards compliant code in the first place.

A good resource for GCC -O options:
[http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html](http://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html)

---

### Post by maximus57 on 2012-10-26
I just had a few minutes to do a quick test on a real 250gb drive with both versions and did see that your second version was slower by a bit. But still under 1/4 second for both in my virtual world running 2 operating systems. I guess I was looking at that 1.5 minutes you had from a random input when I was still thinking about a progress indicator. Your program is so fast compared to my bash script that now I KNOW that I MUST learn C.

At some point in time in the hopefully near future I will try to get an alpha version of the real working utility posted. I will give you credit in it and include your source in the download. Just wondering if you had any specifics as to how you would like credit given.

---

### Post by maximus57 on 2012-10-30
Alpha version of ddrntfsbitmap released. It seems to work, but could really use some real world testing with report of results. I wouldn't use it on any critical data until after you have tested it to see how it works. Includes a help.txt file which I encourage everyone to read first.

---

### Post by Patrick Verner on 2012-10-31
I'm interested in including this in Parted Magic by default when you guys think it's ready for the public to use. =D>

---

### Post by maximus57 on 2012-10-31
> **Patrick Verner said:**
> I'm interested in including this in Parted Magic by default when you guys think it's ready for the public to use. =D>

That is awesome! It might be some time before I am happy with it enough for a public release like that. It might be some time before I can find enough time to work on it more due to outside factors. I also will have to see what I will have to do to make it ready for Parted Magic, and check for dependencies. All in due time...

I am planning on including this new utility in with my original ddrutility. Originally I thought of ddrutility to be a menu driven front end for ddrescue. However, it seems I like to do things backwards and find the hardest things to do first. So I am now thinking that ddrutility might end up being a collection of utilities.

---

### Post by Steve00 on 2012-11-04
I am getting ready for a rescue attempt on a 500G Windows 7 hard drive for my kid. The bad drive will be in an external USB HD enclosure. I have second 1T hard drive, also in an USB enclosure to write whatever I can capture from the bad drive.

I've burned the 12.04 Ubuntu-rescue-remix to a DVD.

While I've nosed around Ubuntu a bit, most of my experience has been at the GUI level with minimal work with the command line.

Is there a tutorial available that will guide me in the next steps? I'm not even sure how to load the latest .sh files noted earlier in this thread.

While I want to retrieve my kid's files, I want to make sure I am very careful not to stomp all over my primary hard drive on my computer!

Thanks for any guidance you can provide.

EDIT:

Sorry. Missed the documentation pages on the Ubuntu-Rescue-Remix webpage. From reading there, it sounds like the HD's NTFS Boot Sector needs to be repaired with TestDisk. I'll try that first and if that fails try the script here.

Haven't found it yet, but I assume the docs will show how to load and run the .sh if I need to do so.

---

### Post by maximus57 on 2012-11-04
> **Steve00 said:**
> I am getting ready for a rescue attempt on a 500G Windows 7 hard drive for my kid. The bad drive will be in an external USB HD enclosure. I have second 1T hard drive, also in an USB enclosure to write whatever I can capture from the bad drive.

I've burned the 12.04 Ubuntu-rescue-remix to a DVD.

While I've nosed around Ubuntu a bit, most of my experience has been at the GUI level with minimal work with the command line.

Is there a tutorial available that will guide me in the next steps? I'm not even sure how to load the latest .sh files noted earlier in this thread.

While I want to retrieve my kid's files, I want to make sure I am very careful not to stomp all over my primary hard drive on my computer!

Thanks for any guidance you can provide.

EDIT:

Sorry. Missed the documentation pages on the Ubuntu-Rescue-Remix webpage. From reading there, it sounds like the HD's NTFS Boot Sector needs to be repaired with TestDisk. I'll try that first and if that fails try the script here.

Haven't found it yet, but I assume the docs will show how to load and run the .sh if I need to do so.

If it ends up that you need to perform a rescue, then you really need to look at the help pages for gnuddrescue and figure out  how to use that first as it will do what you need. If you search some  there are probably also many questions and answers how to use it. It is a great rescue utility that works fine by itself, and my software is just an extension to be used with it as desired.

As I look at my posts, I realize I did not make something clear. My programs are based on the user already  knowing how to use ddrescue. I am sorry to say that my latest test release is not a stand alone utility and also is not for the beginner. While I do really appreciate any willing users to test it, it is not yet ready or documented well enough for someone that is not familiar with using ddrescue to jump into. It will just cause you to ask more questions.

With that being said, there are some very basic instructions in the help file about how to run .sh files.

---

### Post by Steve00 on 2012-11-05
Thanks for the explanation about your utility. Based upon this info and what I've read so far, I THINK the best strategy will be to image the file with gnuddrescue, so I have a backup, and then try running TestDisk to recreate the NTFS Boot Sector (When trying to mount the drive in Windows, we get: "The drive is not formatted, do you want to format it now?".

That way if TestDisk fixes the problem, I'm done. If not, I've got the gnuddrescue image to try to extract the data from.

Does this plan seem reasonable?

---

### Post by maximus57 on 2012-11-06
> **Steve00 said:**
> Thanks for the explanation about your utility. Based upon this info and what I've read so far, I THINK the best strategy will be to image the file with gnuddrescue, so I have a backup, and then try running TestDisk to recreate the NTFS Boot Sector (When trying to mount the drive in Windows, we get: "The drive is not formatted, do you want to format it now?".

That way if TestDisk fixes the problem, I'm done. If not, I've got the gnuddrescue image to try to extract the data from.

Does this plan seem reasonable?

That sounds like an excellent plan. You will have a full backup to work with if the original can't be repaired. Just a side note... if the data is important enough and it isn't recovering easy, sometimes it is even a good idea to make a backup of the backup to work with, if it should get to that point :)

---

### Post by maximus57 on 2013-02-08
I ended up having to work some crazy overtime at my job for awhile, and so have not worked on this project for a few months or so. I have very recently had a career change with much more reasonable hours, and am now in the process of self learning the C programming language in my spare time so I can advance with this project.

But I am wondering where the best place for my project home should be. I started here on the Ubuntu forum because it was easy and the posts stay for years on here. But it is not the proper place for software development. I would like a home that has a forum or such for discussion of bugs and ideas, but something that doesn't require much maintenance by myself. Any suggestions?

---

### Post by sudodus on 2013-02-09
Try Sourceforge! I find many useful things there, but I have no own page (so I don't know how easy it is to create one).

---

### Post by mobodo on 2013-02-18
Just wanted to give some encouragement for the project - ddrutility has been very useful for me.  I do wish it ran faster (it took nearly a full day to process all my bad sectors), so please don't give up if you can optimize it!

Thanks!

---

### Post by maximus57 on 2013-02-25
> **mobodo said:**
> Just wanted to give some encouragement for the project - ddrutility has been very useful for me.  I do wish it ran faster (it took nearly a full day to process all my bad sectors), so please don't give up if you can optimize it!

Thanks!

I have definitely not given up. But the project is at a crawl right now while my brain tries to learn how to code C. I am trying to learn it fast, and that doesn't always work out so well. I have lots of ideas of what I would like to do, but the more I want to do the more complicated it gets. And for some reason, I always seem to jump to the hard things to do.

On a side note, I would like to say one of the last things I did in bash script was to recover individual files from a damaged NTFS drive using ddrescue. It was a multi-step process, but it worked great, except it took way too long, hence the learning C to make fast enough to be usable.

---

### Post by tratb9 on 2013-06-01
I just joined the forum to say thanks for your work so far, this project is well worth a high five!

Edit i just tried to install :ddrutility_1.6-1_all.deb in ubuntu 12.04 and got a few missing libs which are not easy for me to install.

All these are 404
[http://us.archive.ubuntu.com/ubuntu/pool/main/liby/libyaml-syck-perl/libyaml-syck-perl_1.09-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liby/libyaml-syck-perl/libyaml-syck-perl_1.09-1_i386.deb)
[http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdate-manip-perl/libdate-manip-perl_6.11-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdate-manip-perl/libdate-manip-perl_6.11-1_all.deb)
[http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/libtsk3-3_3.1.2-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/libtsk3-3_3.1.2-1_i386.deb)
[http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/sleuthkit_3.1.2-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/sleuthkit_3.1.2-1_i386.deb)

All these are the latest. After downloading, package manager just says "unknown error"

    [http://us.archive.ubuntu.com/ubuntu/pool/main/liby/libyaml-syck-perl/libyaml-syck-perl_1.22-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liby/libyaml-syck-perl/libyaml-syck-perl_1.22-1_i386.deb)    
    [http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdate-manip-perl/libdate-manip-perl_6.39-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdate-manip-perl/libdate-manip-perl_6.39-1_all.deb)
    [http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/libtsk3-3_3.2.3-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/libtsk3-3_3.2.3-2ubuntu1_i386.deb)
    [http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/sleuthkit_3.2.3-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/sleuthkit_3.2.3-2ubuntu1_i386.deb)

Maybe its easy to update the .deb package  ?

---

### Post by maximus57 on 2013-06-02
> **tratb9 said:**
> I just joined the forum to say thanks for your work so far, this project is well worth a high five!

Edit i just tried to install :ddrutility_1.6-1_all.deb in ubuntu 12.04 and got a few missing libs which are not easy for me to install.

All these are 404
[http://us.archive.ubuntu.com/ubuntu/pool/main/liby/libyaml-syck-perl/libyaml-syck-perl_1.09-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liby/libyaml-syck-perl/libyaml-syck-perl_1.09-1_i386.deb)
[http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdate-manip-perl/libdate-manip-perl_6.11-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdate-manip-perl/libdate-manip-perl_6.11-1_all.deb)
[http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/libtsk3-3_3.1.2-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/libtsk3-3_3.1.2-1_i386.deb)
[http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/sleuthkit_3.1.2-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/sleuthkit_3.1.2-1_i386.deb)

All these are the latest. After downloading, package manager just says "unknown error"

    [http://us.archive.ubuntu.com/ubuntu/pool/main/liby/libyaml-syck-perl/libyaml-syck-perl_1.22-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/liby/libyaml-syck-perl/libyaml-syck-perl_1.22-1_i386.deb)    
    [http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdate-manip-perl/libdate-manip-perl_6.39-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libd/libdate-manip-perl/libdate-manip-perl_6.39-1_all.deb)
    [http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/libtsk3-3_3.2.3-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/libtsk3-3_3.2.3-2ubuntu1_i386.deb)
    [http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/sleuthkit_3.2.3-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/s/sleuthkit/sleuthkit_3.2.3-2ubuntu1_i386.deb)

Maybe its easy to update the .deb package  ?

I currently use xubuntu for my programming (in vmware), and can install ddrutility 1.6 on both 32 and 64 bit versions of 12.04. I will have to download and install the regular ubuntu 12.04 to test and see if I can recreate the issue, but I have a few questions. Is your ubuntu up to date with updates, or is it a fresh install? Is it the 32 or 64 bit version? Did you download it from here, or set it up through launchpad? Is you ubuntu really 12.04, or did you let it upgrade (type "lsb_release -a" in a terminal window to see what version you have).

You should still be able to use the .sh file as an alternative. Just read the help file on how to use it. Note that it has 3 requirements that you have to install, they are listed in the help file.

EDIT:
It is possible that the update server your ubuntu installation is connecting to is corrupt. Do a search for "ubuntu change update mirror" for how to change the update server mirror, and see if that solves your problem.

---

### Post by tratb9 on 2013-06-04
I think that's enough help to get me going for now, thanks. Since i dont want to derail your time for newbie trouble shooting in place of the real great work your doing here i will wait, if things dont work, for your project to finish and then ask for more help.

edit
It was plenty of help, simple update fixed the issue & ddrutilities installed. Thanks again

---

### Post by maximus57 on 2013-06-20
I would like to announce that I have moved ddrutility to sourceforge.

[https://sourceforge.net/projects/ddrutility/](https://sourceforge.net/projects/ddrutility/)

I will still reply to posts on here as I get them, but any further work will be at sourceforge. Also, I believe I have the forum page open on it there, so comments and further discussions will be welcome there.

Also, at this time I am not planning on keeping ddrutility updated in Launchpad.

---

### Post by glorifyday on 2013-08-27
I am planning to use your tool as soon as ddrescue -r3 finishes. Thank you for your work - ddrescue is not complete without the ability to easily tell which files are corrupt.

I downloaded Ubuntu Rescue Remix 12.04, but as fas as I can see you've made lots of changes since the version included in URR 12.04.
Is there any newer Live CD release containing your latest script or should I just copy the latest version to a pendrive and run in URR 12.04? Will it work? Are all dependencies satisfied?

I haven't find any discussion on that point, so let me ask: how sure are the results of your script? Do they tend to be over or underestimated, for instance?
How tollerant is the sript with regard to filesystem errors? I've got a 500 GB partition and the corruption starts near the 473rd gigabyte and is not big - do you think I will get accurate info?

---

### Post by scott-dwyer on 2013-08-27
> **glorifyday said:**
> I am planning to use your tool as soon as ddrescue -r3 finishes. Thank you for your work - ddrescue is not complete without the ability to easily tell which files are corrupt.

I downloaded Ubuntu Rescue Remix 12.04, but as fas as I can see you've made lots of changes since the version included in URR 12.04.
Is there any newer Live CD release containing your latest script or should I just copy the latest version to a pendrive and run in URR 12.04? Will it work? Are all dependencies satisfied?

I haven't find any discussion on that point, so let me ask: how sure are the results of your script? Do they tend to be over or underestimated, for instance?
How tollerant is the sript with regard to filesystem errors? I've got a 500 GB partition and the corruption starts near the 473rd gigabyte and is not big - do you think I will get accurate info?


I don't remember exactly what changes I made since the version on URR 12.04, but I would recommend the latest version (1.6), as I know I fixed some errors. Also, there is a fast NTFS option in the newer version. As far I know, the dependencies are the same, and 1.6 should run fine on URR 12.04. It is not available on any other rescue CD that I know of (yet). I was hoping the new version would get on UUR 12.10, but it was never released.

As for tolerance, it relies on some 3rd party functions, and they rely on the filesystem to be fairly intact. Simply put, if it completes a run, then it worked. If it exits with an error, then the file system is too corrupt. If it works, it should be accurate, or as accurate as it can be with the information it was presented. If you don't see any files listed, then the errors are most likely in an unused area (should be true for NTFS, but not always true for the other filesystems).

If the errors are way towards the end of the disk like you indicate, then the file system is most likely healthy enough (critical areas are usually towards the very beginning and in the middle), and you should get accurate info. Just remember, you are working with a disk that has errors. There is absolutely no guaranty whatsoever that it can be 100% accurate.

---

### Post by glorifyday on 2013-08-28
Thanks a lot for your answer, Scott.

I cannot find any examples in your help.txt file.
Is there anything like a recommended set of options for an ntfs drive? A good compromise between verbosity, readability and processing time?

Currently, the ddrescue is still working on my HDD ( third retry now... sooo looooong :-/ ) and I still have a time to speculate what to do in various possible scenarios. If the MFT gets corrupted and is to be restored/recalculated by some recovery software... has anyone got any idea if it is safer to fill the unrecovered blocks with 0 or 1?

---

