---
title: "Brightness adjustment problem for Toshiba L500D"
date: 2012-04-27
forum: General Help
---

### Post by cogitator on 2012-04-27
I upgraded to [COLOR=Red]**Lubuntu**[/COLOR]  12.04, everything seems okay until now, except that I can not set the  backlight of my (laptop's) monitor screen (for example,  "**xbacklight**  -set 50" does not make any effect, nor using the FN+F6 or  FN+F7 keys  does something). In 11.10 it was okay, but now (in 12.04)  is not. [[COLOR=DarkRed]**My  eyes hurts...!**[/COLOR]]

I'll appreciate any advice. Thanks in advance.


[SIZE=1]P.S.#1: Also, a minor problem (maybe) is that the temperature goes up very  quickly now (with 12.04, this didn't happen with 11.10) and so the  cooling fan work more fast and, that means that more energy it consumes.

[/SIZE][SIZE=1]P.S.#2: This is my worst experience in Ubuntu until now.[/SIZE]

---

### Post by cogitator on 2012-04-28
There should be a solution. I really can not comfortably use my pc with that problem in Lubuntu 12.04. All that strong light ...it is like being in a solarium! [SIZE=1][There is a solution... to wear sunglasses, how's that...? Just kidding... but, really, you can not tolerate that.][/SIZE]

Well, if you are willing to help, do so -for the sake of Ubuntu.

---

### Post by brainwash on 2012-04-28
Did you already tell your system to use the vendor-specific driver for the backlight by adding *acpi_backlight=**[I]vendor* [/I]to the kernel parameter list (grub2)? There are also other ways to adjust screen brightness, for example:
```
sudo setpci -s 00:02.0 F4.B=XX
```

XX is the desired brightness in hexadecimal ranging from 00 to FF.

FF = 100%
7F = 50%
00 = 0%

You might need to change the hardware address (00:02.0). To get the correct one, check the output of this command:
```
lspci | grep VGA
```

---

### Post by cogitator on 2012-04-28
Hi "brainwash", I have already tell my system to use this, but it did not change anything and still I can not change the brightness. But thank you for the additional information about this way to adjust the brightness, it may be useful in some other occasion.

All that means that I am going back to** Lubuntu 11.10** and, so my computer will be able to wake up from this 12.04 nightmare... I hope that this situation will change in the near future.

[SIZE=1]Okay, bye-bye 12.04, before the cpu will melt, too...[/SIZE]

---

### Post by Toz on 2012-04-28
What is the make/model of your computer? Sometimes, adding
```
acpi_osi=Linux acpi_backlight=vendor
```
...to the grub kernel line will fix issues like this one. But it depends on your computer.

---

### Post by cogitator on 2012-04-29
Hi "Toz". The model of my computer is: **Toshiba Satellite L500D**

---

### Post by Toz on 2012-04-29
Did you try those kernel parameters from post #5? See [here]("https://help.ubuntu.com/community/Grub2#Editing_the_GRUB_2_Menu_During_Boot") for information on how to test it.

If still no luck, open a terminal window, type in the following commands, and post back the results:
```

cat /proc/cmdline
ls /sys/class/backlight/*/
sudo lspci -vnn | grep -A10 VGA
```

---

### Post by cogitator on 2012-08-15
Hello (again), Toz. I delayed to post a new reply in this thread, because I went back at Lubuntu 10.04 (specifically "Peppermint 2") and there I did not have any problem with the brightness of my monitor. But now that I installed "Peppermint 3" and thus Lubuntu 12.04, the problems did come again. I tried those kernel parameters from post#5, but they did not have any effect. So, I typed in the suggested commands and, here are the results:

```

**"cat /proc/cmdline":**
BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=b1834d50-6d96-4c36-9e52-05cfbeeab5c6 ro quiet splash vt.handoff=7

**"ls /sys/class/backlight/*/":**
/sys/class/backlight/acpi_video0/:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

/sys/class/backlight/toshiba/:
actual_brightness  brightness  max_brightness  subsystem  uevent
bl_power           device      power           type

**"sudo lspci -vnn | grep -A10 VGA":**
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV710 [Mobility Radeon HD 4500/5100 Series] [1002:9553] (prog-if 00 [VGA controller])
    Subsystem: Toshiba America Info Systems Device [1179:ff80]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 9000 [size=256]
    Memory at cfef0000 (32-bit, non-prefetchable) [size=64K]
    [virtual] Expansion ROM at cfe00000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
```

---

### Post by Toz on 2012-08-15
Hi.
You're cmdline doesn't have "acpi_osi=Linux acpi_backlight=vendor" added to it. Make sure it was properly tested. 

1. Edit /etc/default/grub:
```
gksu leafpad /etc/default/grub
```

2. Replace the line that reads:
> GRUB_CMDLINE_LINUX=""
...with:
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
```

3. Save the file.

4. Update grub:
```
sudo update-grub
```

5. Reboot and test. Double-check command line with:
```
cat /proc/cmdline
```
...again to make sure it is there.

-----------------------

If it still doesn't work, have you installed the proprietary driver for your ATI video card?

-----------------------

If the first thing didn't work, can you post back the results of this command:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/max_brightness; cat $i/actual_brightness; cat $i/brightness; done
```

---

### Post by cogitator on 2012-08-15
After the application of all the steps from 1 to 5, now the FN+F6 or  FN+F7 keys  does not working at all.

```
**"cat /proc/cmdline":**
BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=b1834d50-6d96-4c36-9e52-05cfbeeab5c6 ro **acpi_osi=Linux acpi_backlight=vendor** quiet splash vt.handoff=7
```After the application, I also installed the proprietary driver for my ATI video card, but nothing changed.

Here are the results of the below suggested command:
```
**"for i in /sys/class/backlight/*; do echo $i; cat $i/max_brightness; cat $i/actual_brightness; cat $i/brightness; done":**
/sys/class/backlight/*
cat: /sys/class/backlight/*/max_brightness: &#916;&#949;&#957; &#965;&#960;&#940;&#961;&#967;&#949;&#953; &#964;&#941;&#964;&#959;&#953;&#959; &#945;&#961;&#967;&#949;&#943;&#959; &#942; &#954;&#945;&#964;&#940;&#955;&#959;&#947;&#959;&#962;
cat: /sys/class/backlight/*/actual_brightness: &#916;&#949;&#957; &#965;&#960;&#940;&#961;&#967;&#949;&#953; &#964;&#941;&#964;&#959;&#953;&#959; &#945;&#961;&#967;&#949;&#943;&#959; &#942; &#954;&#945;&#964;&#940;&#955;&#959;&#947;&#959;&#962;
cat: /sys/class/backlight/*/brightness: &#916;&#949;&#957; &#965;&#960;&#940;&#961;&#967;&#949;&#953; &#964;&#941;&#964;&#959;&#953;&#959; &#945;&#961;&#967;&#949;&#943;&#959; &#942; &#954;&#945;&#964;&#940;&#955;&#959;&#947;&#959;&#962;
```Note: "&#916;&#949;&#957; &#965;&#960;&#940;&#961;&#967;&#949;&#953; &#964;&#941;&#964;&#959;&#953;&#959; &#945;&#961;&#967;&#949;&#943;&#959; &#942; &#954;&#945;&#964;&#940;&#955;&#959;&#947;&#959;&#962;"(Greek)  =  "No such file or directory".

---

### Post by Toz on 2012-08-15
Try deleting just the acpi_osi=Linux parameter (leave the acpi_backlight=vendor), run 'sudo update-grub' again, reboot and run those same commands again and post back the results.

If still no luck, try also with changing acpi_backlight=vendor to acpi_backlight=video. Again, post back results.

---

### Post by cogitator on 2012-08-16
> try deleting just the acpi_osi=linux parameter (leave the acpi_backlight=vendor), run 'sudo update-grub' again, reboot and run those same commands again and post back the results.Now the FN+F6 and  FN+F7 keys  does working, and by that I mean that you can see the relevant panel (the one with an icon that represents a sun and with an horizontal increasing/decreasing bar), but by pressing them, this does not have any effect in the brightness.

```
**"for i in /sys/class/backlight/*; do echo $i; cat $i/max_brightness; cat $i/actual_brightness; cat $i/brightness; done":**
/sys/class/backlight/toshiba
7
1
7
```> If still no luck, try also with changing acpi_backlight=vendor to acpi_backlight=video. Again, post back results.Still nothing changed.

```
**"for i in /sys/class/backlight/*; do echo $i; cat $i/max_brightness; cat $i/actual_brightness; cat $i/brightness; done":**
[COLOR=#000000][FONT=Arial]/sys/class/backlight/acpi_video0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]7[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]7[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]7[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]/sys/class/backlight/toshiba[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]7[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]7[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]7[/FONT][/COLOR]

```

---

### Post by Toz on 2012-08-16
Is there anything in the bios about screen brightness? I had an older Toshiba (Tecra M Series) and could only get screen brightness to behave if I changed a brightness setting in the bios from Auto to something else (can't remember exactly what the setting was).

---

### Post by cogitator on 2012-08-17
I am still wondering why this problem does not occur in [L]Ubuntu versions under 12.04, that means that it does not occur in versions 11.10, 11.04 and maybe some versions below these, but it does occur in version 12.04. Also, it does not occur in M$ Windows 7.

Now, there is a setting in the BIOS called "Display".
```
Display
     ---> Power On Display
               ---> Auto_Selected *(default)*  =>  *If any external display is connected, the power on display will be in external display only mode. Otherwise it will be in LCD only mode*
               ---> System LCD Only  =>  *Irrespective of external display connection, the power on display will be in integrate LCD only mode*
```It was set to "Auto_Selected" and I changed it to "System LCD Only". Still nothing changed.

---

### Post by Toz on 2012-08-17
The biggest change with the 12.04 series is that it uses kernel version 3.2. Something must have changed to cause you problems with the brightness controls.

With the ATI proprietary drivers, does the system run any cooler?

Can you try one more combination of kernel parameters? Try: **acpi_osi=Linux acpi_backlight=vendor**. The run again:
```
cat /proc/cmdline
```
...and
```
for i in /sys/class/backlight/*; do echo $i; cat $i/max_brightness; cat $i/actual_brightness; cat $i/brightness; done
```

Can you also post back the contents of /var/log/dmesg? Try:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

### Post by cogitator on 2012-08-17
> With the ATI proprietary drivers, does the system run any cooler?Yes, seems it does run cooler than before (when the proprietary driver was not installed) or at least the CPU fan does not run that fast.

*Notice: According to the correction in the [post#17]("http://ubuntuforums.org/showpost.php?p=12178326&postcount=17"), the suggested kernel parameter to try is:** acpi_osi=Linux**.*

```
**"cat /proc/cmdline":**
BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=b1834d50-6d96-4c36-9e52-05cfbeeab5c6 ro **acpi_osi=Linux** quiet splash vt.handoff=7
``````
**"for i in /sys/class/backlight/*; do echo $i; cat $i/max_brightness; cat $i/actual_brightness; cat $i/brightness; done":**
/sys/class/backlight/acpi_video0
7
1
1

``````
**"pastebinit /var/log/dmesg":**
[http://pastebin.com/P9HASSJm](http://pastebin.com/P9HASSJm)
```

---

### Post by Toz on 2012-08-17
Sorry, can you try just **acpi_osi=Linux**? Then:
```
cat /proc/cmdline
for i in /sys/class/backlight/*; do echo $i; cat $i/max_brightness; cat $i/actual_brightness; cat $i/brightness; done
```

From your dmesg:
> [    0.184913] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.185264] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.244301] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
Can you see if there is a bios update available?

If not, it might be a good idea to create a bug report. We can try to create a brightness workaround to at least give you some control.

---

### Post by cogitator on 2012-08-17
I edited my above post([#16]("http://ubuntuforums.org/showpost.php?p=12178084&postcount=16")) with the generated results of the correct kernel parameter to try.

Now, the adjustment of monitor's brightness is working correctly.

> Can you see if there is a bios update available?There is a BIOS update available according to this [link]("http://eu.computers.toshiba-europe.com/innovation/download_driver_details.jsp?service=EU&selCategory=2&selFamily=2&selSeries=178&selProduct=856&selShortMod=907&language=13&selOS=null&selType=null&yearupload=&monthupload=&dayupload=&useDate=null&mode=allMachines&search=&action=search&macId=&country=null&selectedLanguage=13&type=null&page=1&ID=74090&OSID=-1&driverLanguage=42"), but I did not installed it yet.

[As it seems now, the problem is solved and, I think I will apply the following steps:
1) mark the thread as [SOLVED] using the Thread Tools link above,
2) change the title of this thread to "Brightness adjustment problem for Toshiba L500D" (or something better),**  (It seems that I do not have permissions to do that)**
3) edit the tags and adding the "Toshiba L500D" tag, **(It seems that I do not have permissions to do that)**
4) I do not know if "xbacklight" has still problems with 12.04, if so I may add that in a parenthesis in the title of this thread.  **(It seems that I do not have permissions to do that)**]

