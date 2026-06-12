---
title: "commands"
date: 2010-09-13
forum: General Help
---

### Post by wiz2010 on 2010-09-13
I have sorted some useful commands with h/w significance
[http://deb-info.blogspot.com/2010/09/some-useful-commands.html](http://deb-info.blogspot.com/2010/09/some-useful-commands.html)

---

### Post by TNT1 on 2010-09-13
[http://www.debian.org/doc/user-manuals#quick-reference](http://www.debian.org/doc/user-manuals#quick-reference)

---

### Post by overdrank on 2010-09-13
> **wiz2010 said:**
> I have sorted some useful commands with h/w significance
[http://deb-info.blogspot.com/2010/09/some-useful-commands.html](http://deb-info.blogspot.com/2010/09/some-useful-commands.html)

Hi and welcome, I have moved your post and the response to it's own thread. No need to bring up a 2 year old thread. :)

---

### Post by garvinrick4 on 2010-09-13
```
Here is a cheat sheet I made for someone I gave a flash drive with Ubuntu on. Not all the stuff but what I could type up quick at the time.  sudo apt-get purge ubuntuone-client-gnome

sudo apt-get upgrade && sudo apt-get upgrade (to fetch upgrades.) 

If you use GUI upgrade tool NEVER use partial upgrades will dork the system for sure. Just wait till they get full packages. Will not happen when use command line just GUI. 

sudo aptitude update && sudo aptitude upgrade 
Will show packages that are outdated if you need space. 

uname -r (kernel version)

lsb_release -a (ubuntu version)

uname -a (get all kernel info) 

Ctrl+Alt+Bksp (restart X if frozen)

sudo apt-get -f install (fix broken packages) 
dpkg --configure -a (fix broken packages)

sudo apt-get clean (will clean out cache of packages in system) so as to fetch new package from repository. 

sudo update-grub (use everytime you change grub menu) 

sudo grub-mkconfig (will make a new grub config file) 

gksudo gedit to "path"such as /etc/fstab (will open gedit in root 
always use gksudo for opening file system in root from command line.) 

Alt/F2  then type in gksudo nautilus ( root in file system GUI)

Mute Fix: load-module module-device-restore in /etc/pulse/default.pa with #load-module module-device-restore 

sudo dpkg --get-selections > installedsoftware (installed software)

sudoers conf. time stamp -1 =whole session
Defaults env_reset,timestamp_timeout=20



sudo update-grub no window like below

Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

FIX

Grub2 was installed with Windows system partition chosen as the root-directory. This causes the folder /boot/grub to be created on the Windows system partition. Since ntfs partitions are case insensitive this leads to confusions between "/boot" and the already existing folder "/Boot
Solution 
Boot into your Linux OS and deleted or rename the folder /boot on the Windows system partition. Make sure that your don't delete the /Boot folder. The /Boot folder contains the file "bcd" which is necessary to boot Windows Vista/7. 


ALT/F2 together type in "gksudo nautilus" and run wiil open file system in root. 

sudo adduser username audio (10.04 update 7-02-10) 

uname -a (show version UBuntu installed) 

aptitude show "package name" (will show if installed and what it does) 

sudo blkid ( show all labels with sdxy numbers 

sudo fdisk -l (Show all partitions by sdxy numbers 

Run fsck (never on mounted drive) like a chkdsk in Windows. 
sudo e2fsck /dev/sdx# 

Start graphic drivers first in boot #540801 launchpad 
sudo -i 
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash 
update-initramfs -u 

Change permissions media: 
sudo chown -R rick:rick /media/redhat (for example) 
ls -la /media (to give permissions of media) 

Code: 
cd /media 
Then: 
Code: 
sudo chmod a=rwx -R lucid 

aplay -l (audio) 

lspci | grep VGA ( graphics card) 

sudo lspci -v | less (Cards & Drivers) 

{Download boot script. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) 
Make sure script is on Desktop. 

Run this and Results of Script will be on Desktop. 
sudo bash ~/Desktop/boot_info_script*.sh } 

Computer info: lshw | less (everything) 

Samba password: sudo smbpasswd -a linuxcss 

grep menuentry /boot/grub/grub.cfg

grub-probe -t device /boot/grub

[https://help.ubuntu.com/community/Grub2#/etc/default/grub](https://help.ubuntu.com/community/Grub2#/etc/default/grub)

Best web page grub: 
[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202") 

Gparted sites
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)[https://help.ubuntu.com/community/Ho...sAndPartitions](https://help.ubuntu.com/community/Ho...sAndPartitions)[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

Reinstall grub2 
sudo mount /dev/sda5/media/maverick 
sudo grub-install --recheck --root-directory=/media/maverick /dev/sda 

If needed run this twice to reinstall grub2 
sudo grub-install --recheck --root-directory=/media/maverick /dev/sda 

Reinstall grub 2 Live CD 
Make a directory: sudo mkdir /media/maverick 

Mount your OS with grub on it: sudo mount /dev/sda5/media/maverick 

Mount mbr on seperate partition if is one: sudo mount /dev/sda1/media/SYSTEM 

Install Grub to sda: sudo grub-install --root-directory=/media/maverick /dev/sda 
Reinstall: sudo grub-install --recheck --root-directory=/media/maverick /dev/sda 

Unmount partition: sudo umount /media/maverick 

Unmount MBR partition: sudo umount /media/SYSTEM 

Get into root in live CD or any OS partition not mounted Linux. 

sudo mkdir /media/lucid (make directory) 
sudo mount /dev/sda2/media/lucid ( mount a drive) 
sudo cp /etc/resolv.conf/ media/lucid/etc.resolv.conf (internet connection) 
sudo chroot /media/lucid (to root) 
apt-get update (If you want to update and upgrade) 
apt-get upgrade 

Are now in root on karmic with internet connection wifi, I believe in wired can pass this step, have to check out. 

Update and Upgrade chroot
1. - Download/grab a live cd. 
2. - Start live cd and when it loads the desktop open a gnome-terminal. 
3. - Create this dirs: 
sudo mkdir /media/karmic 
sudo mkdir /media/karmic/proc/media/karmic/dev/media/karmic/etc 
4. - Mount your linux partition (for me sda1): 
sudo mount /dev/sda1/media/karmic 
5. - Bind the dirs: 
sudo mount -o bind /proc /media/karmic/proc 
sudo mount -o bind /dev /media/karmic/dev/ 
sudo mount -o bind /dev/pts/media/karmic/dev/pts 
6. - Copy this file 
sudo cp /etc/resolv.conf/media/karmic/etc/resolv.conf 
7. - Update your real linux partition with chroot: 
sudo chroot /media/karmic apt-get update 
8. - Upgrade your real linux partition with chroot: 
sudo chroot /media/karmic apt-get dist-upgrade 
9. - If you have some broken package: 
sudo chroot /media/karmic apt-get -f install 

Test disk windows boot repair

You can repair the boot sector of Windows system partition via "fixboot" from a Windows XP CD, or "bootrect /fixboot" from a Windows Vista/7 CD. But in my experience testdisk works best in this situation. So boot into a Linux OS or Live CD. If your system uses "apt-get" and has "testdisk" in its repositories (in Ubuntu: the universe repository needs to be enabled), you can install and run testdisk via 
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
How to restore the Windows install grub /etc/ XP bootloader For this you will need your Windows install grub /etc/ XP installation CD. Boot into it now. You will get to a part where it asks if you want to repair or recover. To do so, press "r". If prompted, enter your Windows install grub XP administrator password. This will leave you at at a command line, so type in the following two commands: 

Code: fixboot 

Code: fixmbr 

Code: exit 

Vista and 7 fix boot 
How to restore the Windows install grub / Vista or 7 bootloader To restore the Windows install grub bootloader, you must first boot off your Windows install grub Vista/7 installation DVD. If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download for Vista or Win 7. When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer." On the next page, if it finds your Windows install grub Vista/7 installation, make sure it is UNSELECTED before clicking next. Then click on "Command prompt". From there, type in the following: 

Code: bootrec.exe /fixboot 

Code: bootrec.exe /fixmbr 

and click "Restart." 

Install in Ubuntu All 
[http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software](http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software) 

Suppose you have a source file name src.tar.gz, what you do initially is that you need to extract the source files and then in the terminal&#8230;. 
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

My Way to UPGRADE Verision: 
sudo sed -i 's/lucid/maverick/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
 
```

---

### Post by inameiname on 2010-09-13
If anybody is interested, I've put together tons of these and made aliases for many in a 'bashrc' file. There are a lot of good ones I've found from around town, as well as plenty of good aliases and functions. Those newbies I show Linux to always find it useful, so figured I'd share.

[http://gnome-look.org/content/show.php/Ultimate+Bashrc+File?content=129746](http://gnome-look.org/content/show.php/Ultimate+Bashrc+File?content=129746)

---

