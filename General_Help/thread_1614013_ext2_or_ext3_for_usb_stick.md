---
title: "ext2 or ext3 for usb stick?"
date: 2010-11-05
forum: General Help
---

### Post by frank4360 on 2010-11-05
I use 8GB USB sticks for backup of Ubuntu 10.04. I have had a variety of problems with ext3 format (security tar file not readable, etc) and have reformatted to ext2, so far without a problem.

But - am I missing something by not using ext3 (or even ext4)? Should I be sticking with ext3 and try to resolve the problems - bearing in mind that as the USB stick is my backup I need it to be secure!

Thanks in advance for any comments and info.

---

### Post by dcstar on 2010-11-05
> **frank4360 said:**
> I use 8GB USB sticks for backup of Ubuntu 10.04. I have had a variety of problems with ext3 format (security tar file not readable, etc) and have reformatted to ext2, so far without a problem.

But - am I missing something by not using ext3 (or even ext4)? Should I be sticking with ext3 and try to resolve the problems - bearing in mind that as the USB stick is my backup I need it to be secure!

Thanks in advance for any comments and info.
[LIST=1]
[*]Ext3 is just Ext2 with a journal, if you have had problems it is because of another reason.
[*]Ext4 is better than Ext3 (or 2), use that.
[*]Always correctly Unmount or Eject USB devices before removing them, people who do this have few (if any) problems.
[/LIST]

---

### Post by frank4360 on 2010-11-05
> **dcstar said:**
> [LIST=1]
[*]Always correctly Unmount or Eject USB devices before removing them, people who do this have few (if any) problems.
[/LIST]

Thanks for your reply David

After some experimenting, I think that the problem has been the Unmount procedure.

When trying to unmount the USB stick I select "Places" and the drop down box shows, among other directories "Computer", "USB stick" and "cdrom0"

Previously I have selected "USB stick" with either a left or rightmouse click - the result is the same - and when the File Browser shows the USB contents I selected "File". Now any attempt to "Eject" or "safely remove drive" fails with an error message such as "unable to eject USB permission denied" or "Failed to unmount cannot remove directory".

However, if I select "Computer" in the drop down box from "Places" and then select the USB stick from the resulting file list, I can right click and use Unmount, Eject or Safely Remove Drive. Any of these options works.

It seems odd that the first procedure offers the facility to Eject or Safely Remove, but neither option works. In the past I have often just removed the USB stick in frustration, and this is presumably the reason for occasional problems.


Thanks again.

---

