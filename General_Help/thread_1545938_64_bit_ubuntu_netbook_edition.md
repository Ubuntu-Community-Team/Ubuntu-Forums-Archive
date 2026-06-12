---
title: "64 bit ubuntu netbook edition"
date: 2010-08-04
forum: General Help
---

### Post by joshruehlig on 2010-08-04
I just wanted to bring up that most newer netbooks that have atom n450/n455 or upcoming n470/n475/n550 are all Intel 64 compatible. 

Do you think ubuntu netbook edition should start coming out in 64bit edition as well?

Are there downsides power consumption wise to using 64 bit systems?

(This has been asked alot) Are there advantages of using a 64 bit system when ram is below 4GB?

---

### Post by snowpine on 2010-08-04
Ubuntu Netbook is already available for both 32 and 64 bit:

[http://packages.ubuntu.com/lucid/ubuntu-netbook](http://packages.ubuntu.com/lucid/ubuntu-netbook)

My understanding is that using a 64 bit operating system on a 64 bit processor can be faster for certain types of computations. I have no numbers to back this up however and if you mostly do web surfing there is little advantage. I use 64 bit Debian on my Atom 330 nettop, it is still a very slow processor no matter how you slice it. :)

I think, however, that you are mistaken about one thing: Atom n4xx series is single-core and should use a 32-bit OS. Atom 3xx and D5xx are dual core.

---

