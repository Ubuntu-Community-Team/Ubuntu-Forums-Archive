---
title: "A series of glitches"
date: 2009-07-18
forum: General Help
---

### Post by Vignesh S on 2009-07-18
Alright, where do I begin? Oh yes, it all began when I upgraded to the next version of VirtualBox (version 3.02) from 3.0.0. None of the virtual machines would work. Since I had the trial of VMware workstation on me (but was refusing to even load up), I went to Synaptic Package Manager to install what I thought were the required packages. Now this is where the glitches begin. The Synaptic Package Manager just froze up and presuably crashed. This meant that whenever I went to it again, it came up with some sort of error message and it told me to type something into the terminal (sudo dpkg -configure --a). I did, but it said that the file had an error on it near the second line! So that meant that it wouldn't even let me fix up the problem! This also meant that I couldn't install anything either, becuase dpkg was wrecked now!!!

So there was only solution: to reinstall Jaunty. But transferring my important files onto my 16GB Sandisk Cruzer Contour was going to prove to be hard, because at random times, the transferring meter would just stop, or it would even crash the computer!!! In the end, I managed to take the files out via the Ubuntu 8.10 Live CD! But the glitches don't stop there.

I wanted to downgrade from 64 bit Ubuntu to 32 bit because some of the drivers I needed are only available on 32 bit. But 32 bit Jaunty turned out to be impossible to install because within the first few minutes of clicking on Install Ubuntu, it wouldn't work because the installer just kept on crashing. This was also the case with Ubuntu 8.10 and 8.04. I just don't get it. I mean, previous to this, 32 bit Windows XP was also working too, and I thought that would be even more of a reason for Ubuntu to work! Looks like Pentium Dual-Core doesn't like 32 bit. So I decided to stay with 64 bit, and I tried to install that. Everything was going fine, until the partitioning step. It just froze. Same story with 8.10 and 8.04. Maybe it was because the installer wasn't doing a good enough job of formatting. So I decided to install Windows XP to clean it out entirely (the formatting is WAY more thorough on XP). The installation crashed (in other words, it came up with the BSOD while it was copying files), but it was after the formatting. 

So I went to Ubuntu 9.04 64 bit again, and it does exactly the same thing! Now trying 8.10 at the moment, and it doesn't seem to be working either. I am on my last straw here, and my Dad's faith in Linux (let alone Ubuntu), has gone down the drain. I need to know what the problem is here, because this is my computer, and I really need it for school purposes. Surely the Synaptic Package Manager crashing can't just stuff the entire system? This has never happened before with Ubuntu on my Desktop PC, or any other computer I have installed Ubuntu on. 

I don't care if the solution is either free of if I have to pay for it, all I care is that I am back on the road as soon as possible!

In case you need my machine specs. here they are:
Asus P5VD2-X motherboard
2GB DDR2 RAM
320GB hard drive
Dunno what graphics card, but I know it is Nvidia and the Ubuntu driver I used was 9600 driver (or something like that)

---

### Post by oldos2er on 2009-07-18
Can you please copy and paste the output of **sudo dpkg --configure -a** ?

---

### Post by jeppewinther on 2009-07-18
This is starting to smell a bit of Hardware issues. Do you have the means to do a bit of diagnostics on those? A spare harddrive and a screwdriver, and so on?

---

### Post by Arup on 2009-07-19
Go to the BIOS and disable legacy USB support, your file transfer issue with the usb thumb drive should work out then.

---

### Post by moster on 2009-07-19
Run complete computer test from ubuntu cd. Just to be sure there is no chipset/memory errors.

---

### Post by Vignesh S on 2009-07-19
Ok then, lets take this one by one. 

As I said, since I have already formatted the disk, there is no way that I can give the output of what error message that came out, though it was something like an error near the second line of the file.

Now, I can do basic hardware stuff (e.g. Hard drive, RAM, etc) but I need to know where the error lies, which I will come back to.

