---
title: "Two Hard Drives."
date: 2011-08-07
forum: General Help
---

### Post by waltwin on 2011-08-07
I have two hard drives installed in my machine. On one drive I have ubuntu 10.10 installed and on the other I have Windows 7.0. I primarily use ubuntu but there are occasions when I need Windows such as when I download e books from the library to my nook.

I would like to show both drives at startup so I can select either one rather than go through the bios selection routine. 

Any assistance to my problem will be greatly appreciated and I thank you in advance.

waltwin

---

### Post by lmarmisa on 2011-08-07
> **waltwin said:**
> I have two hard drives installed in my machine. On one drive I have ubuntu 10.10 installed and on the other I have Windows 7.0. I primarily use ubuntu but there are occasions when I need Windows such as when I download e books from the library to my nook.

I would like to show both drives at startup so I can select either one rather than go through the bios selection routine. 

Any assistance to my problem will be greatly appreciated and I thank you in advance.

waltwin

I suppose that you have installed the GRUB loader in the MBR of the Ubuntu hard drive. I recommend to configure your BIOS for booting from the hard disk where Ubuntu is installed.

Then boot into Ubuntu, open a terminal and type this command:

```

sudo update-grub

```

Reboot your system. You have to see both options (Ubuntu and Windows) in the GRUB menu at startup.

---

### Post by waltwin on 2011-08-07
> **lmarmisa said:**
> I suppose that you have installed the GRUB loader in the MBR of the Ubuntu hard drive. I recommend to configure your BIOS for booting from the hard disk where Ubuntu is installed.

Then boot into Ubuntu, open a terminal and type this command:

```

sudo update-grub

```

Reboot your system. You have to see both options (Ubuntu and Windows) in the GRUB menu at startup.
Well that wasn't great. I think that I may have done something wrong. I configured my BIOS to boot from my Ubuntu drive. I rebooted. I opened a terminal and typed in sudo update-grub entered my password and now when my system starts I get a screen with many lines, none of which speak to Ubuntu and Windows.

Perhaps I do not understand what you mean when you say  "I suppose that you have installed the GRUB loader in the MBR of the Ubuntu hard drive".

Could you you clarify that for me please or better yet tell me how to do it. I really appreciate your response.

---

### Post by garvinrick4 on 2011-08-07
You can boot Ubuntu drive like you used to by choosing which drive you want to boot
the Window or the Ubuntu. When you boot the Ubuntu drive then you:
```
sudo update-grub
```
Will put Windows in the Ubuntu drives menuentrys to boot from.
#Windows drive will not do this because it does not have the same packages as Ubuntu's grub2.
So if you set Ubuntu drive to boot automatically first everytime as a setting in BIOS then
you will have either choice at everyboot.

---

### Post by lmarmisa on 2011-08-07
I believe that your result was not too bad.

You typed the command **sudo update-grub** and the result was similar to this:

```

luis@UB1010ENG:~$ sudo update-grub
[sudo] password for luis: 
Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-27-generic
Found initrd image: /boot/initrd.img-2.6.35-27-generic
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
[COLOR="SeaGreen"]Found memtest86+ image: /boot/memtest86+.bin[/COLOR]
[COLOR="RoyalBlue"]Found Windows 7 (loader) on /dev/sdb1[/COLOR]
done
luis@UB1010ENG:~$

```

In the previous command you can see several black lines belonging to different kernel versions of Ubuntu, one line (marked in green) for memtest and finally a last line (marked in blue) that belongs to Windows 7.

GRUB shows a menu with different lines at startup. The last line will be Windows 7. The two previous lines will be for memtest. The first lines will be the different kernels of Ubuntu available on your computer. The default option will be the newest kernel of Ubuntu.

---

### Post by oldfred on 2011-08-07
If you look close at lmarmisa's grub image you will see a little tiny arrow on the right side of the grub menu box which is to indicate that you have additional menu entries and can scroll down.

If you have that many entries it may be time to house clean out some old kernels.

---

### Post by waltwin on 2011-08-08
> **lmarmisa said:**
> I believe that your result was not too bad.

You typed the command **sudo update-grub** and the result was similar to this:

```

luis@UB1010ENG:~$ sudo update-grub
[sudo] password for luis: 
Generating grub.cfg ...
Found background image: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-27-generic
Found initrd image: /boot/initrd.img-2.6.35-27-generic
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
[COLOR="SeaGreen"]Found memtest86+ image: /boot/memtest86+.bin[/COLOR]
[COLOR="RoyalBlue"]Found Windows 7 (loader) on /dev/sdb1[/COLOR]
done
luis@UB1010ENG:~$

```

In the previous command you can see several black lines belonging to different kernel versions of Ubuntu, one line (marked in green) for memtest and finally a last line (marked in blue) that belongs to Windows 7.

GRUB shows a menu with different lines at startup. The last line will be Windows 7. The two previous lines will be for memtest. The first lines will be the different kernels of Ubuntu available on your computer. The default option will be the newest kernel of Ubuntu.
You are correct. I found the Windows line and it does load Windows. Can I eliminate all of the other lines to just to just show Ubuntu and Windows?

---

### Post by lmarmisa on 2011-08-08
You can eliminate the undesired old kernels using Synaptic. I recommend to maintain the two newest versions of the Ubuntu kernel. Be careful of what you remove!!!.

This link can help you:

[http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/](http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/)

Repeat the command **update-grub** after the kernel eliminations:

```

sudo update-grub

```

---

