---
title: "Random restart Ubuntu 10.10/Vista 64 bit"
date: 2010-11-01
forum: General Help
---

### Post by TurtleKing on 2010-11-01
My computer has been restarting lately at very random times. My second last unexpected restart was about a month ago. This began from when I first noticed on my Ubuntu 10.04 while playing pwi (perfect world international), and then had the same result on windows but without any reports or blue screens. Now after an update to 10.10 a couple of weeks ago (i thought that fixed the problem) the problem came back.  Anyways, if anyone here has a clue as to what might be the problem am all ears.

I switch to vista after the crash yesterday, and after about 10 minutes or so it had the same result except with a very brief blue screen now. Here is a report from windows vista after the random crash + an automatic restart:
```
Problem signature:
  Problem Event Name:	BlueScreen
  OS Version:	6.0.6002.2.2.0.768.3
  Locale ID:	1033

Additional information about the problem:
  BCCode:	3b
  BCP1:	00000000C0000005
  BCP2:	FFFFF9600017B6A6
  BCP3:	FFFFFA600CB65580
  BCP4:	0000000000000000
  OS Version:	6_0_6002
  Service Pack:	2_0
  Product:	768_1

Files that help describe the problem:
  C:\Windows\Minidump\Mini103110-01.dmp
  C:\Users\name\AppData\Local\Temp\WER-43352-0.sysdata.xml
  C:\Users\name\AppData\Local\Temp\WER9D76.tmp.version.txt

Read our privacy statement:
  http://go.microsoft.com/fwlink/?linkid=50163&clcid=0x0409
```
Notes: I replaced my username with name for security purposes. Also, I used code to make more readable let me know if It cause problems or something. In addition, although vista is more detailed about this problem, this problem also occurred in Ubuntu 10.04 & 10.10 (now).

---

### Post by markinmadison on 2010-11-01
I have had the same problem with 10.04 and now 10.10 except I am using the 32 bit. My advice is to go back to 9.10. That is what I did and it worked for me. In my opinion, and this is only my opinion, 9.10 is the most stable Ubuntu out there so far. I have had major problems with the 10.04 and 10.10 versions.

---

### Post by P4man on 2010-11-01
If both windows and linux bluescreen/panic you can be fairly certain its a hardware problem. Most likely cause: bad ram. In grub menu select the memtest86 and let it run overnight. If you ram is okay it should produce zero errors. 

If the ram turns out okay, check temperatures and voltages in the bios. A bad powersupply is also a rather common cause.

---

### Post by TurtleKing on 2010-11-01
The problem seems to be worse on the Ubuntu or its own Hard-Drive. I had another recent unexpected restart on Ubuntu. One thing i don't understand is why doesn't Ubuntu make a report or automatic test for these type of things? I think it would be really useful as oppose to just restarting without any warnings or after-crash report.

On other note, does anybody recommend a good temperature or voltage free software I can use? In, addition, how do I know whether i have a good or bad voltage/temperature?

---

### Post by P4man on 2010-11-01
Check your ram first; it is the most common cause of spontanenous reboots.

To check the temps and voltages, easiest is checking the bios. Normal temps should be below 50-60C depending on if its a laptop or desktop and CPU type there can be some variance. Above 60-70C is not normal 

Normal voltages should be the nominal voltages + or - 5%. If you see +12 being reported as +10V then you have a problem. Negative voltages are often not reported correctly so feel to ignore those. Relevant ones are +12V, +5V and +3.3V

If your bios doesnt provide this info, run something like everest on windows (has a free trial, check the stability test for those values) or lm-sensors on ubuntu.

---

### Post by TurtleKing on 2010-11-01
I was able to test the ram, and temperature without any error report. I am however, having a bit of trouble trying to figure out how to read the voltage on everest.  I looked under all the categories for a (number)+V and did not see it. Most of what I found were either numbers by themselves or with MB after it. 

