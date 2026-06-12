---
title: "Calibre error communicating with e-book reader"
date: 2010-11-30
forum: General Help
---

### Post by boxcorner on 2010-11-30
Could someone me help, please?

What I think I need to know is how to change a volume's attribute, from read-only to read/write.
The volume in this case is connected to my PC via USB.

Here's the problem that I'm trying to resolve:

I use Calibre with an e-book reader that connects via USB. 
It has been working without any difficulty.

Calibre has suddenly begun to report that it only gets the device information and fails to get the list of books on the device. It generates an error: (30, 'Read-only file system')

I checked the USB connections and upgraded to the latest version of Calibre, all to no avail. 

Ubuntu's Disk Utility shows the reader actually comprises four file systems, two of which are not relevant here because they are memory card slots.

Calibre's author told me to run fsck.vfat on the device, ie run a filesystem check.

So, I used the Disk Utility:
System > Administration > Disk Utility > Sony PRS-650
File system is clean
System > Administration > Disk Utility > Sony PRS-650 Launcher
*The file system is NOT clean.*

So, the volume *Sony PRS-650* is clean, but the volume *Sony PRS-650 Launcher* is not.

He explained that Linux kernels mount filesystems as read-only when there are errors on them.
So, I was told to open Terminal and type:
sudo dmesg
after plugging in the reader, to see why the filesystem is being mounted read-only.

Here's one of the lines from the output:
[ 6346.604342] sd 5:0:0:3: [sdg] *Write Protect is on*

I haven't knowingly turned it on, nor am I aware of anything that might have caused this attribute to have changed.  I have no knowledge of why write protect is on, when it shouldn't be.  Would/could the occurrence of errors on the volume have automatically triggered the attribute to be changed from read/write to read-only?  If so, then how can the errors possibly be corrected, if the volume is read-only?!

The volume *Sony PRS-650 Launcher* is /dev/sdg
So, I was told to run fsck.vfat -y /dev/sdg

rdh@rdh-desktop:~$ sudo fsck.vfat -y /dev/sdg
[sudo] password for rdh: 
dosfsck 3.0.7, 24 Dec 2009, FAT32, LFN
open: Read-only file system

_Addendum_
I have tried doing the following:
Places > select the drive, which is called READER
Right-click on each of the folders and files > Properties > Permissions
All attempts to change the attributes to read and write are ignored
Similarly, when I do the following:
File browser > /media > right-click on READER > Properties > Permissions
All attempts to change the attributes to read and write are ignored

_Solution_
I disconnected the USB cable and then formatted the internal memory:
OPTIONS > Settings > Initialization > Format Memory > Internal Memory
Reconnected the USB cable, started Calibre, which reported "Connected SONY Reader".
Selected a book and clicked on Send to device.
The usual green check/tick mark alongside "Main" appeared in the On Device column.
Disconnected the USB cable and located the book on the reader, all right.

Now, here's the interesting part ...
I reconnected the USB cable and then looked at the four volumes, using Disk Utility.
READER, of course, was mounted, however SETTING (Launcher) wasn't.
So, presumably SETTING is only used when connecting to Sony's bookstore, under either Windows or OS X.

---

