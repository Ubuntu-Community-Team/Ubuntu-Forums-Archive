---
title: "When to choose 64-bit and 32-bit Ubuntu"
date: 2010-04-26
forum: General Help
---

### Post by Sven6210 on 2010-04-26
I have a very simple question but I was not able to find any answer here in the forum - even though I am quite sure the issue has been discussed before.

I intend to switch from Windows XP to Ubuntu 10.04 on my main laptop (so far I only use Ubuntu on my netbook). But I am not sure whether the 32-bit version or the 64-bit version are better suited for me. Can anybody tell me under which circumstances I should use the 64-bit version and under which circumstances it is better to stick to the 32-bit version?

Another question I have: Can an Windows XP in a virtual machine access all the hardware. I am aware of the fact that it will not have full speed with the graphic processing unit (3D effects). I will still need to use Windows XP for some applications and I am not sure whether a dual boot or virtual machine are better suited. Does anybody have advice on that?

Thank you for your help

Sven

---

### Post by Grenage on 2010-04-26
If your processor is AMD64-capable, use AMD64.  I know that's a bit blunt, but unless you have a particular reason not to, it's usually a better choice.

---

### Post by P4man on 2010-04-26
Is it for the netbook in your signature? I dont think it supports 64 bit, but I could be wrong.

As for which is better; generally 64 bit is better (if your system supports  it), as it usually gives a small performance boost. Its definitely the way to go if you have >3GB ram. There are some minor downsides (flash may act up a bit more often even than on 32 bit) but generally there is little reason not to pick 64 bit when you have the choice.

> 
Another question I have: Can an Windows XP in a virtual machine access all the hardware. I am aware of the fact that it will not have full speed with the graphic processing unit (3D effects). I will still need to use Windows XP for some applications and I am not sure whether a dual boot or virtual machine are better suited. Does anybody have advice on that?


No, it cant access your hardware directly. There are pass through's for USB though, although I think that still requires the PUEL version from virtualbox, and not the version in the repositories (or has that been changed meanwhile?). What other hardware would you want it to access directly?

---

### Post by rem on 2010-04-26
I had the 32 bit as well as currently running the 64 bit version of Karmic. I can honestly say, I am happier with the 64 bit performance and speed. Besides this, had no problems installing or running any software so far or doing whatever I needed to do with my computer.

---

### Post by 3rdalbum on 2010-04-26
If it's a 64-bit capable CPU (Intel Core 2 or Core i3/5/7, AMD Athlon64/Sempron/Phenom/Turion or later) and you have more than 1 gigabyte of RAM, then you can use 64-bit. There are no really strong reasons to go 64-bit over 32-bit or vice-versa, except that 32-bit Debs are slightly more common, and 64-bit can address 4 GiB of RAM and more.

Certain Intel Atom CPUs support 64-bit, but I think it's only the ones you're likely to see in "nettop" devices (not netbooks). I would stick with 32-bit on Atom-based systems anyway as you're not likely to see any performance improvement with 64-bit there... possibly degradation.

Otherwise, if it can use 64-bit, you might as well just go for it.

---

### Post by ibuclaw on 2010-04-26
No difference between 32bit or 64bit, other than 64bit applications technically takes up more memory - what with larger addresses and data types - and requires a little bit more disk space, as you'll probably need 64bit libraries *and* 32bit compatibility libraries required side-by-side to allow 32bit applications to run.

Both however are very transparent to the user - and chances am you won't notice really notice the difference. :)

Oh, and using 64bit if you have greater than 4GB RAM is a myth. 32bit is more than capable of using more than 4GBs if you have a PAE enabled kernel. ( Lookup linux-image-generic-pae ).

Regards

---

### Post by Grenage on 2010-04-26
PAE is a dirty hack, but it's nice to have something to fall back to *if* you have no choice.

---

### Post by rem on 2010-04-26
> **ibuclaw said:**
> Both however are very transparent to the user - and chances am you won't notice really notice the difference. :)

well, it really does makes a difference for me when encoding video files or extracting large archives ... besides that, if you have a capable 64-bit CPU why not using 64 bit software? :)

---

### Post by P4man on 2010-04-26
> **ibuclaw said:**
> No difference between 32bit or 64bit, other than 64bit applications technically takes up more memory - what with larger addresses and data types - and requires a little bit more disk space, as you'll probably need 64bit libraries *and* 32bit compatibility libraries required side-by-side to allow 32bit applications to run.

The larger memory requirements are pretty marginal. If you got more than 1 GB, it becomes irrelevant. The upshot can be quite significant though:
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

