---
title: "boot to terminal using USB startup disk"
date: 2012-04-18
forum: General Help
---

### Post by Docaltmed on 2012-04-18
How can I use the USB startup disk to boot into a terminal, bypassing the GUI stuff.

I'm having trouble with my 11.10 machine, and when I boot from the USB, and click the "try ubuntu" button, the display gets scrambled. So I can't get to the terminal that way.

If I hold down the "Shift" key when booting up from the USB, I get a "boot:" prompt, and I don't know what to do with that.

If I hold down the "Shift" key while booting up without the USB, I don't get a GRUB menu, which is why I want to boot to terminal from the USB, so I can try and fix GRUB. 

So here's what I want to do: Use the USB startup drive to boot directly into a terminal and then see if I can fix things from there.

Suggestions?

---

### Post by growingneeds on 2012-04-18
If Ubuntu has issues displaying its GUI at startup, you might have better luck with another distro. Since this is the Ubuntu Forums, I'll leave you to decide which distro is most popular at DistroWatch.com.

---

### Post by oldfred on 2012-04-18
If you are having video issues, you probably need nomodeset or other boot option setting.

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

---

### Post by Docaltmed on 2012-04-18
Thanks, oldfred, I appreciate the assistance. I'll give it a try tomorrow, and if it works, I'll mark off the thread. 

Keeping my fingers crossed...

---

### Post by Docaltmed on 2012-04-23
Ended up upgrading to 12.04. New issues, so I'll start a new thread.

---

