---
title: "How to I check Harddisk and File Integrity"
date: 2011-08-12
forum: General Help
---

### Post by Simon Cropper on 2011-08-12
Hi,

I want to get a program to check (a) hard disk and (b) file integrity.

I have had a file - ODS spreadsheet accessed using LibreOffice - that appears corrupt. I have drilled down and down and eventually identified a corrupt component image inserted in a sheet.

The error that is thrown by LO is a "Error saving 
the document FILE: Write Error. The file could not be written."
 error. The thread can be read here... [http://thread.gmane.org/gmane.comp.documentfoundation.libreoffice.user/9266]("http://thread.gmane.org/gmane.comp.documentfoundation.libreoffice.user/9266").

What has confused me is that my machine can not save the file once a sheet is deleted. It is specific to a particular file. The file is stored on n ext4 disk mounted by fstab. I also share the file using samba. Regardless of how I access this file I get the error. If however, I access the exact same file using OpenOffice 3.1.0 
OOO310m11 (Build: 9399) from an old Windows Vista Tablet and I can manipulate the file successfully - no error is encountered. I can also access the same file from another Ubuntu machine via NFS and Samba and both work. I am confused. I am beginning to think my disk is damaged or something.

How do you check hard disks to verify that the disk surface is intact, and that the expected file sum value matches the value stored in the Linux equivalent to the FAT table.

I am using Ubuntu 10.04 LTS and all hard disks are formated with ext4. All formatting and management of the disks have been done using the 'Disk Utility' in the System > Administration' menu. If I look in gparted it will not check the disk the file is on stating "eslabel: no such file or directory... couldn't find valid filesystem superblock...". The filesystem mounts OK however without any errors. Another harddisk on the same system currently being used for backup does not even have the menu option for checking the disk highlighted.

What is the best way of verifying the integrity of the filesystem, actual files and the underlying physical media?

I should point out it is only this single file that currently displays any issues. I either have a damaged disk, corrupt file or LibreOffice has a very peculiar bug that only appears in a unique combination of events just on my machine.

As part of my investigations I have been updating ubuntu, reinstalled LibreOffice from their website and checked all dependencies have been met.

Any help would be appreciated.

---

### Post by Ozymandias_117 on 2011-08-12
Using the Disk Utility tool, you can check the SMART data on your drive, which will usually tell you if it's dying.  You probably also want to try using fsck to check the filesystem integrity.  (Boot to a LiveCD and fsck from there)

---

### Post by Simon Cropper on 2011-08-14
> **Ozymandias_117 said:**
> Using the Disk Utility tool, you can check the SMART data on your drive, which will usually tell you if it's dying.  You probably also want to try using fsck to check the filesystem integrity.  (Boot to a LiveCD and fsck from there)

Thanks Ozymandias_117 for your suggestions, they were what I needed. 

I had checked the SMART data for each drive and none showed any errors.

I ran '[FONT="Courier New"]fsck[/FONT]' as suggested and found no bad blocks or file system errors (thankfully). I am now confident that the corruption is contained to the file and have through working backwards identified that the file was actually open when I had a power blackout 3-weeks ago. This gives me a cause for the corruption.

For others, I have listed the procedure I used to check the disks as I did not find any tutorials directly relevant to checking ext4 formatted hard disks.

**SHORT STEP-BY-STEP TUTORIAL FOR CHECKING EXT4 HARD DISK FOR ERRORS**

**STEP 1.** Ensure you have access to a Ubuntu LiveDVD/Installation Disk. If not, download a copy using another machine.

**STEP 2.** Change the BIOS on your machine to allow you to boot from a CD.

**STEP 3.** Insert the Ubuntu disk into your CD-ROM and reboot your machine. Choose the option to 'Try Ubuntu' -- don't reinstall the system!

**STEP 4.** Once Ubuntu starts (you will not be required to provide a password) you will be in the main desktop.

**STEP 5.** Using the main menu select the terminal. This can be found under 'Applications > Accessories > Terminal'. A terminal window should now be present.

**STEP 6.** Get a pen and paper to write down the paths to your disk drives. Note that when Ubuntu boots it identifies all the hard disks on the system and creates a directory in the '[FONT="Courier New"]/dev[/FONT]' folder for each. By default these devices are not mounted. If you see a picture on your desktop of a drive then a disk is mounted. _You must unmount all disks that are to be checked before proceeding!_ 

**STEP 7.** Use 'Disk Utility' found under the 'System > Administration' menu to see what drives are on your system. Use this to verify the drives are not mounted. Also note the addresses of the disks to be checked... they should look like '[FONT="Courier New"]/dev/sdc[/FONT]' or '[FONT="Courier New"]/dev/sda1[/FONT]'. Also, ensure the drives are actually ext4 and not some other format. Once you recorded the paths then exit the 'Disk Utility'.

**STEP 8.** OK to proceed with the check type '[FONT="Courier New"]sudo fsck.ext4 -cDftvy -C 0 [COLOR="Red"]/dev/sda1[/COLOR][/FONT]' in the terminal -- remember to substitute your device address. You can only do one disk at a time. On my machine 1TB of data took 3 hours to complete and the bulk of the time (99.99%) was spent checking for bad blocks. If you want to know what the parameters mean then check out the links at the bottom of this post or type '[FONT="Courier New"]fsck.ext4[/FONT]' in the terminal to see a short list of the common command options. Note that '[FONT="Courier New"]fsck.ext4[/FONT]' appears to be a synonym for '[FONT="Courier New"]e2fsck[/FONT]'.

**STEP 9.** As the fsck command has been passed the (v)erbose option parameter details of the progress and any errors will be listed in the terminal window. If errors are found then you will need to consider your options based on whether the fsck package was able to fix them.

**STEP 10.** Once finished you can shutdown the machine. Ubuntu ejects the CD tray so you can remove the disk before competing the shutdown.

**EXTERNAL LINKS (for reference only)**

[LIST=1]
[*][http://manpages.ubuntu.com/manpages/lucid/man8/fsck.ext2.8.html]("http://manpages.ubuntu.com/manpages/lucid/man8/fsck.ext2.8.html")
[*][http://kernelnewbies.org/Ext4]("http://kernelnewbies.org/Ext4")
[*][http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/]("http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/")
[/LIST]

---

### Post by Tom 6 on 2011-08-15
Hi :)
I just use GPartEd and not even as often as i 'should'.  In GPartEd just right-click on a partition and choose "Check".  The Cli way is probably better and gives more options but i prefer point&click where possible (usually)
Regards from
Tom :)

[edit: i dual-boot rather than LiveCd it.  The other side is a very old Fedora that also has Wesnoth]

---