I don't even know what USB legacy support is. A little explaination would be nice please? Also, how do I disable it, and how will it help?

Now, coming back to the hardware, I think that we are onto something here. Got a pic of the mem test going on, and it doesn't look pretty. This is a hardware problem. All I need to know is what exactly the problem is.

Thanks to all who are helping me. You have saved me from chucking out Ubuntu and disregarding it, for it really is a good operating system. After all, there is a reason why I don't use Windows anymore

EDIT: Just realised that I didn't really need the USB legacy support thingy, because as I said, I already managed to take the files out of the computer via the Ubuntu 8.10 live CD

---

### Post by tacantara on 2009-07-19
@ OP:  Once you get everything up and running again, reinstall VB 3.0 (it is still available at their website).  I've had nothing but problems with 3.0.2, and had to reinstall 3.0 to continue using my VB machines.
 
This is not the first case of 3.0.2 problems that have been posted here.  I guess it's time to check and see if a bug report was filed.

---

### Post by Vignesh S on 2009-07-19
This is the image that shows the results of some of the memtest. Sorry if its a bit unclear. I can upload a better one if anyone requests.

---

### Post by Vignesh S on 2009-07-19
By the way, how can I tell if a version of VirtualBox is glitchy or not without upgrading?

In case you are wandering, this is my machine's current status: No operating system is installed, and I think there seems to be hardware problem of some sort, quite possibly the RAM.

---

### Post by moster on 2009-07-19
You have hardware error. It can be only wrong configuration in BIOS or some incompatibility. Ok... lets go from more to less obvius.

If you have more RAM modules or worse different "type" inside, you take it out and leave only one. Run test again to see if there is difference.

Check motherboard manual for RAM settings. RAM can be tweaked or even add little voltage to make it more stable. It is difficult to explain because every board is little specific.

Best try would be with RAM you know it work. And load BIOS defaults.

---

### Post by Vignesh S on 2009-07-20
Yep, I changed everything in the BIOS back to default, though that did nothing. 

Since I had two RAM chips in here, I took out one each time and performed the memtest on each RAM module, and I think that I found my troublesome RAM module.

Just one more thing before I try to convince my Dad to replace the RAM module. As I am typing, I am running the memtest on the module that is OK. So far, it says that only 44% is pass, but it has already done 5 tests and is one the 6th one (22% done). Should I replace that RAM module too, or is that alright to stay, because while both were there, it was performing worse than that. (Now 45% done and 50% pass). Also, there are none of those red things that showed up on the last two memtests (check the image to see what I mean).

Now to see if Ubuntu 9.04 32 bit wants to install...

---

### Post by Vignesh S on 2009-07-20
Ubuntu 9.04 64 bit is currently installing as I type. I was hoping that getting of the glitchy module of RAM would finally let me do that, but obviously, it doesn't my motherboard and Pentium Dual Core very much. Is this just a glitch in 9.04, because I remember my friend coming around to install 8.10 on my computer (that was when I was a Linux newbie, now I am quite far from that), and I am pretty certain that it was 32 bit. In fact, I managed to get my files off the hard drive via the 32 bit 8.10 live CD! It would be nice to have 32 bit, because the Epson CX3900 driver only exists on 32 bit, though if worst came to worst, I guess that I could survive on the 64 bit version. After all, I survived on it for all these months now!

All I am asking is if there is a way to install 32 bit Ubuntu 9.04 onto my machine. The specs of it are on the last page, but here it is again...

Asus P5VD2-X motherboard
Now 1GB DDR2 (the other 1GB was the glitchy module)
Nvidia GeForece 7600GT (or something like that for a graphics card)
Pentium Dual Core

I'll also make a note of the fact that I installed 32 bit Ubuntu 9.04 onto my cousin's machine, and it has the exact same processor. Don't think it had the exact same motherboard, but I'm pretty certain that it was something similar to that.

