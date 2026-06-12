---
title: "Unable to boot Live CD - Ubuntu 10.04"
date: 2010-07-21
forum: General Help
---

### Post by abhishekmodi on 2010-07-21
Hi all,
I download and burnt Ubuntu 10.04 and trying to run the Live CD. It shows up black screen after displaying the red progress dots and nothing happens after that. No CD drive activity is noticed. How can I resolve this problem? I have been troubleshooting it for days!

---

### Post by watupgroupie on 2010-07-21
Going to need some hardware info. How much memory do you have, etc?

---

### Post by abhishekmodi on 2010-07-21
I am doing it on Thinkpad R51 model. it has 2GB of RAM and its Intel celeron processor.Also, if I try to run LiveCD of Ubuntu 8.04, it runs successfully. I am having this problem only with Ubuntu 10.04.

---

### Post by rollin on 2010-07-21
Hi OP. Do you know what graphics card you have for the system?  I'm only mentioning it as I had issues booting 10.04 similar to this. As I found out thanks to the forum the graphic card driver changed from 9.10 (vesa) to nouveau.
Are you upgrading from 9.10?

---

### Post by watupgroupie on 2010-07-21
Also, just to be certain. Check the disk integrity. Can't count how many times I've wracked my head around something for a solution and I had a faulty burn.

---

### Post by abhishekmodi on 2010-07-21
I am not uprading. I am just running live CD version. The laptop has a normal VGA card and it does not have a specific graphics card since it is meant for office use. It is my office laptop hence I am running live CD and not installing Ubuntu in it. I burnt the CD on macbook pro. The disk utility did verify the errors after burning the CD. Also I read in some forums about pressing the F4 button when the boot up menu in show. There we can choose the Safe mode graphics, but I do not see that option here. Also, when I keep F4 pressed during the blank screen, I see the message "stdin: I/O error".

---

### Post by MrRichard on 2010-07-21
I had the same issue you had installing Ubuntu with my ATI 5830 graphics card.

I pressed F4 before you select to install Ubuntu in the boot menu and selected safe graphics mode.
But if you used a software similar to unetbootin to create the live CD, press Tab (or possibly another button) and enter "xforcevesa" without quotes when prompted to type.

(I'm new to Ubuntu, so I apologize if I'm misleading you.:rolleyes: )

Update: After you manage to install Ubuntu, go to System->Administration->Hardware Drivers and you may find that Ubuntu found a driver for your graphics card and other possible devices.

---

### Post by watupgroupie on 2010-07-21
F4 isn't working for him at any point of the LiveCD startup.

---

### Post by rollin on 2010-07-21
I managed to get the Ubuntu 10.04 cd to boot up using the F6 options; 
Selected noapic, nolapic, edd=on, nodmraid, nomodeset.

This enabled me to boot into the live environment but isn't going to help you install as the problem will be there after booting from the installation. I am fairly sure you're having an issue with the graphics card due to the new driver version used in 10.04, seeing as you can boot into 8.04... If you have your graphics card info it should make it easier to help. 

In a terminal (Applications>Accessories>Terminal) copy the following using paste or Shift+Insert:

```
lspci -v | grep VGA
```

---

### Post by abhishekmodi on 2010-07-21
I did this in Ubuntu 8.04:
lspci -v | grep VGA

and got the below result:
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

---

### Post by rollin on 2010-07-22
> **abhishekmodi said:**
> 

and got the below result:
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

Good work. I know how frustrating it can be having driver issues! Have a look at this page on the ubuntu wiki: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) I think they have a solution there. Good luck :)

---

