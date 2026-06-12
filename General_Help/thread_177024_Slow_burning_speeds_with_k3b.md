---
title: "Slow burning speeds with k3b"
date: 2006-05-15
forum: General Help
---

### Post by patsissons on 2006-05-15
I'm just wondering if anyone else has experienced this same problem.

My drive is set with dma on (hdparm -d1 /dev/hdX) and i have confirmed that many times.  My drive is 4x DVD-R compatible.  My disc's are 1-16x compatible.  When i burn a dvd the writing speed states 5678 KB/s (4.10x), but the estimated writing speed as it is burning the disc fluctuates around 1.00x.  This has become really frustrating because its not a consistant problem.  Sometimes it will burn at full speed (which is usually around 3.90x).  But most often it will be slowed down and I cannot for the life of me figure out why.

I am currently using dapper with all of the latest updates.  Any thoughts or suggestions?

---

### Post by LightsOut on 2006-05-15
go to your resource manager and disable KDED. It is a noted problem with k3b that kded causes the program to burn slow. There's a link floating around the fedora forums that talk about it. It's a bug that will hopefuly be fixed soon.

---

### Post by qpieus on 2006-05-23
I have the same problem. DMA is on, burner and media is 16x. Stated buring speed in k3b says 8, 12,16x (whatever I select), but the actual burning speed is around 4x. I have also disabled KDED as suggested above. This did NOT fix the problem for me. I am using ubuntu dapper beta 2. DVD drive is set as master on secondary ide connector. Nautilus disk creator and Nero also will not burn at greater than 4x either. Interestingly, bonfire (search the forums here for a thread on this app) appears to burn at 8x for me, but not higher. So that's an improvement, but I'm very frustrated that I can't burn dvds at rated speed. I am by no means a linux pro and I don't know what else to check...
Any help is appreciated. This problem will keep me from killing my windows partition, which I very much want to do.

---

### Post by djSeverin on 2006-05-24
LightsOut is correct. Disabling KDED before starting a burn will provide a temorary work around until the bug causing K3B to behave like this is identified and fixed.

---

### Post by djSeverin on 2006-05-24
[QUOTE=qpieus]DVD drive is set as master on secondary ide connector. Nautilus disk creator and Nero also will not burn at greater than 4x either. Interestingly, bonfire (search the forums here for a thread on this app) appears to burn at 8x for me, but not higher.[/QUOTE]

What brand of burner do you have and if you can find out, what is its firmware version and model number.

It is very strange that Nero for Linux and Nautilus are having the same problem.

Please also provide in your response the output of
  "sudo hdparm /dev/hdc" and
  "sudo hdparm /dev/hdc -tT"

The first being to verify your settings and the second being to get a sense of the read speeds of your device. Make sure a CD or DVD is in the drive for the second one.

---

### Post by qpieus on 2006-05-24
[QUOTE=djSeverin]What brand of burner do you have and if you can find out, what is its firmware version and model number.

It is very strange that Nero for Linux and Nautilus are having the same problem.

Please also provide in your response the output of
  "sudo hdparm /dev/hdc" and
  "sudo hdparm /dev/hdc -tT"

The first being to verify your settings and the second being to get a sense of the read speeds of your device. Make sure a CD or DVD is in the drive for the second one.[/QUOTE]
djSeverin - thanks for replying. My drive is a Benq 1620, FW B7W9.

sudo hdparm /dev/hdc:/dev/hdc:

/dev/hdc:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

sudo hdparm -tT /dev/hdc:

 Timing cached reads:   1120 MB in  2.00 seconds = 559.81 MB/sec
 Timing buffered disk reads:   14 MB in  3.15 seconds =   4.44 MB/sec

---

### Post by djSeverin on 2006-05-28
Sorry for the delay. Am looking into this.

In the mean time, a few more questions. What version of CDRecord and k3b are you using? Is the IDE cable you have this device hanging off an IDE 40 or 80? Have you run the k3b Setup option from within k3b to ensure the correct group and permissions are set.

