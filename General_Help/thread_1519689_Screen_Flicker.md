---
title: "Screen Flicker"
date: 2010-06-28
forum: General Help
---

### Post by gloria0227 on 2010-06-28
Hello,

I am experiencing screen flicker on my entire screen, this is most notable with dark colors.  How would I go about figuring what is causing this or what information would I need to post on here for others to be able to help?

I dont know if it is useful or not, but I did attach the report after running the System Test.

Thank you,

Gloria

---

### Post by gloria0227 on 2010-07-17
I'm still having this problem. Anybody have any ideas to fix it?

---

### Post by AlphaLexman on 2010-07-17
What is your video card make and model?
What is your monitor make and model?

---

### Post by gloria0227 on 2010-07-18
> **AlphaLexman said:**
> What is your video card make and model?
What is your monitor make and model?

Model of computer A505-S6005

VGA compatible controller: Intel Corporation Core Processor Integrated  Graphics Controller (rev 02)

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
03:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
03:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```This is the computer specifications: [http://laptops.toshiba.com/laptops/satellite/A500/A505-S6005](http://laptops.toshiba.com/laptops/satellite/A500/A505-S6005)

Thanks for your help! :)

---

### Post by AlphaLexman on 2010-07-18
My first impression is the refresh rate (in Hz) for your screen is out of sync with the video card/driver.
Let's eliminate the X11 system first.
Can you CTRL+ALT+F1 to a login screen?
Do you still have the same flicker?
No? CTRL+ALT+F7 will get you back to your GUI.
Yes? Let us know.

Second Let's test the open GL setup.
From a terminal enter:
```
glxgears
```
Do you see three spinning, colored gears?
Yes, but they still flicker... open GL works. It's your refresh rate.
No, open GL doesn't work, could be an issue doesn't eliminate the refresh rate issue.

I know that is a lot of test's, but post back what doesn't work.

Good luck.

---

### Post by gloria0227 on 2010-07-19
When I pressed CTRL+ ALT+ F1, it brought me to a black screen with white writing and I didn't see any flickering. However, when I pushed CTRL+ALT+F7, it brought me to my screen with my login and the purple background and the screen did flicker.

I see the gears and they don't have any flicker. Here's what shows up in the terminal:```
3147 frames in 5.0 seconds
2882 frames in 5.0 seconds
2647 frames in 5.0 seconds
1581 frames in 5.0 seconds
513 frames in 5.0 seconds
1729 frames in 5.0 seconds
2377 frames in 5.0 seconds

```I also went to the system preferences and the monitor to see if I could adjust the refresh rate, but I couldn't. It's set at 60 Hz.

---

### Post by pbidwell on 2010-07-30
I have a very similar problem.  I have a Sony VAIO VGN-NW150J running Xubuntu 10.04.  I get random screen flickering, and it drives me absolutely nuts.  The resolution is set at 1366x768 at 60 Hz.  When I go in to change the refresh rate, it is also set to 60 Hz.  Strangely, there are two "1366x768" options to choose from.  When I switch to the other one, the screen gets a bit blurry, but the flickering stops immediately.  Again, the refresh rate is still stuck at 60 Hz.  I really do not want to use the "blurry" 1366x768, as I feel like am going blind.  And the "flickering" 1366x768 will give me seizures.

glxgears runs flawlessly, no flickering.

So as of right now, I am trying to decide whether I have to be blind or epileptic.

---

### Post by gloria0227 on 2010-08-24
Can anyone help?  The problem is not the refresh rate, I have tried everything from 60hz to 85hz.  Please help! :)

---

### Post by Whisp3r on 2010-08-31
There are several threads related to this problem with Intel video cards. The flicker appeared after 10.04. Thus far, Ubuntu has not been able to fix it. Hopefully this will be fixed with Meerkat.

---

