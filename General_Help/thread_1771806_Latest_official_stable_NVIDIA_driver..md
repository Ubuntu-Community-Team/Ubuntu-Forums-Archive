---
title: "Latest official stable NVIDIA driver."
date: 2011-05-30
forum: General Help
---

### Post by DinoT1985 on 2011-05-30
This fixed my ugly Plymouth splash.

> The official – stable nVIDIA graphics driver release 270.41.19 can  now be installed in Ubuntu 11.04 Natty Narwhal and daily builds of 11.10  Oneiric Ocelot via PPA. This driver release has been added into X  Updates PPA for Ubuntu 11.04 Natty and Ubuntu 11.10 Oneiric few days  before.
 There has been numerous bug fixes and stability enhancements for Linux environments. The major fixes are listed below :
 
[LIST]
[*]Fixed a bug in the VDPAU presentation queue that could cause 1  second hangs when transitioning from blit-based display to overlay-  based display. This would most commonly happen when disabling a  compositing manager.
[*]Fixed a bug that could cause crashes when capturing SDI video.
[*]Fixed a corner-case in which the OpenGL driver could leak resources in applications utilizing fork().
[*]Addressed a Linux kernel interface compatibility problem that could  lead to ioremap() errors and, potentially, functional and/or stability  problems.
[*]Fixed a bug that caused SLI initialization to fail on some Intel based systems.
[*]Fixed a bug that caused SLI initialization to fail when using recent Linux kernels, such as 2.6.38.
[/LIST]
[IMG]http://www.multimediaboom.com/wp-content/uploads/2011/05/nvidia-ubuntu-11.04.png[/IMG]
To install nVIDIA Display Driver release 270.41.19 in Ubuntu 11.04 Natty or 11.10 Oneiric, open Terminal and run :[INDENT]```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```[/INDENT]After the installation restart the system to enable the driver.

---

### Post by wildmanne39 on 2011-05-30
> **DinoT1985 said:**
> This fixed my ugly Plymouth splash.

To install nVIDIA Display Driver release 270.41.19 in Ubuntu 11.04 Natty or 11.10 Oneiric, open Terminal and run :[INDENT]```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```[/INDENT]After the installation restart the system to enable the driver.
Hi, is this driver for the 6150 series card?

---

### Post by DinoT1985 on 2011-05-31
> **wildmanne39 said:**
> Hi, is this driver for the 6150 series card?

Yep it does along with these :).

**GeForce 500 series:**
GTX 590, GTX 580, GTX 570, GTX 560 Ti, GTX 550 Ti, GT 530, GT 520

**GeForce 500M series:**
GT 555M, GT 550M, GT 540M, GT 525M, GT 520M

**GeForce 400 series:**
GTX 480, GTX 470, GTX 465, GTX 460 SE, GTX 460, GTS 450, GT 440, GT 430, GT 420, 405

**GeForce 400M series:**
GTX 485M, GTX 480M, GTX 470M, GTX 460M, GT 445M, GT 435M, GT 425M, GT 420M, GT 415M

**GeForce 300 series:**
GT 340, GT 330, GT 320, 315, 310

**GeForce 300M series:**
GTS 360M, GTS 350M, GT 335M, GT 330M, GT 325M, GT 320M, 310M, 305M

**GeForce 200 series:**
GTX 295, GTX 285, GTX 280, GTX 275, GTX 260, GTS 250, GTS 240, GT 240, GT 230, GT 220, G210, 205

**GeForce 200M series:**
GTX 285M, GTX 280M, GTX 260M, GTS 260M, GTS 250M, GT 240M, GT 230M, GT 220M, G210M

**GeForce 100 series:**
GT 140, GT 130, GT 120, G 100

**GeForce 100M series:**
GTS 160M, GTS 150M, GT 130M, GT 120M, G 110M, G 105M, G 103M, G 102M

**GeForce 9 series:**
9800  GX2, 9800 GTX+, 9800 GTX/GTX+, 9800 GT, 9650 S, 9600 GT, 9600 GSO 512,  9600 GSO, 9600 GS, 9500 GT, 9500 GS, 9400 GT, 9400, 9300 SE, 9300 GS,  9300 GE, 9300 / nForce 730i, 9300, 9200, 9100

**GeForce 9M series:**
9800M  GTX, 9800M GTS, 9800M GT, 9800M GS, 9700M GTS, 9700M GT, 9650M GT,  9650M GS, 9600M GT, 9600M GS, 9500M GS, 9500M G, 9400M G, 9400M, 9300M  GS, 9300M G, 9200M GS, 9100M G

**GeForce 8 series:**
8800  Ultra, 8800 GTX, 8800 GTS 512, 8800 GTS, 8800 GT, 8800 GS, 8600 GTS,  8600 GS, 8500 GT, 8400 SE, 8400 GS, 8400, 8300 GS, 8300, 8200, 8100 /  nForce 720a

**GeForce 8M series:**
8800M GTX, 8800M GTS, 8700M GT, 8600M GT, 8600M GS, 8400M GT, 8400M GS, 8400M G, 8200M G

**GeForce 7 series:**
7950  GX2, 7950 GT, 7900 GTX, 7900 GT/GTO, 7900 GS, 7800 SLI, 7800 GTX, 7800  GT, 7800 GS, 7650 GS, 7600 LE, 7600 GT, 7600 GS, 7500 LE, 7350 LE, 7300  SE / 7200 GS, 7300 LE, 7300 GT, 7300 GS, 7150M /NVIDIA nForce 630M, 7150  / NVIDIA nForce 630i, 7100 GS, 7100 / NVIDIA nForce 630i, 7050 PV /  NVIDIA nForce 630a, 7050 / NVIDIA nForce 630i, 7050 / nForce 620i, 7025 /  NVIDIA nForce 630a, 7000M /NVIDIA nForce 610M

**GeForce Go 7 series:**
Go 7950 GTX, Go 7900 GS, Go 7800 GTX, Go 7800, Go 7700, Go 7600 GT, Go 7600, Go 7400, Go 7300, Go 7200

**GeForce 6 series:**
6800  XT, 6800 XE, 6800 Ultra, 6800 LE, 6800 GT, 6800 GS, 6800, 6700 XL, 6610  XL, 6600 VE, 6600 LE, 6600 GT, 6600, 6500, 6250, 6200 TurboCache,  6200SE TurboCache, 6200 LE, 6200 A-LE, 6200, 6150SE nForce 430, 6150 LE,  6150, 6100 nForce 420, 6100 nForce 405, 6100 nForce 400, 6100

