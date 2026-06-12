---
title: "Cannot load ANY Linux distribution"
date: 2012-04-22
forum: General Help
---

### Post by rbdaves on 2012-04-22
To start with, here is my system which I assembled in Mid March, 2012:

MSI P67A-C43 B3 Intel P67 Socket LGA 1155 MB
Intel®Core&#8482; i5-2500 CPU @3.30Hz 3.30 GHz
2 SSD OCZ 120 G Vertex Plus SATA
EVGA GeForce GTX 550 Video
8 G Corsair High Performance Vengance DDR3 Memory
Lite On 24X DVDRW SATA
BIOS: American Megatrends Inc. V1.17 01/13/2012

I cannot run ANY Linux distribution on this computer.  I've tried using a CD that came in "Ubuntu" magazine and other CD's that I've purchased (Puppy Linux, Damn Small Linux, Knoppix)They all hang at some point.  I downloaded "Ubuntu 11.10 - desktop - i386.iso" and burnt it to disk.  When I tried to run it, I got "Terminated by signal 9".  What's wrong?:confused:

---

### Post by codemaniac on 2012-04-22
Hello rbdaves,
Welcome to the Ubuntuforums .
Just observed that your bios version is shiny new .You should try out some recent most bleeding edge versions of Ubuntu or any other distro .
Official Ubuntu 12.10 release is just knocking at the door ,you can check if all the necessary drivers have been shipped with 12.10 .
Here is the link .
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by mastablasta on 2012-04-22
Did you try to use nomodeset boot parameter? [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

do you maybe have UEFI bios? it requires special adjustments...

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://wiki.ubuntu.com/UEFI-howto](https://wiki.ubuntu.com/UEFI-howto)


[]("https://help.ubuntu.com/community/BootOptions")

---

### Post by IWantFroyo on 2012-04-22
1) I would try Precise (12.04). A quick Google shows no problems. The beta 2 is very usable, or you could just wait several days.

2) You should be using a 64 bit image to use all your RAM efficiently.

3) Have you tried using boot parameters? (noapic, pci=noacpi, etc.)

---

### Post by MonkeyPaw on 2012-04-22
Yes, use a 64bit version of Ubuntu, otherwise you won't be able to use all your RAM.

You might check to see how the BIOS is configuring your graphics. It could be that the graphics card is not getting priority. If that looks okay, you might pull the GTX550 and try running from the motherboard graphics and see if you make any progress. It might help eliminate that as the issue.

---

### Post by rbdaves on 2012-04-22
Firstly, let me advise that I have used Red Hat Linux in the past, but it was a long time ago.  I don't think I'm a beginner, but there's a lot that I have to learn here.

Codemaniac
The link you provided looks like a complete download of the V12.10.  I've already downloaded V11.10 and it's a big file. Your comment about checking if all the drivers have been shipped looks like something that I might do after I get this distribution loaded and running.  Looks like I might have some preparation work to do if I've read the info on this correctly.  Something about setting something up that happens at boot time???

Mustablasta:
How do I use the "nomodeset" parameter if the program won't boot?
I went to one of the links you advised and it says "Chainloading Windows x86_64 UEFI-GPT" with a bunch of instructions that indicate that there's some kind of command line interface.  Get me started, please.  And, yes, I think I have UEFI BIOS-I believe AMI uses this.  

IWantFroyo:
Boot parameters? where do I put them?  Once again, looks like I need some kind of user interface.  It's not Ubuntu, cuz it won't run and I doubt that Windows would know what to do with it.  

Monkeypaw:  Pull the graphics card?  This MSI MB doesn't have built-in graphics.
How do I find out if the graphics card is getting priority?  All I have is Windows.

All you guys:
I've read all  the hype about how easy Linux is.  This isn't easy.  It would seem that if I need to modify the boot routine or put some kind of boot commands or other parameters up front, someone should already have written a program that does all that stuff.

After I downloaded Ubuntu 11.10, I burnt a CD.  I'm assuming that the CD is bootable and should load Ubuntu...yes?  Or is there something else I have to do?

---

### Post by rbdaves on 2012-04-23
Put the Ubuntu V11.10 iso disk into my wife's 3-year-old PC.  It loaded fine and I am preparing this post using Ubuntu/firefox.  So my question about burning the disk is answered.  Getting the Ubuntu to run on my wife's computer was easy.  Getting it to run on my new computer is not.

---

