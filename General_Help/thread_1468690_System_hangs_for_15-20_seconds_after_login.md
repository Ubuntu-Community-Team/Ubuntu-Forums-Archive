---
title: "System hangs for 15-20 seconds after login"
date: 2010-05-01
forum: General Help
---

### Post by Cam2A on 2010-05-01
Hi all, just had a bit of a battle with this one and figured I would let you all know about it in case I wasn't the only one struggling.

Just installed Lucid Lynx on my Desktop and after logging in I would get a 15-20 second pause before Gnome appeared. I found many many potential solutions for this problem on the Internet but none solved it. Finally figured out that it was due to the system seeing a floppy controller when I have no floppy drive. I was led to this conclusion by the following two lines in my syslog (System > Administration > Log FIle Viewer > Syslog).

May  1 18:27:04 Desk-Ubuntu kernel: [   34.636665] end_request: I/O error, dev fd0, sector 0
May  1 18:27:16 Desk-Ubuntu kernel: [   46.813441] end_request: I/O error, dev fd0, sector 0

Note the 12 second delay when it tries to read again.

So if you are getting the pause and seeing the same thing your system log then ...


[LIST=1]
[*]Enter your BIOS and disable the floppy drive
[*]Use sudo and edit /etc/fstab commenting out the line with fd0 in it
[/LIST]

Hope I can save someone else the headache of hunting through the Interwebs and finding 5 different solutions none of which worked. Learning as I go with Ubuntu so I didn't even know how to carry out most of the "solutions" which required more googling. I am migrating from FreeBSD due to application requirements :P

Regards,
Cameron

---

### Post by e45cream on 2010-05-02
Thanks. worked perfectly.

---

### Post by Karail on 2010-05-08
Thank you very much. Desktop loads almost instantly now.

---

