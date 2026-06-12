---
title: "Ubuntu9.10: Problems with the mouse and keyboard"
date: 2010-04-04
forum: General Help
---

### Post by darkside1222 on 2010-04-04
I am having alot of troubles installing ubuntu 9.10. Every time i install ubuntu, it works fine but then after I boot up ubuntu and it loads the logon screen my keyboard and mouse freezes!!! I also have windows 7 dual booted as well so I think windows 7 might be the problem? On windows 7 my mouse and kB works too. Here are my keyboard and mouse names:

Acer Ps/2 keyboard model  KB-0759
Logitec USB optical mouse

Can anyone help me?

Comp spec:
System Manufacturer    ACER
System Model    Aspire M1641
System Type    X86-based PC
BIOS Version/Date    American Megatrends Inc. R01-B4, 11/09/2008

---

### Post by SnickerSnack on 2010-04-04
Have you tried using any other mouse or keyboard?

Have you tried reinstalling ubuntu?

---

### Post by darkside1222 on 2010-04-04
> **SnickerSnack said:**
> Have you tried using any other mouse or keyboard?

Have you tried reinstalling ubuntu?

I have reinstalled ubuntu, no luck
Using other mouse and KB ... no luck

---

### Post by darkside1222 on 2010-04-04
bump...:confused:

---

### Post by jhansonxi on 2010-04-05
> **darkside1222 said:**
> I have reinstalled ubuntu, no luck
Using other mouse and KB ... no luckWhen it freezes, try pinging it by IP address from another PC or install the ssh server (package name ssh) and connecting remotely.  If you can't ping it or connect via ssh then the entire system is locked up, not just the mouse and keyboard.  Most likely cause is a graphics driver problem or a broken BIOS that is fighting with the kernel.  [https://wiki.ubuntu.com/DebuggingACPI](https://wiki.ubuntu.com/DebuggingACPI)

If X is crashing but the kernel is still functioning, you can connect over ssh and see the logs and possible error messages.  The "dmesg | less" and "less /var/log/X.0.log" commands are useful.

Also search for "REISUB" and learn how to properly shut it down if a serious problem occurs (sometimes even if keyboard is useless otherwise).  You can also shut it down over ssh with the "halt" command assuming the hardware hasn't locked up.

---

### Post by darkside1222 on 2010-04-05
Yea the whole system is locked up, it never happended before... tho i have to set no-apic when im installing ubuntu.... So what should i do now?


EDIT haha intresting... how do i enable apic :

Try booting with the "acpi=off" kernel parameter This will disable ACPI support.  If the  error is the same with acpi enabled and disabled, this may not be an  ACPI issue. 

That makes my system work! but I don't know how to enable it when i use it. I get to enable it when its on the ubuntu install cd screen, and everything works. Without acpi=off, The system freezes!

---

### Post by jhansonxi on 2010-04-05
> **darkside1222 said:**
> That makes my system work! but I don't know how to enable it when i use it. I get to enable it when its on the ubuntu install cd screen, and everything works. Without acpi=off, The system freezes!Turning ACPI off is extreme.  Try some of the other boot options to find the simplest solution.  Turning ACPI off entirely will prevent soft power-off at shutdown, disable suspend and power management.

To set it permanently, edit /etc/default/grub and add the option to the "GRUB_CMDLINE_LINUX_DEFAULT=" line then run "update-grub".

---

### Post by darkside1222 on 2010-04-06
Ohhh why is turning off Apci extreme?? I don't understand soft shutdown. So should I make apci=off permanently? or is there any better solution?

---

### Post by jhansonxi on 2010-04-06
Soft powerdown is when the computer turns itself off.  If it is disabled then when shutdown is selected from the menu it will halt but not turn off and you have to press the power button or unplug it.  Not critical, just annoying.

Go through all the ACPI options and see if one of the other ones work instead of acpi=off.

---

### Post by darkside1222 on 2010-04-07
All the other acip options don't work other than acpi=off only. So how do you make acpi=off perm when you cannot enter into the system. i can only go to the logon screen thats all

---

### Post by jhansonxi on 2010-04-07
Edit /etc/default/grub and add it to the line as I indicated above.  Just boot using one of the "recovery" options in the GRUB menu so that it boots to "friendly recovery" mode.  Exit to a root prompt and run whatever text-based editor you want (vi, vim, Midnight Commander's editor).  I normally use the latter.  Just install it with "apt-get install mc" then run mc.  Don't forget to run "update-grub" afterwards.

---

### Post by darkside1222 on 2010-04-07
I tried 1 of the recoverys... but my keyboard seems to be frozen!!!

---

### Post by jhansonxi on 2010-04-07
In the Grub menu, select the recovery option and press "e" to edit it.  Add the acpi=off fix to the kernel line then Ctrl-X to boot.  Another option is to boot normally and then open a terminal and use "sudo gedit" to launch the editor as root in order to change the file.

---

### Post by darkside1222 on 2010-04-07
MY mistake! Apci=off does not work at all! my keyboard is frozen and so is my mouse... I found out that the option in the install menu of ubuntu says noacpi works for me! If i put on noacpi option, the keyboard and mouse works! Im confused now... can you help me

---

### Post by jhansonxi on 2010-04-07
Just use that option instead.

If this turns out to not fix it (or not all the time), you may be experiencing **[bug #555169]("http://https://bugs.launchpad.net/ubuntu/+source/linux/+bug/555169")**.

---

### Post by darkside1222 on 2010-04-07
So I would make noapci perm the same way? And yea the bug 555169

---

### Post by jhansonxi on 2010-04-08
> **darkside1222 said:**
> So I would make noapci perm the same way? And yea the bug 555169Yes.  See the **[Grub2 documentation]("https://help.ubuntu.com/community/Grub2")** for more info.

---

### Post by darkside1222 on 2010-04-08
I tried edit /etc/default/grub and It won't let me save the changes.. it says i need to be a root????

---

### Post by darkside1222 on 2010-04-08
is this right?

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"noapic"

---

### Post by jhansonxi on 2010-04-08
> **darkside1222 said:**
> I tried edit /etc/default/grub and It won't let me save the changes.. it says i need to be a root????If you are in the graphical desktop, open a terminal and enter "sudo gedit".  If you are in a tty, log in as the admin (whichever account is in the admin group, usually the first created) then enter "sudo su".  Then use any text editor.

---

### Post by jhansonxi on 2010-04-08
> **darkside1222 said:**
> is this right?

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"noapic"Get rid of the extra double-quote in the middle.

---

### Post by darkside1222 on 2010-04-08
Thank you soo much!! My mouse and keyboard is working on ubuntu again! Thank!

---

