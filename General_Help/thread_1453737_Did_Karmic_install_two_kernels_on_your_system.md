---
title: "Did Karmic install two kernels on your system?"
date: 2010-04-13
forum: General Help
---

### Post by quadproc on 2010-04-13
I am wondering if anyone else had this happen, or knows what happened.  After I upgraded Jaunty to Karmic, I found that my grub menu has two pairs of OS options and that the kernel is slightly different between the two.  The highest numbered kernel seems to be a working OS release but the next choice in the list does not work correctly - its mouse pointer is invisible!

A bit of history might help to diagnose the problem:

I originally had installed Intrepid in a partition and I used it for a while.  Then I decided to upgrade to Jaunty so I put that release in a different partition.  I had major troubles getting the system going after the upgrade but I eventually succeeded.

Later, I decided to try out Karmic so I created a Live CD of it and tested that.  It seemed to be good so I decided to do a standard upgrade. At this point I still had the original Intrepid version on disk in its own partition.  The release notes suggested that a network upgrade was the preferred way to upgrade to Karmic so I did that, even though I had the CD.  The process seemed to complete OK.  I was getting some X windows complaints and X was running in low graphics mode so I uninstalled and reinstalled the fglrx driver; X was happy afterwards.  That seemed to be the only significant problem with the upgrade.

I noticed that my grub menu now had three fairly new selection pairs, as well as the memtest and the original Intrepid software.  I had gained two pairs during the Karmic upgrade.  I could not tell which was which by the kernel numbers.  I decided that three sets were inappropriate and I decided to remove one set.  I was hoping to remove whichever set was superfluous or unnecessary.  I picked the oldest of the three (i.e., the one with the smallest kernel number) and used Synaptic to abolish it.

Now, I had two pairs left.  The topmost pair is a working Karmic version which I am using right now.  The other pair seems to be a broken version of Karmic.  By that, I mean that it starts up exactly the same as the working version but when it gets to the login screen then there is no cursor!  Actually, the cursor is there but it is invisible.  I found that I could run the cursor all the way to the top right corner, click the left mouse button, and get the shutdown/restart/etc. menu.  The keyboard's arrow keys could then be used to select a menu item and the mouse button would activate it.  But all the while, the cursor was invisible!  Of course, this makes the system useless.

So, I think that I need to use Synaptic to remove the malfunctioning pair.  Questions: why did the upgrade give me two kernels?  Would it be safe to remove the earlier one?

What I would really like is to have both Karmic and Jaunty available from the grub menu.  I am afraid that I will have to do a new install in a different partition to get Jaunty back onto the system, and then will have to repeat all of the customizing and software installations that I have applied during the last year or so.  Does anyone know of a shortcut around that?

The kernel versions of the top pair are:
> 2.6.31-20-generic
2.6.28-18-genericAny insight into what these kernel versions mean, and what the "invisible cursor" bug is caused by, is welcome.  Thanks.

quadproc

---

### Post by cbecker78 on 2010-04-13
the .28-18 is left over from your Jaunty install.  It is the kernel version that comes with 9.04.  I also have that left over, and yes, trying to boot into it results in some odd behaviors.  I assume there is no problem with removing it, but figured to just leave it be since it is not bothering me and I do not exactly have a "space" issue on the HD.

Edit:
> he release notes suggested that a network upgrade was the preferred way to upgrade to Karmic so I did that
yah, I did it that same way... I don't remember if I read the release notes or just decided to do it, but the case is: it is NOT the preferred way.  We are supposedly better off doing a clean install (According to multiple informed posts I have read on this forum).

That is really the only thing that has bugged me off with Ubuntu so far: that they have their software prompt me to update, and then everything I read as I try to fix all of my new problems indicates I shouldn't have clicked on that little tempting button.

---

### Post by quadproc on 2010-04-14
> **cbecker78 said:**
> 

That is really the only thing that has bugged me off with Ubuntu so far: that they have their software prompt me to update, and then everything I read as I try to fix all of my new problems indicates I shouldn't have clicked on that little tempting button.
Yes, I know what you mean.

The Ubuntu folks might want to look into what Sun had done with their update system.  I worked at a place that used lots of Sun workstations and one of the features of their software upgrades was that you could back out of them, item by item.  For example, if you didn't like the new software debugger that was a part of the version upgrade then you could back out that program and you would be back to the debugger that you had had before.  That was a really valuable feature.  Perhaps this discussion should be the start of a new thread?

Thanks for your information on the kernel/version issue, and for letting me know that what I am seeing is not unique.

quadproc

---

