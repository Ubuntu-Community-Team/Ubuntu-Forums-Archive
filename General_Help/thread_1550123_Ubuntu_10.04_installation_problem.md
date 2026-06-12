---
title: "Ubuntu 10.04 installation problem"
date: 2010-08-10
forum: General Help
---

### Post by husnuyldz on 2010-08-10
I m new user in ubuntu forum.. I have a installation problem..&#305; want to setup ubuntu 10.04 but everytime I face black screen and crash...I searched a lot but nothing helped me..
I have toshiba L650-11F...
during the installation ,if only in installation page ,help of f6 &#305; selected acpi=off, after install ubuntu 10.04 , &#305; don't open ubuntu...black screen and crash..
please help me :(

---

### Post by Rubi1200 on 2010-08-10
You could try the workarounds mentioned here:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by husnuyldz on 2010-08-11
Thank you for your answer :) 
I tried all options  in the install screen only acpi=off helped me..but before this &#305; installed same way..and then finish installation,&#305; clicked restart button ..and &#305; faced black screen and crash...in the black screen ,laptop showed some adresses..thanks to acpi=off ,&#305; can use "try to ubuntu before the installation" ...What can I do?

---

### Post by Rubi1200 on 2010-08-11
Sorry husnuyldz but I am having trouble understanding you. 
Did you install Ubuntu yes or no?
Also, please tell us what graphics card you have installed on the laptop.
Thanks.

---

### Post by husnuyldz on 2010-08-11
if &#305; choose acpi=off ,&#305; can install ubuntu 10.04 but after the &#305;nstallation &#305; faced black screen and crash.keyboard and mouse not run...and &#305; never access to ubuntu..

---

### Post by husnuyldz on 2010-08-11
and graphic card ati radeon 5650

---

### Post by Rubi1200 on 2010-08-11
Ok, thanks I understand now.

Well, I want to see if I can help you get back into Ubuntu first and then we can try and figure out what is going on with the crashes and black screen.

Use the Ubuntu CD and try the following please:

Put the LiveCD in and boot the computer;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

xforcevesa

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz xforcevesa --**

Now hit Enter and you should be in.

Let us know what happens.

---

### Post by husnuyldz on 2010-08-11
I tried yoyur said twice...each of time black screen,crash and some adresses

Some adresses:
[0.886367]  [<ffffffff818496e3>] ? kernel_init+0*0/0*156 
[0.886435]  [<ffffffff810141e0>] ? child_rip+0*0/0*20

---

### Post by Rubi1200 on 2010-08-11
Maybe you have a hardware issue with 10.04?

Have you tried 9.10?

[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

See if an earlier version works from the LiveCD and if it does then you need to consider installing it instead of 10.04

Hopefully, someone else also has some ideas about this.

Good luck!

:)

---

### Post by husnuyldz on 2010-08-11
thanks for your efforts :))
I visited a lot of forum but &#305; didn' t find a solution..actually &#305; set up ubuntu 9.10 but I faced some network problems,and eventually I didn't find a solution..thus I didn't want to prefer to use 9.10.. Last time I will try :))I really want to use ubuntu but I suprised every time:S

---

### Post by Rubi1200 on 2010-08-11
If you decide to try 9.10 again and the install goes okay, post any problems with networking here and see if someone can help.

Most problems can be solved, but if there is a hardware issue it can be tricky sometimes.

---

### Post by husnuyldz on 2010-10-14
I solved this problem with " toshiba new bios update " ... I think all toshiba satellite L series notebooks installation problem  solved... this bios update was broadcasted 20 days ago but I discovered two days ago.. 

[http://uk.computers.toshiba-europe.com/innovation/download_bios.jsp?service=UK](http://uk.computers.toshiba-europe.com/innovation/download_bios.jsp?service=UK) 

in this website ,you find new bios update..

---

