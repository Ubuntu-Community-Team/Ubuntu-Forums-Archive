---
title: "Problem loading Windows after ubuntu install"
date: 2010-03-17
forum: General Help
---

### Post by Jimbopix on 2010-03-17
Hey there, I just finished installing Ubuntu on this machine. The install has gone great and Ubuntu's working perfectly. The only issue is that I can't boot my windows partition anymore.

I'll give a quick rundown on my setup and situation. I've got 3 hard drives in the machine.

- Windows 7 Drive
- Ubuntu 9.1 Drive
- Storage Drive

Now, I just installed the Ubuntu drive today and tossed Ubuntu on it. When I boot from that drive, I just get a blank screen with a blinking console curser. When I boot off of the Windows 7 drive, Grub comes up but gives me no options and automatically boots Ubuntu. My first move was to put a windows 7 entry into the menu.lst file in Ubuntu, but there isn't one, and I'd assume that wouldn't work anyway since grub is booting off of the windows drive.

Thanks for any help you can offer!

---

### Post by john newbuntu on 2010-03-18
You mentioned that you could get into ubuntu by booting off of the win7 drive.  Once you are logged in, try the command "sudo update-grub".  Hopefully this will cleanup the menu.list file and add the other OS in the system to this file. The next boot should list all the OS.

Edit: I meant the menu.cfg file and not menu.lst. sorry.

---

### Post by Mark Phelps on 2010-03-18
There's no menu.lst file because when 9.10 is installed new, it doesn't create such a file due to the fact that it uses GRUB2, not legacy GRUB.

Running "sudo update-grub" after you boot into Ubuntu should generate the correct menu entries.  You should see something like "Windows 7 loader on sdan".

---

### Post by Jimbopix on 2010-03-19
Ok yeah i wasn't sure if i should update grub or not since it seems to be booting form the other hard drive anyway. Now that I have a menu.lst, it's got some options in it, Ubuntu 9.10, Ubuntu 9.1 recovery, Chainload into GRUB 2, and memtest.

However when i boot up I still just get "GRUB Loading" with no options before Ubuntu boots. Do you figure that's because the MBR on the windows drive has been messed with? I'm going to try to boot from this Ubuntu hard drive now and see if GRUB will work on this drive now. Then maybe I just have to straighten out the MBR on the windows drive, and point this GRUB to that drive.

Of course I'm not good with MBR's or GRUB, so I may be way out to lunch on this one, haha. It's worth a  shot anyway, thanks guys. I'm sure I'll be back with more issues in a few mins.

---