When my internet download limit refreshes next month, I'll try install 32 bit 8.10 then upgrading it to 9.04, because I might just go over the limit, thus giving me agonizingly slow dial-up like speeds. Pretty sure that it should work. I mean, 8.10 32 bit worked the first time around. Besides, there was also originally 32 bit Windows XP as well.

---

### Post by moster on 2009-07-20
hm.. I do not remember. Be sure to run that memtest at least 1 hour. If you take 1 module out and now is ok, try to again swap modules. If that other suspicious module give you error, then you can say it is bad.

Problem is, that sometimes both modules are OK, but when work in pair errors accord.

In future, when you buy memory, both modules must be same. In that way you will minimise incompatibilities. People do not pay attention and they just add memory with different manufacturrer and maybe slightly different specification and they have problems with computer. That problem can be just like yours. Computer is working, but just not like it should.

If memtest give you no errors, 32 bit ubuntu is preferable. 32 bit Ubuntu IS most stable ubuntu. There is no real need to go to x64 if you have lower then 3 GB of memory no matter what others tell you.

Wish luck :)

---

### Post by Vignesh S on 2009-07-23
I tried to install 32 bit ubuntu, but it came up with some sort of kernel panic. Does that mean that need to replace that RAM module too? I haven't done a memtest yet, trying to avoid doing one, but if I'll do one. Does that mean I need to replace the other RAM module as well? This isn't a big issue, because DDR2 is dirt cheap here. But yeah, I kinda need to know, because I'll be heading to a computer parts seller on this weekend, and I need to know if it needs to be replaced as well.

---

### Post by Vignesh S on 2009-07-24
OK, I replaced all of the RAM modules with a new YeahDome 2GB DDR2 module into my machine.Now, the kernel panic thing doesn't come up now, but it just stays at the loading please wait screen. I thought changing the RAM might help, but obviously, it didn't. This is important, I need 32 bit on this computer. Remember that I installed 32 bit Ubuntu onto my cousin's computer, and it had pretty much the same specs. So I have no idea what the problem is now, but all I know now is that I want answers.

This problem affects the top 3 of the menu options, yet the memtest works perfectly fine. I have no idea what the problem is at all.

---

### Post by moster on 2009-07-25
Or you have some general incompatibility or your cd is badly burned. I cannot think of anything else if memtest runfor 1 hour with no mistakes.

---

### Post by Vignesh S on 2009-07-25
I think it might be a problem with 9.04. The 32 bit cd wouldn't go any further the 'loading please wait screen'. After burning and trying at least around 5 cd's, I decided to go to 32 bit 8.10. And it worked perfectly fine. And I think that its safe to say that this problem is now solved.

One more thing. The same ISO file and the cd's worked perfectly fine on my IBM Thinkpad R31. Dunno what's it with that, but I'm glad that 32 bit is back in business on this machine.

Oh yeah, almost forgot. The time I ran memtest last time came up with no errors. But I think if 8.10 works, then there isn't a problem and it is a glitch with 9.04.

---

### Post by moster on 2009-07-26
That is really strange. Well, glad you sorted everything out. I would on your place download Ubuntu 9.10 alpha, just to try live cd. If you cannot get that working, then you really have some strange incompatibility that you should look into it deeper. Maybe post here full detailed specs of your motherboard, memory, vga..

For example I must install ubuntu on my laptop with special boot parameters or I have problems. It really depends how much you want to deal with stuff like that... but most probably it is solveable.

---

### Post by Vignesh S on 2009-08-08
Might as well tell you moster that 9.10 does work on my computer. So it looks like for now that this problem is solely with 9.04 32 bit.

That's great, considering that I am the type of person that will forgo that rock solid stability for newer technologies and upgrades.

I don't get by what you mean by special boot parameters. Does this mean that I have to go into the BIOS or something? And how can I tell what parameters to put onto my computer?

And by the way, I am willing to delve much deeper into this problem, for it could happen again on 10.04 or another distribution further along the track.

---

