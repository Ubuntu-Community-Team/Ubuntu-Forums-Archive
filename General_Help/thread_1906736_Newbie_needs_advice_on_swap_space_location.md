---
title: "Newbie needs advice on swap space location"
date: 2012-01-09
forum: General Help
---

### Post by chenxinghao on 2012-01-09
I am preparing to install Ubuntu (with dual boot) on the slave drive in an existing Windows Xp Pro PC and am reading the installation instructions. My plan is to put everything related to Ubuntu on this 2rd HD, while leaving everything related to the Windows XP Pro on the C drive.
 
I have three questions:
 
(1) Which hard drive the Ubuntu swap space will be allocated on?
 
(2) Will the Windows XP Pro's system restore option be able to restore the prior MBR before the installation of Ubuntu? 
 
(3) After setting up the Windows-Ubuntu dual boot option, will the PC still be able to boot to Windows XP Pro if the 2rd HD is pulled off line?

---

### Post by imachavel on 2012-01-09
1) it will be located on whatever hard drive you decide to set up your OS on, on a swap partition, considering when the installation prompts you, that you chose to install on a swap partition. How many hard drives do you have installed as master and slave?

2) you can always use fix mbr to restore a master boot record, but why would you need to? If you install on a seperate hard drive, then you chose which hard drive to install on upon boot when you select a new boot device. If you chose the same hard drive, then the safest way to install to is on a separate partition, which hopefully you already created prior to installing the first OS on the FIRST partition. NOW, if you haven't done that, you can boot to windows, and open the linux install cd from inside windows, and chose the 'boot along side this partition' option. Although I've heard that isn't recommended

3) Well the second hd wouldn't require a second partition would it, unless you want to make it confusing. Install to that second hard drive, and it will create a brand new partition on the second hard drive. At boot just chose that hard drive instead of the other one to switch between OS'es. At this point, I'm thinking of installing a second hard drive. I've seen tooooo many posts to trust grub any more, not to mention my current grub issue.

---

### Post by chenxinghao on 2012-01-10
I have a master HD and a slave HD on this desktop PC (IBM ThinkCentre A50p), with the slave HD empty and it is to be used for Ubuntu only.
 
After reading the installation guide, I understand that I will be asked where Ubuntu to be installed and I intend to install everything related to Ubuntu on the slave HD (the 2nd HD from Linux point of view?).
 
I was not sure where the swap space will be installed on; and in this case your point is that the Ubuntu swap space will be allocated on the 2nd HD (the slave).
 
Isn't it true that the MBR is allocated on the master HD? If so, the dual-boot option seems to affect the MBR and even if I pull the 2nd HD off line (after indtall Ubuntu with dual-boot option) the MBR will stay unchanged (until modification. My question was that: would the PC still be able to boot to Windows after I pull the Ubuntu HD off line and without modifying the MBR?

---

### Post by varunendra on 2012-01-11
> **chenxinghao said:**
> Isn't it true that the MBR is allocated on the master HD? If so, the dual-boot option seems to affect the MBR and even if I pull the 2nd HD off line (after indtall Ubuntu with dual-boot option) the MBR will stay unchanged (until modification. My question was that: would the PC still be able to boot to Windows after I pull the Ubuntu HD off line and without modifying the MBR?
No, you won't be able to boot windows after pulling off the slave drive "**IF**" grub is installed on the master hdd (on which xp is installed), while Ubuntu is on the slave one.

The reason is - grub, on the MBR of the master drive, will look for its configuration file on the slave drive - which it won't find since the drive has been pulled off!

Solution is rather simple and safer - leave the master drive as it is, don't even touch it while installing Ubuntu. To install ubuntu safely on the slave drive, following would be the best way for you-

