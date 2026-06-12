---
title: "What is BusyBox v1.13.3 on a black screen mean"
date: 2011-04-05
forum: General Help
---

### Post by videocheez on 2011-04-05
I just recently installed Ubuntu v10.04 via USB installation.  It ran for two weeks with no problems.  The only program I used daily was Nicotine for downloading music.  A couple of days ago, I kept having to power off my computer because it kept locking up.  Yesterday, it failed to boot and had a black screen with some writing that started off reading the following:
"BusyBox 1.13.3 etc.........
Enter Help for a list of commands"

If I knew what these commands meant, I could maybe save myself but I cannot figure out how to boot into the normal Ubuntu OS.  I photographed my black screen for reference and inserted it below.  Any help will be appreciated. I also tried to reinstall Ubuntu from the memory stick but so far the computer will not even re-install it.  I would like to know what has caused this problem and how I can fix it.  Thanks in advance. VC

[http://i225.photobucket.com/albums/dd286/videocheez/IMG_1033.jpg](http://i225.photobucket.com/albums/dd286/videocheez/IMG_1033.jpg)

---

### Post by cheapie on 2011-04-05
Well, you could try using the "Detect any OS" feature of the [Super GRUB2 Disk](http://www.lmgtfy.com/?q=super+GRUB2+disk&l=1) to boot Ubuntu, then run:

sudo grub-install /dev/sda

(assuming that your boot drive is /dev/sda), and then:

sudo update-grub

---

### Post by videocheez on 2011-04-05
> **cheapie said:**
> Well, you could try using the "Detect any OS" feature of the [Super GRUB2 Disk](http://www.lmgtfy.com/?q=super+GRUB2+disk&l=1) to boot Ubuntu, then run:

sudo grub-install /dev/sda

(assuming that your boot drive is /dev/sda), and then:

sudo update-grub

Thanks.  Can I put this superGRUB2 onto a USB stick?  My CD doesn't work too wel.

---

### Post by Hedgehog1 on 2011-04-05
Before you start making changes to the disk:

We need to get a look at what shape your partitions are in.

Please boot off the LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

### Post by videocheez on 2011-04-05
> **Hedgehog1 said:**
> 
Please boot off the LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

I can't boot off of the live USB.  That is my problem.

---

### Post by videocheez on 2011-04-10
Thanks for the help guys.  I decided to re-install.  I just reloaded Ubuntu's latest desk top version and it ran for about 4 days and my computer locked up again.  The only programs that I loaded were Nicotine for downloading music and Samba for communications with the my Windows home network.  I recently purchased a new hard drive for this computer so I think it is okay.  Perhaps it's a motherboard issue.  Now when I try to boot, I see the following message show in the screen shot. Please click on the link below and let me know if you have nay ideas how to deal with this without reloading ubuntu again.
[http://i225.photobucket.com/albums/dd286/videocheez/IMG_1051.jpg]("http://i225.photobucket.com/albums/dd286/videocheez/IMG_1051.jpg")

---

### Post by Dutch70 on 2011-04-10
If you can't boot from a live cd or usb, how are you installing Ubuntu?

---

### Post by videocheez on 2011-04-10
> **Dutch70 said:**
> If you can't boot from a live cd or usb, how are you installing Ubuntu?

I have a USB CD player.  So I guess it's USB indirectly.  I downloaded the alternate download desktop version 10.1.  It takes several times to be successfful re-installing.  I just keep trying untill it works.

---

### Post by Dutch70 on 2011-04-10
If you get or have it installed and it doesn't boot, I suggest you do what Hedge asked you to in post #4. It really doesn't matter if it's a cd or usb at this point. If you can boot to a live cd/usb, you can get your boot info script.

---

