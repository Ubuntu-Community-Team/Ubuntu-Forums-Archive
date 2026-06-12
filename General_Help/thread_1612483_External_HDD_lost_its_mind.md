---
title: "External HDD lost its mind"
date: 2010-11-03
forum: General Help
---

### Post by Bartender on 2010-11-03
OK, this is a weird one.

Have a Seagate 1TB HDD inside an Antec MX1 case.  Never given me any problems.  Last night I was trying out mkvtoolnix on a .m4v rip.  After mkvtoolnix did its thing I tried to move the new file back to the external.  I got an error.  "There was an error while moving file ***"  Now the Seagate won't let me copy or move any files outside of that folder.   

All's I can figure out for sure is this: I had the Seagate plugged into a USB port that apparently is failing.  While trying to figure out what was wrong, I unmounted the Seagate, unplugged it from the USB port, and plugged the wireless mouse receiver into the same USB port.  The mouse doesn't work.  It does work on all the other ports.

Some of the rips have weird symbols instead of the "dot" between filename and the "m4v" or "mkv" extension.  It appears to my uneducated eye that the folder's been corrupted.  Or maybe permissions?

So I took the Seagate to another Ubuntu PC.  The Seagate still refuses to let go of any rips in the "Rips" folder.  I plugged in another external HDD so I could compare permissions.  When I right-click and go into Properties, both drives say Permissions could not be determined, but the second external HDD "just works" while the Seagate is balled up.

Any ideas???

EDIT:  This seems a little dumb, but since I'm not a Linux guru I go for the easy ideas - I also pulled the Seagate 1TB drive out of the one enclosure and tried it in another enclosure.  Made no difference.

---

### Post by Bartender on 2010-11-03
I'm attaching a screenshot.  This pops up for every rip that I try to copy or move from the Seagate 1TB to another external HDD.  However, once I click "Skip" the file appears in the new drive folder and it appears to be the same amount of data as the original.

I know there's at least one way to compare files but sure don't know how off the top of my head.

I guess the thing next thing to do is try and play one of the files even though the error came in...

---

### Post by coffeecat on 2010-11-03
The most likely explanation is that there is a filesystem corruption. Don't try to move anything around or rename anything until you've tried a filesystem repair. What filesystem is it? If you haven't reformatted it, it is probably NTFS in which case you need Windows in order to run chkdsk. If it's a Linux filesystem, post back and we'll take it from there.

---

### Post by Bartender on 2010-11-03
I have gparted on a bootable CD and I'm not afraid to use it :)  
The external is formatted as ntfs for interoperability.  

Thanks for the suggestion!  I'll fire up a Windows PC and try chkdsk.  Chkdsk comes up automatically for the main drive if Winders sees something out of whack but I don't know how to get it to run on an external?  I'll give it a shot and see what happens.  

Back in a bit.

EDIT:  Looks like this is how I'd run chkdsk:  Start>Run; then type in     [COLOR="RoyalBlue"]chkdsk X: /f[/COLOR]    where "X" is the drive letter that Windows assigned to the device.
Another google hit says to use [COLOR="RoyalBlue"]chkdsk E: /r/x[/COLOR] where E is the device.

---

### Post by Bartender on 2010-11-03
I used chkdsk with the /f switch.  "/f" looked like "format" to me but Wikipedia said different.

chkdsk found dozens of errors.  I ran it a second time - no errors.  Plugged it back into our main Linux PC and everything appears to be right as rain.  No weird Oriental-looking symbols and files appear to be transferring.

Thanks very much for the help.  I was freakin out there for a while.

---

### Post by coffeecat on 2010-11-03
I'm glad it worked. Good luck.

---

