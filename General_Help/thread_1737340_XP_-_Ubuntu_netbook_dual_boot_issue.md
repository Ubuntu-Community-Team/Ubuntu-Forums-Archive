---
title: "XP - Ubuntu netbook dual boot issue"
date: 2011-04-23
forum: General Help
---

### Post by buruntu on 2011-04-23
Hi everyone,

I have done the most stupid thing by deleting the current kernel of ubuntu yesterday night (while trying to delete old kernels). Anyways, I have reinstalled Ubuntu but I could not see it to the bootlist (there were memtest of ubuntu and Windows XP at this stage). So wanted to give it a try with EasyBCD. I thought I have successfully added the list elements but pc just does not even show the old boot list element (memtest of ubuntu) and skip to XP. The main partition is E: Windows partition is F: and the ubuntu is in partition of "0,3" so all the stuff is in just one HDD. Here are the details:

There are a total of 2 entries listed in the bootloader.

Default: Ubuntu
Timeout: 10 seconds
EasyBCD Boot Device: E:\

Entry #1
Name: Ubuntu
BCD ID: {default}
Drive: E:\
Bootloader Path: \NST\AutoNeoGrub2.mbr

Entry #2
Name: Microsoft Windows XP
BCD ID: {a2974a06-6d7b-11e0-83e9-444553544200}
Drive: F:\
Bootloader Path: \NST\easyldr16

Could you please enlighten me what should I do? Tried to find the terminal from the Ubuntu netbook edition boot drive but I could not find it so I have downloaded the desktop edition so if you could help me trying to fix it via terminal with the help of boot cd/usb, I would appreciate that.

P.S: I have not formatted the partition of Ubuntu, just reinstalled it.

Cheers,

---

### Post by Paddy Landau on 2011-04-23
EasyBCD is more for Windows installations.

You want to use grub. I believe this will work:

[LIST=1]
[*]Boot into your Live CD.
[*]Go to a terminal.
[*]Enter the command [FONT=Courier New]sudo update-grub[/FONT]
[/LIST]

---

### Post by varunendra on 2011-04-24
> **Paddy Landau said:**
> EasyBCD is more for Windows installations.

You want to use grub. +1, but,
> **Paddy Landau said:**
> I believe this will work:

[LIST=1]
[*]Boot into your Live CD.
[*]Go to a terminal.
[*]Enter the command [FONT=Courier New]sudo update-grub[/FONT]
[/LIST]

I'm afraid this is not going to be as easy.

Please correct me if I am wrong, but I think this command is not meant to be run from Live CD, (it won't work) it has to be run while you are "in" the OS (ubuntu in this case) that is installed on a writable disk (HDD or Flash drive) that has an MBR on which grub is installed, and holds the grub configuration files.

In this case, grub is not even installed on the MBR, it has been overwritten by Windows 7 MBR code. So I believe the OP has to follow this guide to restore grub on MBR:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

@buruntu,
Try any of the 3 methods in the above guide that suits you most.

Once grub is restored correctly, then you may boot into installed ubuntu on your hard disk and perform 'update-grub' to include other boot options (win7, older kernels if exist any) into the grub menu.

---

### Post by Paddy Landau on 2011-04-24
> **varunendra said:**
> I'm afraid this is not going to be as easy.
Oops, I stand corrected. Sorry.

---

### Post by Don1500 on 2011-04-24
> **varunendra said:**
> +1, but,

I'm afraid this is not going to be as easy.

Please correct me if I am wrong, but I think this command is not meant to be run from Live CD, (it won't work) it has to be run while you are "in" the OS (ubuntu in this case) that is installed on a writable disk (HDD or Flash drive) that has an MBR on which grub is installed, and holds the grub configuration files.

In this case, grub is not even installed on the MBR, it has been overwritten by Windows 7 MBR code. So I believe the OP has to follow this guide to restore grub on MBR:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

@buruntu,
Try any of the 3 methods in the above guide that suits you most.

Once grub is restored correctly, then you may boot into installed ubuntu on your hard disk and perform 'update-grub' to include other boot options (win7, older kernels if exist any) into the grub menu.

It's always good to have a burned copy of [Rescatux]("http://www.bootproblems.com/2011/04/18/rescatux-0-26-released/") on hand just for this occasion. (Been there, Done that, got the CD,)

---

### Post by buruntu on 2011-04-26
I just want to make a correction. As an idiot, I did not realize that this EasyBCD thingy is only use for Vista/7. So currently I have XP and Ubuntu netbook remix installed on the HDD and not able to reach to Ubuntu by any means.

Please let me know If I need to do sth else.

Thanks,

---

### Post by Dutch70 on 2011-04-26
Hi and welcome to UF

Lets have a look at your boot info script. Someone should be able to help if I can't, but we will need to see this.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] [ /CODE] tags. 
Do not skip this step or you will lose the formatting & I doubt if anyone will even look at it.

---

### Post by buruntu on 2011-04-26
Will try to boot with livecd now, thanks for the hand mates!

---

### Post by buruntu on 2011-04-26
Thanks everyone so much for helping me out!

@[B]varunendra the povided method worked out, thanks so much!
[/B]

---