### Post by joshruehlig on 2010-08-04
Atom n4xx aren't dual core but they do support intel 64, which means they can run 64 bit os's.
[http://en.wikipedia.org/wiki/Intel_Atom](http://en.wikipedia.org/wiki/Intel_Atom)

I meant the netbook iso available in 64 bit. I know you can just download the netbook packages onto a 64bit build, it just isnt as easy as having it prebuilt and with unity being more integrated into gnome this may be more difficult in the future (10.10).

I dont get why companys get a hardware spec that makes thing better then chooses to still ship 32 bit os's on 64 bit systems (this regards windows systems i have used).

hopefully as more netbooks out there support 64 bit, ubuntu will release a 64bit UNE iso.

---

### Post by CoreyB. on 2010-10-09
> **joshruehlig said:**
> I know you can just download the netbook packages onto a 64bit build, it just isnt as easy as having it prebuilt and with unity being more integrated into gnome this may be more difficult in the future (10.10).

The guide on the Ubuntu Community Wiki will be updated when Maverick comes out.  It is a guide where you install the normal version then just copy and paste 4 commands into Terminal, log out and then log back in and that is it.

[https://help.ubuntu.com/community/UbuntuNetbookEdition/amd64]("https://help.ubuntu.com/community/UbuntuNetbookEdition/amd64")

---

### Post by rudefyet on 2010-10-09
The easiest and cleanest method I've found is to use the minimal amd64 install cd and select Ubuntu Netbook from the tasksel menu

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Also you can use the mini.iso with unetbootin to make a usb stick if you don't have a cdrom.

It took awhile for that page to be updated for Lucid, so if you're looking for a maverick iso and don't want to wait the link is [http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-amd64/current/images/netboot/mini.iso)

---

### Post by joshruehlig on 2010-10-09
Yeah after creating a htpc from a minimal install I think Ill just use this method from now on. Its not too hard and worth it

---

### Post by sendblink23 on 2010-10-09
here is my quiestion, why do you want x64 on a netbook?
Do you have more than 4gb of ram on yours? If not then there is no point of using it, your system hardware will run much better on x86

x64 uses more resources than x86, that is why x86 has a limit of max usable ram.

Trust me even if I have a quadcore or hexacore cpu, if I only have 4gb of ram the system will be much snappier on x86 than on x64 - heck even overclocking the cpu x86 is much more stable(it can reach higher overclocks stable) than x64 - and this is me talking on an overclocked gaming desktop which isn't a tiny small netbook... but since I have more than 4gb of ram then x64 is for me


but ofcourse you can still install x64 for fun

---

### Post by joshruehlig on 2010-10-10
"x64 uses more resources than x86, that is why x86 has a limit of max usable ram."
- I thought 64 bit could allocate more ram because it has 64 bits to code memory use in, instead of only 64. It's not cause someone chose a 4GB limit, its just the limit of using only 32 bit processes.

I thought that using more ram may actually help because on my old (n270, 32bit) netbook I never even use 1/3 of the 2GB ram. I figured the more I can get into ram the faster some things would respond. 

If you have insight on this please explain, I understand that above 3.7ish GB ram you need to use 64bit or a special kernel to utilize it all. Ill do some research on it..

"There are many more general-purpose CPU registers in 64-bit mode. Registers are the fastest memory in your entire system. There are only 8 in 32-bit mode and 16 general purpose registers in 64-bit mode. In scientific computing applications I've written, I've seen up to a 30% performance boost by recompiling in 64-bit mode (my application could really use the extra registers and it wasn't hurt too much by the double-sized pointers)." - [http://superuser.com/questions/56540/32-bit-vs-64-bit-systems](http://superuser.com/questions/56540/32-bit-vs-64-bit-systems)

Here's something else I just found
[http://www.omgubuntu.co.uk/2009/12/ubuntu-64bit-really-is-faster-than-32bit/](http://www.omgubuntu.co.uk/2009/12/ubuntu-64bit-really-is-faster-than-32bit/)

---

### Post by formaldehyde_spoon on 2010-10-10
> **sendblink23 said:**
> here is my quiestion, why do you want x64 on a netbook?
Do you have more than 4gb of ram on yours? If not then there is no point of using it, your system hardware will run much better on x86

x64 uses more resources than x86, that is why x86 has a limit of max usable ram.

Trust me even if I have a quadcore or hexacore cpu, if I only have 4gb of ram the system will be much snappier on x86 than on x64 - heck even overclocking the cpu x86 is much more stable(it can reach higher overclocks stable) than x64 - and this is me talking on an overclocked gaming desktop which isn't a tiny small netbook... but since I have more than 4gb of ram then x64 is for me


but ofcourse you can still install x64 for fun

What a terribly misinformed post!!!

Software compiled for 64 bit can gain performance increases possible from 64 bit hardware regardless of whether you have 4GB RAM.  Being able to address more RAM is not the *only* advantage of 64 bit.  You have more registers, and longer registers. 

The reason 32 bit has a 3-4 GB memory limit is because 2^32 is the largest number it can send down the bus to request data.  It is not related in any way to resource usage.  64 bit also has a memory limit, but it is incredibly large. 

OP please do NOT trust this poster. He is feeding you incorrect information.  The only way it would EVER be even *remotely* possible for a 32 bit OS to outperform a 64 bit OS is if running programs X, Y and Z in 32 bit used almost all, but just not quite all of your memory - then X, Y, and Z in 64 bit *may* be able to use all of your physical memory.
If you can get yourself in this exact situation then: 
 - you are one-in-a-million.
 - you have bigger problems than choosing between 32 and 64 bits - buy more memory immediately.
 - you are still benefiting from the other benefits of 64 bit. 

The choice between choosing 32 or 64 bit Ubuntu is extremely simple: if you have 64 bit hardware (you do) then use 64 bit Ubuntu.  Otherwise you must use 32 bit. 

Edit: @OP I see you've already found some info on 64 bit, good!  Go ahead and install 64 bit, you won't regret it.

---

### Post by joshruehlig on 2010-10-10
Well I get my Intel G2 M SSD on Wednesday, gonna fdisk align some partitions on it, Install Minimal 64 bit ubuntu and add unity interface (and maybe later switch back to gnome). Im excited to see the boot speeds and battery life. Im assuming I gotta put the discard option on each ext4 partition in fstab as well...

Post back with results

---

### Post by Techrocket9 on 2010-10-14
It always amazes me how often I find exactly what I am looking for on the Ubuntu Forums.

I came on here thinking "I bet no one has ever asked for an x64 build of Remix. I'll probably have to make a new thread an hope someone replies." ButI find this.

Awesome.

---

### Post by Skip Da Shu on 2010-12-02
While I personally use, almost exclusively, x64 versions, I am surprised that nobody brought up the old adobe flash issue or other software that's not avail in 64b versions.

---

### Post by joshruehlig on 2010-12-03
> **Skip Da Shu said:**
> While I personally use, almost exclusively, x64 versions, I am surprised that nobody brought up the old adobe flash issue or other software that's not avail in 64b versions.

sudo add-apt-repository ppa:sevenmachines/flash
sudo apt-get update
sudo apt-get install flashplugin64-installer

If you have an nVidia card or broadcom crystal and have the drivers loaded you will now get hardware acceleration! Gonna install my broadcom crystal on my girlfriends netbook and see if she can get HD youtube without stutter

---

