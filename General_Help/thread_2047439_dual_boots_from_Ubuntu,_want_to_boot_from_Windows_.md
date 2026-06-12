---
title: "dual boots from Ubuntu, want to boot from Windows 7"
date: 2012-08-24
forum: General Help
---

### Post by ubi123 on 2012-08-24
So I installed Ubuntu Linux (version 12.04) on my HDD alongside Windows  7. When I turn my laptop on, I want to select Ubuntu or Windows from  Windows, not from Linux. However, when I turn my computer on, the OS  select screen is "run" (I don't know how to say it) by Linux. Instead of  a Windows screen asking me for the OS, it's a Linux screen. How would I  change this?

---

### Post by beboylips on 2012-08-25
You are using GRUB by default. You don't need to change that. GRUB can recognize and boot quite a bit of different OSes. If you want to automatically boot Windows (as first choice instead of Linux), try editing the file  /boot/grub/menu.lst (using sudo). Just change the order of the listed OSes as you wish.

Be very careful, if you make a mistake, you won't be a able to boot. So make a backup before editing it. 

If you really insist on booting "Linux with Windows", try this:
[http://blog.famzah.net/2011/11/12/boot-linux-using-windows-7-boot-loader/](http://blog.famzah.net/2011/11/12/boot-linux-using-windows-7-boot-loader/)

---

### Post by MG&amp;TL on 2012-08-25
> **beboylips said:**
> You are using GRUB by default. You don't need to change that. GRUB can recognize and boot quite a bit of different OSes. If you want to automatically boot Windows (as first choice instead of Linux), try editing the file  /boot/grub/menu.lst (using sudo). Just change the order of the listed OSes as you wish.

Be very careful, if you make a mistake, you won't be a able to boot. So make a backup before editing it. 

If you really insist on booting "Linux with Windows", try this:
[http://blog.famzah.net/2011/11/12/boot-linux-using-windows-7-boot-loader/](http://blog.famzah.net/2011/11/12/boot-linux-using-windows-7-boot-loader/)


+1 for that link, but using menu.lst won't have worked since Grub 2 came out. I suggest using Grub Customiser or similiar tool to change the boot order if that's what you end up doing.

A better question might be 'why do you care?' - Booting from Ubuntu causes less problems, that's why we use it.

---

### Post by beboylips on 2012-08-25
> **MG&TL said:**
> +1 for that link, but using menu.lst won't have worked since Grub 2 came out. I suggest using Grub Customiser or similiar tool to change the boot order if that's what you end up doing.

A better question might be 'why do you care?' - Booting from Ubuntu causes less problems, that's why we use it.

Very true, GRUB is a better solution in any case.

---

### Post by sienile on 2012-08-25
There's 2 ways to solve this. 

If you just want to boot directly into Windows, when GRUB boots, note the placement of Windows in the boot list (what number it is from the top). Open a terminal and type```
sudo gedit /boot/grub/grub.cfg
```In there is a line that sets the default. (I can't recall what it is from memory and right now I'm repartitioning using the LiveCD, so I don't want to fubar anything by mounting my drives and checking.) Currently it's set to 0. Change this number to 1 minus the number you noted.


If you really want to use Windows BCD as your boot loader, boot into Windows. Download EasyBCD, you can find it with Google. Add an entry for GRUB2. Then set your default boot option to whatever you prefer.

I'm not sure if it will set the default boot drive to the one with Windows/BCD, so you might need to boot into the Ubuntu LiveCD and run Boot-Repair. ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) Info on how to install it.) When it opens after scanning, click "Advanced Options". Go to the "Other Options" tab. Check "Place boot flag on" and select your Windows partition.
[]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by lindsay7 on 2012-08-25
Just install Startupmanager and use it to set the default OS.

---

### Post by Wim Sturkenboom on 2012-08-26
If you use the windows bootloader, you will also get a boot menu where you select what you want to boot; similar to what you have now. At least that's how it used to be; things might have changed.

So there is not really much difference (to my knowledge) in the user experience.

[windows bootloader to boot linux](http://www.google.co.za/search?q=windows+bootloader+to+boot+linux&btnG=Search&sclient=psy-ab&hl=en&site=) google results

Make your pick :)

Please note that you have to fix your MBR so the windows bootloader will be used instead of grub, else you will first get grub to pick an OS and next the windows bootloader to select an OS again.

---

### Post by sgage on 2012-08-26
> **Wim Sturkenboom said:**
> If you use the windows bootloader, you will also get a boot menu where you select what you want to boot; similar to what you have now. At least that's how it used to be; things might have changed.

So there is not really much difference (to my knowledge) in the user experience.

[windows bootloader to boot linux](http://www.google.co.za/search?q=windows+bootloader+to+boot+linux&btnG=Search&sclient=psy-ab&hl=en&site=) google results

Make your pick :)

Please note that you have to fix your MBR so the windows bootloader will be used instead of grub, else you will first get grub to pick an OS and next the windows bootloader to select an OS again.

You will have to fix your MBR -and- make an entry in the Windows Bootloader for Ubuntu. I highly recommend the free (Windows) utility EasyBCD for both tasks. I've been using it for years.

---

### Post by Mark Phelps on 2012-08-26
To restore your original Windows MBR, you will need to do the following:
1) Boot into Win7
2) Use the Backup feature to create an burn a Win7 Repair CD
3) Boot using the Repair CD
4) Run Startup Repair.  You may have to run it three times -- as it tends to repair the MBR on the third pass.

When you reboot, you will NOT see a menu that includes Ubuntu.

You will then need to install EasyBCD and use it to add an option for Ubuntu.

---

