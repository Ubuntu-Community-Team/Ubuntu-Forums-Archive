---
title: "Black screen on booting! Help ;s"
date: 2010-11-16
forum: General Help
---

### Post by VixinG on 2010-11-16
Hello,
I use xubuntu 10.10, and I am new in Linux, so I wrote in terminal "sudo chmod 0700 /home" and "/usr"... :-s
That's because I was installing wine137 and I needed permission (I AM NEWBIE) and I used "make install" instead of "sudo make install" :( so I wrote "chmod 0777" to all computer files, then I thought it's dangerous, so I changed to 0700... I don't know why, but after rebooting everything is fine, but when loading OS, I get Black Screen and nothing happens... Everything what can I do is insert this Desktop CD with xubuntu 10.10 and login to OS without installing it... Can I repair disk from here? Help please :d I have Gigolo, so...

/edit:
I found on other linux forum:
How to enter to recovery mode:

1). The easiest one is to choose: 

                **QUOTE**                  Ubuntu, kernel 2.6.XX-XX-XXX (recovery mode)          
from the boot menu.
If the boot menu is hidden, simply press the Esc key to make it show up.

But I don't have any boot menu, and there's no chance to press esc because I don't have too much time, and I don't know where :3

---

### Post by yuki-nagato on 2010-11-17
> **VixinG said:**
> Hello,
I use xubuntu 10.10, and I am new in Linux, so I wrote in terminal "sudo chmod 0700 /home" and "/usr"... :-s
That's because I was installing wine137 and I needed permission (I AM NEWBIE) and I used "make install" instead of "sudo make install" :( so I wrote "chmod 0777" to all computer files, then I thought it's dangerous, so I changed to 0700... I don't know why, but after rebooting everything is fine, but when loading OS, I get Black Screen and nothing happens... Everything what can I do is insert this Desktop CD with xubuntu 10.10 and login to OS without installing it... Can I repair disk from here? Help please :d I have Gigolo, so...

/edit:
I found on other linux forum:
How to enter to recovery mode:

1). The easiest one is to choose: 

                **QUOTE**                  Ubuntu, kernel 2.6.XX-XX-XXX (recovery mode)          
from the boot menu.
If the boot menu is hidden, simply press the Esc key to make it show up.

But I don't have any boot menu, and there's no chance to press esc because I don't have too much time, and I don't know where :3

Immediately after the bios screen disappears, hit the esc key.  It will bring up a list of your kernels and a recovery option beneath each.

Be very careful with sudo especially when modifying permissions on some important directory like /home.

The first number is the permission for the creator of the file
The second number is for those within the file creator's group
The third is for everything else
There is no fourth number.

4 is read
2 is write
1 is execute
0 is nothing
6 = 4+2 (read + write)
7 = 4+2+1 (read + write + execute)

here's a handy guide:
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

---

