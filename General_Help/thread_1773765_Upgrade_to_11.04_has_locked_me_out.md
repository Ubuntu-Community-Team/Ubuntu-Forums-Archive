---
title: "Upgrade to 11.04 has locked me out"
date: 2011-06-02
forum: General Help
---

### Post by MickeyPilgrim on 2011-06-02
Hi All,
1.I'm not a complete newbie, but have very limited command line experience.
2.After a year on Lucid 10.04 I installed all updates and did an online upgrade to 10.10 Great!
3.Enthusiasm got the better of me and I clicked the upgrade to 11.04. Big mistake.
4.I get the 11.04 desktop, but it has no response to mouse clicks. I'm locked out - can't click to log in to my private files.Is all lost? The cursor moves OK and the keyboard works (They are wireless and I guess I'll put on wired ones to eliminate any problem there as I fix stuff.)
5.I have never done my own installation or partition work.
6.There are a few things I did not back-up, and I'll miss them. Some bookmarks in Firefox may be impossible to ever find again.
I really need the Evolution e-mail

I dual boot with XP and am now booting up from an old 9.04 disk that I found.
I thought I was doing a minor upgrade to Natty 11.04, but the screen tells me I have 2.6.32-32-generic kernel Is there any going back?

Mickey

---

### Post by garvinrick4 on 2011-06-02
Get to 11.04 blank desktop:
Hit /ctr/alt/F1 and sign in with user name and password
```
lsb_release -a
```What did that tell you: If you upgraded to natty it will tell you so, if so.
```
unity --reset
```When or if you have internet connection wired or wireless
```
sudo apt-get install compizconfig-settings-manager
```ctrl/alt/F7

then open a terminal ctrl/alt/t
```
ccsm
```make sure ubuntu unity plugin is checked:

---

### Post by MickeyPilgrim on 2011-06-02
garvinrick4

Many thanks. Remember I'm lacking experience beyond what I read in Ubuntu For Non-Geeks"   I shure hope you will check back in a bit while I do what you suggested.
You know your answer came to e-mail (that I have to access through webmail) and the code comes through OK, but your words of direction are eliminated. 
MickeyPilgrim

---

### Post by sanderj on 2011-06-02
> **MickeyPilgrim said:**
> Hi All,
1.I'm not a complete newbie, but have very limited command line experience.
2.After a year on Lucid 10.04 I installed all updates and did an online upgrade to 10.10 Great!
3.Enthusiasm got the better of me and I clicked the upgrade to 11.04. Big mistake.
4.I get the 11.04 desktop, but it has no response to mouse clicks. I'm locked out - can't click to log in to my private files.Is all lost? The cursor moves OK and the keyboard works (They are wireless and I guess I'll put on wired ones to eliminate any problem there as I fix stuff.)
5.I have never done my own installation or partition work.
6.There are a few things I did not back-up, and I'll miss them. Some bookmarks in Firefox may be impossible to ever find again.
I really need the Evolution e-mail

I dual boot with XP and am now booting up from an old 9.04 disk that I found.
I thought I was doing a minor upgrade to Natty 11.04, but the screen tells me I have 2.6.32-32-generic kernel Is there any going back?

Mickey

When you boot Ubuntu, do you still get the login screen? Does it look like this:

[http://4.bp.blogspot.com/-SC0X_SIdupw/TZIsmY73jyI/AAAAAAAACA8/l2ZCvM8OdJw/s1600/Ubuntu-GNOME.png](http://4.bp.blogspot.com/-SC0X_SIdupw/TZIsmY73jyI/AAAAAAAACA8/l2ZCvM8OdJw/s1600/Ubuntu-GNOME.png)

If so: does your mouse still work at that moment? If so, can you select "Classic desktop (no effects)" like in the screendump, and then login?


HTH

---

### Post by MickeyPilgrim on 2011-06-02
garvinrick4

I got the blank desktop. Had a monitor problem that dropped the "left-most character" but I think my notes will make sense to you.

lsb_release -a    told me,
LSB Modules are available
  stributor ID Ubuntu
  scription Ubuntu 11.04
release 11.04
code name naty


unity --reset told me,

Warning no DISPLAY variable set,
setting it to :0   aceback (most recent call last):
File "/usr/bin/unity", line 198, in <module>
reset_unity_compiz_profile ()

File "usr/bin/unity", line 74, in reset_unity_compiz_profile except GError,e"

  me Error: global name' GError is not defined

:)garvinrick4  ....How do I get out of the blank desktop? I tried "shutdown, r, and -r" but finally had to hit the power button.  Oh, I finally found & fixed the monitor's horizontal setting - hope the above makes sense. Thank you for your time and consideration.
MickeyPilgrim

---

### Post by MickeyPilgrim on 2011-06-02
Hi Sander,
  The mouse will move the cursor, but clicks have no effect - neither left or right clicks.
  I do not get the desktop you linked to. My old 10.04, and then 10.10 opened on a password free desktop named "pass" so others had some access to the computer. I would just change user to "MickeyPilgrim" to get to my stuff.
  After this upgrade I would have a Unity desktop with icons all over on the left. But, of course, it did nothing when I clicked on anything.

Thanks for your time and thought.
MickeyPilgrim

---

### Post by garvinrick4 on 2011-06-02
You can try to reset compiz settings:
```
gconftool-2 --recursive-unset /apps/compiz 
```

---

### Post by garvinrick4 on 2011-06-02
> :smile:garvinrick4   ....How do I get out of the blank desktop? I tried "shutdown, r, and  -r" but finally had to hit the power button.  Oh, I finally found &  fixed the monitor's horizontal setting - hope the above makes sense.  Thank you for your time and consideration.
MickeyPilgrim 	

To get out of  desktop:
ctrl/alt/F1
to get back to desktop
ctrl/alt/F7
You can run commands from there it is the terminal:

And you can run to restart:.
```
sudo reboot
```
```
sudo shutdown -r now
```
Now below to shutdown:
```
sudo halt
```
```
sudo shutdown -h now
```

---

### Post by garvinrick4 on 2011-06-02
Mickey Pilgram here is a kind of Cheat Sheet with some short commands
that I had in a Tomboy note, old or new they are worth keeping around for
a New linux user. There are not any dpkg commands in here I do not believe
that is a nice command to learn in Debian. Basic commands below:
[SIZE=2]Beginners Cheat Sheet:[/SIZE]
```


Make bash script execute without chmod:

sudo bash ~/Desktop/boot_info_script.sh  (after ~/location/file_name.sh)


Medibuntu key:
gpg --keyserver keyserver.ubuntu.com --recv 2EBC26B60C5A2783

gpg --export --armor 2EBC26B60C5A2783 | sudo apt-key add -

stop and restart network below
sudo service network-manager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state
sudo service network-manager start

gedit /var/lib/NetworkManager/NetworkManager.state

iwconfig
sudo ifconfig wlan0 up (activate radio signal)
ifconfig wlan0 (check out wifi)
iwlist scan (scan all ssid)
iwlist wlan0 scan (scan wifi ssid)


Make executable and execute.
chmod +x wireless_script.sh.
./wireless_script.sh



sudo apt-get upgrade && sudo apt-get upgrade (to fetch upgrades.) 



sudo aptitude update && sudo aptitude upgrade 
My preference to use aptitude:
sudo apt-get install aptitude 

sudo apt-get install nautilus-open-terminal (open in terminal)

sudo service gdm restart (restart gdm ( desktop)

which (package name) path to:

smbtree (samba tree)

ifconfig -a (internet cards and IP address.)
iwconfig

gedit /var/log/apt/history.log (log of upgrades and removals)

gedit /var/log/aptitude

testparm -s (what samba shares looks like)

pcmanfm (natty file manager)

gconftool-2 --recursive-unset /apps/compiz (reset compiz settings)

unity --reset (reset unity)

sudo service gdm restart

gnome-session-save --kill (logout-terminal)

gnome-appearance-properties (appearance package)

uname -r (kernel version)

/usr/lib/nux/unity_support_test -p (test if unity is 3d)

lsb_release -a (ubuntu version)

uname -a (get all kernel info) 

dpkg -L <package name> (path to package)

gedit /var/log/aptitude

gedit /var/log/apt/history.log

sudo lshw -c video (video driver)

Ctrl+Alt+Bksp (restart X if frozen)

sudo apt-get -f install (fix broken packages) 
dpkg --configure -a (fix broken packages)

sudo apt-get clean (will clean out cache of packages in system) so as to fetch new package from repository. 

sudo parted -l (in gigs)

Medibuntu key
wget --quiet [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O - | sudo apt-key add -

sudo update-grub (use everytime you change grub menu) 

sudo grub-mkconfig (will make a new grub config file) 

gksudo gedit to "path"such as /etc/fstab (will open gedit in root 
always use gksudo for opening file system in root from command line.) 

sudoers conf. for longer time in root.
Defaults env_reset,timestamp_timeout=20

Mute Fix: load-module module-device-restore in /etc/pulse/default.pa with #load-module module-device-restore 

sudo dpkg --get-selections > installedsoftware (installed software)

sudoers conf. time stamp -1 =whole session
Defaults env_reset,timestamp_timeout=20


Plymouth themes install
sudo update-alternatives --config default.plymouth 
sudo update-initramfs -u

No password login
sudo gpasswd -a $USER nopasswdlogin


ALT/F2 together type in "gksudo nautilus" and run wiil open file system in root. 


uname -a (show version UBuntu installed) 

df -h (mounted drives) and % used..

aptitude show "package name" (will show if installed and what it does) 

grub-install -v (version of grub)

sudo blkid ( show all labels with sdxy numbers 

sudo fdisk -l (Show all partitions by sdxy numbers 

Run fsck (never on mounted drive) like a chkdsk in Windows. 
sudo e2fsck /dev/sdx# 

Start graphic drivers first in boot #540801 launchpad 
sudo -i 
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash 
update-initramfs -u 

sudo chown -R rick:rick /path/to

aplay -l (audio) 

lspci -k (cards and drivers)

sudo lshw -C network (network cards)
sudo lshw -C network > network.txt 

lspci | grep VGA ( graphics card) 

sudo lspci -v | less (Cards & Drivers) 

{Download boot script. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) 
Make sure script is on Desktop. 

Run this and Results of Script will be on Desktop. 
sudo bash ~/Desktop/boot_info_script*.sh } 

Computer info: lshw | less (everything) 

Samba password: sudo smbpasswd -a linuxcss 

grep menuentry /boot/grub/grub.cfg

grep upgrade /var/log/dpkg.log

grep 01-27 /var/log/dpkg.log | grep upgrade

grub-probe -t device /boot/grubhttps://help.ubuntu.com/community/Grub2#/etc/default/grub

Windows 7 and Vista repair disks.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
  
Best web page grub: 
[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)

FIX

Grub2 was installed with Windows system partition chosen as the root-directory. 
This causes the folder /boot/grub to be created on the Windows system partition. 
Since ntfs partitions are case insensitive this leads to confusions between "/boot" 
and the already existing folder "/Boot Solution 
Boot into your Linux OS and deleted or rename the folder /boot on the Windows system partition. 
Make sure that your don't delete the /Boot folder. 
The /Boot folder contains the file "bcd" which is necessary to boot Windows Vista/7. 

nomodeset

Ubuntu 10.04 LTS enables the new kernel-mode-setting 
(KMS) technology by default on most common video chipsets. 
While this is a major step forward for the graphics architecture in 
Ubuntu, in some rare cases KMS will prevent your 
video output from working correctly, or from working at all. 
If you need to disable KMS, you can do so by booting with 
the nomodeset option. You can also save this setting so that 
it's applied at every boot by adding it to your grub config 
(for GRUB 2: edit /etc/default/grub and add nomodeset to 
GRUB_CMDLINE_LINUX, then run sudo update-grub


Gparted sites
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/Ho...sAndPartitions](https://help.ubuntu.com/community/Ho...sAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

This is for Microsoft fix mbr Vista and 7
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Below XP
[http://support.microsoft.com/kb/330184](http://support.microsoft.com/kb/330184)

INstall grub to mbr use your own sda#
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

chroot (drs305) copy and paste please:

From live Cd or another install with same architecture (32 or 64 bit) Will mount partition I am using . 
Will mount and bind /dev /dev/pts /proc /sys. Will copy internet connection from live cd. 
Will chroot (get into root of sda5). apt-get update to check internet connection
install grub to mbr (master boot record) and now this install controls grub. 
Updates the grub to install all other O.S's in grub config and menu entrys. Exits root. Unmounts (umount is right)
/dev/pts /dev /proc /sys. Unmounts /mnt where sda5 was mounted. Reboots. Commands below.

sudo mount /dev/sda5 /mnt
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done 
sudo cp /etc/resolv.conf/mnt/etc/resolv.conf
sudo chroot /mnt
apt-get update
grub-install /dev/sda
update-grub
exit
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
sudo umount /mnt
sudo reboot

[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099") 

Chroot is the best way to install grub I believe and you can update-grub while in chroot.
There are many ways to install grub some with just a couple of commands this way makes sure for new user that it gets done.

This is chroot another way with internet connection for what needs to be accomplished:

sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev 
&& sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys 
&& sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt 

##run anything you want without sudo:
dpkg --configure -a
apt-get update && apt-get upgrade
exit

sudo umount /mnt/dev/pts && sudo umount /mnt/dev && 
sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt


Test disk windows boot repair

You can repair the boot sector of Windows system partition via "fixboot" from a Windows XP CD, 
or "bootrect /fixboot" from a Windows Vista/7 CD. But in my experience testdisk works best in this situation. 
So boot into a Linux OS or Live CD. If your system uses "apt-get" and has "testdisk" in its repositories 
(in Ubuntu: the universe repository needs to be enabled), you can install and run testdisk via 
sudo apt-get install testdisk
sudo testdisk
First screen: Select "No Log" and press enter.
Second screen: Select the hard drive containing the Windows system partition and choose "proceed".
Third screen: "intel"
Fourth screen: "advanced",
Fifth screen: Select the Windows system partition and choose "boot"
Sixth screen: "BackupBS"
Seventh screen: type "Y" to confirm

then press "q" a few times to quit testdisk, reboot and see whether you can boot into Windows.
Then go to linux and run update-grub


Install Windows bootloader with Linux Live CD: 

Restore basic windows boot loader - universe enabled 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Mute Fix: load-module module-device-restore in /etc/pulse/default.pa with #load-module module-device-restore 


XP fix boot 
How to restore the Windows install XP bootloader For this you will need your Windows install  XP installation CD. 
Boot into it now. You will get to a part where it asks if you want to repair or recover. To do so, press "r". 
If prompted, enter your Windows install grub XP administrator password. 
This will leave you at at a command line, so type in the following two commands: 

Code: fixboot 

Code: fixmbr 

Code: exit 

Vista and 7 fix boot 
How to restore the Windows install grub / Vista or 7 bootloader To restore the 
Windows install grub bootloader, you must first boot off your Windows install grub 
Vista/7 installation DVD. If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, 
you can get the same effect with a Vista recovery disk, which you can download for Vista or Win 7. 
When you get to the Regional settings, select your Location/Keyboard setting then click next. 
On the next page you must click on "Repair your computer." On the next page, if it finds your 
Windows install grub Vista/7 installation, make sure it is UNSELECTED before clicking next. 
Then click on "Command prompt". From there, type in the following: 

Code: bootrec.exe /fixboot 

Code: bootrec.exe /fixmbr 

and click "Restart." 




Suppose you have a source file name src.tar.gz, what you do initially is that you 
need to extract the source files and then in the terminal&#8230;. 
navigate to the folder where the source file is extracted using the cd commands&#8230;.. and then 
type the following&#8230; 

./configure 

make 

sudo make install 

clean install 

lets see what each one of them does&#8230; 

./configure&#8230;.. checks whether the required dependencies are available on your system or not&#8230;.. if not an error is reported&#8230;. 

make...... compiles the source code and make install is used to install the program in to the location 

if it asks for an installation location it is recommended to install all the source to /usr/src 

clean install...... removes any temporary files created in the installation process of the source and thats it your source file in installed in your system. 

UPGRADE Debian Way && My way and source.list upgrade. 

For command line upgrades run: 

Code: 
sudo aptitude install update-manager-core 
sudo do-release-upgrade -d 

BTW, if you want to upgrade without the tools, I think it is wise to do it the Debian way: 

# Change sources to new release 
perl -p -i.lucid -e 's/lucid/maverick/' /etc/apt/sources.list 

# Start upgrading to new release 
sudo aptitude update 
sudo aptitude install dpkg aptitude apt 
sudo aptitude safe-upgrade 
sudo aptitude full-upgrade 

My preferred Way to UPGRADE Verision: 
sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 

[COLOR=Red]##[/COLOR]Ubuntu recommends update manager in GUI for all dist-upgrades[COLOR=Red]##[/COLOR]

Pulse audio link
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

```

---

### Post by MickeyPilgrim on 2011-06-02
GARVINRICK4
Entering 
gconftool-2 --recursive-unset /apps/compiz
didn’t  do anything
adding a space,
gconftool -2 --recursive-unset /apps/compiz
gave me this instruction,
Error while parsing options: unknown option -2
Run gconftool –help to see a full list of available command line options
So, I did that. And I have tried all kinds of things to follow those instructions. I’ve entered –h, and –help, and gconftool [OPTION], and gconftool [-h]     And nothing works that I can see.
Now, I don’t know anything about compiz, except for what I got from Google and wiki compiz. And I can’t find any directions to guide me as I “try and reset compiz settings”. I’m wondering why this special effects interface should be keeping 11.04 from getting my mouse click, effectively locking me out from Log In.
So, I’m hoping you can point me in the right direction. I posted this same basic problem to the forum “Installation & Upgrades” yesterday, and never had any suggestion offered. [http://ubuntuforums.org/showthread.php?t=1773201](http://ubuntuforums.org/showthread.php?t=1773201) 
 Am I in the right forum? Is this why people subscribe to Canonical?
Please excuse my being so cranky, but I had read that if an upgrade didn’t work, I could select a previous version. At boot up, I am still offered a choice of XP, Ubuntu with Linux 2.6.38-8, or “previous version” – but no previous version is there. Is there a forum that would guide me to log in and recover vital Evolution e-mail?

MickeyPilgrim

---

### Post by garvinrick4 on 2011-06-02
At log in Window click on your user name then go down to bottom bar and there
will be a button or to switch to classic Ubuntu that does not take 3D. Should be
able to run classic Ubuntu instead of Unity interface. Change to classic ubuntu and log in.
Have you run this to see if you machine is 3D capable:
Should all say yes.
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by garvinrick4 on 2011-06-02
> GARVINRICK4
Entering 
gconftool-2 --recursive-unset /apps/compiz
didn’t  do anythin
You won't see it do anything. 

#Are you 3D capable?

---

### Post by MickeyPilgrim on 2011-06-02
I am away from the desk now, but can you tell me- Is there a way to click on a user name or a button by using the keyboard? As you may remember, the mouse clicks do not get any response. It would be great if this could be done by keyboard.

MickeyPilgrim> **garvinrick4 said:**
> At log in Window click on your user name then go down to bottom bar and there
will be a button or to switch to classic Ubuntu that does not take 3D. Should be
able to run classic Ubuntu instead of Unity interface. Change to classic ubuntu and log in.
Have you run this to see if you machine is 3D capable:
Should all say yes.
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by garvinrick4 on 2011-06-02
Do you still have that install disk? Do you know your sda number of linux install.
will show you if you run:
```
sudo fdisk -l
``` (lower case L)
It will be like sda1 maybe or sda5 maybe or post and I will pick it out.
I will give you some copy and pastes for the Live CD where we can get into
the root of your 11.04 install and try to fix it. Just need the sda# and you have
to have a install Cd and choose Try Ubuntu instead of install and that is then a Live CD.
Has to be the same architecture 32 or 64 bit. Most likely 32 bit.

---

### Post by MickeyPilgrim on 2011-06-03
Garvinrick4
Hi,

usr/lib/unity_support_test -p
told me,
Error: Unable to open display
Segmentation fault

================================

sudo fdisk -l
told me five lines that do not seem pertinent about disk size sectors, etc. Then it told me,

Device    Boot Start   End   Blocks    ID  System 
/dev/sda1   *  1     9931   79769858+  7   HPFS/NTFS
/dev/sda2      9931  19458  76519425   5   Extended
/dev/sda5      9931  19064  73357321  83   Linux
/dev/sda6     19064  19458  3161088   82   Linux Swap/Solaris

============================================================

garvinrick4 asked,Do I have the install disk?

No.  

  I followed instructions from "Ubuntu For Non-Geeks". After doing all updates on the 10.04 I had installed after a motherboard failure, I upgraded to 10.10. It went so well that I decided to hit the upgrade to 11.04. That's what has caused my disaster. No disk involved. I get in now through an old 9.04 disk.

  Frankly, I don't get why ubuntu even offers that upgrade button on something as major as a new kernel. Many newbee problems on the forum deal with upgrades. The "Upgrade & Installation" forum is not well tended and the best advice is to back up and do a new clean upgrade installation.  
  It feels like a dirty trick has been pulled on me. I followed instructions, OMGUBUNTU is daily reading, I watch the forums. I trusted what I read- that if an upgrade did not work out then I could boot into the prior version.
  But in the hours between the move from10.10 to 11.04 I saved some important material that wasn't backed up. I'm  screwed. The flaw isn't in the programing. There should not be a button inviting anyone to do what I so regretfully did. Ubuntu Quicksand

MickeyPilgrim (Apologies for the rant)

---

### Post by garvinrick4 on 2011-06-03
You have a 9.04 disk use it.
Put in your install CD and choose Try Ubuntu and get internet working(firefox works)
and open a terminal and copy and paste these one at a time: Some are long just copy
and paste whole thing into. Trying to fix install is what we are doing. Lets see if it can be straightened out.
```
sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /sys /mnt/sys && sudo mount -o bind /proc /mnt/proc && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt 

``````
dpkg --configure -a
``````
apt-get update 
``````
apt-get upgrade
``````
dpkg --configure -a
``````
exit
``````
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt
``````
sudo reboot
```#Now Choose linux and hope she boots up for you.

---

### Post by sanderj on 2011-06-04
A problem with this forum is when different people give different advices to the same original poster: annoying and confusing for everybody.

And, yes, I'm exactly going to that. I apologize for that.

The OP said in his first post:

> **MickeyPilgrim said:**
> Hi All,
1.I'm not a complete newbie, but have very limited command line experience.

<snip>

6.There are a few things I did not back-up, and I'll miss them. Some bookmarks in Firefox may be impossible to ever find again.
I really need the Evolution e-mail



There has been a lot of impressive advice using the command line. However, if does that does not work for the OP, here's my advice:

[LIST=1]
[*]Live-boot Ubuntu for a test/try-run
[*]mount the old harddisk (via the GUI: Nautilus, and then walk to the harddisk)
[*]copy the relevant stuff from the old home directory to an external drive (hard disk or usb stick or maybe CD/DVD), and 
[*]then re-install Ubuntu on the harddisk.
[*]boot the freshly install Ubuntu and copy back the relevant stuff from the external drive
[/LIST]

If the OP wants to do the above, here are the relevant directories that have to be copied:
[LIST]
[*]~/.evolution/ contains all evolution mail stuff
[*]~/.mozilla containts the firefox stuff
[/LIST]

HTH

---

### Post by sanderj on 2011-06-04
> **MickeyPilgrim said:**
> Hi Sander,
  The mouse will move the cursor, but clicks have no effect - neither left or right clicks.
  I do not get the desktop you linked to. My old 10.04, and then 10.10 opened on a password free desktop named "pass" so others had some access to the computer. I would just change user to "MickeyPilgrim" to get to my stuff.
  After this upgrade I would have a Unity desktop with icons all over on the left. But, of course, it did nothing when I clicked on anything.

Thanks for your time and thought.
MickeyPilgrim

(long shot) Have you tried using a different mouse? Does the clicking work then?

---

### Post by MickeyPilgrim on 2011-06-05
There is no joy in Mudville.

Nothing yet has taken me to a point where 11.04 will open. Yes, thanks, I tried a different wired mouse.

Thanks to those who got me better acquainted with using the terminal command line. I wish I had learned something from this. I hope to go through the suggested commands to learn what the intended use is.

There is an article at [http://www.addictivetips.com/ubuntu-linux-tips/how-to-update-ubuntu-11-04-kernel-to-2-6-39-0/](http://www.addictivetips.com/ubuntu-linux-tips/how-to-update-ubuntu-11-04-kernel-to-2-6-39-0/) that looks like it might be useful.

Something else is odd - I got absolutely no consideration from the Installation and Upgrades forum.

MickeyPilgrim

---

### Post by MickeyPilgrim on 2011-06-05
Well, upgrading the kernel to 2.6.39-0 did not work either.

I give up.

I would like to put 10.04 back on my computer, but when I try, I'm faced with instructions that lead me to place that along side of 11.04 and XP. XP is sda1, 11.04 is sda5 withe the swap at sda6.

Can anyone direct me to some directions on how to downgrade? I have no experience with partitions.

MickeyPilgrim

---

