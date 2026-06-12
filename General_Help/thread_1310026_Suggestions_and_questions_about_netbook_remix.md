---
title: "Suggestions and questions about netbook remix"
date: 2009-11-01
forum: General Help
---

### Post by whatsanike on 2009-11-01
I was able to get the SD card which In plugged in to a USB card reader to boot the ACER Aspire One netbook, by downloading the utility file at [https://help.ubuntu.com/community/Installation/FromImgFiles#Windows](https://help.ubuntu.com/community/Installation/FromImgFiles#Windows) to make the the downloaded .iso bootable. 

The netbook booted OK after I figured out the bios boot order. Now Ubuntu just ran from the "stick" and doesn't seem to be on the HD. I did defrag the HD, which wasn't too easy as Win XP reported MDIB.TMP and another hidden file not getting defragged. So I booted XP in Safe Mode, got a Command Line, and used the Dos "Attrib" command to get rid of the impediments to deletion. After that I had a pretty clean picture of the defragmentation. So I should be ready to repartition the drive for a dual boot.

Not sure of the procedure now to get UBUNTU to run from the HD. 

A couple of suggestions:
The mouse default speed or cursor pad was set to max, whereas the default for XP takes t least 2 strokes on the pad to move the cursor all the way across the screen. UNR should come up with a slower default speed. No clue how to change it. The default in the OS would better be slower to avoid aggravation.

The wireless networks are not recognized by default, like in XP on my netbook. Maybe that would  not be practical to put in the distrib, but if it is, it would make it more attractive to use "out of the box" without hassle.

Anyway now I need to get it to run on the HD, and repartition for a dual boot with XP. I have about 2 gb free space and 5.5 gb used for XP and associated programs. 5.5+2=7.5 gb on the Acer Aspire One.

---

### Post by teh603 on 2009-11-02
Odd. I haven't used the .img installer ever. I always use the .iso.

I have a mac at home, so its as simple as telling the disc utility to burn the .iso to a blank CD. Then I just hook up an external CD drive to the AAO and run the installer like usual.

In Ubuntu, you can take the .iso and use System -> Administration -> USB Startup Disc Creator to "burn" the .iso to your USB stick. If you have an external CD burner, you should be able to use Brasero to burn it to a CD and then install off what you just burned.

I don't know how to do this in windows. I know most of the "default" burning apps packaged with CD or DVD burners won't burn an image file, which is designed to force people to buy the commercial version. I also don't know of any open source burning software, but that's not to say it isn't out there.

Anyway, once you've been able to boot into Ubuntu, you just run the installer and go from there. You'll have to talk to someone else if you want to choose which OS to boot, however. I just reformatted my whole drive as ext4 and obliterated windows.

Edit: On the touchpad issue- we'll have to agree to disagree on this one. I like a hyperactive trackpad. Then again, I've also got a hyperactive trackball on the mac, and no mouse.

Edit 2: On the wifi issue, try hitting the kill switch, and then restart. Wifi worked out of the box on my AAO. That having been said, there's a standing driver issue where the wifi freaks out and you have to power cycle the computer to get it to come back up. If you're just restarting it won't work.

---

### Post by whatsanike on 2009-11-02
I did read the web page about the wi-fi issues. Do you have to hit the kill switch every time you run the OS to get the wi-fi to come up, or just the first time you run UBUNTU?

You say run the install. I will try to use GRUB to dual-boot after I partition the HD for both OS's. But where is the install located in the GUI, which came up on my screen?

---

### Post by WVillet on 2009-11-04
Hi I was wondering if you could maybe help me.Im still new at these forums so please bear with me.
Ive got a asus eee 2gb surf netbook and was running easy peasy's version of the netbook remix.Due to space requirments it was installed on a 8Gb SD card.When attemting installation with the new netbook remix 9.10 the installation freezes up when you get to the menu where you choose where you want to install(Thinks its gparted). I really want to install this version the live boot is so fluent and fast and the looks is amazing

I have seen posts on google where people attempted installing on their sd card with success.

Any advice would help
Thanx

---