Thank you very much, Toz, for your willingness to help.

---

### Post by Toz on 2012-08-17
No worries. If you don't mind, can you post back another copy of your /var/log/dmesg (now that you only have acpi_osi=Linux and brightness working)? I'm curious to see if there are any changes.
Thanks.

---

### Post by cogitator on 2012-08-17
```
"pastebinit /var/log/dmesg":
[http://pastebin.com/ppJ8Vit5](http://pastebin.com/ppJ8Vit5)
```I would like to hear your evaluation.

---

### Post by Toz on 2012-08-17
Thanks. I've read a lot about flaky bios and acpi implementations by Toshiba that affect things such as brightness and performance. Kind of curious if they've been sorted out yet.

I actually like their laptops and am considering getting one, but am worried about this. Its good that the brightness is working again. How is the laptop with heat and performance now that you have the proprietary drivers installed?

As for your dmesg, some interesting errors:

> [    0.184900] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.185252] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.252309] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness

> [    0.284697]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.284701]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d

> [    0.305694] pnp 00:09: [Firmware Bug]: [mem 0x00000000-0xffffffffffffffff disabled] covers only part of AMD MMCONFIG area [mem 0xe0000000-0xefffffff]; adding more reservations

> [    0.440316] ACPI: Battery Slot [BAT1] (battery absent)
Is your battery being recognized?