### Post by jawilljr on 2012-04-23
rbdaves, to set "nomodeset" when booting when boot the livecd, please see [this post](http://ubuntuforums.org/showpost.php?p=11571901&postcount=5).

> When you see the purple screen with symbols at the bottom, hit the space bar, select your language, then F6 and mark nomodset. Esc gets you out of that so you can select to Try Ubuntu. The resolution may not be perfect (1280x1024 on my 1080p HDTV), but it should work.

Also see this [this thread](http://ubuntuforums.org/showthread.php?t=1890257), especially [this post](http://ubuntuforums.org/showpost.php?p=11575142&postcount=18) in the same thread.

It appears that chowoutside almost has the same setup you do.

Hopefully setting nomodeset fixes your problem.

Jerry

---

### Post by mastablasta on 2012-04-23
> **rbdaves said:**
>  
Mustablasta:
How do I use the "nomodeset" parameter if the program won't boot?
I went to one of the links you advised and it says "Chainloading Windows x86_64 UEFI-GPT" with a bunch of instructions that indicate that there's some kind of command line interface. Get me started, please. And, yes, I think I have UEFI BIOS-I believe AMI uses this. 
 
 
you could try post 7 here. a nice guide. maybe more simple.
[http://ubuntuforums.org/showthread.php?t=1903323](http://ubuntuforums.org/showthread.php?t=1903323)
 
though this guide is more for installing with UEFI while the live OS should boot without this.
 
>  
All you guys:
I've read all the hype about how easy Linux is. This isn't easy. It would seem that if I need to modify the boot routine or put some kind of boot commands or other parameters up front, someone should already have written a program that does all that stuff.

yeah i would also expect this, however UEFI is new and used only by a few manufacturers. it will eventually replace BIOS. BIOS boot doesn't need any special setup. hence all the hype about easy of use... i am guessing that installing windows on UEFI is also not as trivial....
 
try to use a 64 bit image, not because of ram (because 32bit can handle it with PAE kernel) but because of the CPU architecture.

---

### Post by codemaniac on 2012-04-23
> **rbdaves said:**
> Firstly, let me advise that I have used Red Hat Linux in the past, but it was a long time ago.  I don't think I'm a beginner, but there's a lot that I have to learn here.

Codemaniac
The link you provided looks like a complete download of the V12.10.  I've already downloaded V11.10 and it's a big file. Your comment about checking if all the drivers have been shipped looks like something that I might do after I get this distribution loaded and running.  Looks like I might have some preparation work to do if I've read the info on this correctly.  Something about setting something up that happens at boot time???

Mustablasta:
How do I use the "nomodeset" parameter if the program won't boot?
I went to one of the links you advised and it says "Chainloading Windows x86_64 UEFI-GPT" with a bunch of instructions that indicate that there's some kind of command line interface.  Get me started, please.  And, yes, I think I have UEFI BIOS-I believe AMI uses this.  

IWantFroyo:
Boot parameters? where do I put them?  Once again, looks like I need some kind of user interface.  It's not Ubuntu, cuz it won't run and I doubt that Windows would know what to do with it.  

Monkeypaw:  Pull the graphics card?  This MSI MB doesn't have built-in graphics.
How do I find out if the graphics card is getting priority?  All I have is Windows.

All you guys:
I've read all  the hype about how easy Linux is.  This isn't easy.  It would seem that if I need to modify the boot routine or put some kind of boot commands or other parameters up front, someone should already have written a program that does all that stuff.

After I downloaded Ubuntu 11.10, I burnt a CD.  I'm assuming that the CD is bootable and should load Ubuntu...yes?  Or is there something else I have to do?

Boot parameters are Linux kernel parameters which are generally used to make sure that peripherals and physcal devices are dealt with properly.  For the most part, the kernel can auto-detect information about your peripherals. However, in some cases you'll have to help the kernel a bit.Here is a community howto .

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by MonkeyPaw on 2012-04-23
> **rbdaves said:**
>  Pull the graphics card?  This MSI MB doesn't have built-in graphics.
How do I find out if the graphics card is getting priority?  All I have is Windows.

You are correct. The i5 has integrated graphics, but your motherboard doesn't use them. Have you successfully installed any OS on this machine before?

---

### Post by rbdaves on 2012-04-23
> **MonkeyPaw said:**
> You are correct. The i5 has integrated graphics, but your motherboard doesn't use them. Have you successfully installed any OS on this machine before?

I have installed Windows 7 on this computer.  MSi has a feature called "Live Update" which I ran yesterday and it took hours, but updated my BIOS and other stuff.  That made no difference in getting Ubuntu to run on my puter, however, using the "nomodset" command was the "golden key" and I am typing this post from within Ubuntu.  It's working and life is good.

Thanks everyone for your help.):P

---

### Post by techsupport on 2012-04-23
> **rbdaves said:**
> To start with, here is my system which I assembled in Mid March, 2012:

MSI P67A-C43 B3 Intel P67 Socket LGA 1155 MB
Intel®Core™ i5-2500 CPU @3.30Hz 3.30 GHz
2 SSD OCZ 120 G Vertex Plus SATA
EVGA GeForce GTX 550 Video
8 G Corsair High Performance Vengance DDR3 Memory
Lite On 24X DVDRW SATA
BIOS: American Megatrends Inc. V1.17 01/13/2012

I cannot run ANY Linux distribution on this computer.  I've tried using a CD that came in "Ubuntu" magazine and other CD's that I've purchased (Puppy Linux, Damn Small Linux, Knoppix)They all hang at some point.  I downloaded "Ubuntu 11.10 - desktop - i386.iso" and burnt it to disk.  When I tried to run it, I got "Terminated by signal 9".  What's wrong?:confused:

Also I would try installing Ubuntu from a USB Flash Drive. Sounds like you could be having a data corruption issue on whatever you are using to make your cds. Flash Drive installations of Ubuntu are faster too.

---

### Post by rbdaves on 2012-04-23
> **techsupport said:**
> Also I would try installing Ubuntu from a USB Flash Drive. Sounds like you could be having a data corruption issue on whatever you are using to make your cds. Flash Drive installations of Ubuntu are faster too.

Thanks for that input.  The problem is solved if I use the "nomodset" command as suggested in an earlier post by jawilljr

---

### Post by MonkeyPaw on 2012-04-23
> **rbdaves said:**
> I have installed Windows 7 on this computer.  MSi has a feature called "Live Update" which I ran yesterday and it took hours, but updated my BIOS and other stuff.  That made no difference in getting Ubuntu to run on my puter, however, using the "nomodset" command was the "golden key" and I am typing this post from within Ubuntu.  It's working and life is good.

Thanks everyone for your help.):P


Well, the BIOS update didn't hurt anyway. At least you are up and running. :)

---

### Post by jawilljr on 2012-04-23
I would also mark this thread as "Solved"

Jerry

---

### Post by rbdaves on 2012-04-24
> **jawilljr said:**
> I would also mark this thread as "Solved"

Jerry
Well, not really.

I tried Ubuntu 11.10 from a CD.  Then installed it "next to Windows7.  Now, my computer has a dual boot screen giving me options to run Ubuntu or Windows.  If I choose Ubunto, it just freezes with a purple screen.  

I guess I'm back to having to do something to get this thing to run.  Where do I start?

---

### Post by dcstar on 2012-04-24
> **rbdaves said:**
> Well, not really.

I tried Ubuntu 11.10 from a CD.  Then installed it "next to Windows7.  Now, my computer has a dual boot screen giving me options to run Ubuntu or Windows.  If I choose Ubunto, **it just freezes with a purple screen**.  


Press CTRL-C or CTRL-ALT-DEL and see if it then continues and loads (look at the disk activity light).

If it does, immediately do a Hardware Driver check to install any video drivers.

You really should be using the 12.04 install which should support later hardware.

---

### Post by Cheesemill on 2012-04-24
Have you applied the nomodeset fix to your installed OS?
When you tried it earlier it was a one off for the Live CD, you have to make the fix again and permanently now you have installed:
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by b1ackcr0w on 2012-04-24
> **mastablasta said:**
> Did you try to use nomodeset boot parameter? [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

do you maybe have UEFI bios? it requires special adjustments...

[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://wiki.ubuntu.com/UEFI-howto](https://wiki.ubuntu.com/UEFI-howto)


[]("https://help.ubuntu.com/community/BootOptions")

FYI - I have logged a bug in Launchpad, and am reliably informed that there is an upstream bugfix. Sadly it missed the freeze for 12.04 Precise, but will be in Precise +1.

Also FYI - I have a 550 Ti, and the nomodeset does indeed force both the live and installed systems to use the vesa driver, (you have to do it both when booting live, and first boot of installed) so you can get a system up and install the proprietary drivers. 

Hope that helps.

---

### Post by rbdaves on 2012-05-01
I put an older video card in my computer and removed the new one.  Ubuntu then ran just fine.  

I think I'll wait until Ubuntu 12 comes up with a way to work with my new video card.

---

