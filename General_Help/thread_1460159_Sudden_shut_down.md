---
title: "Sudden shut down"
date: 2010-04-22
forum: General Help
---

### Post by hexwind on 2010-04-22
Hey people

I have been using Ubuntu 9.10 since it was released. I had a dual boot install with Windows XP and then I upgraded to Windows Seven. During this period I have experienced a sudden shut down after some time while working on Windows (either XP or Seven, but it was more on Seven). It shuts down by itself as if I have pulled the power plug. And when I want to restart it again, it doesn't, it fails. It doesn't happen when I'm using a particular software, it shuts down when I'm using Photoshop/Illustrator CS3, surfing the net, watch a movie, or doing some codings on VB 6 (I have to, coz it's school stuff, so i can't go for any other softwares that are available on Ubuntu).

I thought I should install VirtualBox and have Windows 98/2000 as a guest OS in order to be able to use VB 6 without any problems. During the install, I have experienced the same thing EVEN when i'm on Ubuntu !! (although it happened only once).

Some people told me that Windows shuts down because of the dual boot, but I fail to fathom the reasons, Windows doesn't recognize the Ubuntu partition, does it? (i'm installing it on a separate partition EX3 along with a SWAP one). 

The fans are clean and work (but dunno if they work fine or not hehe).

My computer information is as follows :
Pentium4 640 (P) HT 3.2 GHz
1 GB RAM (2 x 512)
160 GB   SATA HD (with a similar external one)
ATI Radeon x1300 Pro 

Any help is appreciated ! 
Thanks guys.

---

### Post by thomasaaron on 2010-04-22
Test the machine to see if it every shuts down with Ubuntu. If it does, I'd start suspecting hardware.

Running memtest86 would be a good idea, as would be running diagnostics on your hard drive.

---

### Post by hexwind on 2010-04-22
> **thomasaaron said:**
> Test the machine to see if it every shuts down with Ubuntu. If it does, I'd start suspecting hardware.

Running memtest86 would be a good idea, as would be running diagnostics on your hard drive.
Can it be due to lack of RAM or Graphic memory? 
memtest86 would solve problems on my RAM or hard drive?

---

### Post by Herman on 2010-04-22
The first thing I do for most computer problems is try a different operating system, such as an operating system in a Live CD and see if the problem persists or not.
Obviously, if the computer works better with the Live CD operating system running it, it's either a hard disk problem or an operating system problem with the OS in the hard disk.

I agree with the other posters, it's a good idea to run memtest86+ and test your computer's memory modules.

If you boot into the computer's BIOS and take a look in the hardware monitoring section of your BIOS, you might be able to watch your voltages, fan speeds and temperatures. If you watch carefully in there for a while, you may see something wrong like a fan stopping or wildly fluctuating voltages instead of nice steady, constant voltages.

If you have Ubuntu installed in a hard disk or even in a USB, (not in a Live CD), and the computer shuts down while Ubuntu is running, you can go into /var/log and read the bottom of your log files and that may tell you why the machine shut down on you. 

Take the covers off the machine so you can watch the CPU fan and case fans, and either turn the machine around or use a mirror to keep and eye on the power supply fan at the back of the machine. Monitor whether or not all of your fans keep spinning. 
Sometimes you might only need to clean dust out of the machine if it's shutting down due to some part overheating, other times you might need to replace a fan, those are cheap and easy to replace. One machine I fixed had a dead lizard stuck in the power supply fan and all I had to do was remove that and the machine worked okay after that.

You may need to take  your PC to somebody who is qualified to work on the hardware, especially if it's a new machine and still under warranty. If you don't know what you are doing, don't touch anything inside your machine without the help of someone more experienced or without reading a lot first.
If you have an older machine or one you built yourself, and you have the required skills, you could try a different power supply to see if the machine works better with a different power supply.
Faulty power supplies are quite common and a replacement power supply is relatively cheap.

Usually, the problem is not in the motherboard, but that's a possibility to consider, (last). Sometimes unplugging things and plugging them back in again helps, and sometimes it happens that you can dismantle a computer, clean all the parts and re-assemble it and it will be fixed without replacing any parts. I don't know how to explain that except to say it seems like connectivity problems, I imagine caused by parts expanding and contracting, and dust particles working their way into the cracks in between the expanding and contracting parts, I'm not sure. What I do know is that uplugging things and re-plugging sometimes does often cure problems without any expense, (except your time if you have the skills to do it yourself, it could cost you some money if you need to pay a technician to do it for you). :)

Another machine I fixed had the CPU fan running erratically and stopping, and replacing the fan didn't help, it was the motherboard's control of the fan that was faulty, but rather than replace the whole motherboard just for that reason, I rewired the fan to a molex connetor and plugged it directly into power from the power supply so it would no longer be under the motherboard's control, (or lack thereof), and just runs fast all the time as long as the computer is turned on. It consumes more energy, but the computer keeps running, and it's cheaper than replacing the motherboard.

---

### Post by hexwind on 2010-04-22
Thanks ! 
The problem is, Ubuntu works FINE 99% of the time, I remember it shut down by itself only once, and today while installing Windows 98, browsing the forum and running emesene. that's why I posted here, coz it didn't only affect Windows, but it did so to Ubuntu (although it was just twice).

---

### Post by tgalati4 on 2010-04-22
Sounds like a power supply.  All it takes is for one capacitor to go then the power supply will shut down suddenly to prevent a MOSFET fire.

Sounds like Windows 7 put the hex on your older hardware.

Take the PS apart, clean it and look for leaking/bulging capacitors.  Resolder any poor connections on the board, especially around hot components.

---

### Post by Herman on 2010-04-22
A friend of mine has a laptop that has Windows 7 and it keeps shutting down at random,or so it seems, but it runs a Ubuntu Lucid Lynx Beta2 Live CD just fine.
We're waiting for Lucid to be released and then we'll wipe Windows 7 off his hard disk and install Ubuntu instead. :)

---

