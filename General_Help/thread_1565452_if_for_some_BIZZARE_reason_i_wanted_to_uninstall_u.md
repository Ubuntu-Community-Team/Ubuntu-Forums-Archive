---
title: "if for some BIZZARE reason i wanted to uninstall ubuntu..."
date: 2010-08-31
forum: General Help
---

### Post by acornty on 2010-08-31
title. when i first made my computer a dual boot system (done by watching a youtube tut) i made sure that it was possible to "un-do" a dual boot system, which it is. basically you get a program, easybcd, and rewrite the mbr so it replaces grup bootloader with vista longhorn loader in my situation. my only concern is that, to select windows vista from grub, it says windows recovery environment loader. so I'm scared that vista longhorn loader wont work and i wont be able to get into my computer. can anybody help me here?

---

### Post by acornty on 2010-09-03
could anyone please help me this!!?!?

---

### Post by uRock on 2010-09-03
Have you tried booting Windows in the past three days?

If it still works, then using Lilo will fix the MBR as if you had never installed ubuntu nor grub. 

To use Lilo follow these directions coutesy of Mr. Presense1960

> **presence1960 said:**
> You can repair the MBR to a windows MBR from  ubuntu or the ubuntu live CD. Install lilo by running in terminal  ```
sudo apt-get install lilo
```Ignore the warning and next run in  terminal ```
sudo lilo -M /dev/sdX mbr
```where is sdX is your  disk/device, i.e. sda, sdb,sdc, etc
  This will make Ubuntu disappear from the boot record, then you just need to use the LiveCD or whatever partitioner you prefer to remove the Linux partition and either grow the Vota NTFS or create a second NTFS partition that can be used by Windows.

---

### Post by harrismh777 on 2010-09-04
> **acornty said:**
> my only concern is that, to select windows vista from grub, it says windows recovery environment loader. so I'm scared that vista longhorn loader wont work and i wont be able to get into my computer. can anybody help me here?

If I understand you correctly, grub  is currently installed and the grub menu has a vista option on the menu; however, when you select the vista option the recovery message is displayed... right?

Ok, many systems (all of HPs for instance) have a recovery partition which allows the user to reload the machine to factory defaults (including wiping out the mbr and reinstalling the default vista system). Sometimes the linux installation gets confused and marks the recovery partition as the windows partition. 

Did you make recovery disks after you got your windows system? You might be able to recover from there. Be careful about running the recovery partition code, it may reload your system to factory settings. 
You might also be able to recover by modifying the grub menu list settings yourself (depending how much you know about grub; and which grub you are using generation 1 or 2). 

Can you boot into windows or no?

---

### Post by acornty on 2010-09-04
> **harrismh777 said:**
> If I understand you correctly, grub  is currently installed and the grub menu has a vista option on the menu; however, when you select the vista option the recovery message is displayed... right?

Ok, many systems (all of HPs for instance) have a recovery partition which allows the user to reload the machine to factory defaults (including wiping out the mbr and reinstalling the default vista system). Sometimes the linux installation gets confused and marks the recovery partition as the windows partition. 

Did you make recovery disks after you got your windows system? You might be able to recover from there. Be careful about running the recovery partition code, it may reload your system to factory settings. 
You might also be able to recover by modifying the grub menu list settings yourself (depending how much you know about grub; and which grub you are using generation 1 or 2). 

Can you boot into windows or no?
well my grub says windows recovery environment loader. when i click on it it just boots regularly into windows. my laptop has a built in recovery hard drive.

---

### Post by harrismh777 on 2010-09-08
Did you provide a separate partition for /boot?

Grub loads in two phases. Phase one is located on the master boot record MBR. This loads just enough to be able to see the hard drive and load phase two. Phase two boots the rest of the system. If /boot is on the same partition as the rest of your linux system (all on one partition) then removing that partition and using it for something else will remove phase two of your boot loader and vista will not boot any longer (not until you rebuild the MBR so that your vista partition will boot-up.
If you placed /boot on a separate partition at install ( I have separate partitions for /var /tmp /home /boot /opt /usr / and /usr/local at a minimum, for security reasons and for other conveniences ) then you can remove your linux partion(s) and continue to boot vista from the grub menu. 

Now, as for your menu item having the wrong Title, you can edit your grub menu.lst file and change the menu title to anything you want... back when I actually booted into windoze (and I never do any more) I used to call it the Other Silly System. Call it what you want... but calling it the windoze recovery partition is irony at its best.   :-))

Talk to folks using windows, ask lots of questions, and become familiar with modifying the grub menu list. This takes some initiation, and not everyone is familiar with grub2 yet... like me.   So, be careful.



:D

---

