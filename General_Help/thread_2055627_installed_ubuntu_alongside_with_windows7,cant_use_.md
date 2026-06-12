---
title: "installed ubuntu alongside with windows7,cant use windows"
date: 2012-09-09
forum: General Help
---

### Post by philip9910 on 2012-09-09
[FONT=Times New Roman][SIZE=4]So i just recently installed Ubuntu alongside with my windows 7 and when i restarted my computer it doesn't give me a menu asking me whether i want to use Ubuntu or windows 7 it just goes to Ubuntu, please help me because i need to use a lot of programs that i can only use on windows. [/SIZE][/FONT]

---

### Post by critin on 2012-09-09
In ubuntu open a terminal or use Ctrl+ Alt + t  to get to a terminal-- type

sudo update-grub

it will ask for your password.  enter the password, but you won't see it.  Hit enter and let it run.  When it's finished, exit the term.    Restart.

---

### Post by lmm5247 on 2012-09-09
> **critin said:**
> In ubuntu open a terminal or use Ctrl+ Alt + t  to get to a terminal-- type

sudo update-grub

it will ask for your password.  enter the password, but you won't see it.  Hit enter and let it run.  When it's finished, exit the term.    Restart.

When you update grub, you should see something like below (but with an option for windows)
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

---

### Post by oldfred on 2012-09-10
It may be a Windows issue which this will not fix, but run the BootInfo report and post link it creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by philip9910 on 2012-09-11
i just did that but nothing happened i restarted it and it still went back to Ubuntu. i don't want to get rid of Ubuntu i just want to run it along with windows as i chose during the installation of Ubuntu. now is there anyway i can get a boot menu asking me whether or not i want to go on Ubuntu or windows 7 and the file report is [http://paste.ubuntu.com/1196825/](http://paste.ubuntu.com/1196825/)

---

### Post by oldfred on 2012-09-11
Grub menu has 3 Windows entries, so grub menu should show on reboot. How are you  shutting down? If not  a normal shutdown grub may have issues.

Both the entries in sda2 & sda3 should boot Windows. The menu item for sda1 is the recovery environment.

The update grub had this per BootInfo, so it found the Windows and added them to the menu:

> update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-30-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-30-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Windows 7 (loader) on /dev/sda3
Unhide GRUB boot menu in sda5/boot/grub/grub.cfg


---

### Post by critin on 2012-09-11
> **philip9910 said:**
> i just did that but nothing happened.   the file report is 
[http://paste.ubuntu.com/1196825/](http://paste.ubuntu.com/1196825/)

> oldfred suggested:
run the BootInfo report and post link it creates.Did you actually choose to do the Recommended Repair too, or just the Create Boot Info?

From what I see in the last line (544) of pasted info, this step was not done.  

[I]Reinstall the GRUB of sda5 into the MBR of sda

line 544:  [/I]...
boot files of Ubuntu 12.04.1 LTS] are far from the start of the disk.You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk).[I] 

I believe it's waiting for you ,  But I could be wrong.

[/I]

---

### Post by philip9910 on 2012-09-11
i only did the recommended repair,and can i do all of this using GP partition?

---

### Post by critin on 2012-09-11
> **philip9910 said:**
> i only did the recommended repair,and can i do all of this using GP partition?

Run boot repair first and choose Repair.  If that doesn't do it, post back and someone will help you further.

If boot repair asks you if it should do something and continue, always say yes.   It may can do the stuff it asks, but needs permission.  It may not be able to, so just stay close and pay attention.

---

### Post by oldfred on 2012-09-11
Boot Repair is mostly for fixing Ubuntu or grub2 boot issues. It will install a Window like boot loader but cannot repair Windows.

If Ubuntu boots you do not need to run more repairs with Boot-Repair.

What happens when you boot Windows from sda2 and from sda3. Both should work and if not then you need a Windows repairCD or USB.

---

### Post by YannBuntu on 2012-09-12
Hello

Your problem is not a broken GRUB, but a hidden GRUB. Here are 2 options that may solve this problem:

1) run Boot-Repair, click "Advanced options", go to the "GRUB options" tab, tick the "Uncomment GFXMODE" option, click the "Apply" button. Reboot the PC.

2) If still not good: run Boot-Repair, click "Advanced options", go to the "GRUB options" tab, click the "Edit GRUB configuration file", remove the # at the start of the "GRUB_TERMINAL" line, save the file, close the text editor, click the "Apply" button. Reboot the PC.



> **critin said:**
> Did you actually choose to do the Recommended Repair too, or just the Create Boot Info?

FYI, you can see the chosen action at the bottom of the log:

```
=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sda5 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot
```

---

### Post by philip9910 on 2012-09-12
> **YannBuntu said:**
> Hello

Your problem is not a broken GRUB, but a hidden GRUB. Here are 2 options that may solve this problem:

1) run Boot-Repair, click "Advanced options", go to the "GRUB options" tab, tick the "Uncomment GFXMODE" option, click the "Apply" button. Reboot the PC.

2) If still not good: run Boot-Repair, click "Advanced options", go to the "GRUB options" tab, click the "Edit GRUB configuration file", remove the # at the start of the "GRUB_TERMINAL" line, save the file, close the text editor, click the "Apply" button. Reboot the PC.





FYI, you can see the chosen action at the bottom of the log:

```
=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sda5 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot
```
thank you yannbuntu option 1 worked like a breeze thank you so much this is the only thing that helped my situation.

---

### Post by philip9910 on 2012-09-12
thank you guys for your ideas but i have finally gotten the answer from someone named yannbuntu so ill give you the information he told me : 

Your problem is not a broken GRUB, but a hidden GRUB. Here are 2 options that may solve this problem:

1) run Boot-Repair, click "Advanced options", go to the "GRUB options" tab, tick the "Uncomment GFXMODE" option, click the "Apply" button. Reboot the PC.

2) If still not good: run Boot-Repair, click "Advanced options", go to the "GRUB options" tab, click the "Edit GRUB configuration file", remove the # at the start of the "GRUB_TERMINAL" line, save the file, close the text editor, click the "Apply" button. Reboot the PC.

---

### Post by offgridguy on 2012-09-12
Glad this worked out for you, Don't forget to use thread tools to mark this as solved.
Happy ubunting.

---

