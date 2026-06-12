---
title: "About to format"
date: 2010-08-12
forum: General Help
---

### Post by ExSuSEusr on 2010-08-12
I have two HD's - one with Ubuntu and one with XP.  I'm about to format the XP with a clean copy.  However - the last time I did this it ate up the boot table and I could not access my Ubuntu partition.

Before I get started - how can I prevent this from happening?  I know Windows like to overwrite the boot table during install.  So, unplugging the Ubuntu drive isn't going to work (did that the last time I installed Windows).

Thanks...

---

### Post by dabl on 2010-08-12
Without knowing exactly what you mean by "format", you might check here: [http://ubuntuforums.org/showpost.php?p=9712185&postcount=2](http://ubuntuforums.org/showpost.php?p=9712185&postcount=2)

If you are installing Windows, then [[COLOR="SeaGreen"]**this**[/COLOR]](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) or [[COLOR="SeaGreen"]**this**[/COLOR]](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony) may be helpful.

---

### Post by lukeiamyourfather on 2010-08-12
The first disk with Windows has a boot loader on it. This allows the operating system to boot or choose another operating system. Ubuntu installs its own during the install process so you can choose between either Windows or Ubuntu. When you install Windows again it writes over that boot loader with the Microsoft one. To get it back run the GRUB updater from a Ubuntu live disc. Alternatively install Windows as you normally would on the first disk, then on the second disk put GRUB and Ubuntu. Then tell the BIOS to boot from the second disk. If Windows changes then GRUB and Ubuntu won't be affected. Or if you remove the second disk with Ubuntu then Windows will boot like it normally would.

---

### Post by earthpigg on 2010-08-12
if it where me, i'd pop open the case and unplug the ubuntu hard drive. that's where you have grub installed, right?

then, just make sure BIOS knows which hard drive to boot from.

---

### Post by gchand7 on 2010-08-12
If your using two drives you will have to choose which drive you need to boot from in the bios. I use to do it that way, now since 10.04 all I have to do is choose from the grub list when my ubuntu is loading. I have 5 hd's  7,xp pro,ubuntu,and 2 for storage.

---

### Post by ajgreeny on 2010-08-12
> **earthpigg said:**
> if it where me, i'd pop open the case and unplug the ubuntu hard drive. that's where you have grub installed, right?

then, just make sure BIOS knows which hard drive to boot from.
Actually, that would not be the default way, which is to put grub not on the ubuntu hard drive, but on the MBR of the first disk, usually windows if you have it, and only the grub configuration files go on the ubuntu partition/drive.

This means that if the OP does what you say, grub will still be wiped out and have to be restored to the first disk's MBR.  However, that is a very quick job, and should only take about 4 simple terminal commands.

Assuming you have 10.04 find out what your drives are using live CD:
    ```
sudo fdisk -l
```From that you need to find the device name of your Ubuntu drive, something like &#8220;/dev/sdb1&#8243;.
Still in the terminal, type:
    ```
sudo mkdir /media/sdb1
```    ```
sudo mount /dev/sdb1 /media/sdb1
```To reinstall grub:
    ```
sudo grub-install --root-directory=/media/sdb1 /dev/sda
```Push enter and you&#8217;re done! Of course you need to replace &#8220;/dev/sdb1&#8243; and &#8220;/dev/sda&#8221; with what you found in the fdisk output.

---

### Post by ExSuSEusr on 2010-08-12
Thanks guys/gals - I will give it a shot.

After backing everything up of course!

Ok, I was a little vague in my OP.  Basically (I'm sure most of you already gathered what I am trying to do) I built a PC a couple of years ago and put two physical hard drives in it.  One was meant for Windows and one was meant for Ubuntu.  The ONLY reason I wanted / needed Windows was for a game called Everquest II and MS Office 2007 and a few other things that I just didn't want to screw around with in Ubuntu - like iPhones, so on.

Anyway, I like to format my Windows drive once or twice a year - just something I do.  

The first time I did it (with both drives connected) upon reboot the Windows splash screen instantly appeared not giving me, obviously, the option to boot into Ubuntu.

The second time I did it - I thought by unplugging the Ubuntu drive would solve the problem it didn't.

Then I learned that the master boot record is overwritten by Windows IF you install Windows first.  If you install Windows FIRST than Ubuntu you don't have any problems.

So, this time - because I finally have Ubuntu set the way I want it and don't want to have to go through all that again - I wanted to make sure I learned how to correct the problem when it happens.

Seems there's a lot of good information here - so I will print it all up and get started.

Thanks again - I'll let you know how it goes!

---

