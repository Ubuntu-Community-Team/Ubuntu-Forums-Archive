---
title: "unable to access WIndows7 throught Grub"
date: 2011-03-31
forum: General Help
---

### Post by blalalabla on 2011-03-31
i've installed ubuntu 10.10 yesterday and i went to check something in my MS OS, im choosing "windows 7 loader XYZ"(XYZ reffers to something sda/....)
in it comes back to the grub menu,
any help please?
im searching for hours for a solution and i can't find.

thanks,
amir

---

### Post by Kirboosy on 2011-03-31
Boot into ubuntu and run in a terminal ```
sudo update-grub
```If that doesn't fix it then your Windows 7 is probably corrupt...That means you will have to use a Windows 7 disk to repair it and that might take out GRUB...could get messy. :(


~Caboose

---

### Post by blalalabla on 2011-03-31
here's the output :
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic-pae
Found initrd image: /boot/initrd.img-2.6.35-28-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

nothing changed, still can't access windows.

---

### Post by Kirboosy on 2011-03-31
[Guide for fixing Windows MBR]("http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html")

[Recovering Ubuntu after Installing Windows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Rubi1200 on 2011-03-31
Hi,

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Mark Phelps on 2011-03-31
> **blalalabla said:**
> i've installed ubuntu 10.10 yesterday and...

Did you allow the Ubuntu installer to shrink your Win7 OS to make room for Ubuntu?  

IF you did, you may now have a corrupted Wint OS partition -- one that will not boot anymore.

The link you were gave for fixing that presumes that you have a Win7 disk -- which, if your PC came preinstalled with Win7, you probably do not.

BEFORE you did the dual boot, you should have gone into Win7, launched the Backup function, and used to that to create a burn a Win7 Repair CD -- which you could use for that link.

Since you probably did not do that, go to the appropriate link below, download and burn the Win7 Repair CD:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

You can the use that CD (in concert with the info in the link) to repair your Win7 boot.  Just understand that it's likely to take three passes to get it working.  So, don't get discouraged if it is not fixed in one pass.

---

### Post by blalalabla on 2011-03-31
before i do the steps that you told me,
i just want to mention that before i saw youre comments i reinstalled ubuntu 10.10, i had no extra information on it so i had no fear to erase all the partition .

but now, 
when i try to access windows it stucks with blinking " _ " 
oh weird,should i do youre steps in this problem too?

---

### Post by Rubi1200 on 2011-03-31
I think you should follow the advice I gave in post #5

First post the results so we can see what is really going on instead of playing guessing games.

Thanks.

---

### Post by blalalabla on 2011-03-31
im sorry man i tried the other way by using the Cd tool and checked for problems and used the command prompt and when i boot now it only blinks the dash!im using my phone to comment :( anyhelp please?

---

### Post by blalalabla on 2011-04-01
anybody?

---

### Post by Quackers on 2011-04-01
It is usually better to try to fix what has gone wrong, rather than compounding the issue by re-installing. It is possible that the second installation wiped out Windows.
Rubi1200 has given details of the first step to be taken (in post #5). He also asked again in post #8. 
If you ask for advice it is common courtesy to follow that advice, or at the very least question it.

---

### Post by Kirboosy on 2011-04-01
Did it give any errors at any point along the way?

---

### Post by Mark Phelps on 2011-04-02
> **blalalabla said:**
> im sorry man i tried the other way by using the Cd tool and checked for problems and used the command prompt and when i boot now it only blinks the dash!im using my phone to comment :( anyhelp please?

Did you create and burn the Win7 Repair CD?

Did you then boot from it and run Startup Repair three times?

It very often takes all three passes to completely repair a Win7 boot problem.

---

