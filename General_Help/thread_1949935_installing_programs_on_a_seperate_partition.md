---
title: "installing programs on a seperate partition"
date: 2012-03-31
forum: General Help
---

### Post by bobman321123 on 2012-03-31
I'm running ubuntu 12.04, and I'm wondering if there's any way for me to install my programs on another partition. 
If so, how?

---

### Post by kc1di on 2012-03-31
Hi,
Well I'm not sure I understand your question exactly. when you install a program it installs packages where the programer /packager tells it to install them.  This may be in any directory it calls for.  Normally the execute file or script is installed in /usr/bin directory.  But with some it may be in /opt as well or others.  

If you mean can you store information that a program generates to another partition , That should be possible.  

Maybe some more specific cases your talking about would help get more answers. 

good luck,

---

### Post by bobman321123 on 2012-03-31
Well I have a large data partition, and I'm trying to keep the partition size of each of my installs down to a minimum. However, if I install large amounts of programs, the size of my installed system will swell dramatically. 
If I were to install blender using ```
sudo apt-get install blender
``` is there a way to move the installed program to somewhere else?

---

### Post by kc1di on 2012-03-31
> **bobman321123 said:**
> Well I have a large data partition, and I'm trying to keep the partition size of each of my installs down to a minimum. However, if I install large amounts of programs, the size of my installed system will swell dramatically. 
If I were to install blender using ```
sudo apt-get install blender
``` is there a way to move the installed program to somewhere else?
how big a hard drive and what partitions do you already have?

---

