---
title: "Possibly need to resize partition scheme, lack of knowledge the  cause"
date: 2011-01-26
forum: General Help
---

### Post by YeeP on 2011-01-26
I setup a dual boot system, with approximately 200gig planned for ubuntu 10.10. Based on the article here: [https://help.ubuntu.com/community/DualBoot/Partitions](https://help.ubuntu.com/community/DualBoot/Partitions)

And this quote:
> # sda1 Recovery Partition, unchanged
# sda2 Windows partition, shrunk preferably from inside Windows, hopefully about 30Gb
# sda3 Primary Partition, 10Gb, file-system = ext3, in the Partitioning Section of the installer change the "Mount Point" = /
# sda4 Extended Partition at least 25Gb

    * sda5 Logical Partition, at least 10Gb, file-system = ext4 or to share with Windows as Ntfs, in the installer change the "Mount Point" = /home
    * sda6 Logical Partition, 10Gb, file-system = ext3, no Mount Point. This is an experimental area for trying other distros and installing a new release of Ubuntu before upgrading to it properly
    *

      sda7 Logical Partition, between ram & 2xRam, perhaps slightly over 2xRam, 'file-system' = "linux-swap". 

I defined my linux partitions in this way:
[IMG]http://i440.photobucket.com/albums/qq123/YeeP79/gparted_partitions.jpg[/IMG]

I assumed at that point that the "sda3" "/" would be for booting purposes. I would have to guess that I was wrong, because it is filling up very  quickly. As you may be able to tell by the screen shot, "sda5", "/home" was what was assumed to be the file structure to store all of the programs and such. 

I have only been running this setup for a week, and would expect to not be seeing my "boot" partition growing so quickly. 

Do I need to resize it? 
Where do the standard programs that I get from the ubuntu software center install at (partition wise)?

I suppose I dont mind wiping that section dry and starting over, but I would give a resize a try if possible. Any help would be much appreciated.

Thanks.

---

### Post by Quackers on 2011-01-26
10GB /root partition should be ok for some time yet, I would say. I have 3 /root partitions and none are bigger than 12GB, and none of those are more than half full. Having said that, I haven't installed lots of programs either :wink:

---

### Post by srs5694 on 2011-01-26
> **Quackers said:**
> 10GB /root partition should be ok for some time yet, I would say. I have 3 /root partitions and none are bigger than 12GB, and none of those are more than half full. Having said that, I haven't installed lots of programs either :wink:

First, I'd like to nip a potentially confusing terminology issue in the bud: As a general rule, you should not have a separate /root partition, and YeeP does not have a separate /root partition. The term "/root", spelled precisely that way, with a leading slash ("/"), refers to the directory called precisely that ("/root"), which is the root user's home directory. (Even though Ubuntu doesn't permit direct logins by the root user by default, the /root directory does exist.) This directory should be, and normally is, a normal directory on the root (/) partition. Note how I've written that -- the directory (and partition) is referred to as "/" on the command line and is pronounced "root". This is very very very different from the /root directory! To avoid confusion and very bad misconfigurations, it's imperative that this distinction be maintained. The root (/) partition is required, and it's where everything that's not put explicitly in another partition goes. A default Ubuntu installation, if you use the automatic partitioning options, puts everything except swap space in a single huge root (/) partition. This includes the /root directory.

Now, YeeP has created a separate /home partition, which is fine (and I generally recommend doing so), so that configuration includes root (/), which holds all the OS files, and /home, which holds user files. In this configuration, all Ubuntu files for programs, libraries, fonts, temporary files, and so on goes in the root (/) partition; but user files (word processing documents, MP3 files, etc.) go in the /home partition (unless you explicitly put them somewhere else).

Ordinarily, 10 GiB is enough for a root (/) partition when you've got a separate /home partition, although if you install everything imaginable, store user files in unusual locations, or use the system as a mail server or in some other ways that might store more files on root (/) than is typical for a desktop system, having more space might make sense. I generally advise devoting between 5 GiB and 20 GiB to the root (/) partition; the larger values make sense when you've got plenty of disk space to throw around and want to give yourself wiggle room for growth.

It's possible that YeeP has temporary files accumulating somewhere, such as installed Debian package files in /var/cache/apt/archives/. That particular directory can be cleaned out by typing "sudo apt-get clean". Other directories might need to be cleaned out in other ways. It's also possible that YeeP has been installing lots of software that's just consuming a lot of space. If so, then one of three things can be done:


[list]
[*]Stop installing software -- if no more software is installed, the root (/) filesystem will stabilize in space used. (There'll be some small changes for other reasons, but nothing huge.)
[*]Clean out unused software -- You can use Synaptic to peruse your packages and remove those that you're not using in order to make room for testing packages you do want to use.
[*]Resize root (/) -- You can increase the size of root (/) if you really want to install everything and the kitchen sink. This will require reducing the size of one of the surrounding partitions. Back up before attempting to do this; partition resizing operations are inherently risky, and any resize operation in this case will necessarily involve a partition move, too. It may also be necessary to boot using [Super GRUB 2 Disk](http://www.supergrubdisk.org) and re-install GRUB 2 after resizing, particularly if you reduce the size of /dev/sda2 to increase the size of /dev/sda3.
[/list]

---

### Post by YeeP on 2011-01-26
Wow, thank you for the awesome information!

Where does Ubuntu store the applications in the file structure? 
Please excuse me if this is too simplified of a question. The reason I ask is I had planned to make the largest partition of the aloted space for use by linux, where that should go.

In other words, if you look at my screenshot, that would have been the sda5 or "/home" partition.

I did this because in the article it refers to it as the "file structure". It seemed logical at the time.

Thanks again.

---

### Post by srs5694 on 2011-01-26
I think you're looking at it the "Windows way," which is the wrong way for Linux. This may be hard to convey properly, since the distinctions can be subtle....

As you probably know, Linux doesn't use drive letters; instead, partitions and removable media are mounted at locations in a single directory tree, based off the root (/) directory. You can create separate partitions for any directory you like (/home, /var, /usr, /usr/local, or whatever), with a handful of exceptions. (You can't put /etc on its own partition, for instance, since it holds /etc/fstab, which defines where partitions are mounted.)

The purpose of the major directories that Ubuntu installs by default, and therefore of likely standard partitions if you wanted to carve an installation up into lots of partitions, are defined in the [Filesystem Hierarchy Standard (FHS).](http://www.pathname.com/fhs/) I encourage you to read that document if you want the details. In short, though, program files are installed in a variety of directories, including /bin, /sbin, /usr/bin, and /usr/sbin. These program files usually rely on libraries (stored in /lib, /usr/lib, and some other locations). There are also often fonts, configuration files, and other files upon which programs rely, all scattered about. Most of these, though, end up in /usr. This contrasts with Windows, which tends to scatter files from any given program around a bit less, enabling programs (especially small programs) to be installed in their own directories. This isn't normally done in Linux, though; in Linux, we rely on package management tools, such as the Debian package system used by Ubuntu, to keep track of these files and enable easy uninstallations and upgrades.

The Windows method makes it easy for users to install programs where it's convenient, but it makes it hard for the OS to locate program files. The Linux way makes it hard for users to install programs anywhere but the conventional place, but it makes it easy for the OS to locate program files.

In Linux, the root (/) partition holds Linux and /home holds user files, as I noted earlier. (There can be some fudging on this point, particularly when people try to treat Linux like Windows in one way or another.) Thus, separating root (/) from /home does as you want to do, broadly speaking; however, it seldom makes sense to devote more than about 20 GiB to the root (/) partition, since Linux system files seldom grow to need more space than this. If your root (/) partition needs more than 20 GiB, chances are something else is going on. For instance, mail servers often store users' mail in /var/spool/mail, which would be part of the root (/) partition in the 2-partition scheme under discussion. (This is one of the exceptions to the rule of user data going in /home.) If you were running a mail server, it would make sense to split /var off into its own partition for this reason; but chances are you're not doing this.

Advanced Linux users and administrators of servers often split off multiple filesystems into their own partitions, such as /var for a mail server, as just noted. Sometimes it makes sense to split /usr off in this way, since it holds most programs and related data; but for most desktop Ubuntu users, there's little or no advantage to splitting off anything but /home, swap space (which isn't mounted like most partitions), and any partitions associated with non-Linux OSes.

---

### Post by YeeP on 2011-01-26
Link has been bookmarked. I also created a bootable gparted usb. I think I will take space from the extended partition /home, to be specific and try to increase the side of my root. Thank you so much for the insight. :guitar:

---

### Post by YeeP on 2011-01-27
Apparently you cannot re size an extended partition. Or at least shift space out of one by resizing what is inside it, partition wise, then resizing the extended partition. So, I just dumped the install and am rebuilding it. 

The option to have it install "along side" is not a good option when you already have "section" of the HD set aside for the install. It will select the other OS's partition and divide it. As a "beginner", I am curious as to why I cannot select something along the lines of "install on this partition". I know that ubuntu will create multiple partitions, so that is a little to simple of a statement, but I think you get my point. 

It seems that the two options of either

1) Share a pre-existing partition with another OS.
2) Create your own partition scheme

Seems like we are missing a possible middle road here... At this point, because I have followed the recommended articles and used the windows "shrink" program to change the size of the windows partition. Therefore creating a space for my linux OS... I have now backed myself into a corner where I must use the advanced partition setup. 

Obviously, the fall out here is myself and lack of knowledge. 

Would there be a better way to do this?  Maybe I should boot up windows, download something like partition magic, and resize the windows partition to the entire HD.  Then boot into the Ubuntu install, and have it install itself "along side" another OS. As far as what I can find on line, I am only seeing problems with that when trying to boot into windows after the fact. Could be wrong. I wish I did not need windows, but my wife needs it to connect to her work. :(

---

### Post by oldfred on 2011-01-27
For some reason they eliminated the install into free space option and confused the other options where users can too easily overwrite windows. The manual option is the best way, but you have to understand partitions and what sizes you want to make partitions.

You can resize an extended partition, but the liveCD usually mount swap which is usually inside the extended partition. You can right click on the swap partition and swapoff. Any mounted partition in the extended partition mounts the entire extended.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Partitioning basics with some info on /data, older but still good
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")


Some examples of installs and issues:
Issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
From kansasnoob:
[http://ubuntuforums.org/showpost.php?p=10145206&postcount=15](http://ubuntuforums.org/showpost.php?p=10145206&postcount=15)
Trust me here! If you choose either "Use entire partition" or "Use entire disc" you are not likely to end up with "Alongside" anything! You will most likely lose the OS and any data contained therein!
Installs:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by srs5694 on 2011-01-27
Oldfred has posted good advice. I'll add that the manual partitioning option isn't all that difficult; however, you do need to understand a bit about partitions. The worst of it is probably the primary/extended/logical silliness. In case you (or some other reader) doesn't know:


[list]
[*]**Primary partitions** were the original type. The Master Boot Record (MBR) partitioning scheme that's used on most PCs is limited to four primary partitions. This became a problem long ago....
[*]**Extended partitions** are really just a special type of primary partition; they hold the next type....
[*]**Logical partitions** are partitions that reside inside an extended partition. You can have as many of them as you like (the theoretical maximum is about 2^31 partitions), but they must all reside within a single extended partition.
[/list]


Windows (and some other OSes) must boot from primary partitions, but Linux is not so limited; it can boot from either primary or logical partitions. If you need to move space from a primary to a logical partition, or vice-versa, you'll have to resize both the extended partition and the logical partition. Doing so with GParted usually requires booting from a live CD, since GParted won't let you resize a partition that's in use, and as a practical matter, most Linux installations on disks with logical partitions end up using at least one logical partition, and therefore the extended partition.

When installing fresh, I recommend creating an extended partition and making all Linux partitions logicals. That way you'll consume as few of the limited primary partition slots as possible. A partial exception: If you're installing Linux alone on a disk with no existing partitions, make one partition (probably the root partition) primary. That increases your options for boot loader installation. You might not need this flexibility, but you'll have it if you need it.

---