I would try Im sensors, but am afraid Ubuntu might restart while testing again or possible make it worse. 

My suspicion is that this may have something to do with the Ubuntu Hard-Drive. I have had it for 3 years which is what the warranty suggest. Also, I think thats why the random restarts does not happen as often as the Ubuntu 10.10 compared to my Vista + its own Hard Drive. Although I am not able to determine why is vista restarting as well. Perhaps because technically Ubuntu hard drive runs the bios?

If you don't mind can you please explain how to figure out the voltage using everest?

Edit: Never mind, turns out everest free edition does not offer this service.

---

### Post by TurtleKing on 2010-11-01
Here are the results from Speed Fan on the voltage:
+12V: 12.35V
+5V: 5.03V
+3.3V: 3.31V

---

### Post by P4man on 2010-11-01
Ah well, try speedfan then;
[http://www.almico.com/speedfan441.exe](http://www.almico.com/speedfan441.exe)

edit: you beat me to it.

Voltages look very normal. What temps are you seeing?

---

### Post by TurtleKing on 2010-11-01
I just noticed the temperature report from Speed Fan and it different from everest report:
(flame icon)GPU: 63C
Temp1: 25C
Temp2: 27C
(flame icon)Temp3: 79C
HD1: 21C
HD0: 26C
Core: 13C

Should I worry about these results? Also, I am confused as to why these things are suggested to be hot since the temperature for my room is cold. :confused:

---

### Post by P4man on 2010-11-01
I dont know what temperature sensor that is, but thats very hot. GPU temps tend to be high, especially if you have a highend card like a geforce 4x0 (460/470/480) series or radeon 48xx then 63C is not extreme. 79 is. If that is the cpu it is way too high. Open your case and check if your fans are running and not clogged up with dust. What sort of computer is this?

---

### Post by TurtleKing on 2010-11-01
I had cleaned it about a month or so with a compressed air can. And just did it again. I then went ahead into Ubuntu OS, and after a while of inspecting the fans + idle the computer restarted. Now I am sure its not a dust problem as I can clearly see the blades of all the fans are dust free let alone the entire inside. 

This is a desktop mostly used for Gaming/Typing papers:
Case: Antec Three Hundred Black Steel ATX Mid Tower Computer Case

Processor: AMD Athlon 64 X2 5600 Brisbane 2.9GHz Socket AM2 65W Dual-Core Processor Model ADO5600DOBOX

RAM: 1 CORSAIR 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual Channel Kit Desktop Memory Model TWIN2X4096-8500C5

Video Card: 1 EVGA 256-P2-N761-TR GeForce 8600 GTS 256MB 128-bit GDDR3 PCI Express x16 HDCP Ready SLI Supported Video Card

Hard Drives 1: Western Digital Caviar Black WD6401AALS 640GB 7200 RPM 32MB Cache SATA 3.0Gb/s 3.5" Internal Hard Drive -Bare Drive

Hard Drive 2:Seagate Barracuda 7200.12 ST3500418AS 500GB 7200 RPM SATA 3.0Gb/s Hard Drive - OEM

Power Supply: OCZ StealthXStream OCZ600SXS 600W ATX12V / EPS12V SLI Ready Active PFC Power Supply

Motherboard: GIGABYTE GA-MA770-UD3 AM2+/AM2 AMD 770 ATX AMD Motherboard


fans: 
case: A rear-mounted 120mm TriCool fan as well as a top-mounted 140mm TriCool fan – both with 3-speed switch control – draw air through the case. I have both fans set to high.

videocard: 1 fan

power supply: 1 fan

Sorry for the long post, but hopefully this will help determine what needs to get replaced or inspected.:(

---

### Post by P4man on 2010-11-01
It *could* be a misreading by speedfan, but it could just as well be a heatsink that isnt mounted properly; but why dont you check in the bios? It should have a PC health page or similar where you can monitor temps and voltages.

BTW, GPU temp seems suspiciously high for those kind of cards... an 8600 is a cool card normally. 63 isnt excessive, but that is while its doing nothing.

---

### Post by TurtleKing on 2010-11-01
Here is the report from BIOS PC Health Status
I. Voltage:
1. Vcore: 1.312V
2. DDR2 1.8V: 2.112V
+3.3V: 3.412V
+12V: 12.239V

II. Temperature:
1. Current system temperature: 26C
2. Current CPU temperature: 35C

III. Fan Speed:
1.Current CPU fan speed 1654 RPM
2.Current system fan1 speed 0RPM
3.Current system fan2 speed 0RPM
4.Current power fan speed 0RPM

I tried and touch the video card (I assume its what GPU stands for) to see whether it was warm or hot, and its feels a bit normal. And as for the temp3 speed fan I am not sure what that means or what it represents.

---

### Post by TurtleKing on 2010-11-01
Well from researching on google it looks its a speed fan misinterpretation. "it seems to be the product of my mobo not having whatever sensor it looks for temp3 from, gets a dummy value, and outputs a garbage temperature" ([http://www.overclockers.com/forums/showthread.php?t=435031](http://www.overclockers.com/forums/showthread.php?t=435031)).  I really want to go  back to my Ubuntu since I used it more often for work related stuff.

Any other suggestions as to why the random restart?

---

### Post by TurtleKing on 2010-11-01
bump

---

### Post by TurtleKing on 2010-11-01
bump x2

---

### Post by P4man on 2010-11-02
FYI, its considered rude to bump more often than once a day.

Anyway, yeah scratch the temps as cause, yours are fine. I dont think I read you tested memtest86 overnight, that is still my first guess. Next thing to test is the harddrives. Boot ubuntu and run disk utility in the system > administration menu, select your harddrives and check the SMART status. If it says its not supported, go in to your bios and enable smart for your drives.

---

### Post by TurtleKing on 2010-11-02
As for the memtest86 it reported 100 percent passed with no errors. Now, for the matter of the hard drive, what am I exactly looking for in the SMART section? I do see "relocated sector count" highlighted red with a warning sign, and a couple highlighted gray with n/a.

On other note, I apologizes for the bumps but I am starting to get worried on time limit. If I were to eventually have to reinstall Ubuntu 10.10 from scratch, (not upgrades) I want to do it quickly overnight rather than at a more inconvenient time. As I have mentioned, I use my Ubuntu hard drive for work related stuff, so I want to get it fixed before I get too much piled up work later.

---

### Post by TurtleKing on 2010-11-02
Well if its any help this is what is displaying now for the Reallocated Sector Count:

Normalized: 99
Worst: 99
Threshold: 36
Value: 52 sectors

Note: I was just checking the purchase date for both hard drive, and I noticed that both are not more than 2 years old. I am currently running a self test, but it would be great I can get a response as to how to continue. I don't want to start price shopping early for nothing. I mean 2 years is even below the warranty. (Although customers have reported crappy refund service for their hard drives.)

---

### Post by P4man on 2010-11-03
52 bad sectors probably wont prompt the manufacturer to replace your drive yet, but its a sign of trouble ahead. Whether or not that explans the rebooting is hard to say. If the drive doesnt have partitions that are readable to windows, then its doubtful it would cause windows to reboot as well. But perhaps you can disconnect the problematic drive and boot ubuntu from USB or CD and see if its stable in a live session.

TBH, it could still be anything, but its almost surely a hardware problem. Whether your videocard, motherboard, PSU or something else is tricky to say. Perhaps the files mentioned in the windows crash report you posted in your first post can shed some more light on it

---

### Post by TurtleKing on 2010-11-03
Well as for hard drive setup, my Vista hard drive is set to master and my Ubuntu hard drive is set to slave, maybe that may be the cause of both OS restarting? (I not an expert on hardware/OS) In terms of partition the volumes reads, 
488GB ext4 <--Ubuntu OS
Extended 12GB <--not really sure what this is for
12GB Swap Space <--not really sure what this is for

In addition, I agree with you that its more likely a hardware problem. I have been hearing this annoying noise lately (like clicking) when I turn on the computer after its been shutdown for more than an hour. However, when I opened the case on one of the power on I couldn't tell where it was coming from.

I will try and disconnect the hard drive and boot from CD, and then report back the results.

---

### Post by P4man on 2010-11-03
> **TurtleKing said:**
> Well as for hard drive setup, my Vista hard drive is set to master and my Ubuntu hard drive is set to slave, maybe that may be the cause of both OS restarting? (I not an expert on hardware/OS) In terms of partition the volumes reads, 
488GB ext4 <--Ubuntu OS
Extended 12GB <--not really sure what this is for
12GB Swap Space <--not really sure what this is for

master/slave wouldnt matter, and apparently ubuntu has its own drive (which is not readable for windows) so even a hardware problem with the drive probably wouldnt affect windows. i say probably, but Im not entirely sure here. You could just disconnect the ubuntu harddrive and try windows for a while and see if that becomes stable then, assuming the windows drive is free of errors.
> 
In addition, I agree with you that its more likely a hardware problem. I have been hearing this annoying noise lately (like clicking) when I turn on the computer after its been shutdown for more than an hour. However, when I opened the case on one of the power on I couldn't tell where it was coming from.

Click of death? Anything like this:
[http://en.wikipedia.org/wiki/Click_of_death#Hard_disk](http://en.wikipedia.org/wiki/Click_of_death#Hard_disk)

(play the audio file on that page)

---

### Post by csogilvie on 2010-11-03
my install of 10.04 was rock solid.  Now that I've upgraded to 10.10 I have random restarts too.

Sometimes as often as once a day.  Sometimes it lasts a few days.

Gone are the days of my previous 45+ days of uptime.

---

### Post by TurtleKing on 2010-11-03
I can't really blame this on 10.10 though since I got it with 10.04 and upgraded to 10.10 thinking it would fix it.

As for the click of death no it does not sound like that, mine doesn't really have a rhythm to it.

I am gonna try it just using windows and the cd, and see if I get a random restart in for about a week. I assume if I don't then its something with Ubuntu or Ubuntu-Hard Drive. If i do receive a restart, then I will I guess check back here to see for more possible test, or solutions.

I am really hoping that the motherboard or processor is out of the equation as these were really expensive to purchase.

So see you all in a week I guess. I hope its just a program in Ubuntu to say the least.:(

---

### Post by TurtleKing on 2010-11-06
Well the computer had a system failure on vista (without the Ubuntu hard drive being connected.:cry:  I had left the computer idle for about 20-30 minutes, and when I came back and turned on the monitor I was at the vista login screen. Once I logged in vista gave me the system crash warning + notes. Here is the note same as the first page:
```
Problem signature:
  Problem Event Name:	BlueScreen
  OS Version:	6.0.6002.2.2.0.768.3
  Locale ID:	1033

Additional information about the problem:
  BCCode:	3b
  BCP1:	00000000C0000005
  BCP2:	FFFFF9600017B6A6
  BCP3:	FFFFFA600CB65580
  BCP4:	0000000000000000
  OS Version:	6_0_6002
  Service Pack:	2_0
  Product:	768_1

Files that help describe the problem:
  C:\Windows\Minidump\Mini103110-01.dmp
  C:\Users\name\AppData\Local\Temp\WER-43352-0.sysdata.xml
  C:\Users\name\AppData\Local\Temp\WER9D76.tmp.version.txt

Read our privacy statement:
  http://go.microsoft.com/fwlink/?linkid=50163&clcid=0x0409
```

would it be helpful to show what the files that might describe the problem say? or is that something you guys know already? Anyone have any more recommendation on what to hardware to check?

---

### Post by P4man on 2010-11-06
Im not exactly an expert in windows dump files, but feel free to see what you can learn with this:
[http://support.microsoft.com/kb/315263](http://support.microsoft.com/kb/315263)

But TBH, I think you are better off swapping components if you have spares. Powersupply, motherboard and videocard are the most likely culprits now that youve excluded ram and hdd.

---

### Post by TurtleKing on 2010-11-06
The weird noise I had mentioned early I just found was coming from the CPU. I also opened one of the files the window crash report mentioned and, and on one of them it mentioned the processor in it. 
I was wondering if this could be a role in the random crash as well? 

I unfortunately don't have spare hardware to perform individual hardware test. And I don't have enough money to buy spare parts for everything either. I wish sometimes computer could just tell us what they need us to replace or inspect. lol

---

### Post by P4man on 2010-11-06
cpu's dont make noise (other than a sizzeling noise when they melt). But fans do. COuld it be a cable blocking the cpu fan? Or a chipset fan?
You could try opening your case and putting a large deskfan pointed at your machine. See if that makes it stable.

---

### Post by TurtleKing on 2010-11-06
The sound only comes into place when I turn on the computer after a long period of being idle (20-30 minutes). Afterwards, it begins to sound normal again. The CPU does have a fan, and from having it open I currently don't see anything blocking or hovering close to it. 

Could the CPU be unmounted and remounted again from the motherboard without needing something either than a screwdriver? I was thinking maybe if I unplugged it from the motherboard, I could get a better view point on whether something burned or if something does not look right. However, if I need the weird stuff it mentioned on the manual when my brother installed it, then I rather leave it to a professional.

---

### Post by P4man on 2010-11-06
For most AM2 coolers you wouldnt even need a screwdriver:
[http://www.youtube.com/watch?v=MzZQgJDyzGI&feature=related](http://www.youtube.com/watch?v=MzZQgJDyzGI&feature=related)
But you would need thermal paste and I doubt it will accomplish much since the temps seem okay. The sound could be the fan bearings which are worn out, and the sound stops when the grease heats up.

---

### Post by TurtleKing on 2010-11-06
Man this really sounds like a trip to a technician or replacing most of the hardware. :(

---

### Post by TurtleKing on 2010-11-07
hmm I am starting to contemplate on whether this may have something to do with the video card. I keep getting kicked and crashed lately on serveral games for problems with display driver. I don't know though if it can get bad enough to make windows get a BSOD or freeze.

---

### Post by P4man on 2010-11-07
To quote myself: > Powersupply, motherboard and videocard are the most likely culprits now that youve excluded ram and hdd.

Gaming would stress all 3 of those, so its hard to say which is cause. But yeah, it definitely could be the videocard. Perhaps try running furmark, it basically stresses only the gpu:
[http://www.ozone3d.net/benchmarks/fur/](http://www.ozone3d.net/benchmarks/fur/)

---

### Post by TurtleKing on 2010-11-07
I tried the download link and noticed it only had Vista 32 bit, mine is 64 bit will that matter? Also, what settings do i run it under? (stability, benchmarking & extreme burning mode, displacement mapping, post fx, etc.)

---

### Post by TurtleKing on 2010-11-08
SCORE:855 points (60000 ms)

Max GPU Temp: 84°C

Resolution: 1280x1024 (FS) - MSAA: 0X

FPS: min=13  max=20  avg=14

Renderer: NVIDIA GeForce 8600 GTS

Drivers: 8.17.12.6089 (10-8-2010) - nvoglv64

GPU-Z: Core:675MHz - Mem:1008MHz - Shader:1450MHz

CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 5600+

CPU Speed: 2605 MHz System memory: 4093 MB

OS: Windows Vista 64-bit build 6002 [Service Pack 2]

um...did it pass? lol

---