**NVS Series:**
NVS 300

**Quadro series:**
6000, 600, 5000, 4000, 400, 2000D, 2000

**Quadro FX series:**
FX  Go1400, FX 5800, FX 580, FX 570, FX 5600, FX 560, FX 5500, FX 550, FX  540, FX 4800, FX 4700 X2, FX 4600, FX 4500 X2, FX 4500, FX 4000, FX 380  LP, FX 3800, FX 380, FX 370 Low Profile, FX 3700, FX 370, FX 3500, FX  350, FX 3450/4000 SDI, FX 3400/4400, FX 1800, FX 1700, FX 1500, FX 1400,  CX

**Quadro Notebook series:**
5000M, 2000M, 1000M

**Quadro FX Notebook series:**
FX  880M, FX 770M, FX 570M, FX 560M, FX 540M, FX 380M, FX 3800M, FX 370M,  FX 3700M, FX 360M, FX 3600M, FX 350M, FX 2800M, FX 2700M, FX 2500M, FX  1800M, FX 1700M, FX 1600M, FX 1500M

**Quadro NVS series:**
NVS 450, NVS 440, NVS 420, NVS 295, NVS 290, NVS 285, NVS 210S / 6150LE

**Quadro NVS Notebook series:**
NVS 510M, NVS 4200M, NVS 320M, NVS 160M, NVS 150M, NVS 140M, NVS 135M, NVS 130M, NVS 120M, NVS 110M

**Quadro Plex series:**
Model IV, Model II, D Series, 7000

**Quadro G-Sync series:**
G-Sync II

**Quadro SDI series:**
Quadro SDI

**ION series:**
ION LE, ION

**C-Class Processors:**
Tesla C870, Tesla C2070, Tesla C2050, Tesla C1060, T10 Processor

**M-Class Processors:**
Tesla M2070-Q, Tesla M2070, Tesla M2050, Tesla M1060

[http://www.nvidia.co.uk/object/linux-display-ia32-270.41.19-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-270.41.19-driver-uk.html)

---

### Post by wildmanne39 on 2011-05-31
> **DinoT1985 said:**
> Yep it does along with these :).

**GeForce 500 series:**
GTX 590, GTX 580, GTX 570, GTX 560 Ti, GTX 550 Ti, GT 530, GT 520

**GeForce 500M series:**
GT 555M, GT 550M, GT 540M, GT 525M, GT 520M

**GeForce 400 series:**
GTX 480, GTX 470, GTX 465, GTX 460 SE, GTX 460, GTS 450, GT 440, GT 430, GT 420, 405

**GeForce 400M series:**
GTX 485M, GTX 480M, GTX 470M, GTX 460M, GT 445M, GT 435M, GT 425M, GT 420M, GT 415M

**GeForce 300 series:**
GT 340, GT 330, GT 320, 315, 310

**GeForce 300M series:**
GTS 360M, GTS 350M, GT 335M, GT 330M, GT 325M, GT 320M, 310M, 305M

**GeForce 200 series:**
GTX 295, GTX 285, GTX 280, GTX 275, GTX 260, GTS 250, GTS 240, GT 240, GT 230, GT 220, G210, 205

**GeForce 200M series:**
GTX 285M, GTX 280M, GTX 260M, GTS 260M, GTS 250M, GT 240M, GT 230M, GT 220M, G210M

**GeForce 100 series:**
GT 140, GT 130, GT 120, G 100

**GeForce 100M series:**
GTS 160M, GTS 150M, GT 130M, GT 120M, G 110M, G 105M, G 103M, G 102M

**GeForce 9 series:**
9800  GX2, 9800 GTX+, 9800 GTX/GTX+, 9800 GT, 9650 S, 9600 GT, 9600 GSO 512,  9600 GSO, 9600 GS, 9500 GT, 9500 GS, 9400 GT, 9400, 9300 SE, 9300 GS,  9300 GE, 9300 / nForce 730i, 9300, 9200, 9100

**GeForce 9M series:**
9800M  GTX, 9800M GTS, 9800M GT, 9800M GS, 9700M GTS, 9700M GT, 9650M GT,  9650M GS, 9600M GT, 9600M GS, 9500M GS, 9500M G, 9400M G, 9400M, 9300M  GS, 9300M G, 9200M GS, 9100M G

**GeForce 8 series:**
8800  Ultra, 8800 GTX, 8800 GTS 512, 8800 GTS, 8800 GT, 8800 GS, 8600 GTS,  8600 GS, 8500 GT, 8400 SE, 8400 GS, 8400, 8300 GS, 8300, 8200, 8100 /  nForce 720a

**GeForce 8M series:**
8800M GTX, 8800M GTS, 8700M GT, 8600M GT, 8600M GS, 8400M GT, 8400M GS, 8400M G, 8200M G

**GeForce 7 series:**
7950  GX2, 7950 GT, 7900 GTX, 7900 GT/GTO, 7900 GS, 7800 SLI, 7800 GTX, 7800  GT, 7800 GS, 7650 GS, 7600 LE, 7600 GT, 7600 GS, 7500 LE, 7350 LE, 7300  SE / 7200 GS, 7300 LE, 7300 GT, 7300 GS, 7150M /NVIDIA nForce 630M, 7150  / NVIDIA nForce 630i, 7100 GS, 7100 / NVIDIA nForce 630i, 7050 PV /  NVIDIA nForce 630a, 7050 / NVIDIA nForce 630i, 7050 / nForce 620i, 7025 /  NVIDIA nForce 630a, 7000M /NVIDIA nForce 610M

**GeForce Go 7 series:**
Go 7950 GTX, Go 7900 GS, Go 7800 GTX, Go 7800, Go 7700, Go 7600 GT, Go 7600, Go 7400, Go 7300, Go 7200

**GeForce 6 series:**
6800  XT, 6800 XE, 6800 Ultra, 6800 LE, 6800 GT, 6800 GS, 6800, 6700 XL, 6610  XL, 6600 VE, 6600 LE, 6600 GT, 6600, 6500, 6250, 6200 TurboCache,  6200SE TurboCache, 6200 LE, 6200 A-LE, 6200, 6150SE nForce 430, 6150 LE,  6150, 6100 nForce 420, 6100 nForce 405, 6100 nForce 400, 6100

**NVS Series:**
NVS 300

**Quadro series:**
6000, 600, 5000, 4000, 400, 2000D, 2000

