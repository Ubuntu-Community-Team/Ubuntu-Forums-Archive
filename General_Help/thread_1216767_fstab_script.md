---
title: "fstab script"
date: 2009-07-18
forum: General Help
---

### Post by Psycho.mario on 2009-07-18
Hello everyone. I wrote a script to append lines to /etc/fstab without actually opening a text editor. It asks you a series of questions like what to mount and where, using zenity.
Here it is:
```
#!/bin/bash
dev=`zenity --entry --text="Which device do you want to mount?" --entry-text=/dev/ --title=Device`
mount=`zenity --entry --text="Where do you want to mount $dev? (e.g /media/disk or /mnt/disk)" --title=Mountpoint`
if [ -d $mount ]
then
    zenity --info --text="$mount Exists" --title=$mount Exists
else
    zenity --error --text="$mount does not exist, Attempting to create" --title="$mount does not exist"
    gksu mkdir $mount
    gksu chmod 777 $mount
fi
fs=`zenity --list --text="Please choose the appropriate filesystem (auto if not sure)" --radiolist --column="" --column="Filesystem" adfs affs auto autofs coda coherent  cramfs  devpts  efs  ext2  ext3 hfs hpfs iso9660 jfs minix msdos ncpfs nfs ntfs proc qnx4 reiserfs romfs smbfs sysv tmpfs udf ufs umsdos vfat xenix xfs --title=Filesystem`
options=`zenity --entry --text="Extra Options? Please seperate with commas (See man mount for help)" --entry-text="user,noauto,exec,utf8" --title=Extra Options`
dump=`zenity --entry --text="Please enter 'dump' parameter. (0 if not sure)" --entry-text="0" --title="dump"`
pass=`zenity --entry --text="Please enter 'pass' parameter. (0 if not sure)" --entry-text="0" --title="pass"`
final="$dev $mount $fs $options $dump $pass"
zenity --warning --text="Are you sure you want to append $final to /etc/fstab?"
echo "$final" | sudo tee -a /etc/fstab
test=`tail --lines=1 /etc/fstab`
if [ "$test" == "$final" ]
then
    zenity --info --text="$final successfully appended" --title="Success!"
else 
    zenity --error --text="$final failed to be appended" --title="Failure"
    zenity --info --text="$final" --title="Please manually append to /etc/fstab"
fi
zenity --info --text="Now run mount -a" --title="Finished"
exit 0

```
I would be very happy if you could try this out, and tell me how to improve it.
Please do not be too harsh, as this is only my second serious script, and i am only a teenager, with a few months' experience with bash scripts

Thanks in advance.

---

### Post by Psycho.mario on 2009-07-18
Bump

---

### Post by HotForLinux on 2009-07-18
zenity --list --radiolist "" a "" b "" c "" d "" e --text="Choose from the COMPLETE list"  --column="" --column="valors"

---

### Post by Psycho.mario on 2009-07-19
I don't quite understand this, can you put into context please?

---

### Post by Psycho.mario on 2009-07-19
OK, line 12 is now:
```
fs=`zenity --list --radiolist --column="" "" adfs "" affs "" auto "" autofs "" coda "" coherent "" cramfs "" devpts "" efs "" ext2 "" ext3 "" hfs "" hpfs "" iso9660 "" jfs "" minix "" msdos "" ncpfs "" nfs "" ntfs "" proc "" qnx4 "" reiserfs "" romfs "" smbfs "" sysv "" tmpfs "" udf "" ufs "" umsdos "" vfat "" xenix "" xfs --text="Please choose the appropriate filesystem (auto if not sure)" --column="Filesystem"`
```

Thanks for the help

---

### Post by Psycho.mario on 2009-07-19
After some major trial and error in which i wiped /etc/fstab a few times, i have corrected line 19. Here is the finished(?) script.

```
#!/bin/bash
gksudo -m "Backing up /etc/fstab" -D "Backing up /etc/fstab, just in case" cp /etc/fstab /etc/fstab.`date +%a%d%b%y`
dev=`zenity --entry --text="Which device do you want to mount?" --entry-text=/dev/ --title=Device`
mount=`zenity --entry --text="Where do you want to mount $dev? (e.g /media/disk or /mnt/disk)" --title=Mountpoint`
if [ -d $mount ]
then
    zenity --info --text="$mount Exists" --title=$mount Exists
else
    zenity --error --text="$mount does not exist, Attempting to create" --title="$mount does not exist"
    gksu mkdir $mount
    gksu chmod 777 $mount
fi
fs=`zenity --list --radiolist --column="" "" adfs "" affs "" auto "" autofs "" coda "" coherent "" cramfs "" devpts "" efs "" ext2 "" ext3 "" hfs "" hpfs "" iso9660 "" jfs "" minix "" msdos "" ncpfs "" nfs "" ntfs "" proc "" qnx4 "" reiserfs "" romfs "" smbfs "" sysv "" tmpfs "" udf "" ufs "" umsdos "" vfat "" xenix "" xfs --text="Please choose the appropriate filesystem (auto if not sure)" --column="Filesystem"`
options=`zenity --entry --text="Extra Options? Please seperate with commas (See man mount for help)" --entry-text="user,noauto,exec,utf8" --title=Extra Options`
dump=`zenity --entry --text="Please enter 'dump' parameter. (0 if not sure)" --entry-text="0" --title="dump"`
pass=`zenity --entry --text="Please enter 'pass' parameter. (0 if not sure)" --entry-text="0" --title="pass"`
final="$dev $mount $fs $options $dump $pass"
zenity --warning --text="Are you sure you want to append $final to /etc/fstab?"
gksudo "sh -c 'echo "$final" >> /etc/fstab'"
test=`tail --lines=1 /etc/fstab`
if [ "$test" == "$final" ]
then
    zenity --info --text="$final successfully appended" --title="Success!"
    zenity --info --text="Now run mount -a" --title="Finished"
else 
    zenity --error --text="$final failed to be appended" --title="Failure"
    zenity --info --text="$final" --title="Please manually append to /etc/fstab"
fi
exit 0
```

Please feel free to comment or correct to help me. :)

---

### Post by HotForLinux on 2009-07-22
Line 12: You got it!
Line 19 is 
> test=`tail --lines=1 /etc/fstab`I don't see what have you changed.



Why don't you post the number of the llines or post the whole script with:

> cat -n myscriptIs everything now as you wanted?

---

