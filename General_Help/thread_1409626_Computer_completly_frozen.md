---
title: "Computer completly frozen"
date: 2010-02-17
forum: General Help
---

### Post by veedub6 on 2010-02-17
I really need some help please,
 
I am a newbie to Ubuntu. Just intalled Ubuntu 9.10 and installed it on my Sony Vaio laptop, did the partition stuff to separate Windows so I could have a dual boot option.
 
Here's the prob:
Everything seemed to work well until I made the recommended updates by Ubuntu. Then restarted my computer in a normal way, and it didn't load in the graphic mode. Stopped in the console the last line I could see was:
 
init: networking main process (504) terminated with status 1
 
Then started to look into the forums for an answer to my problem but just made it worse. My screen is now completly frozen (I can't type anything, and can't even reboot it holding the power button!). 
 
Here's what is on my screen now:
 
[ 10.674329] [<c03f7700>] panic+0x43/0xe7
[ 10.734028] [<c0328ff0>] mount_block_root+0x24f/0x272
[ 10.798916] [<c07b8978>] ? sys_mknod+0x27/0x30
[ 10.853419] [<c010112c>] mount_root+0x59/0x5f
[ 10.913196] [<c07b8964>] prepare_namespace 0x14e/0x100
[ 10.968683] [<c078e338>] ? sys_acess+0x20/0x30
[ 11.026309] [<c078e3bf>] kernel_init+0x77/0xbe
[ 11.080813] [<c078e348>] ? kernel_init+0x0/0xbe
[ 11.136349] [<c0104007>] kernel_thread_helper+0x7/0x10
 
Is there something I can do or should I just throw my computer away?
 
Thanks

---

### Post by Satoru-san on 2010-02-17
NO! dont throw it away D:!!!!!!! That wont fix it D:

Basically there looks to be something wrong with the kernel upgrade. You need to boot the old kernel.


Right after you turn on your computer hold down the shift key untill you get a boot menu called grub, you should have some options such as ubuntu and mem test.

choose the version of ubuntu that is the oldest (lowest number) but not the recovery mode.

The computer should boot. If it doesnt let us know, if it does I can tell you how to make it continue working.

:D Welcome to the forums! Enjoy it here! :D
**DONT BLINDLY RUN COMMANDS THAT PEOPLE ON THE FORUMS TELL YOU**
[i]some times people will post malicious command that will destroy your 
install[/i]
If you have any questions about what the commands do, ask someone!

---

### Post by veedub6 on 2010-02-17
I didn't do it.... LOL!
 
Thanks for the heads up!

---

### Post by Satoru-san on 2010-02-17
> **veedub6 said:**
> I didn't do it.... LOL!
 
Thanks for the heads up!

You seriously need to **hold** the shift key. 

So you are saying that grub menu didn't come up when you held the shift key from the moment you turned your comptuer on to the time it "froze"?

It is not possible for that unless your keyboard isnt plugged in :P is the little numberlock light come on or can you get the caps light to come on?

---

### Post by veedub6 on 2010-02-17
No i'm saying I stupidly entered commands that I found on this Forum.

Now it's fine, well better than before. I had to remove the battery though!
 
After I start Linux oldest version, here's what i get

fsck from util-linus-ng 2.16
/dev/sda2: clean BLABLABLA files BLABLABLA blocks
fsck from util-linux-ng 2.16
init: udevtrigger main process (476) terminated with status 1
init: udevtrigger post-stop process (476) terminated with status 1
init: udevmonitor main process (473) killed by term signal
/dev/sda4: recovering journal                           i think this is my "swap" partition
/dev/sda4: clean BLABLA BLA files,  BLABLA BLA blocks
init: networking main process (500) terminated with status 1
 
How the hell can I fix this problem?

---