> [    1.152475] ACPI Error: Could not disable RealTimeClock events (20110623/evxfevnt-254)

Plenty of acpi bugs - which is why I asked whether you had updated the bios. It would be interesting to research each of these to see if there are fixes and/or create a bug report so that this can get looked at.

---

### Post by cogitator on 2012-08-18
> How is the laptop with heat and performance now that you have the proprietary drivers installed? The heat is okay, but not that good as in previous version of [L]Ubuntu. Also, it depends with what you are doing with your computer. Let's say that you are watching videos consequently (that is, when the one stops then you play another), or when running computer games that needs a lot of processing power, or when you have opened multiple windows, then is getting worse.
Here is a list that shows in order, from good to worse, which version (from the ones I have tried) is the best about heat, from the others:
[
"Peppermint Two ([L]Ubuntu 10.04)", "Lubuntu 11.10", "Peppermint Three([L]Ubuntu 12.04)", "Lubuntu 12.04", ...and every other distro I have tried
]
It seems that the older the version of [L]Ubuntu, the better are things about heat. I think the same things apply about performance (in my Toshiba laptop), too.

> Is your battery being recognized? I have uninstalled my battery. I may install it again and see.

> Plenty of acpi bugs - which is why I asked whether you had updated the  bios. It would be interesting to research each of these to see if there  are fixes and/or create a bug report so that this can get looked at.     Do you suggest to do the BIOS update (if it is necessary and if that will help you to decide better about the purchase of a Toshiba laptop) to see if that will make any difference?


