---
title: "Serious errors occurring"
date: 2010-07-14
forum: General Help
---

### Post by pYrO1v1aniac on 2010-07-14
On my girlfreind's MSI GX720 laptop, after a while of use, weird errors start happening. Closing firefox brings up a blank small window, as if a notification window, with firefox at the top, and the browser won't close. Can't start any other programs, and have to force a hard reset, because the shutdown window appears blank and nothing happens.

After the hard resets, it always runs a full FSCK after it shows a corrupted filesystem error of some kind, but then the errors always start happening again.

On top of that, it's performance is very poor, using way more ram and constant CPU, heavy fans than my far less well specced laptop
(She has a dual core 2.4ghz, Nvidia 9600M, 4GB of DDR2, I have a dualcore 2.4, 2GB of DDR2 and an Nvidia 8600GT). She can't play fullscreen flash videos without major tearing, many normal operations cause strange freezeups, and system monitor shows her system is using way more CPU all the time even idling than mine. It did the same with 9. and 8. distros.

What could be causing all of this?

---

### Post by ajgreeny on 2010-07-14
I would imagine the tiny window you see is exactly that; a tiny window from some pop-up or other.  You should be able to resize it by dragging a corner or side until you can see the shutdown button, or even see what it contains, if anything.  I have had the same thing happen to me once or twice in the past, but not for a long time, so it may be that I have some add-on that is now stopping this happen, though I don't remember adding anything that would do this since it last occurred.

As for the full screen flash movies, I am not surprised about your comment, and I am sure you will find lots of posts bemoaning the poor performance of flash in ubuntu and linux in general on web forums, including this one;  I'm afraid it's a linux/Adobe flash problem, not a ubuntu one.

You do not mention anything about video drivers on either your nor your girlfriend's machine, but that would be the first place to start looking for better video performance, ie System ->Administration ->Hardware Drivers, if you have not already done so.

---

### Post by pYrO1v1aniac on 2010-07-14
No, it's definitely not a popup, since it occurs on random sites, and there are no addons on her system, and it only appears when she tries to close firefox. I think it's supposed to contain the "Are you sure you want to close multiple tabs" dialog, but it's empty, and each time it appears, it can be got rid of, but firefox itself won't do anything.

Also, UI elements like force quit just throw up blank boxes too, and I can't start new programs. The shutdown dialog is also a blank box of the right size.

She's using Nvidia Proprietary current, same as me, but my laptop will happily play flash video, where hers won't, even though my specs are one generation behind hers.

---

### Post by ajgreeny on 2010-07-14
Could it be a glitch in her FF profile?   Try renaming her ~/.mozilla folder and starting FF again, then restore her bookmarks from the .json backups in the old profile.

---

### Post by NoBugs! on 2010-07-14
> **pYrO1v1aniac said:**
> 
After the hard resets, it always runs a full FSCK after it shows a corrupted filesystem error of some kind, but then the errors always start happening again.


Could it be a damaged hard drive? Have you checked it with gsmartcontrol?

---

