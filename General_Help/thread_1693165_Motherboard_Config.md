---
title: "Motherboard Config"
date: 2011-02-22
forum: General Help
---

### Post by Julian Luna on 2011-02-22
Hello all
Still need to properly configure my motherboard I believe, specially my graphic card driver because if I try to play quadrapassel it actually looks awfull. If I open tibia which is a really basic graphics game; It looks awfuller than awfull. So I believe it's not wine's graphic drivers (If ever existed) but I think it's my graphic generic drivers, I googled how to know which graphic card I have since I don't remember and i'll paste you something:

julian@julian-A780GM-A:~$ sudo lspci |more
[sudo] password for julian: 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gf
x)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE p
ort 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI 
mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTran
sport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address M
ap
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Cont
roller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellan
eous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Cont
rol[COLOR=Red]
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics[/COLOR]
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI E
xpress Gigabit Ethernet controller (rev 02)

I don't know which one of those is my graphic card since I don't know what the hell.
(Amiryt if I guess it's the graphic card what I colored Red?) And my Additional Drivers tool offered me this: (Since is working well with ubuntu's graphic things like... when you move windows, maximise em, etc. BUT not with games)
-----------------------------imaginary quote---------------------------------------------
ATI/AMD propietary FGLRX graphic driver:
- 3D-accelerated proprietary graphics driver for ATI cards.

