---
title: "Now it is a USB floppy problem"
date: 2010-05-16
forum: General Help
---

### Post by oldefoxx on 2010-05-16
My wife needs a floppy working with her PC, and using a USB floppy, I managed to give her one.  This is with VirtualBox and Windows 2000, which have mostly worked well for a good while.  The trouble was, that
passing the floppy as USB caused Windows to see it as Drive B:  Don't know why, but no way to change it, and she has to have it as Drive A:
Solution seemed to be not to pass it as USB, but set up Shared Folders
to point to it, then map it as A: when Windows sees it as a Network
Drive. That has worked for her, and I have used that method for months-.

-Only trouble is, that method does not work any more.  There have been two upgrades to VirtualBox, and that might be part of the problem, but
if I could just get the USB floppy to show up as drive A:, I would not have this problem at all.  USB devices show up and work pretty good.

That is not the only problem either.  Now I see a new entry under/media named /$BOOTVOL3, and I don't know where the heck that came from.  If I do a dir on /media/$BOOTVOL3, I find inside exactly the same folder names as I have under /media, except without the $BOOTVOL3.  So where is this coming from? Oh, but the floppy drive is also missing.

Under /Places/Computers, the floppy shows up as 1.5media.  It may instead show as a floppy drive at times, but that cannot be mounted or unmounted.  And it may also show an extra USB drive, but that cannot be mounted or unmounted either.  What's with all these extra drive designatons all of a sudden?

Seeing as this is a USB connected device, I am not even sure where I can find it among the many folders and files.  I mean you cannot go to /etc/fstab and add an entry that starts: /dev/fd0 /media/floppy, because there is no /dev/fd0.  So what do you do instead?  I guess it is under /proc somewhere, but how does that help you?
 
This, and the fact that leaving the keyboard idle for a bit causes the screen to quit updating and even locks up the VirtualBox client, means that there is a lot to ask of users who only want to sit down and get their job done, whatever that is.

But that thing about $BOOTVOL3 is particularly wierd.  Where the heck did that come from?  And what else got messed up at the same time.

Maybe some of you out there can tell me, which would be appreciated.  And quickly too.  My wife needs that floppy drive A; back for her embroidery stuff, and she is on a deadline.

---

### Post by -humanaut- on 2010-05-16
If I remember correctly Virtualbox can't "see" USB devices. If Ubuntu can see it why not copy the files on to the HDD then simply copy them over to the virtualbox instances of Windows?

---

