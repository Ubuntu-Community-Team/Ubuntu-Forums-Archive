---
title: "Creative Live Cam Socialize Web Camera"
date: 2011-08-25
forum: General Help
---

### Post by altkon on 2011-08-25
Dear Ubuntu Forum memebers,
I have received the following reply from the Creative Customer Support.
My problem is that their Live! Com Socaliaze Web Camera is not
working with my Ubuntu 11.1 System apparently because it is not
a Linux Kernel 2.6 version but a 6.2 one.
Is there a work around to resolve this issue??
Thank you.
altkon




Dear Andre,

Thank you for getting back to us.

Please be informed that Live! Cam Socialize can only work on the following Operating System:
Microsoft® Windows® 7 32-bit or 64-bit / Windows Vista® 32-bit or 64-bit with Service Pack 1 / Windows XP Professional x64 Edition / Windows XP with Service Pack 2
Apple® Macintosh® OS X 10.5
Linux® Kernel 2.6

If you still require assistance, please reply to this email and include any previous correspondence to ensure a quick response.

Best Regards,

Martina
Worldwide Customer Response
Creative

---

### Post by no2498 on 2011-08-25
what all programs you try the cam in
open a terminal type dmesg click enter
did it load anything for the cam look close to the bottom
in the terminal type lsusb click enter
that should give a number and name for your cam
put the number and name in google and do a search
hope it helps you

---

### Post by Topsiho on 2011-08-25
> **altkon said:**
>  because it is not
a Linux Kernel 2.6 version but a 6.2 one.


Your Linux kernel IS a 2.6 version. A 6.2 version doesn't exist.

Topsiho

---

### Post by altkon on 2011-08-25
> **Topsiho said:**
> Your Linux kernel IS a 2.6 version. A 6.2 version doesn't exist.

Topsiho

I am sorry for the confusion..
However since my Ubuntu 11.1 has a Linux Kernel 2.6 version my camera should be recognized by my system, but nevertheless it does not work.

---

### Post by no2498 on 2011-08-26
whats the output of lsusb

---

### Post by altkon on 2011-08-27
> **no2498 said:**
> whats the output of lsusb
This is a screenshot of the outcome.

/home/user/&#917;&#960;&#953;&#966;&#940;&#957;&#949;&#953;&#945; &#949;&#961;&#947;&#945;&#963;&#943;&#945;&#962;/Screenshot.png

In case you cannot open it says:
Bus 001 Device 003:ID041e:4083 Creative Technology, Ltd Live Cam Socialize
(VF0640)
Bus 001 Device 001 ID 1d6b:002 Linux Foundation 2.0 root hub

All drivers that I found in Google for VF640 are for windows nothing for Linux.

My operating system is Linux user-Satellite-A200 2.6.38-11-generic i686

I tried to "sudo apt-get install cheese" but without success.

---

### Post by altkon on 2011-08-27
Now I am at the pleasant condition to inform you that I managed to conduct
an MSN video call connection with Empathy.
My only problem now is that I have an incoming Audio Voice but no
outgoing voice..
Appreciate if you could guide me to work around this issue as well.
Thanks a lot to all of you.

---

### Post by no2498 on 2011-08-28
i see it found the cam
now do this

open a terminal type dmesg click enter
 did it load anything for the cam look close to the bottom

in your package manager look for and install guvcview
try the cam in it

---

### Post by Duncan Williams on 2011-08-28
sorta repeating advice already given.
I have recently setup my little webcam and was at first confused as to what to do.
Using `synaptic' or `software manager'
install:
cheese
guvcview
plug in your webcam first
click on either program
you should get a result.

---

### Post by no2498 on 2011-08-28
no dmesg  should say it loaded a cam grabber and tell what driver it loaded

close the terminal before you open the package manager
we can only use 1 at a time

---

### Post by altkon on 2011-08-30
> **altkon said:**
> Now I am at the pleasant condition to inform you that I managed to conduct
an MSN video call connection with Empathy.
My only problem now is that I have an incoming Audio Voice but no
outgoing voice..
Appreciate if you could guide me to work around this issue as well.
Thanks a lot to all of you.

from System> Sound Preferences >Hardware>Input >selected Livecam
Socialize VF0640 raised the voice..now tested and it works.
I was able to make a MSN Video call with my friend.
Now this case resolved..
Thanks a lot to everybody

---