This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards.
-----------------------------imaginary quote---------------------------------------------
The thing is that driver is not running well. And I need to know another thing; when I run some programs on wine1.2 they work awfull, one example is fruityloops studio, soulseek, frostwire (Actually asked me for a newer version of java which I downloaded and properly installed it on the terminal but didn't work)

So basically my wine is being rude with me, what to do?
I googled to the limbo but didnt' found anything, my errors are so particular

Also umm there's another... kind of... green hole in the front of my pc which I think is part of the bluebirds or I don't know but I have 2 green holes, one on the back for the speakers and one on the front that I guess it's for the earphones. But I want to configure the front one cause if I plug there my earphones it doesn't sound... thanks.

---

### Post by grahammechanical on 2011-02-22
First, you should check out the Wine website -
[http://www.winehq.org]("http://www.winehq.org/")

You need to confirm that those programs work with wine. You might also need to change the wine configuration settings.

Second, Go to System>Administration>Additional Drivers and see if the is a video driver available for download and see if it is activated.

Also, ask yourself this, If you were running these programs (games) on a Windows OS would your machine meet the specification requirements? Is the CPU fast enough? Do you have enough RAM and video memory? If these programs do not run well on the OS they were designed for because the machine is under specified, then they will not run well on Linux. In my opinion.

Regards.

---

### Post by Julian Luna on 2011-02-22
Well, I believe those programs should work fine with wine since a lot of people actually ran good stuff with wine already, one of my friends is available to run air rivals which actually requires really good graphics capability of a computer. Those games used to run just fine before I switched to ubuntu 10.04 from Windows XP.

Configuration Settings? I don't really understand D: My additional drivers tool already gave me the driver I described before and compiz works just fine, looks awesome and fast, the computer is fast as hell, it's a dual core processor and RAM gigas, the computer overruns the game's system requirements but there's something wrong with the graphic card configuration cause it works with compiz but not with games, I don't think it's wine's problem cause the Ubuntu's games dont run well (QuadraPassel by exampel).

Thanks, I hope someone haves a solution

---

### Post by cascade9 on 2011-02-22
I couldnt find 'quadrapassel' at WineHQ. Considering that it seems to a tetris clone, I dont know if anybody would have bothered even trying, theres got to be linux native several tetris clones. 

Tibia 7X wont work with WINE, 8.X should- 

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1563](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1563)

> **Julian Luna said:**
> The thing is that driver is not running well. And I need to know another thing; when I run some programs on wine1.2 they work awfull, one example is fruityloops studio, soulseek, frostwire (Actually asked me for a newer version of java which I downloaded and properly installed it on the terminal but didn't work)

Dear gawds...soulseek with WINE? Why? Its awful with windows! Use nicotine or museek. 

Theres got to be a gnuatella (frostwire) linux native client out there somewhere, but I dont know about it.

---

### Post by Julian Luna on 2011-02-22
Well thanks, you seem to know a lot; my up to date tibia isn't running fine, no game is running fine with it... Air rivals promts a hackshield error but I believe it's due to the graphic card generic driver...

My ubuntu is x64 btw and my processor supports it :/

---

### Post by Frogs Hair on 2011-02-22
Quadrapassel is installed by default with Ubuntu 10.10 and does not require wine . I don't think it requires proprietary drivers . You can install a proprietary driver if needed from System > Administration > additional drivers or hardware drivers .

---

### Post by cascade9 on 2011-02-23
You might need to install DX or do some video hacks with WINE to get those things going, or it could be simply a problem with 'free' online games. Hard to tell....

---

### Post by mastablasta on 2011-02-23
in addition to what others said (check propper wine settings)
 
well WINE is using sort of emulation and it requires a bit more power than a native windows system would. so if you are runnign cool special effects in the backgorund they might be taking out prescious resources from you. have you tried turning off the desktop effects before running wine?
HD3200 is a chip not a dedicated graphics card and it probably uses your computers ram memory. add to that simulation, then compiz special effects and things start to pile up fast. 
 
also if you feel like drivers are the issue perhaps you should try to instal 10.10 and then their newer proprietary drivers (if necessary).

---

### Post by Julian Luna on 2011-02-23
Oh well ... it's really sad, I know quadrapassel doesn't require wine but whenever I open it; it looks awfull. Installed d3dx9 because the console advertised me "You shoulnd't be using this, it's very invasive! Use d3dx9 instead" Even if I tried installing directx9 it wasn't running properly on the terminal. I'm very sad I just want my graphics to work, I don't think it's my desktop effects but I would try, everyone tells me to disable them but no one told me how to disabl'em :/ Even the compiz should I just uninstall it? Thx. Remember my ubuntu is 10.04 I heard 10.10 has a lot of problems

Buying which graphic card is an economycal option supported by Ubuntu?

Edit: Dissabled every compiz effect and set to "None" my System -> Preferences -> Appeareance -> Vissual Effects. Also closed my CairoDock and now Quadrapassel runs just fine but Tibia still looks as ****. You know this is strange; on windows my graphic card was completely powerfull I could of run let's say, Tibia and Air Rivals at the same time and having little little troubles. I mean, is there a way to directly enable the drivers of my motherboard that I have on a CD? [Black Series]

---

### Post by cascade9 on 2011-02-23
If you installed the windows version of quadrapassel, it does require WINE. Its only the linux native version that wont need WINE. 

You'd do best to find a guide for how to install DX9 with WINE. 

As for a decent cheap card with good linux support- GT220.

---

### Post by mastablasta on 2011-02-24
> **Julian Luna said:**
> You know this is strange; on windows my graphic card was completely powerfull I could of run let's say, Tibia and Air Rivals at the same time and having little little troubles. 
 
 
no, it's not strange at all. ATI made good drivers for windows and they just started with the drivers for linux. or decided not to include all the features in linux drivers to save some dvelopment time and money (remember linux market is very tiny compared to windows). so consider the drivers to be in *beta* stage :-)
 
option to try is to upgrade to 10.10 (!!! remove the proprietary drivers before upgrade !!!) and then install a newer version of ATI drivers.
 
try opensource drivers made by community (again maybe better to do it on 10.10) and if they don't work well try to upgrade them to edgers version (development version).
 
or get the card suggested to you by cascade9

---

### Post by Julian Luna on 2011-02-24
Thanks bros you rock you know? Well I hope I find later a good driver in beta stage cause I'm afraid to switch to 10.10 cuz i heard a lot of ppl is having problems with it and I don't know if the x64 version is working fine. Also I think I installed ubuntu twice, if I open "File System" there appear all my ubuntu folders, and there's another partition of 20 gigas where I first tried to install ubuntu there but it failed to run somehow I think cause it wasn't installed "Alongside another SO" (Or whatever the phrase is) So I want to delete this 20gigas partition, it's like... ubuntu files are there but I'm using the ones in "File System" which is directly in / ... so how to delete this one ? Is it safe? Tia

Edit: Just changed my tibia's graphic configuration, here are my experiments:
Using Directx9=Looks awfull
Using Directx5=Looks bad
Using OpenGL=Works fine

...
Someday there was an inteligent scientist who made a spider to obey him
"JUMP" .. he told him, and the spider jumped 16 inches
He writed a note and cutted one of the spider's legs
"JUMP" .. he told him, and the spider jumped 14 inches.
He took a note again and kept making the same experiment
12 inches, 10 inches, 8 inches, 6 inches, 4 inches, 2 inches...
Cutted the last leg of the spider and his notes were those:

8 legs = 16 inches a jump
7 legs = 14 inches a jump
6 legs = 12 inches a jump
5 legs = 10 inches a jump
4 legs = 8 inches a jump
3 legs = 6 inches a jump
2 legs = 4 inches a jump
1 leg = 2 inches a jump
0 legs = Does not hear.

Im gonna upgrade probably to 10.10 or 11.04, i'll remember to delete the graphic card's propietary drivers before doing so. <3

PS: Does anyone know how do I write Ascii on ubuntu? I need to type alt+12, alt+13, alt+14, etc (Window$ commands). Where is the page to donate money to ubuntu?

---