[SIZE=1]P.S.: It seems that I do not have permissions to change some things in this thread (like topic's title, tags), as they are proposed in [post#18]("http://ubuntuforums.org/showpost.php?p=12178557&postcount=18").[/SIZE]

---

### Post by Toz on 2012-08-20
> **cogitator said:**
> Do you suggest to do the BIOS update (if it is necessary and if that will help you to decide better about the purchase of a Toshiba laptop) to see if that will make any difference?I'm not sure that a bios update would help - it would depend on what was updated in the bios and whether Toshiba is fixing the fundamental problems with their bios implementations (with respect to Linux interoperability).

---

### Post by Toz on 2012-08-20
> **cogitator said:**
> P.S.: It seems that I do not have permissions to change some things in this thread (like topic's title, tags), as they are proposed in [post#18]("http://ubuntuforums.org/showpost.php?p=12178557&postcount=18")

I've taken care of it.

---

### Post by Toz on 2012-08-20
I've just been reading up on buggy bioses and DSDT tables (one such link: [http://forums.opensuse.org/archives/sf-archives/archives-tips-tricks-tweaks/320199-howto-fix-your-buggy-dsdt.html]("http://forums.opensuse.org/archives/sf-archives/archives-tips-tricks-tweaks/320199-howto-fix-your-buggy-dsdt.html")), and was wondering if you could try the following kernel parameter to see if it allows for proper recognition and use of the brightness keys:
```
acpi_os_name="Microsoft Windows XP"
```
...and
```
acpi_os_name="Microsoft Windows 2000"
```

According to that document, these switches change the way the bios builds the DSDT tables. Perhaps if we tell the bios that we have a windows system, it would make more functionality available to us.

Thanks for testing this for me.

---

### Post by cogitator on 2012-08-22
[B]acpi_os_name="Microsoft Windows XP":
[/B]
```
**"cat /proc/cmdline":**
BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=b1834d50-6d96-4c36-9e52-05cfbeeab5c6 ro acpi_osi=Linux **"acpi_os_name=Microsoft Windows XP"** quiet splash vt.handoff=7
``````
**"for i in /sys/class/backlight/*; do echo $i; cat $i/max_brightness; cat $i/actual_brightness; cat $i/brightness; done":**
/sys/class/backlight/acpi_video0
7
1
1
``````
**"pastebinit /var/log/dmesg":**
[http://pastebin.com/EBp5FtMb](http://pastebin.com/EBp5FtMb)

```----

**acpi_os_name="Microsoft Windows 2000":**

```
**"cat /proc/cmdline":**
BOOT_IMAGE=/boot/vmlinuz-3.2.0-29-generic-pae root=UUID=b1834d50-6d96-4c36-9e52-05cfbeeab5c6 ro acpi_osi=Linux **"acpi_os_name=Microsoft Windows 2000"** quiet splash vt.handoff=7
``````
**"for i in /sys/class/backlight/*; do echo $i; cat $i/max_brightness; cat $i/actual_brightness; cat $i/brightness; done":**
[COLOR=#000000][FONT=Arial]/sys/class/backlight/acpi_video0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]7[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]1[/FONT][/COLOR]
``````
**"pastebinit /var/log/dmesg":**
[http://pastebin.com/DUMaFiQa](http://pastebin.com/DUMaFiQa)
```----

Both of them allows proper use of the brightness keys, that is I can increase/decrease the brightness of my monitor by pressing the keys FN+F6 and FN+F7, but I am not sure about recognition.

P.S.: If I did something wrong in the above, tell me and I will fix it in time (the corrections will be in the same post).

---

### Post by Toz on 2012-08-23
Thanks, but I can't read the linked dmesg reports - it says they are private. Is there any way you can flag them as public?

---

### Post by metalcat on 2012-08-24
The idea of Toz works like a charm. On my Tecra M11 I finally can change the brightness of my screen. If the brightness is the only problem with the BIOS you have, making the BIOS believe we are on a Wintendo is the way to go. :guitar:

---

### Post by Toz on 2012-08-24
@metalcat,
If you don't mind, can you post back the actual kernel command line that you are using? I'm curious to see which one worked.
```
cat /proc/cmdline
```

Thanks. And btw, welcome to the forums.

---

### Post by cogitator on 2012-08-25
> **Toz said:**
> Thanks, but I can't read the linked dmesg reports - it says they are private. Is there any way you can flag them as public? Now, the linked dmesg reports have been set as public.

---

