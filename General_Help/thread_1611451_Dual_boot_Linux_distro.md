---
title: "Dual boot Linux distro?"
date: 2010-11-01
forum: General Help
---

### Post by Yezinki on 2010-11-01
Hi there,

1. Would a dual boot of Ubuntu & Linux Mint 9 KDE be better than Ubuntu & Kubuntu?

2. What version would you recommend for Ubuntu & Kubuntu, 10.04 LTS or 10.10?

3. My machines have only 1 Internal main HDD, plan installing 2 Linux distros  on one & Windows on the other machine....is that fine.........or having windows on both is an advantage....personally don't wanna mess up with too many OSs....what are your thoughts?

4. Coming to dual Linux distro install on the machine with 250 GB HDD, how should I proceed?

5. Install Ubuntu first & than Kubuntu or Mint KDE after?

4. 3 Primary partitions & 1 logical for the swap?

5. Linux install 20 GB in size & what should be the size of the other 2 primary partitions?

6. 4th partition, Logical/swap 1 GB?

7. File system ext4?

8. Would I require Grub to install the 2nd distro or the bootable DVD will install it automatically after Ubuntu?

9. Can Kubuntu/Mint or any other Linux distro share the partitions of the 1st or would I need to create another 4 partitions for each distro?

Thanks.

---

### Post by hhh on 2010-11-01
These questions are mostly a matter of choice. Why do you want to run both Gnome and KDE, isn't that just going to get confusing?

I find the 10.04 release to be rock-solid and it's a Long Term Support release, plus if you're not on a netbook there are almost no new features in 10.10, but that's a personal choice again.

If you did want both Gnome and KDE, maybe the easiest way to go would be to install Ubuntu and then ```
sudo aptitude install kubuntu-desktop
```and choose your session from the login screen.

Keeping Windows and Ubuntu on the same hard drive isn't problematic once they are both installed, but I've seen people have problems getting Ubuntu installed on Windows 7 machines. There are many tutorials online to walk you through though. In any case, it's usually recommended that you install Windows first and then Ubuntu, and then Grub2 will handle booting both.