[LIST]
[*]To avoid confusion with partitions, assign relevant names to your existing partitions on the XP drive, while you are in XP.
[*]Boot with Live CD
[*]open gparted, choose the slave drive to create/edit partitions.
[*]Make sure it is not your XP drive (you can recognize that with the partition labels you assigned in 1st step)
[*]Create an ext4 partition of desired size for Ubuntu installation (recommended is 20+ GB)
[*]Create a swap partition on the same drive (recommended size is at least equal to the amount of RAM if you want to use hibernation feature, or 2GB if you don't need hibernation.)
[*]Start installation process.
[*]On the stage where you have to select where to install, choose 'manual partitioning' option.
[*]Choose the just created ext4 partition as mount point for '/' (formatting is not required)
[*]proceed with installation, and choose 'Advanced' option for Grub installation.
[*]Choose to install grub on the same drive on which Ubuntu is going to install (should be **/dev/sdb** as per your current scenario. Be cautious! it has to be sdb or sda, not sdb1, sdb2 etc.).
[/LIST]
To be 'extra-safe', just pull-out the XP drive while you are installing Ubuntu. This will avoid any possible confusion with drive/partition selection, and you also won't need to get into advance grub installation step.



This way, the XP drive and its MBR will not be touched and you can boot XP normally as if Ubuntu doesn't exist at all (regardless of whether the slave drive is plugged or not). When you need to boot into Ubuntu, just bring up the BIOS boot menu by pressing relevant hot-key during boot-up (usually it is F9, but may differ depending upon your BIOS version), and select the second hard drive to boot from.


**_PS_:**
If you prefer to pull out the master drive while installing Ubuntu (safer and recommended if it is easy for you), and later want to include XP in grub's menu, you will have to run:
```
sudo update-grub
``` command from ubuntu. You can enjoy an extra benefit by doing this. That is - permanently change the hard drive priority in BIOS boot preference, so that you don't have to bring up BIOS' device boot menu everytime you have to switch between the two OSes. You will then be able to boot both XP and Ubuntu from grub menu, while still being able to boot XP if the slave drive is pulled off (since XP MBR is still intact on the original drive).



One more thing that is worth mentioning - the XP "Restore-Point" feature only restores certain files (exe, dll, etc). It DOES NOT and CAN NOT restore MBR. The fixmbr command imachavel mentioned has to be run from XP's installation CD when you boot it with 'Recovery' option. So if you don't have the XP installation CD, simply forget it.

Sorry for the epic post, but hope you find it helpful. I'd be glad to provide step-by-step assistance if you need.

---

### Post by chenxinghao on 2012-01-11
Thank you for the epic-effort advice - now I can understand.
 
I installed Ubuntu 11.10 (made a CD disk first, since my PC, an IBM ThinkCenter A50P, doesn't boot from its USB ports. Here are what I did:
 
(1) Installed a second WD 300GB HD as the slave (formated but empty), intended for Ubuntu only; In Windows XP Pro, I named the slave drive as "Ubuntu"; the master drive, also a WD 300GB unit, is seen as "Local drive." Then I inserted the Ubuntu CD disk in the CD drive bay and shutdown the PC.
 
(2) Turned on the PC and told the PC to boot from the CD drive; It starts to install Ubuntu; When asked (with three choices), I chose "install Ubuntu along side Windows" (or something to that fact); later when asked to which partition to install, the pulldown selection lists "300 GB disk xxxxxx) with no other choice; at the lower half of the same screen, it lists "150GB for /dev/..." on the left and "150GB for Ubuntu" on the right; and then the installation process went on ... I basically let the installation process take its course with the default settings (or whatever it said on the screen) without making any change.
 
(3) The CD drive ejected; I remove the Ubuntu CD disk from the bay, closed the drive tray and hit the Enter key; the PC restarted with a list of chioces to boot from: on top is the highlighted line of "Ubuntu Linux 3.0.0.4 ....." (confusing - shouldn't it be Ubuntu 11.10?) and the PC boots Ubuntu successfully! I played a little within the desktop, such as Firefox, Libre applications and the workspace: I found out that I can not open Firefox in multiple workspaces - if Firefox is open in workspace A, trying to open a new Firefox session/window in workspace B always brings workspace A back to the full screen. The same goes with all three of the Libre applications in the launch pad/bar.
 
In the "Home Folder" I see a "300GB disk" (I guess the "Local drive" - seen in Windows XP Pro - is lost in translation) and the "Ubuntu" disk device; I could not find a way to see the usage and free space numbers.
 
(4) I shutdown Ubuntu and restarted the PC to boot to Windows XP Pro; it performed disk checking (I guess it recognized the modification to the MBR) and the all familiar Windows XP Pro came up successfully; it sees the master HD in its full size and a slave HD in a 136GB (after formating from original 150GB). Only now I realized that the 300GB slave drive was partitioned into half-half: one for Windows XP Pro and one for Ubuntu and it seems that, from Ubuntu's view, Windows XP Pro is hanging under /dev/...
 
I renamed the master HD from "Local drive" to "WinXPpro" (so that Ubuntu can pick it up.
 
I am OK with this setup for now - I guess I can always go back to let Ubuntu to claim the full capacity of the 300GB slave drive.
 
So far so good with Ubuntu. I have the following for the next few days: 
 
(a) Find ways to see the storage usage, real-time meters on CPU time, Memory usage and network load.
 
(b) Install the driver for the Netgear wireless card - the Ubuntu installation process did not recognize the card in the PC and I have not found "detect new device" feature in Ubuntu.
 
(c) Look for a (stable) C/C++ sofware development kit/package for Ubuntu and install.
 
(d) Look for a emacs-like editor. 
 
(e) How to get to HELP in/from the Ubuntu desktop screen?
 
Your advices and help are very much appreciated.
 
Thank you.

---

### Post by varunendra on 2012-01-12
You're welcome :)

The label "Logical drive" means the partition  is not labelled at all, hence the generic term - "Local drive" in  windows. The generic term in linux is different for such partitions,  depending upon the flavour you are using. In ubuntu, it is usually "**<*partition size*> Filesystem**", but if the partition is labelled (i.e., has a name assigned), it'll be listed by its name.

As for your current installation, here are a few things I can explain based on your description:
(1-2)  the option you chose (alongside windows) forces you to install Ubuntu  on the same hard drive on which windows is installed, hence no option to  choose the other HDD in the drop-down list. In order to install it on  the slave one, you had to choose "Something else" option, which would  have allowed you to manually select drive and partitions. Sorry, I  didn't mention it in my earlier post because I forgot that the  installation interface has been slightly changed since 11.04 onwards. It  used to be something like "Manually choose.." in earlier versions (I'm  still on 10.04). So now your XP drive's MBR has been overwritten by  Grub2. But that's alright because Ubuntu is also on the same hard drive  now, so you can safely pull-out the slave drive whenever you want,  without affecting the OS booting.

(3) In the grub menu, you see  "Ubuntu with Linux 3.0.0.4.." because it shows the OS name + kernel  version in use, not the OS version. The OS is Ubuntu, and the kernel is  3.0.0.4 (you'll see more of them whenever one adds up during an update).
The  behaviour of Firefox or other apps is normal in accordance with Unity  Desktop scheme. They find it useful to avoid opening multiple instances  of same apps (while some of us find it irritating). If you like opening  separate instances of them on separate workspaces, you'll either have to  use a different Desktop environment, or may have to do some tweaking in  Unity that I'm unaware of. [COLOR=DarkRed]*[Update: Just realized that you can right-click on any launcher to choose "New window/document" to open a new instance of the application on the same or different workspace]*[/COLOR]

In your home folder, you see the "300  GB disk" because it is Ubuntu's way to list a partition which has no  label. "Local drive" is actually not a label, it is windows way to list  partitions without a label. As soon as you assign it a label either in  Ubuntu or Windows, it will show up by that label in both OSes. You can  see usage statistics only when a partition is "mounted" (goto the drive  > right-click > properties). To get a detailed usage info, you can  use "Disk usage analyzer" application (search for it in dashboard >  More apps, or type the name in search-box).

(4) XP disk checking is normal, because you changed the size of the partition without its knowledge ;)



Now answers to your questions:

(a)  For realtime CPU/Memory/Swap/Network usage statistics, you can use  "System Monitor". To see Storage usage, try out the "Disk usage  analyzer" application suggested above (you can also invoke it by global  shortcut **Alt+F2 >** type **baobab **> press **enter**)

(b) Start a new thread with your networking support question and post its link here. I'll be glad to help if I could.

(c)  For C/C++ programming, try "CodeBlocks". It is in the Software Center.  For better suggestions, post the question in "Development &  Programming > Programming Talk" section of the forums.

(d) I'm not aware of emacs, but typing "emacs" in Software center brought up "GNU Emacs" on the top! :)

(e) In ubuntu dash, type "help".


**_PS_:**
Now  that the original question of this thread is solved, I suggest you to  mark it as [Solved] (follow my signature to see how), and post new  threads in relevant sections to get better and precise help on specific  topics.

Hope you enjoy Ubuntu. Have a nice day!:popcorn:

---

### Post by chenxinghao on 2012-01-12
Thank you for all the inputs.
 
Actually, the 2nd HD(300GB)  seems half taken by Ubuntu and helf taken by Windows XP Pro. This is because in Windows XP Pro's "My Computer, it shows the full size of the master HD (WinXPpro) and the slave HD (also a 300GB) in half the size (with nothing on it).
 
In Ubuntu's Home Folder, it shows the master HD (WinXPpro) with all the Windows folders and files plus a few new files (e.g., pagefile.sys of 4.3GB) and folders (System Volume Information, MSOCache and RECYCLER etc.). The 2nd HD shows  just two folders: RECYCLER and System Volume Information.
 
The Disk Usage Analyzer shows the following:
 
Total filesystem capacity: 594.6GB (used 17.3GB avaliable: 577.3GB)
 
Folder                 Usage           Size
/                         100%           16.8GB
>media                80.1             13.5GB
>usr                   12.8              2.1GB
>var                    4.4             744.1MB
....
 
 
For the top two entries, the usage is already full or close to full. Should I be worried?
 
Also, this analysis doesn't show which folders sit on which HD. Is there a way to know?
 
Soon after Ubuntu is up, the two HD icons will show up at the bottum of the Launcher bar at left. Right click on either pops up the HD name with Eject next to it, nothing else. Where is the Properties button/selection that you mentioned?
 
These are my last questions for this thread and I will close it soon.
 
Thank you very much.

---

### Post by varunendra on 2012-01-13
> **chenxinghao said:**
> Actually, the 2nd HD(300GB)  seems half taken by Ubuntu and helf taken by Windows XP Pro. This is because in Windows XP Pro's "My Computer, it shows the full size of the master HD (WinXPpro) and the slave HD (also a 300GB) in half the size (with nothing on it).
Then I've no idea how it handles the drives/partitions in "Install alongside windows" option in various situations, because when I simulated a similar setup in a virtual machine (one 20GB master drive with single ntfs partition + one 20GB slave drive with XP on it), it always picked up only the XP drive, no matter how I connected it or whether the blank drive was formatted or not.

But anyway, as I mentioned in my first post, if Ubuntu has got installed on the slave drive while its boot loader (GRUB2) is on master one (the XP drive), then you won't be able to boot XP if the Ubuntu drive is disconnected. Although it is possible that XP and GRUB bootloaders get installed on different drives (it depends on how they 'recognize' HDD orders during installation), this chance is very 'thin' since you didn't change the boot order in BIOS before or after installation- meaning - BIOS is getting 'Grub' now where it used to see XP bootloader earlier.

If you want to confirm exactly what is where now, please download [Boot Info Script]("http://bootinfoscript.sourceforge.net/") and run it as explained on the download page. Then post back the contents of its RESULT.txt file here.

 
Now a few more explanations to what you 'see' in Ubuntu:

> **chenxinghao said:**
> In Ubuntu's Home Folder, it shows the master HD (WinXPpro) with all the Windows folders and files **plus a few new files (e.g., pagefile.sys of 4.3GB) and folders (System Volume Information, MSOCache and RECYCLER etc.). The 2nd HD shows  just two folders: RECYCLER and System Volume Information**.These 'new' files and folders were always there, only hidden by default. If you enable "show hidden" as well as "show system files" in XP, you'll be able to see them from XP too. They are hidden so that you don't accidentally delete them. In Linux, the way to 'hide' files/folders is different - by adding a 'dot' (.) before its name. pagefile.sys is virtual memory in windows - like 'swap' in linux. Sys.Vol.Info is where 'Restore Points' are created and restoration files are stored in windows, and 'Recycler' is the folder where your 'deleted' files (in XP) are stored that show up in 'Recycle Bin' until you permanently delete them. So if you delete them in Ubuntu (intentionally or accidentally), it won't corrupt XP, but you will loose your current restore points and any files that are in Recycle Bin of XP, and they will recreated fresh as soon as you log into XP again. So better leave them as they are.
[COLOR=DarkRed]**EDIT:** ..and the MSOCache - as the name suggests - is the cache folder for MS Office installation. It is used to repair or add/remove features to MS Office installation when it is required. So if it is deleted, you will have to provide the installation source to the Office installation if it got corrupted or needs to add features.[/COLOR]



 > **chenxinghao said:**
> The Disk Usage Analyzer shows the following:
 Total filesystem capacity: 594.6GB (used 17.3GB avaliable: 577.3GB)
 
Folder                 Usage           Size
/                         100%           16.8GB
>media                80.1             13.5GB
>usr                   12.8              2.1GB
>var                    4.4             744.1MB
....
 
For the top two entries, the usage is already full or close to full. Should I be worried?

Also, this analysis doesn't show which folders sit on which HD. Is there a way to know?
  No there's nothing to worry about in above details. Note that that "100%" is only 16.8 GB in size (of 594.6 GB total). The Disk usage analyzer always shows only the space 'usage' details of a drive/folder, and lists the total usage as 100%. For example if you scan a folder of 500MB size of data in it, the analyzer will show on top the 500MB as 100%, then below that it will show the usage details of the subfolders which have occupied that 500MB space - listing them in descending order (max. sized folder on top, least sized folder at bottom).
 
You have scanned the 'Filesystem', that is, root of Ubuntu. It will show the drives/partitions as 'folders' where they have been 'mounted', and if a drive has not been mounted, it will not show up in the scanning results. This behaviour is perfectly ok and in accordance with Linux filesystem hierarchy. You just need to get used to it.

But for now, you can get partition-wise details by scanning them individually by-

[LIST]
[*]Click on "Scan a folder" (instead of scanning filesystem)
[*]in the browser, click the partition you want to scan (listed as xxGB filesystem, or by its name). Doing so will automatically 'mount it, just click 'Open' button.
[*]Remember, it will ALWAYS show 100% on top as total usage :)
[/LIST]


> **chenxinghao said:**
> Soon after Ubuntu is up, the two HD icons will show up at the bottum of the Launcher bar at left. Right click on either pops up the HD name with Eject next to it, nothing else. Where is the Properties button/selection that you mentioned?Oh, my mistake, I wasn't clear enough..
You have to go 'into' the partition and then right-click in any empty area of it. You can do so by clicking the drive/partition icon either in the launcher or in the side pane of any opened window (to open and get into it). That will give you the 'Properties' option in the bottom of right-click drop-down menu. This property box will also show you the remaining space on that partition.
[COLOR=DarkRed]**EDIT2:** You can also use **df -u** command in terminal to get a detailed "disk-free" info.[/COLOR]

A few more things worth mentioning here:

Not only in the partition itself, but whenever you right-click in an empty area of 'ANY' folder, it will show you - among other things about the folder - the free space remaining on the partition on which the folder is "physically" located. For this reason, you may sometimes get different 'free space' numbers on different folders in "filesystem" because although they may appear in the same parent folder (/media for example), they are physically located on different partitions. Scared? ;) Don't worry, you'll find it useful more than you might be confused now after using Ubuntu for a while.

Another thing - most of the 'methods' I've mentioned in this thread and those you may find later are bound to Unity specific 'Desktop-Environment'. For a wider range of experience, try different Desktop-Environments, and choose the one that suits you best. For example, LXDE (default in Lubuntu) is popular for its simplicity and lightness on system resources, XFCE (default in Xubuntu) is also popular for its lightness while being almost equally featured as GNOME (which was default for Ubuntu in versions earlier than 11.04. Now Unity has replaced it). KDE is (arguably) considered to be most resource hungry in its attempt to offer maximum eye-candy and features. (If I remember correctly, it shows partition-usage meter by default beside each mounted partition in its browser - thought it might interest you ;)). For a better idea about different DEs, you should read this old, but very useful post by our dear friend late Robin: [http://ubuntuforums.org/showpost.php?p=10653379&postcount=11](http://ubuntuforums.org/showpost.php?p=10653379&postcount=11)


Lastly, you don't need to thank me. Actually I'm enjoying this thread. Your questions remind me of the days when I first came in touch of Ubuntu (before that I had tried Red Had 9, got scared but kept using it for 6-8 months without knowing that we can 'mount' and access windows partitions in it ;)). This way, I think I need to thank you for returning me moments of my old exciting days :).

