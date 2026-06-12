---
title: "Windows 7 won't boot"
date: 2010-01-09
forum: General Help
---

### Post by CaKiwi on 2010-01-09
I have a Compaq Presario CQ60 with Nvidia GeForce 8200M graphics card. When I first installed Windows 7 followed by Karmic in dual boot I could boot into both OS. Now when I try to boot into Windows, it displays the Windows logo and then drops back to the grub menu. It may have started happening after Windows 7 installed updates. I tried reinstalling both Windows and Karmic again and it again worked initially but now Windows no longer boots. Does anyone have any suggestions about what may be causing this or how I can fix the problem without reinstalling?

Thanks in advance

---

### Post by CaKiwi on 2010-01-10
I reinstalled Windows 7 without doing any updates and then reinstalled Karmic. My first attempt to boot into windows 7 dropped back to grub after displaying the windows logo, but every subsequent attempt has been successful. Has anyone else had this problem?

---

### Post by Leppie on 2010-01-10
are you sure this issue is related to grub?

---

### Post by CaKiwi on 2010-01-10
It doesn't seem to be related to grub. Maybe it is something to do with the graphics card?. Maybe the windows update installs a new driver.

---

### Post by CaKiwi on 2010-01-12
Anyone have any thoughts on this?

---

### Post by Leppie on 2010-01-13
you could try using the 7 recovery disk: [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by WeAreTheSiNs on 2010-01-13
C'mon Windows 7?

You serious?

---

### Post by CaKiwi on 2010-01-15
I still don't have a solution for this problem

---

### Post by Leppie on 2010-01-15
so does it still go back to the grub menu if you're trying to boot into 7?

---

### Post by warfacegod on 2010-01-15
This very much strikes me as a Windows problem. One that would be better fixed on a Windows forum. When you do fix 7, come back here and we'll help you fix ubuntu because fixing 7 will almost certainly frag Linux.

---

### Post by CaKiwi on 2010-01-15
@Leppie Yes, when I try to boot Windows 7, it displays a logo, then the screen flashes and after a few seconds it goes back to the grub menu. I can boot into Ubuntu without problems.

---

### Post by CaKiwi on 2010-01-15
@warfacegod, Since Windows runs by itself without problems and only has problems when it is booted from grub, I doubt whether I would get any help from a Windows forum. I was hoping someone here has had the problem and found a solution

---

### Post by Haitoyou on 2010-01-15
I think I know what you are talking about.

I believe Microsoft implemented a new method of breaking Windows 7 if it encounters another operating system installed duing OS updating. Windows 7's updates scans for an MBR that is typically installed with Windows installations. When it detects Grub installed instead, it breaks itself, unwilling to boot until the MBR is reinstalled through some sort of recovery disc.

This to me smells like a near-future anti-trust lawsuit just waiting to happen for M$. I just hope a lawyer smart enough with this kind of stuff gets wind of this.

Preventing your OS from working if other OS's are installed would be the equivalent of your car dealership's mechanic refusing to work on your car if you happen to also own a rival company car.

---

### Post by CaKiwi on 2010-01-23
The problem seems to be that after doing a Windows update and rebooting using Grub, the boot fails when Windows tries to finalize the update. I'm wondering if the problem could be solved if I reinstalled the Windows boot loader to boot directly into Windows and added Grub to it in the same way that a Wubi installation does. Does anyone know how to do this? Any other suggestions?

---

### Post by warfacegod on 2010-01-23
Installing the Windows bootloader will probably fix Windows, however, The Windows bootloader doesn't know how to boot Linux. In essence, you'd be flipping your issue over.

---

### Post by CaKiwi on 2010-01-23
Isn't there a way to get the Windows bootloader to boot either Windows or Grub? That seems to be the way a Wubi install does it.

---

### Post by c0mput3r_n3rD on 2010-01-23
Not exactly sure about how to fix your problem, how ever a good rule of thumb is to defragment windows SEVERAL times before adding another partition.  You could possibly of had some important information that windoze miss-managed and was at the far end of the HDD that got written over.

---

### Post by sethhikari on 2010-01-23
> **Haitoyou said:**
> I think I know what you are talking about.

I believe Microsoft implemented a new method of breaking Windows 7 if it encounters another operating system installed duing OS updating. Windows 7's updates scans for an MBR that is typically installed with Windows installations. When it detects Grub installed instead, it breaks itself, unwilling to boot until the MBR is reinstalled through some sort of recovery disc.

This to me smells like a near-future anti-trust lawsuit just waiting to happen for M$. I just hope a lawyer smart enough with this kind of stuff gets wind of this.

Preventing your OS from working if other OS's are installed would be the equivalent of your car dealership's mechanic refusing to work on your car if you happen to also own a rival company car.

Ummm Nope... I boot both just fine, have been for a year now

---

### Post by Leppie on 2010-01-23
have a read through this page:  [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by sethhikari on 2010-01-23
> **CaKiwi said:**
> Isn't there a way to get the Windows bootloader to boot either Windows or Grub? That seems to be the way a Wubi install does it.

I think you can install Grub to your windows partitioner and it will boot from windows boot menu, don't remember how I did that long time ago.

---

### Post by Leppie on 2010-01-23
> **sethhikari said:**
> I think you can install Grub to your windows partitioner and it will boot from windows boot menu, don't remember how I did that long time ago.
see post #19

---

### Post by CaKiwi on 2010-01-31
I have got around this problem by doing a Wubi install. I played around trying to change the windows boot record to boot into Windows and Ubuntu using EasyBCD without success. So that now I am booting into Windows 7 straight from the boot record, Windows can successfully complete any updates. I'm surprised that no one else has reported the problem.

---

### Post by Mark Phelps on 2010-02-01
> **Haitoyou said:**
> I believe Microsoft implemented a new method of breaking Windows 7 if it encounters another operating system installed duing OS updating....
Load of BS!!!  Have a desktop PC with multiple OSs installed -- including several versions of MS Windows (XP, Vista, and Win7) and several different Linux distros -- and it boots just fine.

> This to me smells like a near-future anti-trust lawsuit just waiting to happen for M$. I just hope a lawyer smart enough with this kind of stuff gets wind of this.
Any lawyer "smart enough" will know what a complete waste of time this would be.

> Preventing your OS from working if other OS's are installed would be the equivalent of your car dealership's mechanic refusing to work on your car if you happen to also own a rival company car.

As already said, I have multiple OSs installed (including Win7) and they haven't prevented anything from working.

---

### Post by Mark Phelps on 2010-02-01
> **CaKiwi said:**
> I have got around this problem by doing a Wubi install. I played around trying to change the windows boot record to boot into Windows and Ubuntu using EasyBCD without success...

Did you check with the folks on the NeoSmart Technology forums about this EasyBCD problem? I use EasyBCD on one of my machines and found them to be quite helpful.

---

### Post by babybean on 2010-02-08
Hi, just thought I would let you know, you arnt the only one with this problem. I have a Compaq CQ60 as well. Boots to ubuntu no problems at all, but same problem when it comes to win 7... loads a bit then bam, the screen almost flashes as if there is a power cut and the computer reloads. Thankfully I dont get this all the time, just at the times I really need windows lol. Kind of annoying, but I will live.
I know it will load if the blue light comes on for the wifi, ater that happens it is safe :o

---

### Post by CaKiwi on 2011-04-02
I tried installing 10.10 as a dual boot on this system and I am still having problems getting windows 7 to boot. This time it will boot sometimes but mostly it just goes back to the grub menu. I can boot into Ubuntu without problems. Does anyone have any thoughts on this?

---

### Post by CaKiwi on 2011-04-04
This is still a problem for me. I tried installing EasyBCD and changing the Windows boot record but it hasn't helped. I can boot into Windows 7 about 1 time in 4. It doesn't seem to have anything to do with Windows update.

---

### Post by bcbc on 2011-04-05
> **CaKiwi said:**
> The problem seems to be that after doing a Windows update and rebooting using Grub, the boot fails when Windows tries to finalize the update. I'm wondering if the problem could be solved if I reinstalled the Windows boot loader to boot directly into Windows and added Grub to it in the same way that a Wubi installation does. Does anyone know how to do this? Any other suggestions?

easyBCD
EDIT: oops - never mind - didn't see there was another page :)

---

### Post by CaKiwi on 2011-04-05
After I used EasyBCD to modify the Windows boot record, my system boots into the Grub2 menu and, if I choose Windows, goes to the Windows boot record that I've modified with EasyBCD. From there booting into Windows fails more that half of the time. What I would really like to try is to boot directly into the Windows Boot record that I have modified and from there boot either Windows or Ubuntu. I think this is what a Wubi install does. Anyone know how to do this?

---

### Post by walt.smith1960 on 2011-04-05
I use a boot manager to do what you're doing. It creates an "extended MBR" so that each operating system thinks it's the only operating system on the hard disk. It manages various flavors of Windows fine. It can be persnickety about Linux, perhaps because GRUB is installed in the Linux partition not in the MBR of the hard drive. I'be found that if Linux sees more than one partition during partitioning, the install won't boot.  If only one partition is seen by the Linux installer regardless of how many partitions are actually present, the install will be  successful.  Once working, it seems to be quite reliable. 

[http://www.terabyteunlimited.com/bootit-next-generation.htm](http://www.terabyteunlimited.com/bootit-next-generation.htm)

---

### Post by bcbc on 2011-04-05
> **CaKiwi said:**
> After I used EasyBCD to modify the Windows boot record, my system boots into the Grub2 menu and, if I choose Windows, goes to the Windows boot record that I've modified with EasyBCD. From there booting into Windows fails more that half of the time. What I would really like to try is to boot directly into the Windows Boot record that I have modified and from there boot either Windows or Ubuntu. I think this is what a Wubi install does. Anyone know how to do this?
If you use EasyBCD you should boot directly to the Windows Boot Manager, not to the Grub2 menu. This likely means that Grub2 is still in your MBR - and there is no point in having an entry in the BCD to boot Ubuntu in that case.

Wubi uses grub4dos. I don't believe there is any benefit to using grub4dos in place of easyBCD.

---

### Post by CaKiwi on 2011-04-05
I think you're right, bcbc. So how do I get grub2 out of the MBR, replace it by the Windows BCD and where do I put the grub2 menu and how do I link to it?

---

### Post by bcbc on 2011-04-05
> **CaKiwi said:**
> I think you're right, bcbc. So how do I get grub2 out of the MBR, replace it by the Windows BCD and where do I put the grub2 menu and how do I link to it?
I've never used easyBCD... but here is the guide [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

It includes a step on reinstalling the windows bootloader (Step2). I could tell you how to do that separately but I don't think there's any advantage to running multiple sets of instructions. My advice is to follow the guide.
> **Step Three**
Go to the "Setup Bootloader" page in EasyBCD, and select "Install the  Windows Vista/7 Bootloader to the MBR" then press "Write MBR":

---

### Post by CaKiwi on 2011-04-05
Thanks bcbc! I followed the directions you suggested and now I am booting into Windows successfully, at least so far. I had already set up the BCD correctly and just needed to write it to the MBR

Thanks again :KS :KS :KS

---