**Quadro FX series:**
FX  Go1400, FX 5800, FX 580, FX 570, FX 5600, FX 560, FX 5500, FX 550, FX  540, FX 4800, FX 4700 X2, FX 4600, FX 4500 X2, FX 4500, FX 4000, FX 380  LP, FX 3800, FX 380, FX 370 Low Profile, FX 3700, FX 370, FX 3500, FX  350, FX 3450/4000 SDI, FX 3400/4400, FX 1800, FX 1700, FX 1500, FX 1400,  CX

**Quadro Notebook series:**
5000M, 2000M, 1000M

**Quadro FX Notebook series:**
FX  880M, FX 770M, FX 570M, FX 560M, FX 540M, FX 380M, FX 3800M, FX 370M,  FX 3700M, FX 360M, FX 3600M, FX 350M, FX 2800M, FX 2700M, FX 2500M, FX  1800M, FX 1700M, FX 1600M, FX 1500M

**Quadro NVS series:**
NVS 450, NVS 440, NVS 420, NVS 295, NVS 290, NVS 285, NVS 210S / 6150LE

**Quadro NVS Notebook series:**
NVS 510M, NVS 4200M, NVS 320M, NVS 160M, NVS 150M, NVS 140M, NVS 135M, NVS 130M, NVS 120M, NVS 110M

**Quadro Plex series:**
Model IV, Model II, D Series, 7000

**Quadro G-Sync series:**
G-Sync II

**Quadro SDI series:**
Quadro SDI

**ION series:**
ION LE, ION

**C-Class Processors:**
Tesla C870, Tesla C2070, Tesla C2050, Tesla C1060, T10 Processor

**M-Class Processors:**
Tesla M2070-Q, Tesla M2070, Tesla M2050, Tesla M1060