64 bit mode offers other improvements as just memory addressing (more registers mostly) and allows compilers to target more recent CPU's since 64 bit code isnt going to run on a pentium 2 anyway. Those things really do help.
> 
Oh, and using 64bit if you have greater than 4GB RAM is a myth. 32bit is more than capable of using more than 4GBs if you have a PAE enabled kernel. ( Lookup linux-image-generic-pae ).

Sure the OS can use > 4GB then, but your apps cant as each process is still limited to a 32 bit address space. There are other pitfalls with PAE like absymal performance and all sorts of issues when you have videocards with >1GB video memory etc. As aleady said, PAE was just a hack, about as ugly as EMS memory in the DOS days.

---

### Post by ibuclaw on 2010-04-26
> **rem said:**
> well, it really does makes a difference for me when encoding video files or extracting large archives ... besides that, if you have a capable 64-bit CPU why not using 64 bit software? :)

Proprietary Software (ie: Flash). No that is not the only example of such a software, and yes I am aware of a 64bit prerelease. :)

---

### Post by 98cwitr on 2010-04-26
The only practical reason to go with a 64bit OS is for RAM utilization over 4GB...if you don't have => 4 GB of RAM there is NO POINT in going with a 64bit OS.

---

### Post by jerome1232 on 2010-04-26
> **ibuclaw said:**
> Proprietary Software (ie: Flash). No that is not the only example of such a software, and yes I am aware of a 64bit prerelease. :)

It's no more buggy than the 32 bit version in my experience. There are extremly few pieces of software that you cannot get to run in the 64 bit version, I don't think I've actually run into one before.

---

### Post by Grenage on 2010-04-26
> **98cwitr said:**
> The only practical reason to go with a 64bit OS is for RAM utilization over 4GB...if you don't have => 4 GB of RAM there is NO POINT in going with a 64bit OS.

That's not true, AMD64 generally performs tasks a little faster.

[QUOTE=jerome1232]It's no more buggy than the 32 bit version in my experience. There are extremly few pieces of software that you cannot get to run in the 64 bit version, I don't think I've actually run into one before.[/QUOTE]

I agree; it used to be hit and miss, but most users won't encounter any problems.

---

### Post by Paddy Landau on 2010-04-26
> **Sven6210 said:**
> I am not sure whether a dual boot or virtual machine are better suited.
If you will use Windows only occasionally, and you have sufficient RAM and CPU speed, go for virtual machine.

Otherwise use dual boot, as you'll get the native Windows.

Also check whether the Windows software you need will run under Wine. (I strongly recommend that you use [PlayOnLinux]("http://www.playonlinux.com/"), which is a front-end to make using Wine very easy.)

---

### Post by 3rdalbum on 2010-04-26
PAE is a solution, but I'm unsure about how well proprietary drivers work with it. Apparently on Windows you need special drivers to be able to deal with it.

---

### Post by rem on 2010-04-26
> **ibuclaw said:**
> Proprietary Software (ie: Flash). No that is not the only example of such a software, and yes I am aware of a 64bit prerelease. :)

when you're right, you're right. lucky me i don't have to use too much of that proprietary software (even the flash pre-release works great). after all, my experience using the 64bit version is a success...

---

### Post by Sven6210 on 2010-04-26
Thank you for the feedback so far. Actually there might be a misunderstanding. I have Ubuntu 10.04 on my netbook in the 32-bit version already. Now I plan to install it on my main laptop with a Core 2 Duo which should support the 64-bit version.

Actually I will give the 64-bit version a try. If I go the step, why not fully getting it.

Would I be able to use iTunes in a virtual machine synchronizing with my iPod? And how do you do to access data from Ubuntu and Windows XP at the same time? Do you put all data on an NTFS partition that you will mount into Ubuntu? And can a virtual machine access such data from a physical NTFS partition?

Thank you for your help

Sven

---

### Post by P4man on 2010-04-26
> **Sven6210 said:**
> 
Would I be able to use iTunes in a virtual machine synchronizing with my iPod? 

Should work. But you may need the PUEL version of virtualbox from their website, as the one in the repository doesnt support passthrough of USB devices (or at least didnt, Im not sure if that has been changed, can anyone confirn ?)

I also read in Lucid (10.04) you have to run "sudo hald" before running virtualbox to get USB devices to work, although I suspect they will fix that in VB eventually.

> And how do you do to access data from Ubuntu and Windows XP at the same time?  Do you put all data on an NTFS partition that you will mount into Ubuntu?

Yes ubuntu can read/write ntfs. you can reconfigure the Music, Images, Documents etc folders to point to your existing windows folders. Of course if you get a virus in windows... 
> 
 And can a virtual machine access such data from a physical NTFS partition?

AFAIK, no (edit: unless its an USB drive). But you can let ubuntu mount it, and share it with the VM.

---

