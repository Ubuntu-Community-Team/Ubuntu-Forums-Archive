---
title: "Ecryptfs error locking counter -can't access home directory"
date: 2009-12-05
forum: General Help
---

### Post by themollusk on 2009-12-05
Hi guys,

I'm seriously screwed. I finally decided to click on Upgrade to 9.10 from 9.04(64bit edition) and now I seriously regret it. I've lost access to all of my important files. 

During the upgrade there was some error about ecryptfs, and it said something about it being ignored, and then it kept installing anyways. So I figured everything would still be alright. Well, now I've lost access to all of my home directory. When I installed ubuntu 9.04, I did so using ext4 and the option to encrypt the home directory. Everything worked perfectly until the upgrade.

Now, when I log in, I can see my home directory(and the folders) but there's nothing in them. There's a README.txt file and a "Access your private data" file in the home folder. I clicked on the access your private data thing, entered the correct password and it looked like it worked/no error message. It then returned me back to the folders, but they're still inaccessible(ie, nothing in them, but the total used space sizes are still there.) So I typed what the readme file said to do in the Terminal, and this is the result.

ecryptfs-mount-private

Enter your login passphrase:
Inserted auth tok with sig [23998f508e402f2e] into the user session keyring
open: Read-only file system
Error locking counter

That's it, and I still can't access anything. I go back in the folders and they're still blank. I really hope one of you guys can help. I've got a lot of important stuff on there that I still need access to. I had no idea that the upgrade would cause me this much stress.

Thanks a lot

---

### Post by dpm1661 on 2010-01-17
Hi,

 I'm getting this same error with [FONT="Courier New"]ecryptfs-mount-private[/FONT].  A Google search for the phrase gives surprisingly few results.  As far as I can tell, the error happens when the program tries to write a file composed of the username and some other identifiers to the /tmp directory, but fails.  Permission issues, maybe?  I have no idea what I'm doing, so I can't figure this one out.  I've given up trying to fix it, and I'm going to start over with a new user account on my machine.

HOWEVER, you can recover your files by mounting your private directory manually.  I just found this answer, recently: 

