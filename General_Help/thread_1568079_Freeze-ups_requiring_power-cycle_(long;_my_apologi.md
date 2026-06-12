---
title: "Freeze-ups requiring power-cycle (long; my apologies)"
date: 2010-09-04
forum: General Help
---

### Post by benenglish on 2010-09-04
I have system freeze problems where everything freezes except the mouse pointer.

Here's the information I've gathered in an attempt to diagnose.

**[SIZE="4"]Hardware:[/SIZE]**

My machine is built on a ZOTAC GF9300-D-E LGA 775 Mini ITX Intel Motherboard with an Intel Core 2 Duo E8500 Wolfdale 3.16GHz 65W Dual-Core Processor and 4 gigs of RAM in the form of a G.SKILL PI Black 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Desktop Memory Kit.

The video card is a ZOTAC ZT-20201-10L GeForce GT 220 with 1GB of 128-bit DDR3 memory, plugged into the only available PCI Express slot.

The keyboard and mouse are USB-connected generic parts that apparently came in the box with an HP computer bought long ago.

**[SIZE="4"]Operating System:[/SIZE]**

I am using 10.04 LTS.  Since installation, I have accepted all default updates suggested by Update Manager.

[SIZE="4"]**Observed behavior, initial:**[/SIZE]

Screen freezes were first noticed when scrolling.  When rapidly scrolling down a long web page in Firefox, either by using the scroll wheel or by rapidly dragging the slide on the side of the window, freezes happened consistently.  By experimentation, I found that this could be avoided by scrolling slowly (too slowly for this to be a useful solution) or by not selecting the slider but, instead, pointing above or below it and holding down the left mouse button.  This did not work if I pointed above or below the slider and left-clicked quickly; that action would again lock the machine.

Further testing showed that this was not limited to Firefox.  Rapidly scrolling down a long list of messages in the Pan newsreader caused the same problem.

Rapidly moving the scroll wheel back and forth also causes the problem, but not as consistently.

After trying to use the machine like this for some time I found that occasionally a simple quick motion of the mouse pointer could cause the same problem.  This seems to occur consistently only when the video subsystem is already busy; I can only reproduce this particular failure mode when already playing video.

When the display freezes, nothing responds except mouse pointer movement.  The system will not react to any click or keyboard input.  Note that if the lockup occurs while playing video (using VLC), the screen freezes on the current video frame but the audio continues until the end of the video.

When the freeze happens while Pan is downloading files/messages, Pan stops downloading.  The progress bar simply freezes.  Unlike if I were to close Pan during a download, when a freeze happens, Pan forgets where it was.  After a reboot, it will have lost the list of files awaiting download and will no longer remember to use as the default download file location the last one I selected.  It's as if all updates made to Pan during that session are reverted to the previous instance.

The problem has existed since the OS was first installed.  All the updates that have been accepted since that time have made no change.  I find that, given the way I use my computer, it's impossible for me to work for an hour without a lockup.  Generally, I can't keep it running for more than 20 minutes or so until I hit a freeze condition.

[SIZE="4"]**Steps taken to diagnose:**[/SIZE]

Per the instructions at [https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze), I enabled apport and intended to induce a freeze.  Unfortunately, the instructions do not give instructions for determining if “...apport will collect it.”  After traipsing off on a side trip to [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport), it appears that the instructions for forcing apport to start may not survive the reboot process, so I edited etc/default/apport to change the “enabled” setting from 0 to 1.  Having done this, I tried to induce a freeze by starting Pan, going to a high-volume newsgroup, and dragging the window slider up and down rapidly.  I was unable to create a freeze immediately.  In an attempt to stress the system, I started two videos in two different players, opened a few dozen tabs in Firefox, started a large download via Pan, and attempted in several applications to do the sort of rapid scrolling that causes problems.

No dice.  No freeze.

I then saved the current state of this document and tried to simply work as normal, assuming a freeze would eventually hit me.  Sure enough, a short while later (less than an hour) I got my first freeze.

In var/crash, no files were found after a reboot.  There was no notification on the desktop from apport.  As per the instructions, I continued to work hoping that after some future crash apport would produce a useful report.

After multiple crashes, no data is found in var/crash.  In this configuration, apport is a bust.

**[SIZE="4"]Unable to report a bug:[/SIZE]**

Per the troubleshooting doc page, the stock reply for inadequate freeze bug reports is:

[I][INDENT]Thanks for reporting this bug and helping to make Ubuntu better. What you have described is a generic X freeze. It could be caused by any number of things, and you need to take some additional steps to provide a complete report. 
When did you upgrade to this version of Ubuntu? When did you first notice the freezes occurring? 
How frequently do the freezes occur? How many per day would you say you experience? 
List the applications you typically have open at the time of the freeze. 
Think back to the last few times it froze. What activities were you doing in each of those times? 
Do you have compiz enabled? Does the issue go away if you disable it? 
If your system is a laptop, do you suspend/resume it? Had you resumed at some point prior to the freezes? 
[COLOR="Red"]**Finally, and most importantly, please collect a GPU dump after reproducing the bug.**[/COLOR] Packages to install and directions for doing this are available at: 
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze#How%20to%20Get%20a%20Batchbuffer%20Dump%20(-intel%20only](https://wiki.ubuntu.com/X/Troubleshooting/Freeze#How%20to%20Get%20a%20Batchbuffer%20Dump%20(-intel%20only)) 
With the GPU dump in hand, we will be able to upstream this bug. 
For more tips on troubleshooting freeze bugs, please refer to this link: 
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)[/INDENT][/I]

Please note the part shown in red.  Furthermore, at the last link in that reply, there's a note that says:

*[INDENT]Include a Batchbuffer Dump. On -intel this is REQUIRED.[/INDENT]* 

I don't know what “On -intel” means (there's no definition or link for more info at the first use of that term in the document), but I assume that since I have an Intel processor, it applies to me.

Thus, I refer back to the troubleshooting doc to figure out the next step.  The next step is to try to get a batchbuffer dump by other means, specifically by replacing my kernel with a “mainline kernel” (of which there are several and hardly a word of guidance as to which I should choose), reproducing the error, then copying various log files into the bug report.

Excuse me?  I'm a user, just like 99%+ of the people who have installed Ubuntu.  Digging around in computer internals is occasionally fun but asking me to swap out kernels for diagnostic purposes is simply too much.  I'm not willing to go that far.  I doubt very many people in my position would be.

Thus, the bottom line, as I read all this, is that I am unable to gather the data required to submit a proper bug report that will actually get noticed and worked.  If I were to submit a bug report based on the data I've been able to gather, I'd get a not-so-polite “Thanks but kiss off” reply.

**[SIZE="4"]A plea for help[/SIZE]**

Does anyone have any idea what I might be able to do to fix this situation?  As I've read other posts, I get the impression that this is a longstanding problem with enough different causes and permutations that there's never been a real fix.

I hope that's not the case.

Realistically, I fear my next step is going to be to copy off my files and install a different distro.

I hope I don't have to do that.  I greatly appreciate the built-in whole-disk-encryption available via the alternate install disk for Ubuntu and would like to continue to use it.  I've done so for the last 3 or 4 machines I've had and all the spare hard drives lying around my house are encrypted with it.  To switch to another distro or OS, I'd have to pull one of my old/slow/retired computers out of the closet and use it to decrypt and transfer data.  This would entail weeks of work spread out over the next several months, a commitment I want to avoid.

I would really like to stay on Ubuntu.

So if anyone could point me where I should go next, I'd be highly appreciative.

Thanks in advance for any help,

Ben in Texas

---

