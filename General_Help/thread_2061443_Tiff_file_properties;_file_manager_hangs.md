---
title: "Tiff file properties; file manager hangs"
date: 2012-09-22
forum: General Help
---

### Post by dasbrow on 2012-09-22
File manager is hanging when I try to view the properties of tiff files.

When I right mouse click on a tiff file in my Pictures directory of my Home folder and select Properties, my file manager hanges and I must "force quit".  I have copied two tiff files from Pictures to the desktop and the properties have displayed ok.  I copied 1 tiff file from Pictures to Music and the properties request again hung the file manager requireing a "force quit".

Background:  I built a new system upgrading from an i5-2500k to an i5-3570k ... new everything except the case, mouse, keyboard and monitor.  The Picture, Music and Document folders were saved to an external drive before the rebuild and copied back after the system was assembled. Files in the Document and Music folders display properties ok. I have Virtualbox install guesting Win 7 (64) and shared the Pictures folder.  Music and Documents folders are not shared but Virtualbox has not been launched during this session.  Although copying a tiff file to the desktop allows me to view the properties, moving the entire Pictures folder to the desktop does NOT help.  Creating a new Pictures folder in Home and copying a tiff file from the Pictures folder now on the desktop does NOT help.  Copying a tiff file from the Pictures folder on the desktop (which will not display properties) allows me to view the properties (and provides a preview of the image not displayed in the directories usually - I haven't questioned that in the past).  Moving that tiff file from the desktop to the new Picture folder in my Home folder reintroduces the problem and opening the properties screen hangs the file manager.

Does anybody know what is wrong?  And, how to fix it?

Thanks.

Dino

---

### Post by coldraven on 2012-09-22
Just guessing here: 
Is there a setting in your file browser not to show previews for files over a certain size? Some of these TIFF files can be very big.
I seem to remember that you can set folder specific options but I cannot remember how..
Sorry that this is not very helpful, hopefully someone else will join in.

---

### Post by dasbrow on 2012-09-22
Thanks, Coldraven. That explains why some tiff files show a preview in the file manager and some don't.  But, there is nothing in this same Preferences screen that would explain why calling up a files properties would hang the file manager.  Any thoughts on that?

---

### Post by dasbrow on 2012-09-22
The problem appears to be associated with the interface but that may be a red herring.  If I launch Ubuntu 12.04 in 2D, the tiff file properties are read and displayed ... I can hear the hd spin when I launch the request.  Under 3D, I don't her the drive read when the request is launched.  Sounds like a clue BUT it doesn't work when I launch Ubuntu in Gnome Classic OR Gnome Classic (no effects).  I'd kind of think it should work in the no effects mode just as it does in 2D mode.  No the case, however.  So, something more is going on.  I'm using the Intel on-chip gpu (HD 4000).  I had trouble with the HD 3000 version on the i5-2500K chip, which was one reason I tried the i5-3570K chip.  on the 2500K system, I installed the nVidia GT 640 card to try to avoid similar but not the same interface issues but that only partially helped.

Anybody got any idea what's going on or not going on?  It's like the command to display the properties can't or won't find the data to display.

---

### Post by frontierlab on 2012-12-20
I have the same issue, suddenly today.
When I try to open and view the properties of tiff files, specifically ones I got from skype file transfer, my finder freezes up, windows start to duplicate, I don't have full control of the mouse and then other windows, including skype and the console duplicate when I try to move them. I have to force quit and sometimes even do a hard shut off. At one point in attempting to shut down I got the message that Compiz was running and was frozen (no idea what that means).

Sorry I can't offer any help. I just wanted to post to say I seem to have the same issue and it has just become a problem today. I have often gotten similar files from the same source and never had any problem before.

I did make a copy (using copy-paste to desktop) of the files and then I had no problem, could see all properties and nothing weird happened. But I find this worrysome.

---

### Post by frontierlab on 2012-12-20
ok I just noticed something... i have a problem with files makes .tif (one f) and no problem with files marked .tiff(2 Ts)

But again, this problem only started today I think, had some older tif with one T files and it was always fine and today I have a problem viewing the properties of those files too.

help?

---

