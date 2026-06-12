---
title: "access hfs+ from ubuntu"
date: 2010-12-23
forum: General Help
---

### Post by noorez on 2010-12-23
HI,

I've tried searching google but it seems that I'm getting a lot of old results that are not relavent to newer ubuntu releases.

I have an external hard drive which I formatted to HFS+ (case sensitive, journaled) with Snow Leopard and I would like to access it from ubuntu for read/write. Now as I understand it the latest linux kernels should be able to read and write from this type of file system however the disk does not show up when I plug in the external drive.

Does anyone have any ideas for what I might be missing?

---

### Post by coffeecat on 2010-12-23
> **noorez said:**
> Now as I understand it the latest linux kernels should be able to read and write from this type of file system however the disk does not show up when I plug in the external drive.

At least until recently, Ubuntu was able to mount hfs+ journalled filesystems read-only. The filesystem had to be non-journalled to be read-write. However, whether it is journalled or not, a hfs+ external drive should automount as soon as it is plugged in. It always has for me in Ubuntu.

Which version of Ubuntu are you using?

In case the latest kernel does support read-write for journalled hfs+, I'll prepare a drive in MacOS Snow Leopard and try it in Natty Alpha which is running the 2.6.37 kernel. I'll post back shortly.

---

### Post by noorez on 2010-12-23
When I try to access volume from the places menu I receive this message:

" Error mounting: mount: unknown filesystem type 'hfsplus' "

---

### Post by coffeecat on 2010-12-23
No read-only with hfs+ journalled in natty with kernel 2.6.37.

When you plug a hfs+ formatted USB drive in it should be automounted, an icon appear on your desktop and a Nautilus window open. You should not need to go to the Places menu. And this is **without** the apps hfsplus, hfsprogs and hfsutils installed - in case anyone suggests this.

If you plug a NTFS or FAT32 drive in, is it automounted?

And - again - which version of Ubuntu are you using?

---

### Post by noorez on 2010-12-23
Hey,

I'm using Ubuntu 10.10. And NTFS volumes do mount and open as expected in Nautilus.

---

### Post by coffeecat on 2010-12-23
Hmm. Curious.

Well, I can confirm that a hfs+ formatted USB drive automounts just fine in 10.10 with a nautilus window opening as expected. But read-only for journalled. It's odd  that your error message implies that the system recognises that it's hfsplus but calls it unknown. I wonder if there is something wrong with the filesystem/formatting. 

Do you have anything on that drive? Can you afford to experiment with it? You could try reformatting it in Snow Leopard both journalled and unjournalled and see what happens when you retry it.

Also - if the drive was previously formatted with an mbr/ms-dos partition table before you formatted in MacOS, Snow Leopard's Disk Utility may have left that alone and created a hfs+ partition on a mbr partition table. I wonder if that was the problem. Try reformatting  in Snow Leopard's Disk Utility, but click on the 'Options' button and choose GUID partition table.

---

### Post by noorez on 2010-12-23
Hey,

So i've reformatted my drive with HFS+ (case sensitive, not journaled) and it successfully mounted in Ubuntu 10.10. However it is still not allowing me to write to the folder even though I have created it as a non-journaled system.

EDIT:

So after a quick test it seems that this is a permissions error that I'm not sure how to fix. It seems that the owner for the hfs+ drive has an id of 99 whereas my unix id is 1000. Is there a way that I can get around this?

---

### Post by coffeecat on 2010-12-24
> **noorez said:**
> So after a quick test it seems that this is a permissions error that I'm not sure how to fix. It seems that the owner for the hfs+ drive has an id of 99 whereas my unix id is 1000. Is there a way that I can get around this?

Yes, this is a bit crude but it works.

Plug your non-journallled hfs+ formatted drive into Ubuntu, let it be automounted and then see where in /media it is mounted. In the command below I'll call this *mountpoint*, but just substitute whatever the folder name in /media that your system is using. Open a terminal and:

```
sudo chmod 777 /media/mountpoint
```The interesting thing about this is that this does not change the permissions of the mountpoint folder /media/mountpoint/. It actually changes the permissions of the root of the filesystem - in this case the hfs+ one on the external drive. It is a little-understood thing that chown and chmod can act on the root of a filesystem as well as on files and folders. It also means that this is a once-only command. You will be able to remove the drive and remount it and use it without repeating the command. 