If you are installing two Linux distros on the same machine, the order isn't too important. My choice is to install Ubuntu last and let Grub2 handle booting everything. You can always change which distro Grub will handle things though (for example, if I want my aptosid partition to handle bootloading then I boot to that OS and run the equivalent of ```
sudo update-grub
``` ...and then...```
sudo grub-setup /dev/sda
``` I say "the equivalent of" because aptosid doesn't use sudo.

The easiest way to partition is to keep Windows on one machine and do two ext4 or ext3 partitions on the other machine plus a swap partition. You can put an entire OS in one partition, and that's the default way Ubuntu, Kubuntu and standard Mint do it anyway.

---

### Post by hhh on 2010-11-01
Swap is another subject where people have all sorts of opinions, but if hard drive space isn't an issue then equal to your RAM is a good starting point, but not more than 2G RAM unless you need suspend/hibernation, in which case you need at least as much swap as RAM.

The bootable CD or DVD or USB will install Grub again over the other Grub version, this is no problem as I mentioned before.

For partitioning, you can refer to this shot of gParted and do something similar. In this shot of my slightly small hard drive, I have XP, then aptosid, then Ubuntu. I didn't allocate quite enough space for Ubuntu as I wasn't expecting it to be as solid and comfortable as it is, but it doesn't really matter to me since I don't store much on my hard drive. I used extended partitions in case I wanted to add more partitions later, again it's choice. Click for full screen...

[[IMG]http://img801.imageshack.us/img801/7797/screenshotmsa.png[/IMG]](http://img801.imageshack.us/img801/2640/screenshotkl.png)

---

### Post by oldfred on 2010-11-02
Each root partition only needs to be 10-20GB, especially if you create separate /data partition(s). 

If sharing with windows you will want a NTFS partition for any data you may want in either windows or Linux. You can also create a /data partition for any data you do not need in windows but may want to share with other linux partition. 

You should not share /home (unless you use different user IDs for each which defeats most of the purpose of sharing).

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
Some info but grub2 issues are dated, grub2 works well now for most. No separate grub partition required.
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

---

### Post by Yezinki on 2010-11-02
Thanks for sharing your experienced thoughts.

1. I want to run both Gnome & KDE because I like the layout, interface of KDE.

2. Since shall be using it on my desktop so would go by your advice Ubuntu 10.0.4 LTS.

3. By using the code “sudo aptitude install Kubuntu-desktop” hope things won’t get messed?

4. If I ever want to keep windows on this desktop that would be XP & not W7Ult , that I plan on my other machine....Linux distros on desktop & W7 on laptop.

5. IF I keep windows along with Linux distros, should they be installed with in, using webui or a separate install?

6. If I keep it pure Linux than Kubuntu install first followed by Ubuntu correct...any advantage of having them separate vs. KDE interface in Ubuntu?

7. Pros & cons of having Ubuntu & Kubuntu outside XP vs. within?

8. If I keep windows for the Dell notebook & Linux distros for  the desktop would need 2 ext4 partitions & 1 for swap...RAM on this machine is 2 GB so swap should be equal....what should  be the approx size of 2 ext4 partitions & should they both be primary?

9. I usually partition the drives using Disk Director Linux Boot CD.

10. Could you care to post 2 partition plans...1st for Windows along with Linux distros & 2nd only for Linux distros with their approx sizes, types....size of the disk is 250 GB.

Best Regards!

---

### Post by hhh on 2010-11-02
Odd that you marked this solved and still had a bunch of questions;^)

My suggestions, and I'd read through them all and the associated links if I were you, knowledge is good stuff...

1) If you like KDE, then you'll end up spending 99% of your time on it, so install Kubuntu and be done with it.

2) Install Kubuntu 10.04.

3) If you install Kubuntu and decide you want to mess around with Gnome, it would be 'sudo aptitude install ubuntu-desktop' (w/out quotes, small u, or small k for kubuntu-desktop) and then choose Gnome session from the login screen. See this for more info!!!!!...
[http://psychocats.net/ubuntu/gnome](http://psychocats.net/ubuntu/gnome)
...especially this part...> In the terminal, paste in the command

sudo apt-get update && sudo apt-get install ubuntu-desktop

You'll be presented with a very long list of software packages to be installed and then asked to confirm. Before you confirm it, consider whether you might ever want to cleanly uninstall Gnome later. If you might, then highlight (yes, with your mouse) all the packages to be installed and copy them to a text file. You can then later sudo apt-get remove and then paste back into the terminal the long list and be back to your vanilla Kubuntu. 

Bookmark that site. Ubuntu forum moderator aysiu has done a great job putting that site together and keeps those tutorials up to date with each release.

4) Fine. One question, is XP already on the desktop? If so, my suggestion would be to leave it there and install Kubuntu next to it. DEFRAGMENT XP FIRST!!! Then resize your partitions with your Disk Director or with GParted which is on the Ubuntu Live CD under System>Administration>GParted (I'm sure it's on the Kubuntu Live CD too, probably under the same menu but I don't use Kubuntu/KDE).

5) Wubi is a good way to test if you will like the Ubuntu/Kubuntu experience but is not recommended for a permanent installation. If you haven't yet, by all means install Kubuntu via Wubi, see if your system works, if you can install proprietary drivers, etc..., live with it for a couple of days, and if all is well remove it via Add/Remove Programs in Windows Control Panel. Then DEFRAGMENT YOUR DRIVE before installing Kubuntu permanently via the Live CD or via Unetbootin/USB drive. Kubuntu is available as one of the Desktop Environments option in the installer screen. I started my Ubuntu experience with Wubi, but the project doesn't look very up to date to me and I have seen people have problems with Grub as a result of using Wubi. See the WubiGuide and Psychocats for more info...
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[http://psychocats.net/ubuntu/wubi](http://psychocats.net/ubuntu/wubi)

6) See the Psychocats website. In my opinion, you should just install Kubuntu and be done with it.

7) I don't recommend installing Kubuntu/Ubuntu permanently inside of Windows. It will be a slower system and program updates could mess things up badly. Keeping Kubuntu separate from Windows is recommended. Here is a nice video of someone running the Ubuntu installer and installing it side by side with Windows. The Kubuntu installer should be almost identical, and the Windows version doesn't matter...
[http://www.youtube.com/watch?v=Taq_3LlTW_I](http://www.youtube.com/watch?v=Taq_3LlTW_I)
Easy, right? In that video, the Ubuntu partition was automatically set to ext4. I'm afraid I'm not sure if it was set up as primary or extended.

EIGHT [stupid emoticons!]) Primary partitions are fine if you are doing just 2, size is up to you, it seems you have a good bit of disk space. If you keep Windows you could still have them be primary. See this link for info on partitioning...
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://en.wikipedia.org/wiki/Disk_partitioning#PC_partition_types](http://en.wikipedia.org/wiki/Disk_partitioning#PC_partition_types)

9) You can see from my screenshot that GParted makes partitioning easy as you can quickly see what drive you're working with, what file system you are creating, if it's primary, logical, extended, linux-swap or another, if the partition is mounted at the moment and how big the partition is in relation to the entire disc space. I recommend it, but I have no experience with Disk Director.

10) If you follow the video tutorial, you won't even mess with partitioning except for determining the partition size. Otherwise, see my screenshot. After shrinking my NTFS partition, I created an extended partition with the rest of the disc space (sda2 in this case). From there I could have created as many partitions as I could fit on 70G of disc space. If you create primary partitions, you can only have up to 4. Ignore the unallocated bit, that created itself as a result of cylinder rounding, I think. Then, when I installed, I chose manual install in the installer and created the mountpoint "/" on the partition I was installing to. I didn't need to format as ext4 since I already had with Gparted, but I could of, it wouldn't have harmed anything.

!IMPORTANT: Before installing Kubuntu, I recommend burning yourself a Super Grub Rescue Disc, which makes restoring the Windows Master Boot Record a snap...
[http://www.supergrubdisk.org/category/download/supergrubdiskdownload/](http://www.supergrubdisk.org/category/download/supergrubdiskdownload/)

Of course, be careful when repartitioning, one wrong move can have dire consequences! On the plus side, it seems like you don't mind if you make a mistake on your desktop as you'll still have the laptop.

After you defragment XP, you can shrink the XP partition. At that point, IT IS RECOMMENDED THAT YOU BOOT BACK INTO WINDOWS. XP will prompt you to do a disc check... DO IT!!!!! Then boot fully into Windows. After that you should have no problems with your Windows partition.

I've concentrated on dualbooting with Windows, but that's because I don't see the point in wiping a perfectly good (for the most part) operating system. Again, DEFRAGMENT FIRST!!!! I hope this helps, post back with problems or a success story!

---

### Post by Yezinki on 2010-11-03
1. For marking solved..........poor typo..........for which I apologize.

2. Using this command, sudo aptitude install kubuntu-desktop, choosing KDE in log in session is exactly the same as Kubuntu separate install or just the lay out...does not have certain apps like vlc, wine etc?

3. Cannot install Wifi driver, though get connected via Ethernet.

Shall keep you posted about the progress.

Regards!

---

### Post by Yezinki on 2010-11-03
Where are the downloaded files/ISOs saved in Ubuntu by default & which burning software is recommended to burn them?

Thanks.

---

### Post by Yezinki on 2010-11-03
Should the KDE Desk top folder & KDEuBlog be shut down........it's settings & usefulness if any?

Thanks.

---

### Post by hhh on 2010-11-03
Where are downloaded files saved? Where did you set Firefox up to download them? Usually ~/Downloads.

You can burn and run the Kubuntu Live CD to see how similar it is to running a KDE session in Gnome. As I said, I don't use KDE. I hate the menu structure. For burning iso files...
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

The KDE desktop folder and uBlog part of the plasma set of widgets and it's usefulness is personal. Of course they can be turned off.
[http://userbase.kde.org/Plasma](http://userbase.kde.org/Plasma)

Your Wifi issue depends on what kind of card or USB adapter you are using. A Google search for your card + linux might yield a linux driver, otherwise you can probably use the Windows driver using Ndiswrapper. Open a new thread for that issue if you get stuck. Some more links...
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Yezinki on 2010-11-03
1. In Downloads.

2. Thanks for the info regarding Plasma desktop.

3. WiFi wont get installed?

Regards!

---

### Post by hhh on 2010-11-03
My last post had links on WiFi. If you still have problems, you should open another thread for that in the Networking and Wireless forum...
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

Glad you have things running, cheers.

---

### Post by Yezinki on 2010-11-03
Thanks a ton hhh.

1 last question can I install windows after installing Ubuntu & Kubuntu?

Best Regards!

---

### Post by oldfred on 2010-11-03
The main requirement for windows is a primary partition. You have to have a primary partition for windows to boot from.

Windows will also install its boot loader in the MBR, so you have to be prepared to reinstall grub from whichever version of Ubuntu you want to primarily boot from.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

It also is better to have a shared NTFS partition for any data you may want in both Linux and Windows. You can easily read the windows system partition but you also can damage it by writing into the wrong place or deleting something you should not. I only write into another system partition to make repairs and  keep most data outside the system partitions.

Older but goes over some of the issues, but use grub2 not any of the other alternatives shown:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

---

### Post by Yezinki on 2010-11-09
I tried a dual boot e XP & Kubuntu.........Kubuntu was real slow, dragging system monitor displayed Core 2 being used 99% all the time.

Had earlier tried it on the same machine no issue.

Reinstalled its running fine.......may be dual boot doesn't agree with my Sony desktop.

Regards!

---

