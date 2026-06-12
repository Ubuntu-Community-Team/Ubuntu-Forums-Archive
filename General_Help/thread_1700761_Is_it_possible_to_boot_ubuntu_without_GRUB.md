---
title: "Is it possible to boot ubuntu without GRUB?"
date: 2011-03-05
forum: General Help
---

### Post by gooner11 on 2011-03-05
I have recently installed ubuntu 10.10 on a diffrent hard drive than my windows 7 installation. It worked perfectly but I didnt want GRUB as my boot loader. So I restored the original MBR.

 What I want is to go in to the boot selection of my motherboard and select the hardrive that I have insttalled ubuntu on and boot it that way. But it didnt work. It just goes in a black screen with a blinking cursor. Is there any way to fix it?

---

### Post by Mark Phelps on 2011-03-05
The Ubuntu install needs SOME boot loader in order to work.  Typically, folks just use GRUB.  But, there's also LILO.

And ... GRUB4DOS -- which is installed using the NeoSmart Technology EasyBCD app -- which you install in Windows.

If you want to use GRUB, my recommendation is to disconnect your Win7 drive, boot from the Ubuntu CD, and install GRUB from that.

For details, see Section 12 in the following:

[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

If you want to use EasyBCD instead, go to the NeoSmart Technology website as they have forums to assist you with installing and configuring it.

---

### Post by Crazedpsyc on 2011-03-05
If it is a one-time rescue, you can use a cd-based bootloader like PLOP
plop.at

---

### Post by gooner11 on 2011-03-05
So it seems that I cant just go to the boot selection of my bios and pick the the hard drive that ubuntu is installed on.

---

### Post by YesWeCan on 2011-03-05
Of course you can.
Your aversion to Grub is because...?

Let me assume it is because you don't want your Windows boot messed up. Quite right. I guess you installed Ubuntu on the second drive and it went and stuck its bootloader on the Windows drive. Why it does this by default is beyond me but it sure causes a lot of people a lot of grief.

You are in the lucky position of being able to keep your Windows disk completely untouched. That's what I would want. In fact, when I install Ubuntu on a second drive I actually disconnect the Windows drive during the procedure to guarantee my Windows drive is not messed with.

The thing is you need to be able to boot Ubuntu. Ubuntu doesn't have a bootloader of its own. I see no reason not to use Grub2. You just don't want it anywhere near your Windows drive. But you do need it somewhere on your Ubuntu drive. It is best to install it to the MBR of the Ubuntu drive.

Once you have installed it there you can boot the Ubuntu drive directly from the bios as you want. Just as you can boot Windows directly using the bios.

You can also add the Grub2 bootlaoder to the Windows boot menu by installing EasyBCD in Windows (free download). This is arguably more convenient than selecting the drive in bios each time. Your Ubuntu drive is not altered in any way.

You can also do the same thing using Grub2. When booted in Ubuntu you simply use the command 'sudo update-grub' and Grub2 scans your disks and adds OSes it finds to the Grub boot menu, in this case Windows. Your Windows drive is not altered in any way.

---

### Post by gooner11 on 2011-03-05
Thanks a lot @YesWeCan that really helped me out. I really appreciate it.

---

