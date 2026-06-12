---
title: "Unable to burn CD/DVD"
date: 2010-06-11
forum: General Help
---

### Post by humbug01 on 2010-06-11
I feel really stupid here. I've looked around but no fix I can figure out. I downloaded a i386 iso of Ubuntu to install on my daughter's laptop and I can't get the CD/DVD Creator on my main computer to burn it to either CD or DVD.

I *know* I've done it before but maybe that was on Jaunty not Lucid which I have on my computer now.

I can load the iso file into CD/DVD Creator and when I get to the "Write to disc" option it says: "Write disc to: FILE IMAGE" and there is no option to write it to my CD/DVD drive. It's as if the DVD writer is not mounted.

EDIT: The md5 checksum is fine, by the way....

Any help please?

Thanks in advance,

Steve

---

### Post by humbug01 on 2010-06-12
Let me eleaborate on this problem in case it helps with the solution. Following the instructions on this site:

[http://www.ubuntu.com/server/get-ubuntu/download](http://www.ubuntu.com/server/get-ubuntu/download)

I'm following the steps under #2 "Burn your CD or create a USB drive" for Ubuntu which are in part as follows:

> 
The procedure may differ slightly depending on which version of Ubuntu you are using.

   1. Insert a blank CD into your burner. A 'CD/DVD Creator' or 'Choose Disc Type' window might pop up. Close this, as we will not be using it.
   2. Look for the downloaded ISO image in the file browser.
   3. Right click on the ISO image file and choose 'Write to Disc'.
   4. Where it says 'Write disc to', you may have options such as 'File image' as well as your CD drive. Choose your CD drive. Your CD drive may show as something like 'BD-MLT UJ-210S'
[snip]


I followed exactly up to this point and under step #4 the only option I have is "File image". When I click the option box it turns blue but my CD/DVD drive does not show up.

Any ideas? My CD/DVD component is an Optiarc DVD RW AD-7220S.

Thanks again,
Steve

---

### Post by TeoBigusGeekus on 2010-06-12
Why don't you use Brasero or K3b?

---

### Post by humbug01 on 2010-06-12
Fair question. I'd really prefer getting the Nautilus CD/DVD Creator program working if it's a setting or fixable problem on my system. (I installed Lucid with the alternate method with a minimalist approach and don't have Brasero or K3b on my system.)

S

---

### Post by ezsit on 2010-06-12
You need Brasero for the "Write to Disc" right-click feature to work. Brasero IS the built-in, default, CD burning backend, not Nautilus. Nautilus simply calls Brasero to do the actual  CD/DVD writing.

Also, if you did not install Brasero, K3B, or some other CD/DVD writing software, did you remember to install things like dvd+rw-tools, wodim, cdrdao, cdrecord, mkisofs, etc.? You could always use the command line tools if you have them. Something like (from within the directory containing the ISO file):

sudo cdrecord -v speed=16 dev=/dev/cdrom ubuntu-10.04-desktop-i386.iso

---

### Post by humbug01 on 2010-06-13
Thanks for the response EZ. Is this a change in Lucid that Brasero is required to burn CD/DVDs? I used the "CD/DVD Creator" in Jaunty alone, though I probably confused the issue by calling it that (it's how it's listed in the Gnome menu). The package is "nautilus-cd-burner" which did work without any other burner program in Jaunty for me (a few weeks ago before I upgraded to Lucid). Here's the info on this package from "aptitude show":

> Package: nautilus-cd-burner
New: yes
State: installed
Automatically installed: no
Version: 2.25.3-0ubuntu4
Priority: optional
Section: universe/gnome
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 3,293k
Depends: libc6 (>= 2.4), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78),
         libgconf2-4 (>= 2.27.0), libglade2-0 (>= 1:2.6.1), libglib2.0-0 (>=
         2.18.0), libgnome2-0 (>= 2.17.3), libgnomeui-0 (>= 2.22.0), libgtk2.0-0
         (>= 2.8.0), libhal1 (>= 0.5.8.1), libnautilus-burn4,
         libnautilus-extension1 (>= 1:2.29.1), genisoimage, wodim, gconf2 (>=
         2.10.1-2), cdrdao, nautilus, dvd+rw-tools
Description: CD Burning front-end for Nautilus
 Lets you burn CDs and DVDs easily with GNOME, by drag-and-dropping files in the
 GNOME file manager.


Anyhoo, I'll just keep poking around with this....

S

---

### Post by ezsit on 2010-06-13
The depends for nautilus-cd-burner look good. However, on my Karmic Koala box, when I open Nautilus CD Burner, after I select files to burn, it opens a small Brasero dialog box to ask for burn propterties and to select a burner, so I assume Brasero is doing the actual burning. 

I also have xfburn installed and that does not depend on a lot of the stuff that Brasero and others depend upon. If you are looking for something really light, give xfburn a try. It is part of the XFCE desktop, but it does not pull in many depends, a handful of small stuff at most.

---

### Post by humbug01 on 2010-06-13
Thanks EZ. Much appreciated. I'll look into Xfburn and I did try cdrecord from the command line and can burn a data CD that way with no problem which is a step forward.

---

### Post by humbug01 on 2010-06-14
I see that I'm not the only one with this problem:

[https://answers.launchpad.net/ubuntu/+source/nautilus-cd-burner/+question/110919](https://answers.launchpad.net/ubuntu/+source/nautilus-cd-burner/+question/110919)

However, I read further from Google and found that nautilus-cd-burner is depricated in Gnome in favor of Brasero, so it is no longer being updated. As a result, I purged it and installed Brasero and it works through Nautilus with no problems.

I should have listened to you guys from the start! Thank you for your help and sorry to be so stubborn but I wanted to fix it before moving to new software if possible. Not possible if depricated upstream though....

:)

---

