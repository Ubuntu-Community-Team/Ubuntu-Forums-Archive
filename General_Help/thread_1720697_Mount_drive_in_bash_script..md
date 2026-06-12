---
title: "Mount drive in bash script."
date: 2011-04-03
forum: General Help
---

### Post by gencon on 2011-04-03
Hi,

I've written a script which does various rsync commands to a Linux server where I backup all my files.

My Ubuntu (Lucid) PC has 3 internal drives in it, the Ubuntu partations are all on one disk, then I have 2 further disks both have a single NTFS partition (leftover from my Windows days).

When I want to mount one of the NTFS drives I just hit the drive name in Nautilus, handily they are both listed in 'Places'. They get mounted in:

/media/FDrive
/media/DDrive

Back to my rsync script - it rsyncs files from both /media/FDrive and /media/DDrive. So at the moment I make sure both disks are mounted before running my rsync script, if they're not I just mount them by clicking on them in Nautilus before running the script.

But now I want to run my rsync script using a cron job. So I've written a test in the script to check if they are mounted, like this:

```
cat /etc/mtab | grep /media/DDrive > /dev/null
RetVal=$?
if [ $RetVal -eq 0 ]; then
    echo DD mounted
else
    echo DD not mounted
fi

cat /etc/mtab | grep /media/FDrive > /dev/null
RetVal=$?
if [ $RetVal -eq 0 ]; then
    echo FD mounted
else
    echo FD not mounted
fi
```That works fine but I need some info.

1) What mount command do I need to run in the script if one or both drives are not mounted? I would like it to be identical to whatever is run if I click on the drives in 'Places' in Nautilus.

2) If I am running the mount command from the script, will I need to use 'sudo mount' even though that's not needed in Nautilus? If so can I just make root the owner of my rsync script so that an unattended backup is possible from the cron job?

3) Do I just un-mount with: umount /media/FDrive ??

For your info I've put my /etc/mtab file on pastie.org so you can see it: [http://pastie.org/1751432](http://pastie.org/1751432)

Thanks all.

---

### Post by Thund3rstruck on 2011-04-03
1) Refer to the 'mount --help' options and map the options to the ones in your /etc/mtab file

2) This depends on who is running it. If you're gonna put the script in the user's crontab (crontab -e) then you'll have to edit the /etc/sudoers file with the visudo command to grant members of a specific group permissions to run the mount command

```

# All members of backup_admins to run 'sudo mount' without requiring password
%backup_admins ALL=NOPASSWD:NOEXEC:/bin/mount,/bin/umount

```

3) Yup; sudo umount /path/to/mount/point

---

### Post by tredegar on 2011-04-03
1) You need to use **mount** *device mountpoint*

2) You need to put an entry in **/etc/fstab** for the device. Best to refer to each device by UUID if these are external devices, as otherwise their **/dev/numbers** may change and cause chaos. Then a user (such as yourself) will be allowed to mount and unmount the device. If you are just backing up your own files this will be fine. If you are going to back up the system files, or other users, you'll need to run the backup as root.

3) Yes, but *only* if it is referenced in **fstab**, or you are running the script as root.

Linux backups to NTFS formatted drives may cause you problems when you try to do a restore, because file permissions and ownerships will not have been correctly preserved by NTFS. My backup drives are all formatted with linux filesystems (ext3, ext4).

Do not rely on your "backup method" until you are *sure* it works, is tested, and reliable.

Once burnt, twice shy. I (almost) got very badly burnt once: Restoring caused a major headache, which I wish I had foreseen, or tested, before it was really needed.

---

### Post by gencon on 2011-04-03
Thanks for the help guys.

tredegar - How do I find the device UUID? They are not external devices, both internal HDDs, so will their /dev/sdb1 and /dev/sdc1 values be safe to use?

Is there no way to find the command Nautilus uses to mount the drives and then copy it?

Cheers.

---

### Post by Thund3rstruck on 2011-04-03
> **tredegar said:**
> 1)

3) Yes, but *only* if it is referenced in **fstab**, or you are running the script as root.


I don't have entries in my /etc/fstab and I have no problem whatsoever unmounting devices using umount /path/to/mount/point. As long as you grant the user running the script the appropriate permission in /etc/sudoers to use the umount command.

---

### Post by tredegar on 2011-04-04
You can find the UUIDs with **sudo blkid**

---

### Post by gencon on 2011-04-05
**EDIT: Ok forget all of the below, I didn't realize I still had to prefix the mount command with sudo and that it just wouldn't ask me for my password. Oops. END EDIT** 

Thanks all.

I got the /etc/fstab solution working fine (nice to learn something new) but I don't want the drives mounted all the time, so this afternoon I tried Thund3rstruck's suggestion of modifying /etc/sudoers - I edited the file with sudo visudo and added this line at the bottom (having read on the web that single user entries should be after the '%admin ALL=(ALL) ALL' line):

ms ALL=NOPASSWD: /bin/mount,/bin/umount

ms is my username. After editing I checked the line had been properly added with: sudo cat /etc/sudoers (no problem there).

This did not work. When I tried to mount the drive I got "mount: only root can do that". I tried rebooting but had the same problem. The identical mount command worked perfectly with sudo.

Please also note that Thund3rstruck suggested this:

%backup_admins ALL=NOPASSWD:NOEXEC:/bin/mount,/bin/umount

Which I modified to:

ms ALL=NOPASSWD:NOEXEC:/bin/mount,/bin/umount

But with NOEXEC added after NOPASSWD it stopped mount from actually mounting the drive regardless of whether trying as ms or with sudo.

Any ideas how I get this working?

PS.  /etc/fstab entries for the drives were removed and the drives were not already mounted while I was trying all this.

Thanks.

---