[eCryptfs -> Questions -> Question #97115: recovering file contents *and filenames* only with lower files and mount passphrase?]("https://answers.launchpad.net/ecryptfs/+question/97115")

You'll need your mount passphrase (the one that got stored to /[FONT="Courier New"]home/.ecryptfs/username/.ecryptfs/wrapped-passphrase[/FONT]).  If you didn't write it down when you made the account, I think there are ways to recover it from this file, but I'm not sure.

In case the link goes dead, here is a synopsis:  You can recover your private data by manually mounting your [FONT="Courier New"]~/Private[/FONT] directory, but first you need to run [FONT="Courier New"]ecryptfs-add-passphrase[/FONT].  Note how you re-use the sigs that [FONT="Courier New"]ecryptfs-add-passphrase[/FONT] returns in the mount options:

```

jason@mplstudent1:~$ [COLOR="Green"]sudo ecryptfs-add-passphrase --fnek[/COLOR]
Passphrase: [COLOR="Green"][PASTE MOUNT PASSPHRASE HERE][/COLOR]
Inserted auth tok with sig [cb339fd9cd9aa264] into the user session keyring
Inserted auth tok with sig [5579a6f5de43727c] into the user session keyring
jason@mplstudent1:~$ [COLOR="Green"]sudo mount -t ecryptfs ~/.Private ~/Private -o ecryptfs_sig=cb339fd9cd9aa264,ecryptfs_fnek_sig=5579a6f5de43727c,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_passthrough=no
[/COLOR]Passphrase: [COLOR="Green"][PASTE MOUNT PASSPHRASE HERE][/COLOR]
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=5579a6f5de43727c
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=cb339fd9cd9aa264
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key
before. This could mean that you have typed your
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : [COLOR="Green"]yes[/COLOR]
Would you like to append sig [cb339fd9cd9aa264] to
[/root/.ecryptfs/sig-cache.txt]
in order to avoid this warning in the future (yes/no)? : [COLOR="Green"]no[/COLOR]
Not adding sig to user sig cache file; continuing with mount.
Mounted eCryptfs
jason@mplstudent1:~$ [COLOR="Green"]ls ~/Private[/COLOR]
Desktop    Downloads  page0002.png  page0004.png  page0006.png  page0008.png  Pictures  scan for final.drc  startvnc   Videos
Documents  Music      page0003.png  page0005.png  page0007.png  page0009.png  Public    ssh_fix.txt         Templates

```

---

### Post by dmrazor on 2010-03-17
I ran into this exact same error with ecryptfs-mount-private as well. With these posts and some further research I found what caused it in my case.

Following tips in: [https://help.ubuntu.com/community/StricterDefaults](https://help.ubuntu.com/community/StricterDefaults) I had changed the mounting of /dev/shm to read-only. This resulted in the:
```
ecryptfs-mount-private

Enter your login passphrase:
Inserted auth tok with sig [23998f508e402f2e] into the user session keyring
open: Read-only file system
Error locking counter
```
behaviour mentioned above.

After I changed fstab to mount /dev/shm read-write again:
```
tmpfs     /dev/shm     tmpfs     defaults,noexec,nosuid     0     0
```
my problems were solved. Hope this can help other people with this issue.

Cheers,

Raz.

---

### Post by COKEDUDE on 2010-12-12
> **dpm1661 said:**
> Hi,

 I'm getting this same error with [FONT="Courier New"]ecryptfs-mount-private[/FONT].  A Google search for the phrase gives surprisingly few results.  As far as I can tell, the error happens when the program tries to write a file composed of the username and some other identifiers to the /tmp directory, but fails.  Permission issues, maybe?  I have no idea what I'm doing, so I can't figure this one out.  I've given up trying to fix it, and I'm going to start over with a new user account on my machine.

HOWEVER, you can recover your files by mounting your private directory manually.  I just found this answer, recently: 

[eCryptfs -> Questions -> Question #97115: recovering file contents *and filenames* only with lower files and mount passphrase?]("https://answers.launchpad.net/ecryptfs/+question/97115")

You'll need your mount passphrase (the one that got stored to /[FONT="Courier New"]home/.ecryptfs/username/.ecryptfs/wrapped-passphrase[/FONT]).  If you didn't write it down when you made the account, I think there are ways to recover it from this file, but I'm not sure.

In case the link goes dead, here is a synopsis:  You can recover your private data by manually mounting your [FONT="Courier New"]~/Private[/FONT] directory, but first you need to run [FONT="Courier New"]ecryptfs-add-passphrase[/FONT].  Note how you re-use the sigs that [FONT="Courier New"]ecryptfs-add-passphrase[/FONT] returns in the mount options:

```

jason@mplstudent1:~$ [COLOR="Green"]sudo ecryptfs-add-passphrase --fnek[/COLOR]
Passphrase: [COLOR="Green"][PASTE MOUNT PASSPHRASE HERE][/COLOR]
Inserted auth tok with sig [cb339fd9cd9aa264] into the user session keyring
Inserted auth tok with sig [5579a6f5de43727c] into the user session keyring
jason@mplstudent1:~$ [COLOR="Green"]sudo mount -t ecryptfs ~/.Private ~/Private -o ecryptfs_sig=cb339fd9cd9aa264,ecryptfs_fnek_sig=5579a6f5de43727c,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_passthrough=no
[/COLOR]Passphrase: [COLOR="Green"][PASTE MOUNT PASSPHRASE HERE][/COLOR]
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=5579a6f5de43727c
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=cb339fd9cd9aa264
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key
before. This could mean that you have typed your
passphrase wrong.

Would you like to proceed with the mount (yes/no)? : [COLOR="Green"]yes[/COLOR]
Would you like to append sig [cb339fd9cd9aa264] to
[/root/.ecryptfs/sig-cache.txt]
in order to avoid this warning in the future (yes/no)? : [COLOR="Green"]no[/COLOR]
Not adding sig to user sig cache file; continuing with mount.
Mounted eCryptfs
jason@mplstudent1:~$ [COLOR="Green"]ls ~/Private[/COLOR]
Desktop    Downloads  page0002.png  page0004.png  page0006.png  page0008.png  Pictures  scan for final.drc  startvnc   Videos
Documents  Music      page0003.png  page0005.png  page0007.png  page0009.png  Public    ssh_fix.txt         Templates

```

Thank you for that information.

---

