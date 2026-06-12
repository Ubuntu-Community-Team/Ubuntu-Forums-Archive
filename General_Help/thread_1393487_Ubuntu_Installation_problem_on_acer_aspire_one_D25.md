---
title: "Ubuntu Installation problem on acer aspire one D250"
date: 2010-01-29
forum: General Help
---

### Post by vortexman on 2010-01-29
[FONT=Times New Roman][SIZE=3]Hi guys!
I have a acer aspire one D250 and I wanna totally remove the windows xp and install ubuntu or make it dual boot.I just made a USB ubuntu installation.but when I restart the laptop it starts the process but suddenly a black screen appears and the curser starts to think (ubuntu thinking curser animation).I even tried to install it 'in windows' but it didn't work.please help me.it happened same with Fedora. 
Another thing is I wanna get rid of this xp but it doesn't allow me,I wanna partition it (it has just one drive,that's all) but i can't!!i used all avalibale partition manager programs but they didn't work.I am confused now,I appreciate your help guys.


Best Regards,
Jav[/SIZE][/FONT]

---

### Post by cjhabs on 2010-01-29
I just recently used the Parted Magic Linux distro off live cd to repartition an XP drive - without losing any data - it worked like a charm. MAKE A BACKUP FIRST in case you are not as lucky as me.
It does take a while - I left it overnight and it broke a 230gb drive up into 100gb and 130gb partitions.

---

### Post by Bobby G on 2010-01-30
Hi Vortexman,

I have, in  the last week, installed Ubuntu on the very same netbook so maybe can help. You will need to use or borrow another computer with ubuntu to make the usb stick - or boot another one with a live CD.

Firstly, download the ubuntu netbook remix version  - that's what worked for me and has a pleasant interface. it's here

[http://www.ubuntu.com/GetUbuntu/download-netbook](http://www.ubuntu.com/GetUbuntu/download-netbook)

The first time I tried to boot off the USB I got just a flashing line. I fixed this by using USB startup disk creator item in Ubuntu, (as before) but this time pushed the format disk button. MAKE SURE you've backed up anything on your usb key first (!)

That did the trick for me.

Ignore all the other posts you may see about bits of hardware not working - everything does! Ethernet & microphone included despite what you may read.

Ethernet requred nothing - it just worked. for the microphone open the terminal application, type alsamixer, then press F5, to get all slider controls. Use right arrow to get to "CAPTUR" slider then press e to get the right slider all the way up and x to get the left slider all the way down.WEIRD, but that's all. No further drivers required or anything. Rather differnt from my Windows experience.
Enjoy

---

### Post by vortexman on 2010-02-01
Hi!
Thanks Bobby,I did it,but this time it goes through the installation procedure,but suddenly the screen went black and I had ubunto thinking cursor (I waited for an hour,nothing happened), what should i do in your opinion?

kind Regards

---

### Post by 00b00nt00 on 2010-02-01
Same problem. I can get the computer to boot occasionally by resetting the BIOS parameters and unplugging the computer, but as soon as you shut down in Ubuntu, the problem re-emerges on the next boot.

If you do a 'safe' boot, the computer displays the log and it will tell you where the computer halts. I forget, but I think it has something to do with the graphics card.

I fixed the problem by installing Windows 7. The computer now works like a charm, for a price.

---

### Post by vortexman on 2010-02-03
[FONT=Times New Roman][SIZE=3]Hi,
I found the problem.when you make the USB cd live with Unetbootin, It causes some errors in some laptops (in booting procedure). I tried it myself.but when you make the USB live CD with "USB startup disk creator item in Ubuntu" the laptop is able to boot without anyt hangings or errors.I don't know why.
thanks guys and especially Bobby.[/SIZE][/FONT]

---

### Post by 00b00nt00 on 2010-02-03
I wish it worked for me. Like I said, I can get it to boot after a number of attempts, but it will never bot up after a shut-down. I have to unplug the power and battery for a few seconds, and if I'm lucky it will boot first time. Funnily enough, once Ubuntu is running there are no problems!

I just can't face coaxing Ubuntu to boot every time; I'm sure I'll break the power button.

---

### Post by webless on 2010-02-06
> **00b00nt00 said:**
> I wish it worked for me. Like I said, I can get it to boot after a number of attempts, but it will never bot up after a shut-down. I have to unplug the power and battery for a few seconds, and if I'm lucky it will boot first time. Funnily enough, once Ubuntu is running there are no problems!

I just can't face coaxing Ubuntu to boot every time; I'm sure I'll break the power button.


I have this EXACT same problem and can't find a fix ANYWHERE!!!!

The only thing I have found that might work is to install from a USB CD drive. If anyone can find another answer please post it or a link to it!!!!!!!

---

### Post by dcordova on 2010-10-19
Well I had the same problem.... but i think i found the solution....
On your BIOS go to Main Menu, then change SATA MODE form IDE to AHCI.
That will fix your problems... I think!

---

