---
title: "Trouble starting a program from a windows partition"
date: 2010-11-24
forum: General Help
---

### Post by slcooper on 2010-11-24
Original question has been posted [here]("http://ubuntuforums.org/showthread.php?p=10149448#post10149448"), and here is the recapitulation of it:

I had a dual boot with XP since Gutsy, but did an overall format before installing Karmic. I installed Karmic after XP, with partitions as follows:

-C:\ - the system partition for XP
-D:\ - called 'Rezerva'
-partition for Ubuntu - made out of half of 'Rezerva' space through setup (partition manager part) of Karmic.
-swap

Back then, I installed MATLAB. Since it is huge, and I seldom use Windows, I installed it on the 'Rezerva' partition and had no troubles using it whatsoever: command "sudo sh matlab" called in "media/Rezerva/Matlab/bin" did the trick. After Karmic, came Lucid - everything worked fine. Now, I updated to Maverick, and I have no ability to change permissions on 'Rezerva' partition. I wouldn't notice that if Matlab hadn't stop working, reporting that:

[FONT=Courier New][FONT=Microsoft Sans Serif][FONT=Courier New]matlab: 1218: /media/Rezerva/Matlab/bin/glnx86/fvwmfix: Permission denied
exec: 1: /media/Rezerva/Matlab/bin/glnx86/MATLAB: Permission denied[/FONT][/FONT][/FONT]

I checked the permissions for those two files: 

[B]Owner: sheldon - Sheldon Cooper
Access: Read and write

Group: sheldon
Access: none

Others
Access: none

[/B]Allow executing file as program checkbox is empty.

None of these options can be changed, neither through terminal or nautilus (whichever user privilege I use), unless I copy the file(s) to my filesystem, for instance on the Desktop: then I can do the change, but the second I copy it back to 'Rezerva', the checkbox gets empty again.

**gunksta** advised in the original thread linked above I post this in a more generic forum, and enclose the contents of etc/fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=70ffc214-da3d-443d-9df8-cd38660c1848 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=7cdea34c-9f25-4b4b-9987-b4c1bae95c52 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0





The partition 'Rezerva' (D), together with "42 GB filesystem" (C) appears in my places menu, it can be mounted by merely clicking it, it all seems ok.

---

### Post by slcooper on 2010-11-25
Maybe an even better question: how did it work before in the first place, if permissions can't be set for these partitions?

---

### Post by Morbius1 on 2010-11-25
First, Linux cannot change permisssions on a Windows filesystem outside of a mount or through fstab. This is the way it's always been.

Second, the default permissions set on mounting NTFS partitions ( and I'm assuming it's an NTFS partition ) through Places has changed since Gutsy which is why it used to work and now it doesn't. You will need to automount your partition by adding a line to fstab so that you can force the permissions you want.

The general steps to automount are as follows:

[1] Go back to Places and unmount [FONT=Courier New][FONT=Microsoft Sans Serif][FONT=Courier New]/media/Rezerva

[2] Create a permanent Rezerva mount point
[/FONT][/FONT][/FONT]```
[FONT=Courier New]sudo mkdir /media/Rezerva[/FONT]
```[FONT=Courier New][FONT=Microsoft Sans Serif][FONT=Courier New]
[3] Find out how you system sees your partition
[/FONT][/FONT][/FONT]```
[FONT=Courier New]sudo blkid -c /dev/null[/FONT]
```[FONT=Courier New][FONT=Microsoft Sans Serif][FONT=Courier New]
You'll get something that looks like this:
[/FONT][/FONT][/FONT]> /dev/sda2: LABEL="WinXP2" UUID="DA9056C19056A3B3" TYPE="ntfs"[4] Using the info above as an example you would add a line in fstab that looks like this:
```
/dev/sda2 /media/Rezerva ntfs defaults 0 0
```[5] Running the following command will check for errors and mount the partition:
```
sudo mount -a
```

---

### Post by slcooper on 2010-11-25
Thanks a bunch! It works now :)

---

### Post by akramhamed88 on 2011-04-20
Thanks very much for the help, this was really useful

---