### Post by moster on 2009-08-08
> **Vignesh S said:**
> Might as well tell you moster that 9.10 does work on my computer. So it looks like for now that this problem is solely with 9.04 32 bit.

That's great, considering that I am the type of person that will forgo that rock solid stability for newer technologies and upgrades.

I don't get by what you mean by special boot parameters. Does this mean that I have to go into the BIOS or something? And how can I tell what parameters to put onto my computer?

And by the way, I am willing to delve much deeper into this problem, for it could happen again on 10.04 or another distribution further along the track.

When you insert bootable cd and while looking into menu you can press F6, if I remember correctly and try checking "ACPI=off" and see if anything is different. It say in bottom on screen "F6 advanced options" or somethiung like that.

If new version solve your problem it is possible but not likely to this happend again because they constantly add something in kernel and nothing is deleted. When some peace of hardware become compatible, it stay so.

If get some problems in future. Post hardware specs, what you do, and what exactly happend in detail. In that way you have great chance that somebody actually answer you. Instead of "freeze, HELP". :)

---

### Post by Vignesh S on 2009-08-08
Looks like I've just had another very piece of bad luck with 9.04. ([http://ubuntuforums.org/showthread.php?t=1234528](http://ubuntuforums.org/showthread.php?t=1234528) to see what I mean). Is there any hope of getting 9.04 to work past that loading please wait screen?

---

### Post by Vignesh S on 2009-08-13
Don't worry, I managed to get the data out. But I'll try out that tip you gave moster. Hopefully, it should work.

---

### Post by Vignesh S on 2009-08-13
When I later upgrade to 9.10, is it possible to re-enable ACPI? I dunno what it is, but if it makes my computer go faster, then yeah, I kinda would want it back.

EDIT: I tried turning off ACPI, and it worked (at least on the live CD anyway. Making sure all my data is backed up before installing it).

---

### Post by moster on 2009-08-13
> **Vignesh S said:**
> When I later upgrade to 9.10, is it possible to re-enable ACPI? I dunno what it is, but if it makes my computer go faster, then yeah, I kinda would want it back.

EDIT: I tried turning off ACPI, and it worked (at least on the live CD anyway. Making sure all my data is backed up before installing it).

Your computer will not be slower with ACPI off but you cannot use standby or advanced power saving functions like CPU throttling without it. If you are not on laptop, and do not use standby then it is really OK.

you can enable/disable it directly in boot menu when grub ask you for choosing OS or in ubuntu by entering this in terminal and deleting or adding right line.

```
sudo gedit /boot/grub/menu.lst
```

this is my menu.lst. You need to find yours and modify bold line if you want to add/delete acpi off boot option.
```
title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		985cf222-a477-4269-9a7d-bb005de5c527
**kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=985cf222-a477-4269-9a7d-bb005de5c527 ro quiet splash **
initrd		/boot/initrd.img-2.6.28-14-generic
quiet
```

---

### Post by Vignesh S on 2009-11-01
Well, after backing everything up, I'm giving Ubuntu 9.10 a crack. I'm going back to 64-bit because I now do very heavy virtualisation with VMware Workstation, and my Virtual machines are begging for a RAM upgrade. I'll take my computer to the max of 4GB, which is only fully addressable by 64-bit. 

It seems ironic considering how much I have been going on about how I wanted 32-bit to work on my computer. But 64-bit flash player is out, and I don't have the printer connected to my computer, so the two reasons why I wanted 32-bit has vanished. 

Fingers crossed that this might work... I'm desperate. I am the type that likes keeping up with the latest from ubuntu! :-D

---

### Post by Vignesh S on 2009-11-02
YAY!!! YEEHAAA!!!! :-D :-D :-D

Ubuntu 9.10 works on my Desktop, 64-bit that is!!!

AWESOMENESS! Now I officially have the latest Ubuntu release on my computer!

Thanks to all who have helped, past and present!! Ubuntu forums are great :-D

:popcorn:

---