[http://www.nvidia.co.uk/object/linux-display-ia32-270.41.19-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-270.41.19-driver-uk.html)
Hi, thank you I will give it a try.:D

---

### Post by ratcheer on 2011-05-31
Damn! I installed this new driver and, for some reason, my window decorations went all goofy. This is on a Natty system that I just fresh installed, Saturday!

Tim

---

### Post by DinoT1985 on 2011-05-31
> **ratcheer said:**
> Damn! I installed this new driver and, for some reason, my window decorations went all goofy. This is on a Natty system that I just fresh installed, Saturday!

Tim

Have you tried another theme to test? i'll see if theres a bug reported.

edit: no bugs matching. have you tried checking Compiz?

---

### Post by ratcheer on 2011-05-31
> **DinoT1985 said:**
> Have you tried another theme to test? i'll see if theres a bug reported.

edit: no bugs matching. have you tried checking Compiz?

Yes, I did try changing the theme, but I saw no difference. I will try a more different theme and report back.

What should I check in Compiz (and how)?

Thanks,
Tim

---

### Post by ratcheer on 2011-05-31
Changing themes does change the colors and some of the window borders and controls, but otherwise the main top bar and the buttons and stuff within application windows still have that vintage Windows NT look. :(

Tim

---

### Post by ratcheer on 2011-05-31
I installed compizconfig-settings-manager. I looked at it but did not change anything. There are so many things in it I don't know which way is up! It doesnt even fit on one page, and each selection may have several tabs of different things it controls.

PS - I think I should open a new thread for this problem. I don't need to be messing up this thread. Thanks.

Tim

---

### Post by 3Miro on 2011-05-31
> **ratcheer said:**
> Changing themes does change the colors and some of the window borders and controls, but otherwise the main top bar and the buttons and stuff within application windows still have that vintage Windows NT look. :(

Tim

What you see is the default Raleigh theme for GTK. It is the fallback if all else fails.

To make a note: the latest **official stable** NVIDIA driver is the one in the repository (you install it with Additional Drivers and update it with the Update Manager). Nvidia may have released a new driver for Linux, but it is not **stable** for Ubuntu. Unofficial ppa drivers should be considered beta (although they can indeed fix important issues). Unless you had an issue with the official stable driver, you should just remove the driver, reboot, remove the ppa and reinstall the **official stable** driver.

---

### Post by ratcheer on 2011-05-31
Thanks, 3Miro. I will try that. I have always had very good luck with the drivers from x-swat PPA, before.

Tim

---

### Post by 3Miro on 2011-05-31
> **ratcheer said:**
> Thanks, 3Miro. I will try that. I have always had very good luck with the drivers from x-swat PPA, before.

Tim

When drivers are released from Nvidia, they usually work, however, the Linux community is so diverse that there is never any guarantees. Sometimes the driver would conflict with something specific to one distro or another and the developers of of that distribution would have to do some work before the driver is called **officially** stable for that distro.

---

### Post by ratcheer on 2011-05-31
> **3Miro said:**
> ...

 Unless you had an issue with the official stable driver, you should just remove the driver, reboot, remove the ppa and reinstall the **official stable** driver.

Indeed, that fixed it. You are wiser than I. Thank you very much.

Tim

---

### Post by DinoT1985 on 2011-05-31
> **3Miro said:**
> When drivers are released from Nvidia, they usually work, however, the Linux community is so diverse that there is never any guarantees. Sometimes the driver would conflict with something specific to one distro or another and the developers of of that distribution would have to do some work before the driver is called **officially** stable for that distro.

To me official means made by the manufacturer that created the card. That is why the title is that. My apologies for any confusion.

---

### Post by DinoT1985 on 2011-06-03
> **ratcheer said:**
> Changing themes does change the colors and some of the window borders and controls, but otherwise the main top bar and the buttons and stuff within application windows still have that vintage Windows NT look. :(

Tim

to touch upon this, answer to correcting this was posted on WebUp8

[http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)

So it also happens in the drivers already in Ubuntu.

---

### Post by bjones1982 on 2011-06-07
Just installed a fresh Ubuntu 11.04 desktop and tried to update my drivers according to the instructions in this thread using :

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

However the driver version did not change.  Still says version 173.14.30 after reboot.  There were no errors when I ran the sudo commands.  So instead I went into "Additional Drivers" and it allowed me to download and install the latest "recommended" drivers with a few mouse clicks.  Now my drivers are updated.  Just wanted to share my experience in case anyone has this same issue.

---

### Post by wildmanne39 on 2011-06-07
> **bjones1982 said:**
> Just installed a fresh Ubuntu 11.04 desktop and tried to update my drivers according to the instructions in this thread using :

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

However the driver version did not change.  Still says version 173.14.30 after reboot.  There were no errors when I ran the sudo commands.  So instead I went into "Additional Drivers" and it allowed me to download and install the latest "recommended" drivers with a few mouse clicks.  Now my drivers are updated.  Just wanted to share my experience in case anyone has this same issue.
HI, you are better off sticking with the 173 driver,I update mine last week and I had to take it right back of it caused a lot of problems, like white windows, and I am using the cube it made my system lag.

---

### Post by Aashiq on 2011-06-07
I'm guessing this doesn't work for GeForce 4 MX 420?

What could I use for that? Computer has really been acting up lately...

---

### Post by pqwoerituytrueiwoq on 2011-06-07
How would i remove the one i installed via Nvidia's installer (the .run file)?
should i just install the ppa one after the next kernel update?

---

### Post by emarkay on 2011-06-07
What about for the 10.04 LTS folks - those who want to stick with what works well, but have always updated their Graphics drivers (as we learned in the Win 3.1 over DOS days..)  :)

---

### Post by DinoT1985 on 2011-06-07
> **bjones1982 said:**
> Just installed a fresh Ubuntu 11.04 desktop and tried to update my drivers according to the instructions in this thread using :

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

However the driver version did not change.  Still says version 173.14.30 after reboot.  There were no errors when I ran the sudo commands.  So instead I went into "Additional Drivers" and it allowed me to download and install the latest "recommended" drivers with a few mouse clicks.  Now my drivers are updated.  Just wanted to share my experience in case anyone has this same issue.

How is the driver working for you?
> **pqwoerituytrueiwoq said:**
> How would i remove the one i installed via Nvidia's installer (the .run file)?
should i just install the ppa one after the next kernel update?

I'm not sure on this. Could you disable it from Additional Drivers and then update at next kernel?

---

### Post by pqwoerituytrueiwoq on 2011-06-07
> **DinoT1985 said:**
> I'm not sure on this. Could you disable it from Additional Drivers and then update at next kernel?
it is empty
the run files bypasses the package manager
edit found something:
sudo nvidia-installer --uninstall

---

### Post by DinoT1985 on 2011-06-07
> **Aashiq said:**
> I'm guessing this doesn't work for GeForce 4 MX 420?

What could I use for that? Computer has really been acting up lately...

Stick with the prop. drivers. The last NVIDIA driver by the company that supports your card is 96.43.19.

[http://www.nvidia.co.uk/object/linux-display-amd64-96.43.19-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-amd64-96.43.19-driver-uk.html)

> **emarkay said:**
> What about for the 10.04 LTS folks - those who want to stick with what works well, but have always updated their Graphics drivers (as we learned in the Win 3.1 over DOS days..)  :)

The info on the driver over at the NVIDIA site doesn't specify an OS version, just says Linux. Could give it a try and disable if the system is slower.

---

### Post by DinoT1985 on 2011-06-07
> **pqwoerituytrueiwoq said:**
> it is empty

See if this helps

[http://us.download.nvidia.com/XFree86/Linux-x86_64/270.41.06/README/installdriver.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/270.41.06/README/installdriver.html)

> nvidia-installer will also install itself to /usr/bin/nvidia-installer, which may be used at some later time to uninstall drivers, auto-download updated drivers, etc. The use of this utility is detailed later in this chapter.

---

### Post by pqwoerituytrueiwoq on 2011-06-07
it gave me 270.29 instead of 270.41.19 running 10.04
Nvidia GeForce GT 430 (Fermi)

---

### Post by airspoon on 2011-06-07
I was so excited to see that an update to the nvidia driver was available, as I am having the problem that many people are having, ("the driver is activated but not currently in use"). So, I installed it right away, then rebooted.

After trying to log in to Unity (Ubuntu) instead of Gnome Classic, it didn't work. However, unlike before this driver update, I got a message saying that my hardware isn't capable of running Unity and it logged me into Gnome Classic (which was better than what it did before). Before this driver update, when I would try to login to Unity, it would just freeze on the purple screen.

So I do see a difference, however this driver didn't seem to alleviate my problem. Is there anyway that I can fix this? While I don't really care that much about Unity (haven't used it), I do want to run 3d effects (such as AWN).

Could it really be true that my nvidia graphics card isn't capable of handling 3d effects or Unity? MY Ubuntu computer has a GeForce FX 5200.

Thanks!

---

### Post by pqwoerituytrueiwoq on 2011-06-07
> **airspoon said:**
> I was so excited to see that an update to the nvidia driver was available, as I am having the problem that many people are having, ("the driver is activated but not currently in use"). So, I installed it right away, then rebooted.

After trying to log in to Unity (Ubuntu) instead of Gnome Classic, it didn't work. However, unlike before this driver update, I got a message saying that my hardware isn't capable of running Unity and it logged me into Gnome Classic (which was better than what it did before). Before this driver update, when I would try to login to Unity, it would just freeze on the purple screen.

So I do see a difference, however this driver didn't seem to alleviate my problem. Is there anyway that I can fix this? While I don't really care that much about Unity (haven't used it), I do want to run 3d effects (such as AWN).

Could it really be true that my nvidia graphics card isn't capable of handling 3d effects or Unity? MY Ubuntu computer has a GeForce FX 5200.

Thanks!
i doubt a opengl 2 128 mb video card will be able to run unity

---

### Post by airspoon on 2011-06-07
Thanks, but when I go to "additional drivers", I'm still getting the:
```
This driver activated, but not currently in use
```

However, this time, I saw more options. "Nvidia 173 [Recommended]", "Nvidia current version" and "Nvidia experimental". I was originally having the issue with the nvidia 173 and after updating the driver, I noticed that 173 was still highlighted in the "additional drivers". So, I activated the "nvidia current" and rebooted. Same problem and in fact, I'm still getting the message that "the driver is activated, but not currently in use", which is what I thought the problem was to begin with, pre-update.

This leads me to believe that the problem isn't with my graphics card, so much as it is with either the driver, or Ubuntu itself. Even if my graphics card can't use Unity (which would be a surprise, considering it handles 3d effects in other, more clunky operating systems), then it should be able to handle the 3d effects with Gnome-Classic, right? Yet, I'm getting the message that "the driver is activated, but not currently in use".

This problem, although it doesn't effect me in any debilitating way, is frustrating and a pain in the butt.

---

### Post by DinoT1985 on 2011-06-07
> **airspoon said:**
> Thanks, but when I go to "additional drivers", I'm still getting the:
```
This driver activated, but not currently in use
```However, this time, I saw more options. "Nvidia 173 [Recommended]", "Nvidia current version" and "Nvidia experimental". I was originally having the issue with the nvidia 173 and after updating the driver, I noticed that 173 was still highlighted in the "additional drivers". So, I activated the "nvidia current" and rebooted. Same problem and in fact, I'm still getting the message that "the driver is activated, but not currently in use", which is what I thought the problem was to begin with, pre-update.

This leads me to believe that the problem isn't with my graphics card, so much as it is with either the driver, or Ubuntu itself. Even if my graphics card can't use Unity (which would be a surprise, considering it handles 3d effects in other, more clunky operating systems), then it should be able to handle the 3d effects with Gnome-Classic, right? Yet, I'm getting the message that "the driver is activated, but not currently in use".

This problem, although it doesn't effect me in any debilitating way, is frustrating and a pain in the butt.
Thats infact a bug thats been reported many times. If you can see Unity and your NVIDIA X Server settings then its installed.

edit: sorry just read your previous post. hmm.. anyone have this before?

---

### Post by airspoon on 2011-06-07
You mean Gnome? I can't see Unity, though I can see Nvidia X-Server settings. I have been reading about that bug ever since installing Ubuntu, though I was under the impression that this latest driver update would fix the issue. Is it not a problem with the driver, so much as it is with Ubuntu or the X-Windowing? Thanks.

---

### Post by DinoT1985 on 2011-06-07
> **airspoon said:**
> You mean Gnome? I can't see Unity, though I can see Nvidia X-Server settings. I have been reading about that bug ever since installing Ubuntu, though I was under the impression that this latest driver update would fix the issue. Is it not a problem with the driver, so much as it is with Ubuntu or the X-Windowing? Thanks.
im not sure if its more an Ubuntu bug or not.

---

### Post by wildmanne39 on 2011-06-07
> **airspoon said:**
> I was so excited to see that an update to the nvidia driver was available, as I am having the problem that many people are having, ("the driver is activated but not currently in use"). So, I installed it right away, then rebooted.

After trying to log in to Unity (Ubuntu) instead of Gnome Classic, it didn't work. However, unlike before this driver update, I got a message saying that my hardware isn't capable of running Unity and it logged me into Gnome Classic (which was better than what it did before). Before this driver update, when I would try to login to Unity, it would just freeze on the purple screen.

So I do see a difference, however this driver didn't seem to alleviate my problem. Is there anyway that I can fix this? While I don't really care that much about Unity (haven't used it), I do want to run 3d effects (such as AWN).

Could it really be true that my nvidia graphics card isn't capable of handling 3d effects or Unity? MY Ubuntu computer has a GeForce FX 5200.

Thanks!Hi, it saying that your driver is not in use is a bug it really is, the proof is that you could see the unity desktop. There is no reason to worry about it saying not in use.

---

### Post by airspoon on 2011-06-07
But I can't see the Unity desktop, that's the thing. Are you saying that the bug is only that it gives that message and doesn't affect anything? I'm just assuming that since I'm getting this message and since I can't seem to get 3d effects or Unity to work, that the two are related. 

Also, now when I try to bring up the Nvidia X-Server settings, it kicks back an error message saying:
```

You do not appear to be using the Nvidia X driver. 
Please edit your X configuration file (just run 'invidia x-config'  as root

```

---

### Post by DinoT1985 on 2011-06-07
see this thread
[http://ubuntuforums.org/showthread.php?t=1743319](http://ubuntuforums.org/showthread.php?t=1743319)
and other option
[http://askubuntu.com/questions/45978/unity-with-geforce-fx-5200](http://askubuntu.com/questions/45978/unity-with-geforce-fx-5200)

---

### Post by jwcalla on 2011-06-07
Does anyone know if the x-swat peeps won't be supporting 10.10 releases any more?  The driver's been out for awhile now and the PPA hasn't been updated for maverick?

---

### Post by mafaldaspeaks on 2011-06-07
> **DinoT1985 said:**
> This fixed my ugly Plymouth splash.

To install nVIDIA Display Driver release 270.41.19 in Ubuntu 11.04 Natty or 11.10 Oneiric, open Terminal and run :[INDENT]```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```[/INDENT]After the installation restart the system to enable the driver.
I have Nvidia GeForce 9300m GS 512mb in my Dell Inspiron laptop.

I did the above commands and restarted. I just want to ask why, when I checked "Additional Drivers" and highlighted the "Nvidia accelerated graphics driver (current version) (recommended)", it says below "Activated but not currently in use". Sorry if this sounds ignorant, but why does it say "not in use"? Isn't the graphics card always in use when the laptop is on?

I attached a screenshot of the message window.

---

### Post by wildmanne39 on 2011-06-07
> **airspoon said:**
> But I can't see the Unity desktop, that's the thing. Are you saying that the bug is only that it gives that message and doesn't affect anything? I'm just assuming that since I'm getting this message and since I can't seem to get 3d effects or Unity to work, that the two are related. 

Also, now when I try to bring up the Nvidia X-Server settings, it kicks back an error message saying:
```

You do not appear to be using the Nvidia X driver. 
Please edit your X configuration file (just run 'invidia x-config'  as root

```Hi, I have been using natty since beta and my driver show's that it is active also and not in use but I have the unity desktop and I am running the cube with many 3d effects. If you have had more then one nvidia driver activate or installed through synaptic or nvidia website then you may have 2 active at the same time, when I tried the latest driver for the second time it left my old driver active and in synaptic I had to uninstall the new one. you can also do 
```
sudo apt-get --purge remove package name[CODE] to get rid of the one you do not want, it will only show one active in additional drivers. If I was not having problems and looked in synaptic I would never had know there were two in use. Also run this command and post back here
[CODE]/usr/lib/nux/unity_support_test -p
```

---

### Post by airspoon on 2011-06-08
Okay, thanks for helping. The results of the unity support test is as follows:
```

dell:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context

```

--Doesn't look too good, lol.

I checked in Synaptic, doing a search for nvidia and I'm now seeing that there is an exclamation point next to the "nvidia settings" (270.29-0ubuntu1 -Tool for configuring the Nvidia graphics driver).

With that being said, I had originally the nvidia 173 driver installed and when I would try to login to the "Ubuntu" (Unity, right?) as opposed to "Ubuntu Classic" (Gnome), my computer would just freeze on the purple screen. I wouldn't get any warnings or dialogs, rather just an occasionally blinking purple screen.

So, when I saw that there was a new driver, I installed it from the terminal, then rebooted. When I went to "additional drivers", I saw that nvidia 173 was still the driver activated, so I activated the "nvidia current", which apparently deactivated the nvidia 173.

However, now it appears as if I broke something, as the Nvidia X-Server settings won't work, citing the lack of an nvidia driver.

Going back to Synaptic, I see both drivers highlighted, though just because they are installed, thus highlighted, doesn't mean that both are activated, right? Additional drivers shows only the new driver as activated (though apparently not in use).

Also, even with the new driver (nvidia current) installed and activated (though not in use), "additional drivers" has a [RECOMMENDED] next to the nvidia 173. Should I re-activate 173, seeing how Ubuntu is recommending it?

Regardless, neither driver seems to allow me to use Unity, or 3d effects on the desktop. Right now however, it appears as if Ubuntu isn't reading any accelerated graphics driver.

I have no idea what to do at this point. Did I install or activate the wrong driver, (considering that Ubuntu is "recommending" the 173)?

---

### Post by wildmanne39 on 2011-06-08
> **airspoon said:**
> Okay, thanks for helping. The results of the unity support test is as follows:
```

dell:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context

```

--Doesn't look too good, lol.

I checked in Synaptic, doing a search for nvidia and I'm now seeing that there is an exclamation point next to the "nvidia settings" (270.29-0ubuntu1 -Tool for configuring the Nvidia graphics driver).

With that being said, I had originally the nvidia 173 driver installed and when I would try to login to the "Ubuntu" (Unity, right?) as opposed to "Ubuntu Classic" (Gnome), my computer would just freeze on the purple screen. I wouldn't get any warnings or dialogs, rather just an occasionally blinking purple screen.

So, when I saw that there was a new driver, I installed it from the terminal, then rebooted. When I went to "additional drivers", I saw that nvidia 173 was still the driver activated, so I activated the "nvidia current", which apparently deactivated the nvidia 173.

However, now it appears as if I broke something, as the Nvidia X-Server settings won't work, citing the lack of an nvidia driver.

Going back to Synaptic, I see both drivers highlighted, though just because they are installed, thus highlighted, doesn't mean that both are activated, right? Additional drivers shows only the new driver as activated (though apparently not in use).

Also, even with the new driver (nvidia current) installed and activated (though not in use), "additional drivers" has a [RECOMMENDED] next to the nvidia 173. Should I re-activate 173, seeing how Ubuntu is recommending it?

Regardless, neither driver seems to allow me to use Unity, or 3d effects on the desktop. Right now however, it appears as if Ubuntu isn't reading any accelerated graphics driver.

I have no idea what to do at this point. Did I install or activate the wrong driver, (considering that Ubuntu is "recommending" the 173)?Hi, right now with both showing installed in synaptic you need to uninstall one of them. I use the 173 but if your are sure that the 173 gave you the purple screen then maybe you should use the other one, but not both and it will only show one active in additional drivers even though they are both in use because they are both installed in synaptic. Also reinstall this before reinstalling the nvidia driver."nvidia settings" (270.29-0ubuntu1 -Tool for configuring the Nvidia graphics driver
and then run the test command for unity again.

---

### Post by DinoT1985 on 2011-06-08
> **mafaldaspeaks said:**
> I have Nvidia GeForce 9300m GS 512mb in my Dell Inspiron laptop.

I did the above commands and restarted. I just want to ask why, when I checked "Additional Drivers" and highlighted the "Nvidia accelerated graphics driver (current version) (recommended)", it says below "Activated but not currently in use". Sorry if this sounds ignorant, but why does it say "not in use"? Isn't the graphics card always in use when the laptop is on?

I attached a screenshot of the message window.
It is in use if you can see Unity. It's a known bug and mentioned earlier in the thread.

---

### Post by mafaldaspeaks on 2011-06-10
> **DinoT1985 said:**
> It is in use if you can see Unity. It's a known bug and mentioned earlier in the thread.
Oh so it's a bug. Thanks for the info!

---

### Post by rickwright on 2011-07-09
> **DinoT1985 said:**
> Yep it does along with these :).

**GeForce 500 series:**
GTX 590, GTX 580, GTX 570, GTX 560 Ti, GTX 550 Ti, GT 530, GT 520

**GeForce 500M series:**
GT 555M, GT 550M, GT 540M, GT 525M, GT 520M

**GeForce 400 series:**
GTX 480, GTX 470, GTX 465, GTX 460 SE, GTX 460, GTS 450, GT 440, GT 430, GT 420, 405

**GeForce 400M series:**
GTX 485M, GTX 480M, GTX 470M, GTX 460M, GT 445M, GT 435M, GT 425M, GT 420M, GT 415M

**GeForce 300 series:**
GT 340, GT 330, GT 320, 315, 310

**GeForce 300M series:**
GTS 360M, GTS 350M, GT 335M, GT 330M, GT 325M, GT 320M, 310M, 305M

**GeForce 200 series:**
GTX 295, GTX 285, GTX 280, GTX 275, GTX 260, GTS 250, GTS 240, GT 240, GT 230, GT 220, G210, 205

**GeForce 200M series:**
GTX 285M, GTX 280M, GTX 260M, GTS 260M, GTS 250M, GT 240M, GT 230M, GT 220M, G210M

**GeForce 100 series:**
GT 140, GT 130, GT 120, G 100

**GeForce 100M series:**
GTS 160M, GTS 150M, GT 130M, GT 120M, G 110M, G 105M, G 103M, G 102M

**GeForce 9 series:**
9800  GX2, 9800 GTX+, 9800 GTX/GTX+, 9800 GT, 9650 S, 9600 GT, 9600 GSO 512,  9600 GSO, 9600 GS, 9500 GT, 9500 GS, 9400 GT, 9400, 9300 SE, 9300 GS,  9300 GE, 9300 / nForce 730i, 9300, 9200, 9100

**GeForce 9M series:**
9800M  GTX, 9800M GTS, 9800M GT, 9800M GS, 9700M GTS, 9700M GT, 9650M GT,  9650M GS, 9600M GT, 9600M GS, 9500M GS, 9500M G, 9400M G, 9400M, 9300M  GS, 9300M G, 9200M GS, 9100M G

**GeForce 8 series:**
8800  Ultra, 8800 GTX, 8800 GTS 512, 8800 GTS, 8800 GT, 8800 GS, 8600 GTS,  8600 GS, 8500 GT, 8400 SE, 8400 GS, 8400, 8300 GS, 8300, 8200, 8100 /  nForce 720a

**GeForce 8M series:**
8800M GTX, 8800M GTS, 8700M GT, 8600M GT, 8600M GS, 8400M GT, 8400M GS, 8400M G, 8200M G

**GeForce 7 series:**
7950  GX2, 7950 GT, 7900 GTX, 7900 GT/GTO, 7900 GS, 7800 SLI, 7800 GTX, 7800  GT, 7800 GS, 7650 GS, 7600 LE, 7600 GT, 7600 GS, 7500 LE, 7350 LE, 7300  SE / 7200 GS, 7300 LE, 7300 GT, 7300 GS, 7150M /NVIDIA nForce 630M, 7150  / NVIDIA nForce 630i, 7100 GS, 7100 / NVIDIA nForce 630i, 7050 PV /  NVIDIA nForce 630a, 7050 / NVIDIA nForce 630i, 7050 / nForce 620i, 7025 /  NVIDIA nForce 630a, 7000M /NVIDIA nForce 610M

**GeForce Go 7 series:**
Go 7950 GTX, Go 7900 GS, Go 7800 GTX, Go 7800, Go 7700, Go 7600 GT, Go 7600, Go 7400, Go 7300, Go 7200

**GeForce 6 series:**
6800  XT, 6800 XE, 6800 Ultra, 6800 LE, 6800 GT, 6800 GS, 6800, 6700 XL, 6610  XL, 6600 VE, 6600 LE, 6600 GT, 6600, 6500, 6250, 6200 TurboCache,  6200SE TurboCache, 6200 LE, 6200 A-LE, 6200, 6150SE nForce 430, 6150 LE,  6150, 6100 nForce 420, 6100 nForce 405, 6100 nForce 400, 6100

**NVS Series:**
NVS 300

**Quadro series:**
6000, 600, 5000, 4000, 400, 2000D, 2000

**Quadro FX series:**
FX  Go1400, FX 5800, FX 580, FX 570, FX 5600, FX 560, FX 5500, FX 550, FX  540, FX 4800, FX 4700 X2, FX 4600, FX 4500 X2, FX 4500, FX 4000, FX 380  LP, FX 3800, FX 380, FX 370 Low Profile, FX 3700, FX 370, FX 3500, FX  350, FX 3450/4000 SDI, FX 3400/4400, FX 1800, FX 1700, FX 1500, FX 1400,  CX

**Quadro Notebook series:**
5000M, 2000M, 1000M

**Quadro FX Notebook series:**
FX  880M, FX 770M, FX 570M, FX 560M, FX 540M, FX 380M, FX 3800M, FX 370M,  FX 3700M, FX 360M, FX 3600M, FX 350M, FX 2800M, FX 2700M, FX 2500M, FX  1800M, FX 1700M, FX 1600M, FX 1500M

**Quadro NVS series:**
NVS 450, NVS 440, NVS 420, NVS 295, NVS 290, NVS 285, NVS 210S / 6150LE

**Quadro NVS Notebook series:**
NVS 510M, NVS 4200M, NVS 320M, NVS 160M, NVS 150M, NVS 140M, NVS 135M, NVS 130M, NVS 120M, NVS 110M

**Quadro Plex series:**
Model IV, Model II, D Series, 7000

**Quadro G-Sync series:**
G-Sync II

**Quadro SDI series:**
Quadro SDI

**ION series:**
ION LE, ION

**C-Class Processors:**
Tesla C870, Tesla C2070, Tesla C2050, Tesla C1060, T10 Processor

**M-Class Processors:**
Tesla M2070-Q, Tesla M2070, Tesla M2050, Tesla M1060

[http://www.nvidia.co.uk/object/linux-display-ia32-270.41.19-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-270.41.19-driver-uk.html)


[SIZE=4]hahaha as if it was true!!!![/SIZE]

Still waiting for a 520M driver tthat works....

---

### Post by randurk on 2012-03-17
> **DinoT1985 said:**
> This fixed my ugly Plymouth splash.

To install nVIDIA Display Driver release 270.41.19 in Ubuntu 11.04 Natty or 11.10 Oneiric, open Terminal and run :[INDENT]```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current
```[/INDENT]After the installation restart the system to enable the driver.


It work ,thank you.

---

### Post by Plaguelock on 2012-03-21
I have a Zotac nvidia ION GT218 that I just installed and Ubuntu 11.10 keeps hanging when I get to the sign in screen. I was able to use the onboard video to add the repository and install the latest yesterday, but I can't get the PC to stop hanging when I go back to new card.:confused:

---

### Post by anson123 on 2012-04-29
I have a similar issue with the Nvidia drivers locking up my system.  Using the default video drivers, my system works fine.  But when I install the additional Nvidia drivers to be able to play games, my system will lock up around 1 minute after i login.  This happens when i try both Ubuntu versions 11.10 and 12.04.  Previously when I had Ubuntu 11.04, I didn't have this problem.  Maybe I need to try older drivers and see what happens...

I have the Nvidia 9800M GTS video card.

---

### Post by vintermann on 2012-08-26
I have a Nvidia GTX 285M, and I have trouble with sporadic crashes. I added this PPA for the latest drivers, and it says they are installed (304), but when I run opengl benchmarks I get like 50 fps (vs. 800 for the one provided by default in "additional drivesr", the one that crashes).

Anyone have any idea why the PPA driver doesn't seem to help with openGL?

---

### Post by jwcalla on 2012-08-26
> **vintermann said:**
> I have a Nvidia GTX 285M, and I have trouble with sporadic crashes. I added this PPA for the latest drivers, and it says they are installed (304), but when I run opengl benchmarks I get like 50 fps (vs. 800 for the one provided by default in "additional drivesr", the one that crashes).

Anyone have any idea why the PPA driver doesn't seem to help with openGL?

There was a change with the 300 series.  Sync-to-vblank is now enabled by default, so some benchmarks might be capped to the refresh rate.

You can disable sync-to-vblank in the nvidia-settings program.

---

### Post by ammofreak on 2012-09-11
Hi ):P:
Thanks for the info. Unfortunately, this repository does not contain the current nvidia drivers. One still has to manually install the newest drivers available. And, of course, as soon as the kernel is updated, one has to re-install the nvidia drivers again. Is there a work-around for this?;)

Ohoh: repository was disabled!!! Indeed, new driver, 304.43 was there. Looking at the install though, I believe the driver is for laptops. Here is the part that is interesting:

Setting up nvidia-current (304.43-0ubuntu1~precise~xup1) ...
INFO:Enable nvidia-current
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Processing quirk ThinkPad T420s
DEBUG:Failure to match Dell Inc. with LENOVO
DEBUG:Quirk doesn't match
DEBUG:Processing quirk Latitude E6530
DEBUG:Failure to match Dimension 8400 with Latitude E6530
DEBUG:Quirk doesn't match
Loading new nvidia-current-304.43 DKMS files...
Building only for 3.2.0-30-generic

Ends up building a generic driver. Can someone clarify?

---

### Post by jwcalla on 2012-09-11
> **ammofreak said:**
> 
Ohoh: repository was disabled!!! Indeed, new driver, 304.43 was there. Looking at the install though, I believe the driver is for laptops. Here is the part that is interesting:

Loading new nvidia-current-304.43 DKMS files...
Building only for 3.2.0-30-generic

Ends up building a generic driver. Can someone clarify?

NVIDIA has only one driver for all GPUs (except legacy GPUs which use previous driver versions).  They don't distinguish between laptops, desktops and workstations.

You can ignore the warnings about the quirks.

The "generic" is Ubuntu's choice of Linux kernel flavor, and the NVIDIA driver is built for that.

So yes, all you need is the x-swat repository, and any kernel or video driver updates that are hereafter pushed out will be installed and configured automatically.

---

### Post by diwanescu on 2012-11-09
Got a Quadro FX 570M in a Lenovo T61p (2GB RAM) with docking station and dual-monitor set-up on 12.04 -  setup working with nvidia driver version 173 but have annoying stuttering and slaggy performance.

any suggestions out there what nvidia driver version to use to get rid of this? Does the latest official stable version resolve?

---

### Post by jwcalla on 2012-11-09
Don't use version 173, that's ancient.  Use version-current.

---

### Post by bogan on 2012-11-10
Hi!, **diwanescu**,

** jwcalla** Posted:> Don't use version 173, that's ancient.  Use version-current. Provided the version you have is 173.14-36, it is not ancient at all; it is dated 4 Oct 2012 and is updated for the latest Xorg-server.

It is the correct driver for your card.

None the less, for the  Quadro FX 570M, Nvidia also recommend the 304.51 and 304.64, the first of which should be available for 12.04 from the x-swat ppa, if not from Additional Drivers or Synaptic.

The  Quadro FX 570M is listed as a supported product for the 304.51.

Edit: I just checked Synaptic in my 12.04, and 304.51 is listed as 'nvidia-current', if you install it, you should also get 'nvidia-settings', it is also v304.51.

It is also advisable to purge the old driver and remove or rename the Xorg.conf file.

Chao!, **bogan**.

---

### Post by COMECON on 2012-11-10
> **diwanescu said:**
> Got a Quadro FX 570M in a Lenovo T61p (2GB RAM) with docking station and dual-monitor set-up on 12.04 -  setup working with nvidia driver version 173 but have annoying stuttering and slaggy performance.

any suggestions out there what nvidia driver version to use to get rid of this? Does the latest official stable version resolve?

You could use **nvidia-current-updates**, which theoretically, will always be the lastest updated driver (at the moment it's 304.x, but it's not updated to 304.64 yet). **nvidia-current **is the lastest driver **at the moment of freeze the development**, that's it, the newest driver available when your Ubuntu version was released. There are also some experimental drivers, but I don't recommend you to enable them as they shouldn't be much stable.
I've been using nvidia-current-updates and never got a problem (assuming my poor GC performance), but today I've updated to 304.64 adding the **ubuntu-x-swat/x-updates **PPA and installing its *nvidia-current*.
TL;DR - I recommend you **nvidia-current-updates**

---

### Post by bogan on 2012-11-15
Hi!, **All,**

 RE:** Warning**! Nvidia beta driver 310 does not support 6xxx series cards, and Nvidia warns it may ignore 7xxx series GPU's.

The same, presumably, applies to the **Additional Drivers 'nvidia-experimental-310' **driver, as well.

I have been running, successfully, the 310.14 driver, with 12.10  Quantal, on an 8GB USB SanDisk, in a computer with a GeForce GT 520  card. That is an nvidia.com downloaded '.run' file.

I transferred the USB to a computer with a GT 7650 card and its graphics  were a total shambles, with a GUI in a very low-res with huge  characters & Mouse cursor, but no launcher or tool bar panel.[  Nouveau was blacklisted.]

When I ran:```
NVIDIA-Linux-x86-310.14.run --latest
``` it listed  310.14 as installed, and 310.16 as the latest available. { Incidently,  310.16 is not listed as an available Beta driver on the nvidia website,  though the whole 7xxx series is listed as supported by 310.14 beta, but  not the 6xxx series}.

However, when I tried to reinstall 310.14, I got a message saying no  graphics card had been detected that was supported by 310.14, and if  installed it would ignore my GPU; ie. the GT 7650. It recommended I  install 304.60.

So if you have a 6000 or 7000 series video card watch out.

Chao!,** bogan**.

---

### Post by juanbuntu on 2013-05-23
What is the most recent nVidia Driver? I have a **[COLOR=#000000][FONT=Calibri]Video Card: [/FONT][/COLOR][COLOR=#000000][FONT=Calibri][B]EVGA 01G-P3-1556-KR**[/FONT][/COLOR][COLOR=#000000][FONT=Calibri] GeForce GTX 550  running on ASUS MOBO with AMD FX-6100 six-core CPU.
[/FONT][/COLOR][/B]The nVidia driver I have is version 280.13. Is there a more recent driver?

---

### Post by deadflowr on 2013-05-23
> **juanbuntu said:**
> What is the most recent nVidia Driver? I have a **[COLOR=#000000][FONT=Calibri]Video Card: [/FONT][/COLOR][COLOR=#000000][FONT=Calibri][B]EVGA 01G-P3-1556-KR**[/FONT][/COLOR][COLOR=#000000][FONT=Calibri] GeForce GTX 550  running on ASUS MOBO with AMD FX-6100 six-core CPU.
[/FONT][/COLOR][/B]The nVidia driver I have is version 280.13. Is there a more recent driver?

I think the latest is 313.XXX, but I think the latest provided through Ubuntu is 310.XXX.
Depending on which version of Ubuntu you're running, it could be labelled either nvidia-310 or nvidia-experimental-310.
I forget what I'm running on my raring build, but running precise I'm using nvidia-current-updates which is 304.88.

---

