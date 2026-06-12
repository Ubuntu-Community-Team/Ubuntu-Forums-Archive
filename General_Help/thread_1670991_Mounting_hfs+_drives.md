---
title: "Mounting hfs+ drives"
date: 2011-01-19
forum: General Help
---

### Post by rmcellig on 2011-01-19
I have several external HFS+ formatted drives that I use on my Mac. Is there a way for me to connect them to my HP laptop running Ubuntu 10.10 and have them read/write capable? I hope there is a tool or some way I can do this.

---

### Post by coffeecat on 2011-01-19
> **rmcellig said:**
> I have several external HFS+ formatted drives that I use on my Mac. Is there a way for me to connect them to my HP laptop running Ubuntu 10.10 and have them read/write capable? I hope there is a tool or some way I can do this.

Only if you disable the journal in MacOS. The Linux driver can only read journalled hfs+. but can write to non-journalled hfs+. To disable the journal in MacOS you have to use the Mac terminal. I can find the command for this if you want it.

---

### Post by rmcellig on 2011-01-19
That seems pretty easy. Thanks!

---

### Post by sum1nil on 2011-01-19
Open synaptic package manager and search for 'hfsplus'. 
I'm not sure about 'automounting' them, but after making a mount point in your home directory like 'mac', you can issue a manual mount using hfs+ as the file system.

Not having external drives, I'm not but assume it's like a usb.

'sudo mount -t hfs+ /dev/sdb1 ./mac'

sda is the main drive sd[letter] would be the additional drives.

Hope this helps.

---

### Post by rmcellig on 2011-01-19
That seems pretty easy. Thanks!

---

### Post by sum1nil on 2011-01-19
Open synaptic package manager and search for 'hfsplus'. 
I'm not sure about 'automounting' them, but after making a mount point in your home directory like 'mac', you can issue a manual mount using hfs+ as the file system.

Not having external drives, I'm not but assume it's like a usb.

'sudo mount -t hfs+ -o rw  /dev/sdb1 ./mac'

sda is the main drive sd[letter] would be the additional drives.

I think there is also an hmount.

Hope this helps.
 

[I believe the driver in this package allows for writing, since I tried to make a mac vm. I had direct access to the hfs+ disk drive and I could copy files to it.]

---

### Post by coffeecat on 2011-01-19
> **sum1nil said:**
> Open synaptic package manager and search for 'hfsplus'. 

Despite what is says in the package description, this is not needed.

> **sum1nil said:**
> I'm not sure about 'automounting' them

Ubuntu will automount external hfs+ drives. You don't need any terminal commands.

> **sum1nil said:**
> [I believe the driver in this package allows for writing, since I tried to make a mac vm. I had direct access to the hfs+ disk drive and I could copy files to it.]

A VM is a special case. If you are using MacOS as the host, Linux may appear to write to a shared folder in the hfs+ partition, but it is MacOS that is doing the writing.

A default installation of Ubuntu  can read hfs+ out of the box but it can only write to a non-journalled hfs+ filesystem.

---

### Post by coffeecat on 2011-01-19
> **rmcellig said:**
> That seems pretty easy. Thanks!

I'm not sure whether you are responding to my offer for that MacOS terminal command, or to sum1nil's suggestion. :) There were originally two instances of your post after my and sum1nil's post - forum trouble. Whatever, and for what it's worth, this post from another thread gives the command:

[http://ubuntuforums.org/showpost.php?p=10080620&postcount=3](http://ubuntuforums.org/showpost.php?p=10080620&postcount=3)

But before you use it I would suggest you reconsider whether or not you want to disable the journal in all your hfs+ drives. A non-journalled filesystem is inherently less robust than a journalled one. I have just one drive formatted (non-journalled) hfs+ which I use simply for  transferring files between Ubuntu and MacOS. I use other (journalled) filesystems to backup and archive files.

The other thing to remember is that hfs+ supports the same Unix system of ownership and permissions as Linux. And because your MacOS UID will probably be 501 and your Ubuntu UID 1000, permissions issues can be a right royal pain when transferring files between the two with hfs+.

---

### Post by srs5694 on 2011-01-20
> **coffeecat said:**
> But before you use it I would suggest you reconsider whether or not you want to disable the journal in all your hfs+ drives. A non-journalled filesystem is inherently less robust than a journalled one.

That's not really true. All that a journal does is to give filesystem check tools shortcuts. The journal records where the computer is about to perform actions on the filesystem so that in the event of a system crash, fsck (or whatever) can concentrate on those areas that were undergoing modification. Without a journal, fsck has to scan through the entire filesystem to ascertain its consistency. Thus, a journal speeds up filesystem checks, but it doesn't make the filesystem any more robust.

That said, I agree that disabling the journal on all HFS+ volumes on a Mac isn't desirable. Those filesystem checks can take a long time on a big disk, so disabling the journal will slow things down. This may be an acceptable price to pay on a data-transfer partition, but there's no point in paying it on, say, your main OS X installation partition (which I wouldn't want Linux writing to anyhow).

> The other thing to remember is that hfs+ supports the same Unix system of ownership and permissions as Linux. And because your MacOS UID will probably be 501 and your Ubuntu UID 1000, permissions issues can be a right royal pain when transferring files between the two with hfs+.

This is easily corrected by synchronizing your UID values. You can do this in Ubuntu with the "usermod" command. (You might then need to use "chown" on user files to make everything consistent.) I'm not sure offhand how you'd do it in OS X. These actions require root privileges, so you'd need to do it with sudo or enable direct root logins and do it that way.

---