### Post by Ein2015 on 2010-04-26
When in doubt, I always choose 64bit. I go to 32bit only if there are problems.

---

### Post by Paddy Landau on 2010-04-26
> **Sven6210 said:**
> Would I be able to use iTunes in a virtual machine synchronizing with my iPod?
I don't know the answer, but apparently 10.04 comes with built-in support for iPod (but not iTunes).

---

### Post by interval1066 on 2010-04-26
> **98cwitr said:**
> The only practical reason to go with a 64bit OS is for RAM utilization over 4GB...if you don't have => 4 GB of RAM there is NO POINT in going with a 64bit OS.

Wrong. Using a 32 bit os with your 64 bit is like computing with one arm tied behind your back. You're best bet is to fully utilize your hardware to its recommended extent, and as a long time user of amd64 ubuntu on my 64bit dual-core athlon it works fine, and I actually forget about my hardware bit width until I actually do something that forces me to remember, like when I need to install a 32 bit hardware driver (like when ndiswrapper has to come into play), but that's very rare. Use the 64 bit stuff when you can, 32 bit when you have to.

---

### Post by Irony on 2010-04-26
I'm using 64 bit Karmic on an a quad core i5 processor. In terms of usage difficulty I haven't really noticed a difference compared to 32 bit. I'm using the 64 bit firefox from the ppas and find that 64 bit flash and 64 bit java to be fault free.

64 bit helps with media processing like encoding videos, GIMP is really quick, OOo 3.2 is fast from the ppas, boot up is faster than Windows 7. I can access NTFS files with no problem.

I've also noticed that quite a few .debs are 64 bit, just installed Dropbox which has 64 bit option.

---

### Post by Paddy Landau on 2010-04-26
> **Irony said:**
> ... boot up is faster than Windows 7.
Well, duh! :wink:

My 32-bit Hardy boots up eight times faster than Windows Vista did on this machine.

---

### Post by Grenage on 2010-04-26
Windows7 boots up slightly faster than Ubuntu 9.10 (for me), it seems to vary a lot.

---

### Post by Calash on 2010-04-26
Go 64.  We are fast approaching the end of life for 32bit operating systems.  If you migrate now you will be ahead of the curve and will not have to worry about it as technology progresses.

---

### Post by julianb on 2010-04-26
> I don't know the answer, but apparently 10.04 comes with built-in support for iPod (but not iTunes).

To be more specific: Developers say that Songbird, the free software alternative to iTunes which comes with Ubuntu10.04, supports iPod synchronization

---

### Post by Irony on 2010-04-26
> **Paddy Landau said:**
> Well, duh! :wink:
Not sure what you are implying, but Karmic is the first version of ubuntu that has booted up faster than windows on my machine. Windows 7 boot is faster than XP yet Karmic is considerably faster than Windows 7.

---

### Post by Paddy Landau on 2010-04-26
> **Irony said:**
> Not sure what you are implying...
Just being ironic (ironically coincidental with your username). Don't read too much into it.

---

### Post by Sven6210 on 2010-04-27
Just a remark concerning boot time - try Ubuntu 10.04. It's amazing fast, on my EeePC 900A it boots in something like 20 seconds. And I mean I can really work then, open Thunderbird or Firefox directly.

My Core 2 Dua needs at least 1 Minute - rather more. Even after the desktop is there it still takes 20 seconds or more until you can start surfin. But I admit that it's also time for a new installation. If I do not reinstall Windows XP after 9 month it gets slower and slower - even though I can not find any malware on my system.

Even my EeeBox in the living room with Windows XP gets slower and slower and it is only used for iTunes and to download form my online VCR - no other applications or web service are used.

Ubuntu 10.04 is amazingly fast.

---

### Post by Sven6210 on 2011-05-17
Now after one year of experience with Ubuntu 10.04 LTS on my major laptop:

[LIST]
[*]I installed the 64-bit version and I never regretted it - it works very well and I would never install any 32-bit version on a 64-bit CPU. If the machine has 64-bit use 64-bit for the OS as well
[*]I installed Ubuntu 10.04 LTS and Windows 7 (both 64-bit) in the dual boot. I hardly use Windows 7 and do nowadays most transactions with Ubuntu. Only few times I still need Windows for one reason or the other, mostly very short term only
[*]Also my Ubuntu 10.04 LTS got slower regarding start-up, probably due to additional installed software, e.g. KVM for virtual machines. However Ubuntu still starts up much faster than Windows 7 - less than half the time
[/LIST]

---

### Post by Paddy Landau on 2011-05-17
I concur. There was a brief problematic period when Adobe released a dud 64-bit version of Flash, but that has since been resolved.

I can't imagine why you'd want 32-bit on a modern machine.

---

