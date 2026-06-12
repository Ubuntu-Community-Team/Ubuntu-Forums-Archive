---
title: "Need Win4Lin enabled Kernel For Ubuntu!"
date: 2005-02-19
forum: General Help
---

### Post by mhancoc7 on 2005-02-19
I have been trying to get Win4Lin going. I have tried compliling my own custom lib, but can't get it to work.

I then found a post on this forum that had a custom Ubuntu Kernel for Win4Lin attached so I downloaded it and installed it, but when I run the Win4Lin installer it tells me that the Kernel is not Win4Lin enabled.

I have downloaded a generic rpm kernel from the netraverse website and tried to convert it to deb, but I can only seem to get it extract the file.  I have tried the following lines:
sudo alien *.rpm
sudo alien -d *.rpm
sudo alien -i *.rpm
sudo alien --to-deb *.rpm

All of these just extract the file. I can't get it to create a deb kernel package. What am I doing wrong?

I have also downloaded the only deb kernel from netraverse in the Misc. downloads section, but it will not install.

I would love to leave Windoze behind forever, but there are some programs that I can't give up. I REALLY need to be able to run Win4Lin. Can someone please help me out with this. If I could just get one of the generic kernels from netraverse converted to deb.

Thanks in advance for any and all help, Jereme :grin:

---

### Post by sleepyhead on 2005-02-20
I don't know if this helps out at all, but the newest version of Win4Lin does not require any changes to the kernel, at least according to their website ([www.win4lin.com](www.win4lin.com)). The new version supports Win2K in addition to Win9X as guest OS's, and should be available this week.

Also, you might want to check out QEMU. I've been playing around with, but haven't got it working correctly yet. BOCHS is another option.

---

### Post by waratah on 2005-02-20
Just curious do the programs that you cannot live without run in wine?   This would be the best way to do this.   wine is a fairly complete method of running windows executables under Linux.

---

### Post by mhancoc7 on 2005-02-23
Well I really need Win4Lin for what I am wanting to do.

Thank you for all your help. I did finally get Win4Lin working, but unfortunately not with Ubuntu. I got it working with MEPIS. I really like Ubuntu, and will be keeping my eye on it. For now I am going to give MEPIS a shot since it is working for me now. If Ubuntu was Win4Lin ready out of the box I would choose it. I know many of you would say just leave Windoze behind, but I don't think that is very realistic. Until I can run all the programs that I use day to day in Linux then I must have some sort of bridge between the Linux and Windows and Win4Lin is it. I wish you all well and I hope that Ubuntu will continue and grow.

God Bless, Jereme:)

---

### Post by bobnielsen on 2005-03-02
'I don't know if this helps out at all, but the newest version of Win4Lin does not require any changes to the kernel, at least according to their website ([www.win4lin.com)](www.win4lin.com)). The new version supports Win2K in addition to Win9X as guest |OS's, and should be available this week."

The new version )Win4Lin Pro) apparently works with W2K and partially (so far) with XP, but not 9X.  

I installed the W4L Home Edition ($29.95) and used their generic 2.6.8.1 kernel (converted with alien to a .deb), which appears to work just fine in Ubuntu Warty. 

I am  also compiling a new 2.6.8.1 kernel from patched Ubuntu source to get a comparison.   If that works well I may  try upgrading to hoary and patching a newer kernel (2.6.11, if the patches are available, otherwise 2.6.10).

Although it probably wasn't necessary, I redid the links to /etc/init.d/Win4Lin to be more in line with the Debian/Ubuntu method.

---

### Post by mhancoc7 on 2005-03-02
I appreciate the info. I did check out the new win4lin site and it looks really good. The ability to run XP is nice too. For now though I am going to stick with SimpyMepis. I have been able to get most everything setup with it pretty easily. I was able to get my Sony Clie syncing. I have also got ACPI working properly. I never really got that issue fixed in Ubuntu. I am not trying to down Ubuntu. I really like it. In a lot of ways it is like comparing apples to oranges. I really like the clean, uncluttered simplicity of Ubuntu, but for now Mepis is meeting my needs. I plan to keep my eye on Ubuntu though. :)

God Bless, Jereme

---

### Post by hazza96 on 2005-03-12
[QUOTE=sleepyhead]I don't know if this helps out at all, but the newest version of Win4Lin does not require any changes to the kernel, at least according to their website ([www.win4lin.com](www.win4lin.com)).[/QUOTE]
I looked on their web site and don't see that information anywhere.

---

### Post by Xian on 2005-03-12
[QUOTE=hazza96]I looked on their web site and don't see that information anywhere.[/QUOTE]
*"Win4Lin Pro&#8482; is the flagship product of the Win4Lin product family. Using Win4Lin&#8217;s high performance virtual computing environment (VCE), Win4Lin Pro runs virtually any Windows 2000 or Windows XP application as intended, without the need to patch the host operating system (e.g. no need to patch the Linux kernel). This next generation product is the perfect solution for the technical workstation, home, or enterprise Linux user."*

- [WIN4LIN PRO Overview](http://test.win4lin.com/index.php?option=content&task=view&id=64)

---

### Post by hazza96 on 2005-03-21
Dam, I should have not been such a scrooge and forked out the money for the Pro version. I have had so many problems trying to install the win4lin 9x I would have saved time and money by spending the little extra.

Now I have to figure out how to just pay the difference and get Pro.

---

### Post by vtrac on 2005-04-13
[QUOTE=hazza96]Dam, I should have not been such a scrooge and forked out the money for the Pro version. I have had so many problems trying to install the win4lin 9x I would have saved time and money by spending the little extra.

Now I have to figure out how to just pay the difference and get Pro.[/QUOTE]
 I've got Win4Lin Pro running Win XP Pro on my 1.6 Ghz Pentium M with 512 megs of RAM, and it's terrible.  The install took about 2 hrs, and Windows craws.. it's not even usable, IMO.  It feels like windows is running on a Pentium II 400mhz with 64 megs of RAM or something.  I've tried VMWare in the past, and that was significantly faster.  I sure hope there is something wrong with my Win4Lin, otherwise, I will have to say that it is not a good product.  Maybe I should try Win4Lin for Windows 9x.

---

### Post by Dana on 2005-04-15
I have heard there are a lot of complaints about Win4lin Pro, perhaps it was released before it was ready. On the other hand I keep hearing good things about Win4lin 9x.

---

### Post by mhancoc7 on 2005-04-15
I am using Win4Lin for Win98 and it is running absolutely great. I have an old Compaq Armada 1750 with 500mhz processor and 192 mb of RAM. Win4Lin runs great. I am using it with SimplyMepis. I switched to SimplyMepis because there was no need to mess with the kernel. It was already Win4Lin ready. I am a newbie and I got a little in over my head trying to get Win4Lin running with Ubuntu.

Jereme  :smile:

---

