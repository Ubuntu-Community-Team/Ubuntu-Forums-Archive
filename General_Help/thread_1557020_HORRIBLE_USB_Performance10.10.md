---
title: "HORRIBLE USB Performance10.10"
date: 2010-08-20
forum: General Help
---

### Post by wtfN00b on 2010-08-20
Uh why does Ubuntu 10.04.1 x86 run like dog **** on USB flash?

Heres what happens, system runs for 10 seconds, freezes for 5, on and on and on, its horrible and basically a useless install,  an endless loop of frustration and system halts.. Is there a special distro or version for USB installs?

Coz installing off the 10.04 cd directly to a 4gb U3 USB stick runs like a DOG POO!!

Yes its USB 2.0, and it should not be doing this, any help, I almost went apeshit insane that after a 2 hour install process, thats the results I got.

Celeron D 2.8ghz/512mb ram, no hard disk, U3 4gb USB 2.0

Im running puppy linux now and I have no hard disks, and since Ubuntu is clearly superior, would be nice to know what Im missing here or of this is a bug specific to my platform.

---

### Post by davrosuk on 2010-08-20
10.10 is still in alpha and should not be used for any real world application. 10.04 is the latest release - I'd suggest trying that.

---

### Post by wtfN00b on 2010-08-20
whoops my bad it is 10.04.1, and yes indeed houston we have a usb problem

---

### Post by LowSky on 2010-08-20
Not all USBdrives are created equal. Just because it is USB 2 doesn't mean that its very fast. I know this isn't something most manufacturers or even retail stores mention but some drive can only handle reading at 5-11MB/sec while other can breeze through reading at 35MB/sec, dont forget write speed are much slower.

You are also are using a Celeron and 512MB of RAM. You are realistically at the bare minimum for RAM and Celerons are not known to be fast chips. These days Ghz really don't mean as much as they used to. Things like How many cores, Cache size and the Front Side Bus are becoming very relevant.

I'm sorry this isn't the answer your looking for but you are comparing Puppy which at full install in a few hundred MB, to Ubuntu which at full install takes up a few GB. 

You should not install to an USB drive without taking a few precautions, like not using SWAP, especially if your computer has so little RAM, it will try to use SWAP and it will really lower performance in your case.

---

### Post by wtfN00b on 2010-08-20
" You are also are using a Celeron and 512MB of RAM."

Dude its not a Socket 370 celeron, lol, its a Socket 775 Celeron D 2.8ghz, cmon man, im not gaming here.

Its a U3 usb drive, the poor performance has nothing to do with the machine.

this is something different, your generalization of my problem does nothing to adress this clear issue with Ubuntu on USB flash. I appreciate your insite, but im an A+ certified tech with 10+ years experience, and this aint normal.

This is definatly an Issue with the OS.

Perhaps the way Ubuntu handles the swap file is causing the issues. Or has it really became a memory PIG??
RAM , thats the one thing I think you hit on the head that is likely a primary factor here due to the OS.
And yeah paging the **** out of a usb drive would do it.

BTW, Puppy handles swap file just fine. U guys might wanna take a note from them. HEHEEHE I couldnt resist, been using puppy for a while now and im gettin sort of loyalist. hehe.

---

### Post by kevinatkins on 2010-08-20
I've noticed that, even with a normal hard disk installation, USB performance over the last few releases has been abysmal, on more than one machine and with a variety of USB flash drives.

In fact, USB 2.0 often doesn't work at all and I've had to switch my motherboard back to USB 1.1 support... This appears to be a kernel problem, and it's in bug reports for various distros all over the web.

For now, I make do with USB 1.1 and accept that file transfers (writes) to USB are appallingly slow. There's *no way* I'd want to try running Ubuntu from a USB stick at the moment!

---

### Post by wtfN00b on 2010-08-20
Yeah thanks Kevin, now I dont feel like im going crazy the only one whos noticed this, I mean, this outta be a big enough deal to get fixed for such a neccesary function,

I did see lots of posts about poor USB performance for the Ubuntu 8/9 series, but couldnt find anything newer. Your post has helped validate my complaint, thank you.

---