### Post by bobman321123 on 2012-03-31
I have a large (nearly 200gb, planning on making it bigger) partition at sda1. (I'll refer to this as 'data').
I have smaller ubuntu installs (11.10 and 12.04) at sda6 and 7. They're about 200 and 40 gb respectively.
I also have 24gb of swap (excessive, I know, but I haven't gotten around to fixing it yet). 

My harddrive is 500gb in total.

---

### Post by oldfred on 2012-03-31
All my installs are 20 to 25GB for / with /home included and I use about 7GB of the 25GB. I have a lot of programs installed. Most of my home is .wine of about 1GB for Picasa.

My dpkg list is about 2200 files where the new 12.04 default was 1423. Many of those are not top level packages but all the support files also.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by kc1di on 2012-03-31
I would say you want something like this

/ partition 20 to 30gb -- that should be plenty to run all programs.

/home  50 to 100gb more if you want 

/data (call it what you like) make it as big as you want.

swap 2gb should be plenty.

---

### Post by bobman321123 on 2012-03-31
But many of the programs I have are 10+ gb, is there any way to install them on /data?

---

### Post by bobman321123 on 2012-03-31
And possibly share them between installations?

---

### Post by kc1di on 2012-03-31
> **bobman321123 said:**
> But many of the programs I have are 10+ gb, is there any way to install them on /data?

There are very few programs that big that's bigger than the system.
What programs you talking about ??
you had mentioned blender before installed it takes less than 70mb.

---

### Post by bobman321123 on 2012-04-02
Stuff like Team Fortress 2, Maya, Portal 2, etc. They're all huge.

---

### Post by kc1di on 2012-04-02
> **bobman321123 said:**
> Stuff like Team Fortress 2, Maya, Portal 2, etc. They're all huge.

First of all all those programs seem to be M.S. Windows or Mac only.
they will not work on linux real well , You could use Wine or perhaps Cross over Linux. But don't think your going to be satisfied with them on Linux.  I may be wrong.  If your using wine to emulate windows api you can install wine and all the executable will be installed in it's hidden folder and you can put that were ever you like.

---

### Post by Mark Phelps on 2012-04-02
> **bobman321123 said:**
> Stuff like Team Fortress 2, Maya, Portal 2, etc. They're all huge.

What's more likely the case, if these are all Games, is that the game support DATA (not the game executables) are taking up nearly all that space.  This is why, in MS Windows, you often get the option to install somewhere other than in "C".

Linux is not a free version of MS Windows, so you need to think differently here.

Also, if these are all MS Windows games, you should check the WineHQ application compability website to read through the game ratings -- to see how well they work in Linux.  Any games rates less than Gold are going to be a waste of your time to install.

---

### Post by bobman321123 on 2012-04-02
Mark Phelps, kc1di, I've gotten all these programs working perfectly through wine before. I know for sure that I can run them on linux. I have them installed on the system I type this on (ubuntu 11.10/12.04). 

Now that that's established,
How do I store the data elsewhere?

---

### Post by 1clue on 2012-04-02
There are easy answers for what you're talking about, and then the not-so-easy realities.

Sharing data on a separate partition is not difficult, but it can be a big headache.  Often you can specify where to put the data (which is what takes all the space) but even if not, these programs usually put the data in a directory belonging to the specific program.  If you must, you can mount a different partition at that location, and problem solved.  That can be either a pure partition mount, or a reference to a directory on a data partition.

In my case, for multiple operating systems accessing the same data, I do the following:
[LIST=1]
[*]I have 4 identical drives.
[*]I use lvm2 and raid, but in a nonstandard configuration.  You don't really need to know about that.
[*]I have /boot on a raid1 partition which is identical across all 4 drives.
[*]Everything else is LVM2, which means I can add or remove partitions at will, choose which drives they go on and resize them with very little consequence.
[*]My / partitions are named by distro and version, and the other partitions for those distros as well.
[*]Common data partitions are named by a different scheme.
[/LIST]

The above design gives me a huge amount of flexibility in terms of partitions, sizes and such.  It also lets me resize any LVM2 partition to be larger or smaller.


Now, for the complicated part.

If you're going to share dynamic proprietary (e.g. a mysql database) application data across distributions, you will find that extremely difficult.  If you intend to share application programs which are NOT statically linked across distributions you will find that virtually impossible.  Dynamically linked applications rely on specific versions of libraries, and different distributions have wildly different versions of those libraries available.

I've tried dual-booting two different instances of the same version of the same distro and sharing my $HOME directory between them and found it impossible to have a happy user experience.  Every time a software update runs, it changes something, updates the $HOME config file and then the other distro doesn't work properly anymore.

What you're going to have the best time with is to share a data directory full of files which are designed to be opened consistently (videos, images, word docs, text files etc) or to have mostly static data.

For game data, you might want to try to make your data directory as a symbolic link from the distro-specific application data directory, pointing at /shared-data/mygame/v1.2.4/

That way as long as you have the same exact app installed on both distros you can save the static data space by sharing data.  As soon as you upgrade one of the distros, you can move the symbolic link to v1.3.0 and no conflicts.

Speaking with years of personal experience on this, you need to walk a fine line to make this work reliably.  You have to figure out what sort of things can be shared and what needs to be separate.

Good luck and have fun.

---

### Post by bobman321123 on 2012-04-02
Thank you very very much. If I had the same version of wine installed, and moved my entire .wine folder over, would that work between distros?

---

### Post by 1clue on 2012-04-02
Short term yes, long term it could get problematic.

It all depends on how many updates you make.  If you install wine and then disable absolutely all updates, then it could work for years.  If you have automatic updates, or the application you're using has continuous online update checking with automatic modifications, then you're going to have trouble.

Also, if you have an Internet license checking scheme, depending on how they do that you might have trouble depending on how they check it.

If you're trying to share dynamic data my opinion is that it's much cheaper and easier to have a whole extra hard drive than it is to try to get this working.  If you're only sharing static info like X-Plane's world data, then probably zero problems since an update to that means you stick in a few DVDs with a long delay between them.

Again I don't know what the nature of the data you're sharing is.  If you tell me app names (you did) I still don't know since I'm not a gamer.

My solution for this type of thing is to use virtual machines, which would not be happily compatible with high performance gaming.  I would put the shared database (if I were using mysql or similar for example) on a VM which works all the time, and have access from whatever VM is handling my user interface.

That said, this scenario almost certainly will not work for you.  Gaming requires low latency which is problematic with virtualized or networked (remote desktop for example) sharing.

---

### Post by dcstar on 2012-04-03
> **bobman321123 said:**
> 
..........
How do I store the data elsewhere?

You copy the entire .wine folder to another **Linux** filesystem (no Windows FAT/NTFS rubbish), and then replace the original .wine folder with a softlink to the new location.

---

### Post by bobman321123 on 2012-04-03
> **dcstar said:**
> You copy the entire .wine folder to another **Linux** filesystem (no Windows FAT/NTFS rubbish), and then replace the original .wine folder with a softlink to the new location.

That'll work if I have the same wine version, right? No matter the OS?

---

### Post by 1clue on 2012-04-03
Are you talking about sharing between two distros, or are you talking about a copy which then becomes two distinct .wine folders?

As long as the "new" wine is the same version or newer than the old one you're fine.  More specifically if the copied-to folder's wine application uses the same configuration file format or newer, then you're fine.  The problem I was talking about is when you have an app which opened a config file, then you go back to an older version and try to open the same config.

Something we haven't talked about yet is concurrent use.  If you're running virtual machines then chances are it will mess up no matter what version you use.  In that case it's best to have a VM running whatever Windows you want, then access it remotely from either other distro.

---

### Post by bobman321123 on 2012-04-03
Mmmm ok. Thanks for all your help! Marked as solved :)

---

