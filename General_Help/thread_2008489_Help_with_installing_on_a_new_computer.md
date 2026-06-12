---
title: "Help with installing on a new computer"
date: 2012-06-22
forum: General Help
---

### Post by andrewguif on 2012-06-22
Basically, I've been working on a new computer, and instead of buying Windows 7, I chose Ubuntu since it's free. I used UNetbootin to put it on a flash drive, but when I tried booting it up on the new computer, it didn't work. It goes from a post screen to the UNetbootin screen, and back. The UNetbootin screen has only one option which is "Default". Other than that, you can edit options, and when you do this, you get a line of text that reads "ubnkern initrd=/ubninit". I really just want to finish my build, what do I do?

---

### Post by wojox on 2012-06-22
Have you tried burning it more than once? 

What video card/chip is it running?

---

### Post by andrewguif on 2012-06-22
Indeed I have burned it more than once. Right now I'm downloading the file again, just in case something happened during that. 

Video card and chip? Assuming you mean GPU and CPU, I have a GTX 550 Ti, and an AMD Phenom II X4. If that's not what you meant, please try to be more specific since I barely know what I am doing.

---

### Post by Robing Goodfellow on 2012-06-22
Personally I've never had much luck with netbootin.  If you can, burn the ISO to a disk and boot from there.  Much easier. YMMV

regards, Richard

---

### Post by hansdown on 2012-06-22
Welcome to the forum,andrewguif.

Unetbootin can be a little funny with some files.

Need to ask;

Where did you download the ISO?

Something that may help...

[http://turbolinux.org/2011/06/unetbootin-howto/](http://turbolinux.org/2011/06/unetbootin-howto/)

---

### Post by oldfred on 2012-06-22
Also with nVidia you need nomodeset. And some very new computers may need other parameters. Is this a new UEFI system or older BIOS based system?

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
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by techvish81 on 2012-06-23
> **robing goodfellow said:**
> personally i've never had much luck with netbootin.  If you can, burn the iso to a disk and boot from there.  Much easier. Ymmv

regards, richard

+1

---

### Post by himely on 2012-06-23
i think it is good

---