You will now be able to drag and drop files and create folders in the normal way. Anything you copy or create will have your UID of 1000. Anything copied onto the drive from MacOS will still have a UID of 99 and whatever rwx permissions MacOS created. You may see padlocks on your Mac files if MacOS set 640 permissions which means you won't be able to edit or change them in situ in Ubuntu, but you will be able to copy them off. It's useful, therefore, when copying files to the drive in MacOS, to make the permissions 646 by making them read-write for "everyone" in the MacOS Get Info. Apart from using the terminal, I can't see how to set permissions of 666 on files in MacOS.

Instead of the chmod command above you could use 'sudo chown' to change ownership of everything, but that might create complications in MacOS. I don't know - the chmod trick works for me. Don't use 'sudo chmod 666' - for some reason that doesn't work to make the drive writeable.

If you're comfortable with the chmod and chown commands, experiment until you find something that suits you. You can use 'sudo chown' and 'sudo chmod' in the MacOS terminal as well, so you can have hours of fun getting nowhere if you want :wink:

Good luck!

**EDIT**: By the way, you mention a 'Unix' ID of 1000. In fact both your Ubuntu UID of 1000 and your MacOS UID of 99 are Unix ones. Both Linux and MacOS use the same system of Unix permissions, and hfs+ supports Unix permissions, which is why you can chown and chmod on it in Ubuntu, once you are able to write to it in Ubuntu by removing the journal.

---

### Post by Twmaster on 2011-01-06
I've got a similar issue. Pulled the disk from my now dead Powerbook. Placed it in a FireWire enclosure and connected it to my Ubuntu box. The drive is formatted HFS+

Every time I try to access my user directory I get a 'permission denied, you are not the owner blah blah..'

I've tried changing permissions and ownership. I really need to get these files off this disk.

Thanks.

---

### Post by coffeecat on 2011-01-06
> **Twmaster said:**
> The drive is formatted HFS+

Since that's an internal drive from a dead Mac, that will probably be the journalled version of HFS+ which means it will be read only in Ubuntu. And that means you won't be able to change permissions on it. 

Two solutions:

1 - Hook it up to another Mac and copy the files to a FAT32 formatted drive, which will effectively lose all permissions.

2 - Use a root nautilus file browser in Ubuntu. Open a terminal and:

```
gksudo nautilus
```Use the file browser that opens with that command to navigate into your mounted HFS+ drive, not the nautilus window that opens when you plug the drive in. You'll find the mountpoint for the HFS+ drive in /media. Now copy what you need with drag and drop as usual. You may find that the files, once copied onto your Ubuntu drive, will be owned by root. If that happens you'll need to:

```
sudo chown yourusername: whatever
```... with or without the -R option if you have a hierarchy of folders and contents to chown.

---

### Post by GreeenGuru on 2011-01-20
> **coffeecat said:**
> 
Plug your non-journallled hfs+ formatted drive into Ubuntu, let it be automounted and then see where in /media it is mounted. In the command below I'll call this *mountpoint*, but just substitute whatever the folder name in /media that your system is using. Open a terminal and:

```
sudo chmod 777 /media/mountpoint
```

Everything I've read up to this point said Ubuntu had read/write access for HFS+ non-journaled by default, so I just spent an hour trying to figure out why Ubuntu didn't have write access to my buddy's external hard drive formatted HFS+ non-journaled.  All I had to do was run ```
sudo chmod 777 /media/mountpoint
``` as explained by coffeecat.  Thank you!!!

---

### Post by coffeecat on 2011-01-20
> **GreeenGuru said:**
> Everything I've read up to this point said Ubuntu had read/write access  for HFS+ non-journaled by default, so I just spent an hour trying to  figure out why Ubuntu 10.10 didn't have write access to my buddy's  external hard drive formatted HFS+ non-journaled.  All I had to do was  run ```
sudo chmod 777 /media/mountpoint
``` as explained by  coffeecat.  Thank you!!!

I'm glad the command worked for you.

The reason you didn't appear to have write access to your hfs+ drive when you first plugged it in was that it was mounted with root-account access only at first. You would have been able to write to it with sudo or by using a root nautilus, but that would have been inconvenient (and unwise for routine use). The chmod command gives fully-permissive permissions for everyone.

---

### Post by Twmaster on 2011-01-22
Thank you for the info. I managed to get the data off the drive by borrowing an Apple laptop from a freind.

;)

---

