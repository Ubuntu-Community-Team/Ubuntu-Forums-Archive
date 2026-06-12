---
title: "how to start ubuntu after installation"
date: 2011-11-18
forum: General Help
---

### Post by sid99999 on 2011-11-18
i have successfully installed ubuntu 11.10 desktop using a pen drive as instructed here [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
, but when i restarted my computer after installation, there was no option for booting ubuntu and as usual windows started booting..


when i inserted my pen drive and restarted computer again , the ubuntu started by pen drive, and then i again tryed to install ubuntu and got the message that ubuntu is alreay installed.

what should i do?

---

### Post by hwttdz on 2011-11-18
Did you go through a grub installation?  Grub is the boot loader which will allow you to choose which operating system to start.

---

### Post by BillyBoa on 2011-11-18
> **sid99999 said:**
>  got the message that ubuntu is alreay installed.

Are you sure? I never saw a message like that.

---

### Post by mike555 on 2011-11-18
If you installed ubuntu and grub to the same usb drive then that is the way it should work..... if the usb is plugged in it should start to ubuntu (if your computer bios is set to boot usb first) , but if not plugged in of course it can't startup, and your regular system should start ......... unless I don't understand your problem .

(edit) after rereading your post I guess you installed ubuntu to your hard drive useing a live usb . but I'm thinking somehow your grub didn't get installed to your MBR .... use the live usb and reinstall grub, I think the terminal command is "  sudo install-grub   "make sure it points to your MBR .

 unless you used a WUBI install , then it's a whole different thing .

---

### Post by Rubi1200 on 2011-11-19
> **sid99999 said:**
> i have successfully installed ubuntu 11.10 desktop using a pen drive as instructed here [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
, but when i restarted my computer after installation, there was no option for booting ubuntu and as usual windows started booting..


when i inserted my pen drive and restarted computer again , the ubuntu started by pen drive, and then i again tryed to install ubuntu and got the message that ubuntu is alreay installed.

what should i do?
Hi and welcome to the forums :)

I am also not quite sure what is going on.

The easiest way to diagnose this would be to post the results of the boot info script.

There is a link at the bottom of my post with instructions.

---

### Post by sid99999 on 2011-11-19
thanx my problem is solved, thanx for the replies :)

i reinstalled it one more time than it worked ....

---

### Post by Rubi1200 on 2011-11-19
Excellent! Glad you got things sorted out in the end :)

Please mark this Solved using the Thread Tools near the top of the page.

---

