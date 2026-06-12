---
title: "Installing ubuntu on my girlfriend's pc"
date: 2010-07-24
forum: General Help
---

### Post by Manuwash on 2010-07-24
Hey guys it's been a while

So my girlfriend came back from a holiday and it results that she somehow ( dont ask me how) wiped out vista from her hd pavillion laptop. There`s nothing there, the pc doesn't have a guarantee anymore so I thought, what the heck, I could install an ubuntu 10.4 there. It's a nice machine so it should run nicely. 

I made her try ubuntu on my laptop and she likes it so she gave me a green light to do it. So how should I go about it? boot the live cd and when I get to the partition part just tell the installer to overwrite the whole c drive and make the partition automatically? 

I'm kind of a noob so I wouldnt want to mess things up more than what they are.

thanks in advance.

---

### Post by geoffjay on 2010-07-24
If you don't need to save or recover anything from the drive then the way you described is correct, launch the installer, accept all of the defaults for partitioning and away you go.

---

### Post by lykwydchykyn on 2010-07-24
You might want to check and see if there's still a partition there to begin with, in case she has anything she wants saved.

Otherwise, I'd say you have the idea of it.

Plus, I'd say spend some time asking her what sort of things she does with her laptop to make sure she has all the software she requires installed and configured from the beginning.

---

### Post by Manuwash on 2010-07-24
cool man I´ll do that then.

Thanks!

---

### Post by Manuwash on 2010-07-24
she uses it mostly to browse, chat and multimedia, the standard lucid lynx should be more than enough for her I think. I hope all works well with the hardware ( not like my laptop's case)

---

### Post by SlidingHorn on 2010-07-24
That's it!  You don't have to worry about losing information that doesn't exist ;)  You may want to look into setting up a separate /home partition.  Here's a good, recent article that could be helpful for you: 

[http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html](http://www.ubuntugeek.com/how-to-create-a-separate-home-partition-in-ubuntu.html)

---

### Post by Manuwash on 2010-07-24
thanks a lot, I will do it with more confidence now.

---

### Post by Manuwash on 2010-07-31
Guys update on my adventure:

I am trying to install lucid lynx 32 bits on my gf's laptop but i am running on the same problem I had installing it on my own laptop. It has an ati radeon graphic card and I bump into a blank screen when I try to install from live cd. 

Now my ubuntu live cd is a bit old, I am thinking maybe they solved this issue already. Should I download the iso again from ubuntu's website?

---

### Post by oldfred on 2010-07-31
I had to do this but have nvidia. The nomodeset works for some other video cards.

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO on USB, or in USB's syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by Manuwash on 2010-07-31
i tried the nomodeset option but i still get only a blinking cursor. I will try deleting quiet splash and using xforcevesa.

You don't think they have solved this in the current iso download do you?

---

### Post by Manuwash on 2010-07-31
nothing works, it's really frustrating, I want to install the 10.4 not the 9.10, but I have never been able to pull that off on an ati radeon card machine, there must be a way.

---

### Post by Manuwash on 2010-07-31
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01817215&tmp_task=prodinfoCategory&lc=en&dlc=he&cc=il&lang=he&product=4000370](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01817215&tmp_task=prodinfoCategory&lc=en&dlc=he&cc=il&lang=he&product=4000370)

those are the laptop specs just in case.

---

