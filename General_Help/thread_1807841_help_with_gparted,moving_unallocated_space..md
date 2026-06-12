---
title: "help with gparted,moving unallocated space."
date: 2011-07-19
forum: General Help
---

### Post by idoza on 2011-07-19
lets starts with a picture :
[IMG]http://img193.imageshack.us/i/screenshotvbw.png/[/IMG][[IMG]http://img193.imageshack.us/img193/9626/screenshotvbw.png[/IMG]](http://img193.imageshack.us/i/screenshotvbw.png/)

Uploaded with [ImageShack.us](http://imageshack.us)
/sda3- windows7
/sda6- ubunto11.04
what i want to do is to add the unallocated space to  /sda3.
i used gparted from live cd ,but still, i didnt manage to move the unallocated space near /sda 3 and extend  sda3.
any help will be appreciated.
thanks.

---

### Post by dandnsmith on 2011-07-19
Working from LiveCD is right (not as in your pic, which has partitions locked).
First move partitions within the extended partition to the (as depicted) lower end, leaving the spare space at the start of the extended partition sda4.
Next shrink the extended partition to enclose only the occupied partitions (I'm assuming we won't bother with that odd 1MB at the end).
Now you can expand sda3 to take in the free space.
I, personally, would do this as 3 distinct operations, in order to allow any problems to show up and be solved at the time.

---

### Post by idoza on 2011-07-19
this is the situation on live cd:
[[IMG]http://img35.imageshack.us/img35/3281/screenshotabd.png[/IMG]](http://img35.imageshack.us/i/screenshotabd.png/)

still got locked partiotions and i cant move any of them within the extended partition to the  lower end.

---

### Post by Quackers on 2011-07-19
Right-click on the swap partition and select "swapoff".
That should clear it.

On a different note sda3 look s like it may need a chkdsk to be run.

---

### Post by idoza on 2011-07-19
thank you very much .

i used this guide also :[http://gparted.sourceforge.net/larry/tips/gfs.htm](http://gparted.sourceforge.net/larry/tips/gfs.htm)

---

### Post by Quackers on 2011-07-19
You're welcome. Some of the moves may take a while.

---

### Post by ajgreeny on 2011-07-19
You need to right click on the swap partition, sda7 and choose "swapoff" to be able to do anything to any of the partitions within the extended sda4.  You may need to right click on sda4 and choose unmount, but I think swapoff should be all that's needed.

Now click on sda6, choose resize/move and drag the partition fully to the right as far as you can.  Do the same for sda5, the small ntfs partition, and then click on "Apply" and go away and make several cups of coffee as it is going to take a very long time to move and check those partitions.  If you are using UUIDs as standard in your /etc/fstab file ubuntu should still boot OK as these activities on partitions should not have changes any UUIDs.

The unallocated space will now be next to the sda3 win7 partition, but before you do anything else shrink the extended partition fully to the right up to the edge of the moved small ntfs partition, so that the unallocated space is now outside the extended partition.

Finally boot to windows 7 and use the win7 disk management utility to enlarge the windows partition to include this unallocated space.  Never use gparted to work on vista or Win7 partitions, as they can be very fussy and you could end up unable to boot them.  Much safer to do that in windows itself.

---

