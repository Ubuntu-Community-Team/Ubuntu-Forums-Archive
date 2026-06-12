---
title: "Cannot boot fresh install, nouveau lockup?"
date: 2010-10-29
forum: General Help
---

### Post by hwttdz on 2010-10-29
So I've installed ubuntu I don't know how many times, and I usually (read the last 10+ times) use the minimal install and then install a selection of packages afterwards.  Anyways I hadn't done a clean install to 10.10 (upgraded from 10.04), and my network was giving me some issues, so I figured it would be better to start from scratch.  But after installing and installing some packages I found that the machine seemed to lock up when starting the graphics.  I'm currently on a live usb drive on the same box so I can reach any files from that machine.  It seemed to flash something about nouveau before it locked up, but I'm not so sure

syslog:Oct 29 01:25:29 poseidon kernel: [    5.185324] [drm] nouveau 0000:02:00.0: GPU lockup - switching to software fbcon

---

### Post by nitinab on 2010-10-29
i am having an almost similar condition ... off the live disk right now ... which takes for ever ... but does boot into graphics mode ... when booting off the hard disk though ... it boots up really slow .. with console login prompt in some 18 seconds or so ... after which it continues to try to start failsafe-x which takes some further two minutes to remove the terminal screen and replace it with the blank screen ... which then stays blank ... on pressing the power button it terminates with an failsafe-x error 1.

Then again there are other assorted problems like the live cd unable to recognize the sound hardware and that the reason i did  a fresh install was that compiz compositioning had stopped working at all after a kernel/compiz i dont remember exactly what upgrade that needed a restart. I used KDE for for a few days which was compositioning still.

So is it the same problem or do i start a new more detailed thread?

---

### Post by laylow45 on 2010-10-29
I ran into major problems when I upgraded from 10.04 to 10.10. Latest Nvidia graphics Linux driver installation with Xserver not compatible. Now booting up into a black screen. :confused: Contemplating reverting to 10.04. Anyone run into similar problems? :confused:

---

### Post by hwttdz on 2010-10-29
Well starting from scratch and avoiding installing gdm until the last possible package.  I think I needed to have nvidia-common and nvidia-current installed before I installed gdm.  Anyways I now have a graphics environment and I'm trying to figure out some themes nonsense.

Sidenote to the people who posted intermediately, it makes it more difficult to answer questions if everything is hodgepodge. If you're having the _exact_ same issue feel free to say I have the same issue.  Or if you think you have the same issue you might ask "do you get this error when you run this command?" but if you have a different error it just confuses issues.

---

