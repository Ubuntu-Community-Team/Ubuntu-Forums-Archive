---
title: "MicroSD Card read-only"
date: 2011-04-03
forum: General Help
---

### Post by Beatter on 2011-04-03
Alrighty, this issue is really making me mad. 
First off, if you suggest me to check the 'lock' switch on the adapter I will do something...

I've got an 8GB MicroSD card from MicroCenter and used it for a while in my phone. I am now trying to format it and use it for other purposes.

I have a built in SD reader on my laptop and I use an adapter and all it says is the card is read-only. I can't delete, write, or even format. I've tried most everything, used about 5 different adapters(including USB to MicroSD adapters), 3 computers, and thrown it at the wall.
I still get the same result. It just says it is read-only.

I am currently in Ubuntu 11.04 and have tried Windows 7 as well.

Please, if anyone can help it would be much appreciated!

---

### Post by wolfen69 on 2011-04-03
First off, check the lock... ;)

Have you tried running gparted as root?

---

### Post by Beatter on 2011-04-03
I just tried that, if I try to delete the partition it claims to have completed but when it refreshes it still has the partition.
When I try formatting the same happens with all the data still intact.

In the information it has a warning that says "Unable to open /dev/sdb read-write (Read-only file system). /dev/sdb has been opened read-only."

---

### Post by racie on 2011-04-03
Perhaps you have a faulty adapter and the lock isn't working properly.  I only suggest this because you get the same result on multiple computers.  Maybe you could borrow another from someone you know to see if this is really the problem or not.

---

### Post by Beatter on 2011-04-03
I've tried multiple adapters, what I'm using right now is a USB card reader with a MicroSD slot. So, no SD adapter.

---

### Post by wolfen69 on 2011-04-03
My guess is the card is toasted.

---

### Post by racie on 2011-04-03
Oh... hmmm.... a little Googling yields this:

> The switch / notch works in same way as the notches on compact audio cassettes and videotape cassette tapes or floppy disks. A closed or covered notch is writable, while an open notch (or removed tab) is protected.
If the switch becomes broken or falls off then the card will become a write-protected ROM card and no longer be writable. A possible troubleshooting solution would be to apply tape over the notched area (avoiding the connectors and the other notch) to configure the card in a permanent writable state.

Basically, it says to put tape over the lock/unlock switch because the switch is probably broken.  It wouldn't hurt to try.

*edit* Also, it wouldn't hurt to try blowing the dirt off of it and wipe it off with a cloth.

---

### Post by Beatter on 2011-04-03
there is no lock switch on the card reader I'm using right now because it has a specific slot for micro sd cards. I just cleaned the card and no change. Also, the adapter I have works fine with other microsd cards.

---

### Post by racie on 2011-04-03
*edit* Whoops... hold on.

---

### Post by Beatter on 2011-04-04
I did not put tape over the card reader...I am not using an adapter therefore there is no lock switch to put tape over. The card reader has a slot for MicroSD cards.

---

### Post by racie on 2011-04-04
Sorry, but the only other reasons for this I can find are:

1. The card is copy-protected by the manufacturer.  We know that this is not the case because this is only for phones.

2. The card needs to be inserted into the adapter with the lock switch on unlock.  When you take out the card from the adapter, it should now be unlocked.  We know this is also not the case because it sounds like you tried it already.

If I find anything else, I'll post back... but this looks like it's about it.

*edit*  Although a found a random post about a Windows Vista solution.  I can't guarantee this is safe or that it would even work.
> Enable/Disable Ability to Write to Removable Disk for vista

run reg edit
go to HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\storagedevicepolicies
set writeprotect to 0 to disable or 1 to enable

*edit2* Ohh wait!  I found another.  Some phones running Symbian OS are able to format many microSD cards, regardless of write protection.  If you know anyone with such a phone, it's worth a shot.

Also, have you tried putting the card into a camera and then connecting the camera to the PC via USB?  Who knows, it might work.



I dunno.... just throwing ideas around.

---

### Post by Beatter on 2011-04-04
No such luck :/ I tried all of those except the Symbian one because I don't know anyone with one.

Thanks for helping though

---

### Post by Chronon on 2011-04-04
Damaged file systems are commonly mounted as read-only to prevent further damage and possible data loss.  You should try fsck.vfat (or the appropriate tool if it isn't FAT32) to find and repair errors in the file system.

---

### Post by lindsay7 on 2011-04-04
Try the Hp usb disk storage tool 2.2.3

You can find it here,

[http://www.softpedia.com/get/System/Hard-Disk-Utils/HP-USB-Disk-Storage-Format-Tool.shtml](http://www.softpedia.com/get/System/Hard-Disk-Utils/HP-USB-Disk-Storage-Format-Tool.shtml)

---

