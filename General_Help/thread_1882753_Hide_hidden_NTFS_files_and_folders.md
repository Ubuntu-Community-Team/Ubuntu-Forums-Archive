---
title: "Hide hidden NTFS files and folders"
date: 2011-11-17
forum: General Help
---

### Post by yoramdavid on 2011-11-17
Hello,

Is there a way to have the NTFS partition mounted without showing the hidden ntfs files and folders under Ubuntu?

I found this [page]("http://www.tuxera.com/community/ntfs-3g-manual/#6") and it seems to be possible.

Thank you.

Yoram

---

### Post by dcstar on 2011-11-18
> **yoramdavid said:**
> Hello,

Is there a way to have the NTFS partition mounted without showing the hidden ntfs files and folders under Ubuntu?

I found this [page]("http://www.tuxera.com/community/ntfs-3g-manual/#6") and it seems to be possible.

Thank you.

Yoram

You put the relevant options in the appropriate place in the /etc/fstab file.

Use the **pysdm** package or do a search on mounting drives for detailed info.

---

### Post by Mark Phelps on 2011-11-18
IF you read the details in that link closely, you'll see that the only files that are really "hidden" are the ones with dots preceding their filenames -- a convention that Windows filesystems do NOT use.

So basically, those settings accomplish little useful.

If you're concerned about folks (or you) accidentally damaging system files, a better solution is to mount read-only.  That way, none of the files or directories can be damages.

---

### Post by coffeecat on 2011-11-18
@yoramdavid, there are two types of hidden files. The Linux ones with the leading dot and the Windows system using the NTFS attribute with hidden flag. According to the link you posted there are mount options for both. My guess is that you want to hide the NTFS folders "System Volume Information" and "$RECYCLE.BIN". The option hide_hid_files works for this, and this is the appropriate /etc/fstab line from one of my systems:

```
UUID=4E74462B225AD5CB /media/Data     ntfs    defaults,uid=1000,umask=000,windows_names,hide_hid_files 0       0
```

That effectively hides those two system folders.

Although you don't ask this, you might want to use the windows_names option as well. You can read up on this in your link but briefly without it, Linux is able to save files to NTFS with so-called forbidden characters such as : in the filename which Windows doesn't support. Rather bizarrely, you can see and use these files in Ubuntu/Linux even on a NTFS filesystem, but if you try in Windows you get an error. 

If you want help with editing your /etc/fstab, just post back.

---

### Post by yoramdavid on 2011-11-19
> **dcstar said:**
> You put the relevant options in the appropriate place in the /etc/fstab file.

Use the **pysdm** package or do a search on mounting drives for detailed info.

Thank you for your help,

I installed pysdm but I nee to read more about how to use it and since my Internet has been down, I had not had the chance yet. Ie, I do not know where to put the option "hide_hid_files" option.

Yoram

---

### Post by yoramdavid on 2011-11-19
> **coffeecat said:**
> @yoramdavid, there are two types of hidden files. The Linux ones with the leading dot and the Windows system using the NTFS attribute with hidden flag. According to the link you posted there are mount options for both. My guess is that you want to hide the NTFS folders "System Volume Information" and "$RECYCLE.BIN". The option hide_hid_files works for this, and this is the appropriate /etc/fstab line from one of my systems:

```
UUID=4E74462B225AD5CB /media/Data     ntfs    defaults,uid=1000,umask=000,windows_names,hide_hid_files 0       0
```

That effectively hides those two system folders.

Although you don't ask this, you might want to use the windows_names option as well. You can read up on this in your link but briefly without it, Linux is able to save files to NTFS with so-called forbidden characters such as : in the filename which Windows doesn't support. Rather bizarrely, you can see and use these files in Ubuntu/Linux even on a NTFS filesystem, but if you try in Windows you get an error. 

If you want help with editing your /etc/fstab, just post back.

Thank you for your help, so I followed what you advised me and it works indeed with those files, is there any way to also hide non-system files and folders which have the hide flag under windows?

Thank you.

Yoram

---

### Post by coffeecat on 2011-11-19
> **yoramdavid said:**
> Thank you for your help, so I followed what you advised me and it works indeed with those files, is there any way to also hide non-system files and folders which have the hide flag under windows?

Thank you.

Yoram

Does it not hide them? I only checked with those two system folders and assumed that it would hide anything in a NTFS filesystem with the hidden flag set. From your link:

> **hide_hid_files**

Hide the hidden files and directories in directory listings, the hidden files and directories being the ones whose NTFS attribute have the hidden flag set. The hidden files will not be selected when using wildcards in commands, but all files and directories remain accessible by full name, for example you can always display the Windows trash bin directory by : “ls -ld $RECYCLE.BIN”.

---

### Post by yoramdavid on 2011-11-19
> **coffeecat said:**
> Does it not hide them? I only checked with those two system folders and assumed that it would hide anything in a NTFS filesystem with the hidden flag set. From your link:

Yes it did!
I am sorry, I checked a partition where I have a hidden folder under windows and it was there.
After your comment I went back and checked another partition and indeed they do not show up.
Sorry for the mis-information and thank  you very much.

