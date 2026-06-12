---
title: "Ubuntu Application Installation Issues Multiply Hard Drives"
date: 2012-03-27
forum: General Help
---

### Post by maydayjay on 2012-03-27
I am new to Ubuntu and Linux and having a learning curve to it with the use of books, Google, and of course Ubuntu Forms.  I have an older custom built system that I recycled for learning Ubuntu / Fedora / Ubuntu Server, and on this system I have 3 hard drives and each is found by Ubuntu Server (current version I have loaded at this time).  I have been able to download packages through FireFox and the Ubuntu Software center, but this is my issue.  Unlike Windows I am not given the choice where the application is installed at, for example when I install Itunes or Media Monkey on a Windows system I can choose which hard drive and the folder in which I wan to install a package as I have 4 hard drives on my Windows 7 machine and I keep one hard drive just for MP3, Itunes, Video, and other Multi Media.  I have one hard drive that I use only for Labs, Vmware, GNS3 and the storage of Cisco IOS Images.  I want to do the same in Ubuntu as the /boot drive is limited in space and I want to make sure that new applications are installed on one of the other Hard Drives and in folders that I create and can find easily like with Clementine and the music or videos I might use with it.  How can I do that in Ubuntu /Fedora/ or other Linux OS?  Thanks in Advance.

---

### Post by oldfred on 2012-03-27
Welcome to the forums.

Linux is not Windows. But you will find applications are much smaller in Linux. And they have to install into the / partition unless it is a smaller custom built app you have.

But you can store all your data in your other partitions. I have 20 to 25GB / (root) partition with many apps installed and have used about 7GB. My /home is still in my /. The normal default is to also store data in /home. Newer users that want to do clean installs often have a /home in a separate partition to separate system from data. But user configuration files are also in /home and I consider those part of system. 

I install system on every drive and rotate newest between drives. And have data partitions which I mount into /home to look like tha default locations to save data. So my /Music is really a link from a mount of  /mnt/data  of a partition on another drive.

I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Another way to share:
Morbius1 uses bind, now:
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)

---

### Post by Mark Phelps on 2012-03-27
One of the hardest shifts when coming to Linux is to STOP thinking like MS Windows.  You're simply NOT going to be able to do all the same things all the same ways.  Software installation is one of those -- as oldfred pointed out.

In addition, in MS Windows, you generally install an app by sticking in a CD, or DVD, or downloading a file -- and then launching an installer.  When it asks you where to install, that generally ONLY lets you choose where to have your DATA files.

I think if you really started digging, you would find that although you have separate drives for different kinds of apps, the app software itself, or at the very least, the Registry values each uses, are actually installed to your OS partition.

In Linux, HOW you install an app also affects where the pieces get placed -- and generally, you have no control over that.  Executables end up in various ...\bin directories, settings end up in hidden files (often under your $HOME directory somewhere), other files end up in other places.

So, you need to forget about replicating HOW MS Windows does things -- Linux is a different world.

---

### Post by dcstar on 2012-03-28
> 
.........
So, you need to forget about replicating HOW MS Windows does things -- Linux is a different world.

And also learn how to format a readable question instead of a "Dog's breakfast".

---

