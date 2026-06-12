---
title: "Mount problems with USB drives and Gparted"
date: 2010-09-14
forum: General Help
---

### Post by grahamst on 2010-09-14
Whenever I insert a USB drive I get the following error message:

Error mounting '[USB name]': DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending.

However, the drive is recognised, a folder is opened and I can work with it normally, including removing it safely when I've finished with it.

After searching in the forums I tried disabling the Nautilus preference settings media_automount and media_automount_open

The only difference was that I didn't get the error message - I could still use the drive as normal.

Is there a way to fix the mount error? Are there any problems associated with leaving it unfixed?

===

I would just live with the above situation, except that I think there's a more general problem with mounting devices. I want to resize my Ubuntu partition using Gparted, but the operation to do this fails at the point when the partition is being checked (e2fsck) because the unmounting procedure that needs to be done before the resize doesn't seem to work.

After I click on 'Unmount', Gparted greys out 'Unmount' and activates the Resize/Move' option, so all seems well, but on the desktop there's an error message saying:
Could not get root for mount '(null)'.

I have a feeling all these mount errors have a common cause.  Is there anything that can be done to fix them?

Graham

---

### Post by widda on 2011-02-28
Ancient as this is, a reply:
I,ve had similar issues with 10.04 and one particular ext usb (Vaio) drive, for which the most effective suggestion was that the drive may have been used in windows and improperly shut down, and needed opening and closing in Windows.   
System messages varied. 
First time for this message tho, but unlike you, I actually can't access drive - doesnt show on desktop. and left or right clicking it under Places, get that message. 
I do know this time that it *was* used in XP last week, so I'll try that when I get back to xpmachine.
Meantime will explore some saved suggestions from previous helpful Linuxians.

---