Hope you didn't fall asleep while reading my 'tiny' post. If you have any more questions, feel free to ask. God bless you with the courage to read more.. :popcorn:

---

### Post by chenxinghao on 2012-01-13
Thank you for being so patient and engaging in answering my "curiosities."
 
The "100%" under USAGE for "/" is confusing and, perhaps, misleading: 100% of what? "/" allocation and partition size (which I don't know how much)? HD storage space? ...
 
To me, anything 100% used is a time to consider adding additional resources (in this case the storage or partition size).
 
Anyways, thank you very much again and "case closed."

---

### Post by varunendra on 2012-01-13
> **chenxinghao said:**
> 
The "100%" under USAGE for "/" is confusing and, perhaps, misleading: 100% of what? "/" allocation and partition size (which I don't know how much)? HD storage space? ...
 
To me, anything 100% used is a time to consider adding additional resources (in this case the storage or partition size).
Ever seen a pie-chart representation of a marketshare or something alike? Think of it as exactly the same - a graphical representation of marketshares of a product, on a spreadsheet or presentation chart.

Let us say 150 million units is the total consumption in the market. Then we will represent that 150 million as 100%. Then we will draw different pie-sections representing different %age of shares that add up to complete that 100% which is just 150 million units.

It does not mean there is no more space in the market for further consumption. It is just meant to give you the idea of shares each party holds at any given time.

Disk usage analyzer is just that. It is not meant to tell you the remaining space; that is something you can get from properties or *df -h* command or various other ways. It is there to give you a better idea of 'who' has occupied how much space on a particular drive or folder, and this info can be useful in several ways.

So it is 100% 'OF' the total data that exists on the subject folder or drive, and the following percentages are the 'shares' that add up to make-up that 100%.

As I said, you will find it very useful once you get used to linux ways (I won't say at this time whether it is a better way or not; that is something everyone has to decide for himself. But mind you - most of whom start liking that way, never turn back to the 'other' ways).

Hope to see you around :)
Cheers!

---

### Post by chenxinghao on 2012-01-13
I get it. And whatever the current "usage" (of disk space) is, each item shows the % of the total, an indirect reporting for usage.
 
In other words, "/" will always be 100%, a constant. The confusing stems from the label of the column, USAGE. It would be useful in the line for "/" to list the exact size of disk allocation instead of 100% all the time. Then, the % numbers down below make more sense. Anyway, just a newbie's crazy way of looking at it.
 
Thank you very much and I start to like Ubuntu and the community.
 
Hope to hear from you on other topics.

---