### Post by kevinatkins on 2010-08-20
> **wtfN00b said:**
> I mean, this outta be a big enough deal to get fixed for such a neccesary function,
Couldn't agree more - it's very frustrating, and very bad news that Linux can't even get USB 2.0 right when USB 3 is already out there....

Further compounding the issue is that Ubuntu now builds the relevant USB modules right into the kernel, so I can't unload the USB 2 module and reload as required, like I could as a workaround before - I now have to resort to disabling USB 2.0 altogether...

---

### Post by clhsharky on 2010-08-20
USB ports not receiving required power for usb2 will result in fallback to usb1.1's lower requirements. 
Its a hardware and  software requirement for "continue of use" and compatibility.
This is a known problem on many laptops, some low end motherboard and inadequate power supply's.
Hardware does degrade, and all so same issue with MS.


Sharky

---

### Post by wtfN00b on 2010-08-20
Great information to add to this discussion sharky, 

In all fairness to the developers, I believe this is an issue that should be looked at further, and tests conducted in a lab, to determine if this is truly a USB/software issue in the OS itself, or, other issues such as Lack of system memory and increased Page file usage.  Even USB 2.0, might not have the bandwidth to keep the system running smoothly during such heavy paging conditions. However, I must say, I am  not convinced of any theory conclusively, as all the other OS Ive used on USB flash do not have this an issue of this severity when swap file is enabled. 



One other thing, that could possibly be a factor, is we have all become reliant on linux distros for, historically speaking, being able to give new life and run well on older systems, this trend may have, or be, drawing to and end. Or at least be a somewhat of a factor in this debate,

Anyone got the equipment to run some tests?   I would say lets do it.

---

### Post by davrosuk on 2010-08-20
I'd add to all this that Ubuntu is pretty full fat - I'm pretty sure that the recommended minimum specs are 1GB of RAM these days. Whilst I'm sure it can be run on less, its going to perform worse - and running from USB this issue is only going to be compounded - possibly as you've found to the point of being unusable.

You might want to see how things perform running Lubuntu which is supposed to be a less resource hungry spin. Maybe try comparing that and/or Fedora 13* to see what happens. :-)

* to see if its *buntu specific

---

### Post by Grenage on 2010-08-20
I found 9.10 to be pretty poor at running full USB2 speed, half the time it would detect drives as USB1.1.

I've not had these problems with 10.04, and my colleague runs a copy on USB.  "It works here" is never that helpful, but it gives you more data to run with.

None of the above has been done on older hardware; all machines have been Quad cores with at least 4GB RAM.

---

### Post by tampablendie on 2010-08-20
I can confirm that this is an OS issue.  I have Ubuntu running on 4 machines and the USB transfer rate is great on all of them except my gaming rig.

xfx x58i
12 gigs of ram
core i7
ubuntu USB transfer rate 4-5 mb/sec ROFL!!!
Vista Ultimate transfer rate 30+ mb/sec

I have had this issue for the past 3 distributions and none of the developers really seem to give a s!&t, as all the launchpad bug reports are listed as low importance!  "USB fully functional on all systems, who the heck needs that?  We need WOBLY WINDOWS NOW!!!!!"

---

### Post by davrosuk on 2010-08-20
> **tampablendie said:**
> I can confirm that this is an OS issue.  I have Ubuntu running on 4 machines and the USB transfer rate is great on all of them except my gaming rig.

xfx x58i
12 gigs of ram
core i7
ubuntu USB transfer rate 4-5 mb/sec ROFL!!!
Vista Ultimate transfer rate 30+ mb/sec

I have had this issue for the past 3 distributions and none of the developers really seem to give a s!&t, as all the launchpad bug reports are listed as low importance!  "USB fully functional on all systems, who the heck needs that?  We need WOBLY WINDOWS NOW!!!!!"

If it works on 3 out of 4 machines okay then that suggests hardware not the OS... ;-)

In fairness its probably a combination of the two - ie some hardware not working fully with the current kernel. My theory is kind of supported by your observations. 

I'd be interested to find out how it performs under 10.10 as it uses the 2.6.35 kernel, which I know has had a lot of improvements for Nehalem & Westmere architectures.

---