I read that I can add an option "noauto" so that the partition is not mounted automatically but I can add the same options as before for when I mount it.
Looks like this: 
[HTML]#Entry for /dev/sda1 :
UUID=B6C4C919C4C8DD2D	/media/Windows_XP	ntfs	defaults,nls=utf8,umask=0222,noauto,user,ro,windows_names,hide_hid_files	0	0[/HTML]

I have not rebooted yet to test it, I wanted to reply first to your message.

Yoram

---

### Post by yoramdavid on 2011-11-21
I had to remove the "defaults" bit at the beginning, then it worked.
Thank you again for the help.

Problem solved, threat closed. :)
(many other still opened...:(

Yoram

---

### Post by yoramdavid on 2011-11-22
> **coffeecat said:**
> @yoramdavid, there are two types of hidden files. The Linux ones with the leading dot and the Windows system using the NTFS attribute with hidden flag. According to the link you posted there are mount options for both. My guess is that you want to hide the NTFS folders "System Volume Information" and "$RECYCLE.BIN". The option hide_hid_files works for this, and this is the appropriate /etc/fstab line from one of my systems:

```
UUID=4E74462B225AD5CB /media/Data     ntfs    defaults,uid=1000,umask=000,windows_names,hide_hid_files 0       0
```

That effectively hides those two system folders.

Although you don't ask this, you might want to use the windows_names option as well. You can read up on this in your link but briefly without it, Linux is able to save files to NTFS with so-called forbidden characters such as : in the filename which Windows doesn't support. Rather bizarrely, you can see and use these files in Ubuntu/Linux even on a NTFS filesystem, but if you try in Windows you get an error. 

If you want help with editing your /etc/fstab, just post back.

Hmmm, can I do the same for an external hdd?
I tried and get an error that only root can boot the device. Even with "user" in options.

---

### Post by coffeecat on 2011-11-22
> **yoramdavid said:**
> Hmmm, can I do the same for an external hdd?
I tried and get an error that only root can boot the device. Even with "user" in options.

Boot the device? I don't follow you. What was the exact error message?

---

### Post by yoramdavid on 2011-11-22
> **coffeecat said:**
> Boot the device? I don't follow you. What was the exact error message?

Thank you for your help.

My mistake: not boot but mount.

With this code:
```
#Entry for /dev/sdb1 :
UUID=3C607E73607E342C	/media/Yoram\040A-Data	ntfs	defaults,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177,,windows_names,hide_hid_files	0	0
```

I get the following error: ```
Error mounting, mount exited with error code 1: helper failed with: mount: only root can mount /dev/sdb1 on /media/Yoram AData
```

So I took the "defaults" bit off and replaced it with "user":
```
#Entry for /dev/sdb1 :
UUID=3C607E73607E342C	/media/Yoram\040A-Data	ntfs	user,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,dmask=0077,fmask=0177,,windows_names,hide_hid_files	0	0
```

And get this error:
```
Ocorreu um erro ao aceder ao 'Yoram A-Data'; o sistema devolveu: A operação pedida foi mal-sucedida.: Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://tuxera.com/community/ntfs-3g-faq/#unprivileged

```

---

### Post by coffeecat on 2011-11-22
I'm puzzled. Try taking the "uhelper=udisks" out. I've not seen that before. Where did you get that from? Also, you have a double comma between fmask=0177 and windows_names. It might not matter, but try removing one comma too.

---

### Post by yoramdavid on 2011-11-22
> **coffeecat said:**
> I'm puzzled. Try taking the "uhelper=udisks" out. I've not seen that before. Where did you get that from? Also, you have a double comma between fmask=0177 and windows_names. It might not matter, but try removing one comma too.

What I do to have that line, I use the NTFS configuration tool then I add and remove what I need in the fstab directly.
Now, I probably should have said that I use Dolphin. See below why:

This time I used this code:
```
#Entry for /dev/sdb1 :
UUID=3C607E73607E342C	/media/Yoram_A_Data	ntfs	user,nls=utf8,umask=0222,windows_names,hide_hid_files	0	0
```
The result in Dolphin is still the same as before, ie:
```
Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://tuxera.com/community/ntfs-3g-faq/#unprivileged

```
But it got auto-mounted by nautilus and I could browse the files.
Then I unmounted from nautilus and I was then able to mount using Dolphin and browse the files.
I unplugged and plugged the USB drive again and mounted it with Dolphin before Nautilus and it worked.
It seems that Nautilus takes over the privileges !
Any way to work around that?

The drive does not show the hidden files and folders, by the way, so that is a plus.

---

### Post by coffeecat on 2011-11-22
> **yoramdavid said:**
> I unplugged and plugged the USB drive again and mounted it with Dolphin before Nautilus and it worked.
It seems that Nautilus takes over the privileges !
Any way to work around that?

Sorry - I don't know. I've never mixed nautilus and dolphin.

---

### Post by yoramdavid on 2011-11-22
> **coffeecat said:**
> Sorry - I don't know. I've never mixed nautilus and dolphin.

OK, thank you for your help.

Yoram

---

### Post by sakamoto on 2012-07-29
for ubuntu 10.04 (lucid) users with outdated ntfs-3g: [https://launchpad.net/~thomas-creutz/+archive/ppa/+build/2602548](https://launchpad.net/~thomas-creutz/+archive/ppa/+build/2602548)

---

