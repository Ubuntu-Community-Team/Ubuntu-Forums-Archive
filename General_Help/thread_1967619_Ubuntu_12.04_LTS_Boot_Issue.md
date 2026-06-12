---
title: "Ubuntu 12.04 LTS Boot Issue"
date: 2012-04-28
forum: General Help
---

### Post by goscotty on 2012-04-28
Hi,

I'm having trouble installing 12.04 LTS from both a Live CD and Live USB (I've tried both - not at the same time of course). What happens seems to be more along the graphics side of the problem. On my PC, I bootup with my USB option which has 12.04 on it, and after doing that I see a thin, grey rectangle (think Breakout) at the bottom left of the screen.

Using the arrow keys, I can toggle to another rectangle vertically, I'm assuming this is the actual Ubuntu live options but they are not rendering correctly. If I don't hit return, I see a single "_" prompt at the top left of the screen, and then my monitor switches to analog, and then back to digital and does nothing. 

To put the question of a faulty Live USB/CD to rest, the same media and its contents install perfectly fine on my Compaq Presario CQ56 with integrated graphics.

My desktop where I am having boot trouble uses an NVIDIA Geforce 550 Ti.

Any ideas?

Thanks

---

### Post by oldfred on 2012-04-28
Welcome to the forums.

I have an older nVidia card and since they integrated drivers into the kernel (10.04?), I have had to use nomodeset on liveCD or USB and on first boot.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Naggobot on 2012-04-28
Similar issue here with ATI Mobility radeon HD 5650. After boot I get only a grey rectangle to the bottom left side of the screen. On 15 in monitor the rectangle is about 1 cm high and 2 cm long. By fiddling with keys I got another question dialogue to open. This was larger and on the center of the screen but no text was visible on the buttons. 

I used live usb and I did not try CD. I used both ubuntu-12.04-desktop-amd64.iso and ubuntu-12.04-alternate-amd64.iso. It was impossible to continue with installation or anything since nothing can be deciphered from the dialogues.

---

### Post by Naggobot on 2012-04-28
Correction

USB created from ubuntu-12.04-desktop-amd64.iso boots fine if I keep my hands of from the keyboard for a few seconds. I get the small gray box on the bottom left but with a little wait the boot proceeds and everything works perfect after that.

---

### Post by goscotty on 2012-04-28
Thanks for the warm welcome and advice guys!

I mounted the 64-bit version of 12.04 LTS on my USB and this infact does boot correctly, and I was able to set the nomodeset option. 

With the 32-bit version however with whatever graphical issues there may be, I simply cannot see the accessibility/keyboard icon, and no amount of key pressing or waiting will help there.

---

### Post by oldfred on 2012-04-28
If it is a newer system 64bit is better anyway. Only if very old processor or less than about 3GB of RAM would 32bit be better. Ubuntu defaults to 32bit as 25% of users are still old 32 bit systems. They assume those with newer systems will know to use 64bit.

Why Ubuntu offically suggests 32bit (25% have 32bit systems)
[https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035088.html](https://lists.ubuntu.com/archives/ubuntu-devel/2012-April/035088.html)

Essentially says if you can use the 64bit kernel you should.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)

---

### Post by goscotty on 2012-04-28
That's a good read, oldfred, thanks! 

I decided to install the 64-bit edition for good and everything is working smoothly - just like I had hoped! 

I'll mark the thread as solved. Thanks everyone for helping me out, and others perhaps!

---

### Post by smile-on on 2012-05-10
Same issue with AST 2050. After boot I get only a gray rectangle to the bottom left side of the screen. I used live usb ubuntu-12.04-alternate-amd64.iso and had no idea of what this gray thing is. It is a shame to use fancy graphic mode in alternate installation iso. It should work with bare minimum to allow installation or at least make error visible. I was happy with 10.04 but so many issues with INSTALLATION of 12.04 put my thoughts to other distr. :confused:
Please, leave fancy staff for desktop keep alternate installation robust !

---

### Post by oldfred on 2012-05-10
@smile-on
It is my understanding that the alternative installer is a text mode only installer. Did you verify that ISO was correctly downloaded with md5sum?

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by smile-on on 2012-05-11
> **oldfred said:**
> @smile-on
It is my understanding that the alternative installer is a text mode only installer. Did you verify that ISO was correctly downloaded with md5sum?


@oldfred, thanks for noticing an issue.
Yes, installer is in text mode. Luckily it was not "improved"! Yes, md5 is OK. 
The problem with gray box is GRUB2 boot menu which is in graphic mode. Initial boot option screen is a thing that renders as A SINGLE GRAY BOX. It is that screen where you may press F6 or choose other options. The root cause is some fancy graphic mode or font that was chosen by grub and it is not simple to change it. Here is a hint [http://ask.fedoraproject.org/question/74/vga0x307-is-deprecated-but-cant-get-gfxmode-to](http://ask.fedoraproject.org/question/74/vga0x307-is-deprecated-but-cant-get-gfxmode-to) and do not forget to update md5 :)

@whom it may concern
Here is a practical workarond for outdated guys who have no 3D video on they servers. 
If all you need is a default installation then after you see a gray box just press enter two times (do not rush) and WAIT until installer switches screen in text mode. The rest of installation is same routine as usual.:)

---

