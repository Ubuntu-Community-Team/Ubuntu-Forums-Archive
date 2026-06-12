---
title: "wizardpen and new kKanvus Note A4"
date: 2010-05-20
forum: General Help
---

### Post by voland66 on 2010-05-20
Hi,
I need some help installing wizardpen driver for Kanvus Note A4 "Digital Organizer". It seems to be new but shows up with 
Vendor ID 5543 (UC-Logic) whose tablets are supported by wizardpen. Moreover product ID is 6003 which is very close to the numbers in various configuration files included with the source code.

But after I follow all the steps in howto, it does not quite work. The stylus moves the pointer on the screen but only in a very small area in the left top corner. 
It is not clear to me if the correct driver is loaded.
On the one hand, wizardpen is referred to in various places in /var/log/Xorg.0.log. On the other hand, there are two places in lshal output referring to the devise and they contain 
 info.linux.driver = 'usb'
and
info.linux.driver = 'usbhid'
as drivers.

Another aspect that I noticed is that wizardpen-calibrate gives rather strange values of BottomX and BottomY -- both are 3999 and much smaller than any numbers I see in messages on the forum.

I can post all the files/information which might be needed, but I am not sure which one will be useful, so please let me know what to post.

I'll appreciate any help.
Yuri
(Actually, I am on mostly kubuntu installation but I doubt it matters for this purpose.)

---

### Post by kamal_sisira on 2010-07-07
Have you got your problem solved? I encountered the same problem with Genius G-Note 7100 and was able to solve the issue. Let me know.

---

### Post by shvahabi on 2010-07-09
I have the same problem with my G-Note 7100

As soon as I close the pen to tablet, the mouse pointer snaps to top left corner and no other moves.

Any one can help please?

---

### Post by kamal_sisira on 2010-07-13
OK. Here's the solution: [http://www.swview.org/blog/configuring-genius-g-note-7100-linux]("http://www.swview.org/blog/configuring-genius-g-note-7100-linux")

---

