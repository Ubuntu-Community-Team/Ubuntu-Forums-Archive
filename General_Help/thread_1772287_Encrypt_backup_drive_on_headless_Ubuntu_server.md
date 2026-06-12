---
title: "Encrypt backup drive on headless Ubuntu server"
date: 2011-05-31
forum: General Help
---

### Post by atconc on 2011-05-31
I have a headless ubuntu server (10.04 x64) in the attic that I use as mostly as a file server for media streaming and backing up other PCs on the home network. The box doesn't have a display, keyboard or mouse connected and is in a location where it's physically difficult to get at.

I'm mostly looking at a solution to protect the system if it were physically stolen(hopefully this is very unlikely) so that I could have a reasonable confidence that no one could boot a live CD and steal any private documents on there.

I don't feel like I need to encrypt the root file system (and I don't want to reinstall!) as most of the data on the system isn't sensitive (MP3s, video files etc). 

I would like to protect the backups of the other systems as they have some personal documents etc on them, 

I need to also balance this with convenience as I need the backups to continue to be automatic or they most likely won't get done at all.

Currently I have a samba share called "backup" that is password protected and points to /media/backup where a 2tb drive is mounted, this drive is used just for backups from the other systems so I would like to encrypt the whole drive.

I realise that I can't have the drive mount completely automatically as it will then be accessible to anyone who can boot the box. The compromise I would like would be that the drive is encrypted and then either:

1.) I log in via ssh and enter a command to mount the drive which prompts for a passphrase - drive stays mounted after I log out until manually unmounted or the system is rebooted

or

2.) On boot something runs automatically which then prompts me for the passphrase when I next connect via ssh - again the drive stays mounted after I log out until manually unmounted or the system is rebooted

I would prefer 2 as then I am less likely to forget to mount the drive after a reboot.

I have seen several tutorials using LUKS to encrypt the drive and manually mount but am wondering if it's possible to achieve 2.  Also wondering if there are any implications for samba if the drive is not available straight away at boot, would I need to restart anything after mounting the encrypted drive for example?

Thanks for any help

---

### Post by psusi on 2011-05-31
Rather than encrypt the backup drive, why not just encrypt the backups?

---

### Post by atconc on 2011-05-31
> **psusi said:**
> Rather than encrypt the backup drive, why not just encrypt the backups?

I am still tinkering with the best way to backup the various systems I have around the house but so far my main methods are syncback SE for selective file backups of windows machines and then occasional clonezilla backups of the windows boxes and my linux based HTPC.

Neither of these applications support encrypting the backups (at least to the best of my knowledge).  

I would also like to avoid using a proprietary solution built into a particular backup application as I like to tinker and often try new applications etc.

---

### Post by psusi on 2011-05-31
You can always encrypt the backup file yourself.

---

### Post by atconc on 2011-05-31
> **psusi said:**
> You can always encrypt the backup file yourself.

Thanks for the suggestion but I'm looking for a more "set it and forget it" approach. I don't want to have to remember to encrypt the daily backups. Also this would stop the back up utility doing any incremental backups

---

### Post by psusi on 2011-05-31
I guess it depends on the utility.  It is pretty easy to automate tar to do such a setup.  I guess when you're using proprietary tools on Windows where you don't have a shell you can script, things are less flexible.

---

### Post by atconc on 2011-05-31
> **psusi said:**
> I guess it depends on the utility.  It is pretty easy to automate tar to do such a setup.  I guess when you're using proprietary tools on Windows where you don't have a shell you can script, things are less flexible.

Unfortunately not going to get away from windows any time soon so am still looking for a drive encryption solution.

---

### Post by lagoy117 on 2011-07-14
> **atconc said:**
> Unfortunately not going to get away from windows any time soon so am still looking for a drive encryption solution.

Could you not use a script and tar (as psusi suggests) on the server to periodically check for new windows backups (whether they are files or folders) and compress/encrypt them.

Then you would only have to run a command to decrypt them before restoring them with whatever windows software you used.

---

### Post by atconc on 2011-08-16
Finally had some time to experiment with this and came up with a solution that meets the requirements I set up so wanted to share in case someone else comes along with a similar problem.

What I basically did was:

[LIST]
[*]encrypt the drive using LUKS
[*]Create a mount point for the drive that doesn't auto mount
[*]Wrote a bash script to check if the drive is mounted and if not then execute the commands to mount the drive (this prompts for a pass-phrase)
[*]Add the script to bashrc so it executes on log-on
[/LIST]

Using this approach the drive is not mounted until the first time I log in after a reboot and enter a pass phrase.  This seems to work ok so far and isn't too much of a pain as I don't reboot often.

Details:

1 - Create your LUKS partition as per this guide:

[http://myotragusbalearicus.wordpress.com/2010/11/15/create-an-encrypted-filesystem-with-luks-on-ubuntu/](http://myotragusbalearicus.wordpress.com/2010/11/15/create-an-encrypted-filesystem-with-luks-on-ubuntu/)

My drive is /dev/sdf1, mount point is /media/backup and mapper entry is encrypted_backup

2- Edit /etc/fstab with an entry for the drive 

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/encrypted_backup    /media/backup   ext4    noauto  0       0

```

3 - Script to check if drive is mounted (checkBackupMount)

(remember to chmod to make executable and change the home location)

```

#!/bin/bash

cat /etc/mtab | grep /dev/mapper/encrypted_backup >/dev/null
 if [ "$?" -eq "0" ]; then
  echo encrypted backup drive is mounted
   else
    echo encrypted backup drive not mounted running mount script
    /home/aaron/mountEncryptedBackup
 fi

```

4 - Script to mount drive (mountEncryptedBackup)

(remember to chmod to make executable)

```

sudo cryptsetup luksOpen /dev/sdf1 encrypted_backup
sudo mount /media/backup

```

5 - Add a reference to the script at the end of .bashrc file

```
/home/aaron/checkBackupMount
```

6 - The system should automatically unmount the drive on shutdown or reboot but I also made a script to do this so I don't have to remember the individual commands.

```

 #!/bin/bash

cat /etc/mtab | grep /dev/mapper/encrypted_backup >/dev/null
 if [ "$?" -eq "0" ]; then
  sudo umount /media/backup
  sudo cryptsetup luksClose encrypted_backup

   else
    echo encrypted backup drive not mounted
 fi



```

Hope this helps someone with a similar need

---

