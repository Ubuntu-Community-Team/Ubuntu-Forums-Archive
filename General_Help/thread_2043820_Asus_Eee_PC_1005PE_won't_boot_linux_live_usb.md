---
title: "Asus Eee PC 1005PE won't boot linux live usb"
date: 2012-08-17
forum: General Help
---

### Post by Superpelican12 on 2012-08-17
I'm trying to install linux on someone else's Asus Eee PC 1005PE netbook.
Processor: Intel Atom N450 Pineview
1GB RAM
Intel GMA 3150 GPU (integrated into CPU)
 Win7 Starter Edition
250GB HDD

I've tried to let it boot a Linux Mint 13 live usb stick, a Xubuntu USB Live USB and a Kubuntu Live USB. All these usb setups boot fine on my own laptop (Asus K53SJ, see signature). I changed the first boot settings in the BIOS (*all*, I went trough the whole BIOS and checked all possible settings!). The computer then boots until the blue screen with "Start <the linux distro>" or "Try <the linux distro> without installing'-screen and I selected that option and pressed enter. After that the screen turns completely black and it stays that way forever...

I'm really desperate as I tried Asus's own Linux Live USB creator program (downloaded from the Asus 1005PE page on the Asus website), Unetbootin and the Ubuntu create startup disk utility...

---

### Post by PhantomTurtle on 2012-08-17
When you get the black screen, press the "DELETE" key a few times. This will switch from the Ubuntu splash screen to the text readout of the startup. If you press it too many times though it will switch back to the splash screen. Usually it only takes once or twice.

---

### Post by Superpelican12 on 2012-08-17
I pressed the delete key several times as you told me but nothing happened...

---

### Post by PhantomTurtle on 2012-08-17
Try this, turn on your computer with the USB plugged in. When you get to a purple screen with a keyboard logo press enter. Select you language and press Enter. Then press "F6" on your keyboard and select "nomodeset" from the menu that pops up. Then press enter on "Try Ubuntu without installing".

---

### Post by Erik1984 on 2012-08-17
Yes this sounds like a "nomodeset" problem. As I guess you are Dutch this link might be useful: [Geen of slecht beeld - Computertip]("http://sites.google.com/site/computertip/geenbeeld") (It's not my site but I used that link a few times as I need nomodeset with my Nvidia card to boot). It's the same procedure as PhantomTurtle suggest but documented step by step.

---

### Post by Superpelican12 on 2012-08-17
It's weird that this netbook has such graphics problem. As it has a Intel GPU (which I thought had great support). Also there seem to be different people that have installed 12.04 on this netbook and no one seems to have posted any problems.

---

### Post by Erik1984 on 2012-08-17
Yes that is weird, but have you tried nomodeset? Maybe you could try the Ubuntu alternate iso as a last resort if that doesn't work.

---

### Post by Superpelican12 on 2012-08-19
I used Unetbootin to create the USB drive and because of that I don't get a purple screen but instead the furthest I come is the Unetbootin screen. F6 doesn't pop up a menu it only "resets the timer" "..... in 10s" to 10s again, so I suspect the only thing F6 does is reload the Unetbootin screen. However the Unetbootin screen also says "Press Tab to edit options". I did just that and I typed "--nomodeset" after what already showed up while pressing Tab. Then I pressed enter and the screen went black forever again just like all the other times...

Are you sure this has something to do with the graphics? After the Unetbootin screen it looks like the screen turns off completely, it not just goes black I think. Also I recently installed Xubuntu on a Samsung N210 netbook which had exact the same processor & graphics. I had no problems at all.

---

### Post by Erik1984 on 2012-08-19
No I'm not sure about nomodeset it just helped me with the black screen (black as in no video signal to monitor). If Xubuntu works on that machine it's a different problem I guess, also the intel integrated graphics makes such a problem less likely. You could still try the alternate iso.

---

### Post by Superpelican12 on 2012-08-21
Finally I got the laptop booting and "surprise" it was indeed not the graphics (phew, you can  still rely on Intel hardware for Linux ;) ). It was the BIOS of the laptop which caused the problem. Which also explains why I didn't had this problem on a Samsung N210 (which has exact the same CPU/GPU/chipset). I was googling and found this: [http://ubuntuforums.org/showthread.php?t=1390856](http://ubuntuforums.org/showthread.php?t=1390856) which directed me to this:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) and this was the part that helped me out:
> 
Some BIOS's (eg., the Eee PC netbook') have trouble recognizing that the  USB is bootable. You may have to trick it into booting using the  following method: At boot, enter the BIOS by pressing F2. Then, right as  you exit the BIOS, hit the Esc key. For some systems, this will bring  up the boot menu. 

Well after "practicing" a few times I finally got to that "boot menu" and selected my USB drive then Xubuntu booted succesfully.

Now I'm struggling with the 4 primary partitions that already came with the laptop thanks to "BootBooster" and 2 Windows recovery partitions. I'm currently still deciding together with the owner whether I should delete Windows or not. Otherwise I'm going to  make an extended partition. For more information about how the 1005PE is partitioned  see: [http://askubuntu.com/questions/31119/install-ubuntu-on-asus-eee-pc-1005pe-dealing-with-special-partitions](http://askubuntu.com/questions/31119/install-ubuntu-on-asus-eee-pc-1005pe-dealing-with-special-partitions)

I hope this is useful for people who have problems with this netbook in the future.

---

### Post by PhantomTurtle on 2012-08-21
That's what sucks about OEM computers, they come with four partitions already making it harder for you to install Ubuntu. I had that on my Dell computer too. I kept the Windows and the Windows recovery partitions and deleted the other two since they were useless to me(I have a OEM CD so there is no need).

---