If possible, can you move the burner to /dev/hdb on the primary IDE and see what happens (You don't NEED to do this, but it just removes a few more possibilities).

---

### Post by CyberAngel on 2006-05-29
[QUOTE=qpieus]I have the same problem. DMA is on, burner and media is 16x. Stated buring speed in k3b says 8, 12,16x (whatever I select), but the actual burning speed is around 4x. I have also disabled KDED as suggested above. This did NOT fix the problem for me. I am using ubuntu dapper beta 2. DVD drive is set as master on secondary ide connector. Nautilus disk creator and Nero also will not burn at greater than 4x either. Interestingly, bonfire (search the forums here for a thread on this app) appears to burn at 8x for me, but not higher. So that's an improvement, but I'm very frustrated that I can't burn dvds at rated speed. I am by no means a linux pro and I don't know what else to check...
Any help is appreciated. This problem will keep me from killing my windows partition, which I very much want to do.[/QUOTE]

The same for me with the exception that nerolinux burns the DVD`s at full speed (even 16x).
Although I`d like to use k3b because it`s more functional than nerolinux (nerolinux has no similarities with that for windows. It can just only burn).

---

### Post by qpieus on 2006-05-29
[QUOTE=djSeverin]Sorry for the delay. Am looking into this.

In the mean time, a few more questions. What version of CDRecord and k3b are you using? Is the IDE cable you have this device hanging off an IDE 40 or 80? Have you run the k3b Setup option from within k3b to ensure the correct group and permissions are set.

If possible, can you move the burner to /dev/hdb on the primary IDE and see what happens (You don't NEED to do this, but it just removes a few more possibilities).[/QUOTE]
CDrecord = 2.1.1a01
K3b = 0.12.14
cdrdao = 1.2.1
I went into k3b setup from within k3b, but I'm not sure what I need to do there. I attached a screenshot.
The drive is on the end of an 80 pin cable, set to master.
I have 2 drives on the other ide cable, so I can't easily swap right now (the OS I'm typing this on is on hdb).
Thank you for your help.

---

### Post by djSeverin on 2006-05-29
qpieus: All looks good to me. As for k3b setup, simply run it and then select Apply and Ok. All it really does it modify the permissions of your CD device and the binaries used to communicate with your burner.

In the case of your screenshot, it is wanting to modify the permissions of your CD device from 660 to 666 and cdrdao from 0755 to 4711. Let it do this and see what the end result is.

Unfortunantly, without actually being infront of your PC, I am otherwise out of idea's. Have been trawling the net but can't see any other obvious reason why you are having difficulty.

CyberAngel - Try running k3b Setup from within k3b and see what your permissions are looking like and if it wants to change anything.

Edit:
One final idea. With regard to the 80 pin cable you are using, make sure you have the primary on the black connector. With udma cables, you have to have the primary and secondry on the correct connector, and finally the correct connector going to the motherboard.

Blue goes to the motherboard, Gray is in the middle of the cable and goes to any slave device (if present) and the Black connector (at the opposite end from the host connector) goes to the master drive.

Finally, don't always rely on hdparm. If you continue to have problems, try 'grep DMA /var/log/messages' and see if you get any results. Some example badness might include:

  localhost kernel: cdrom: This disc doesn't have any tracks I recognize!
  localhost kernel: hdc: irq timeout: status=0xd0 { Busy }
  localhost kernel: ide: failed opcode was: unknown
  localhost kernel: hdc: DMA disabled
  localhost kernel: hdc: ATAPI reset complete

then there may be some other hardware problems that are causing your difficulties.

---

### Post by qpieus on 2006-05-29
OK, thanks for the help. I'll let setup change the permissions and report back. The drive is on the correct connector and I'll try grep DMA too.

---

### Post by CyberAngel on 2006-05-30
[QUOTE=djSeverin]....
CyberAngel - Try running k3b Setup from within k3b and see what your permissions are looking like and if it wants to change anything.
.....[/QUOTE]


The only thing it wants to change is the cd/dvd rom drives from 660 to 666. The strange thing that NeroLinux can burn at maximum speed so I don`t think that this is the problem.
Anyway In 1st of June I am going with a fresh install to dapper so I`ll check k3b again and if I have problems with dapper too I`ll let you know if you can help anymore :)

Thanks ;)

---

### Post by djSeverin on 2006-05-30
CyberAngel: NeroLINUX uses its own API to write to the CD/DVD writer in the form of NeroAPI. If you want, you could try using an alternate API for k3b such as [DVD+RW/+R/-R[W] ]("http://fy.chalmers.se/~appro/linux/DVD+RW/") rather then cdrecord.

---

### Post by CyberAngel on 2006-05-30
[QUOTE=djSeverin]CyberAngel: NeroLINUX uses its own API to write to the CD/DVD writer in the form of NeroAPI. If you want, you could try using an alternate API for k3b such as [DVD+RW/+R/-R[W] ]("http://fy.chalmers.se/~appro/linux/DVD+RW/") rather then cdrecord.[/QUOTE]


I have already installed dvd+rw-tools and dvdrtools packages from apt but k3bsetup hasn`t found anything... How can I set k3b to use a different API?

---

