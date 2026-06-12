---
title: "Widescreen virtual terminal(tty) resolution?"
date: 2009-09-04
forum: General Help
---

### Post by TheShader on 2009-09-04
Hello I'm runing Linux Mint 7(aka Ubuntu 9.04 with some visual stuff and codecs) on a laptop with 1280*800 screen resolution. I'm just wondering, is it possible to make the virtual terminal(ctrl+alt+F1) resolution set to 1280*800? I see that changing the resolution is done by adding a vga parameter to the kernel... There is 1280*1024 which is not 4:3 like others, so why it should not be possible to have 16:10(1280*800)? But how?:)

---

### Post by jward3010 on 2009-09-04
Ha! Just about to ask the same thing, I have a horrible 1024 X 768 set up on a 1280 X 800 screen which spreads itself sideways like a face lift.

Don't like at all.

---

### Post by wiremoons on 2009-09-04
WARNING - be careful when playing around with high screen resolutions - make sure your monitor is capable of supporting the high resolutions first - you don't want to damage your monitor by trying to display settings it is not able to support!

Configure The Framebuffer Resolution
Linux distributions generally (including Ubuntu) include support for framebuffer graphics in the kernel - this is what allows the display of the Tux logo at bootup on some Linux distributions for example. The resolution can therefore be configured to offer a better looking terminal window - if you are not using X Windows. To find out what resolutions your computer can support you can run this command from the terminal window:

      **sudo hwinfo --framebuffer | grep 'Mode'**

You may need to first install *hwinfo* with **sudo apt-get install hwinfo** if the above command is not working. The output of the command will vary slightly from system to system - but on my Dell-540 it looks like this:

root@dell-540:~# hwinfo --framebuffer | grep 'Mode'
  Model: "NVIDIA G84 Board - p403h01 "
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0349: 1400x1050 (+5600), 24 bits
  Mode 0x034a: 1600x1200 (+6400), 24 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+5120), 24 bits
  Mode 0x0362: 768x480 (+768), 8 bits
  Mode 0x0364: 1440x900 (+1440), 8 bits
  Mode 0x0365: 1440x900 (+5760), 24 bits
  Mode 0x0368: 1680x1050 (+1680), 8 bits
  Mode 0x0369: 1680x1050 (+6720), 24 bits
  Mode 0x037c: 1920x1200 (+1920), 8 bits
  Mode 0x037d: 1920x1200 (+7680), 24 bit

Once you have the above output you can choose the best one for the resolution of your screen. These are shown in the 3rd column in the output above. The maximum screen resolutions for my two computers - along with the mode are shown below:

    * Dell 540 with Samsung SyncMaster 2433BM monitor - 1920x1200 (Mode 0x037d)
    * Acer L100 PC with AL1916W monitor - 1440x900 (Mode 0x356)

Trying the Resolution Out

   1. When your computer boots up, press **ESC** to enter the **GRUB menu**
   2. Choose to **edit the boot up command**, then choose to **edit the kernel command**
   3. **Add to the end of the existing kernel boot line** one of the options below:
          * **vga=ask** - to see what resolution are available and choose one to boot into
          * **vga=037d** - to set the desired boot resolution selected from the hwinfo command output as described above. **Change 037d for your own mode!!**

Once you have done the above and are happy with it, you can append the same information to the kernel line of the GRUB boot file: menu.1st to make it permanent

---

### Post by TheShader on 2009-09-05
Thanks! That worked for me! But I had to enter 0x0362 instead of 0362. I mean vga=037d in your example should be vga=0x037d. Just in case someone else reads this ;)

---

### Post by madmax.santana on 2010-10-02
> **TheShader said:**
> Thanks! That worked for me! But I had to enter 0x0362 instead of 0362. I mean vga=037d in your example should be vga=0x037d. **Just in case someone else reads this **;)

That was a nice thing to do.

---

