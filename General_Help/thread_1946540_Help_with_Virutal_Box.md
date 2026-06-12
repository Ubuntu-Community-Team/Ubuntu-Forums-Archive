---
title: "Help with Virutal Box"
date: 2012-03-25
forum: General Help
---

### Post by Spewed on 2012-03-25
Hello, 

I currently have a dual boot of Windows 7 and Ubuntu 11.10(upgrading later). I'd like to know if I can run my existing Windows 7 through Virutal Box and access any files I may have installed on the existing OS. It's getting a little tedious switching back and forth from Ubuntu to Windows 7 everytime I need to do something on Windows, particularly some work related things, or something as simple as viewing Netflix, or playing a game I have on Windows that isn't supported by Linux. 

Is it possible to use Virtual Box for this?

Would I be better off using VMware Workstation for this?

---

### Post by Dreamer Fithp Apprentice on 2012-03-25
It is certainly not the conventional way to do it. People will tell you it CAN'T be done that way  but I'm fairly sure it can. The hardest part will be finding the article I read about it because I'm afraid I don't remember where I saw it. But fairly recently, within the last few months, I read somewhere about someone who did just what you are asking about - mounting another bootable partition with windows on it as the hard drive to a VM running in a linux. The problem he had was with the licensing. The windows installation kept asking him to register it every time he booted the VM after having run it directly and vice versa. He went round and round with MS about it. Their position was that he needed 2 licenses. As to the legal side, even God doesn't what the law "is" until the courts have mangled it and decided which shades of red and green are meant by black and white, but he showed that by literal interpretation of the wording of the license he WAS in compliance to run it that way with only ONE license, but the outrageous thing was that regardless of the legal question the MS techs were wrong TECHNICALLY and showed no comprehension of their error when it was explained to them. Two licenses does NOT fix the problem. Shows you the kind of "look it up and give prepared answer #768" TV watching morons they have working at "tech support" for MS. The guy did figure out a hack to make it work. I don't remember the details but the hack wasn't extensive. Something on the order of a small batch file that ran at startup. Sorry I can't tell you where I saw that but now that you know it CAN be done you can sic google on it. I think I read it in some geek blog. Pretty sure it wasn't here. If I run across it again I'll try to remember to post a link here.

---

### Post by Spewed on 2012-03-25
> **Dreamer Fithp Apprentice said:**
> It is certainly not the conventional way to do it. People will tell you it CAN'T be done that way  but I'm fairly sure it can. The hardest part will be finding the article I read about it because I'm afraid I don't remember where I saw it. But fairly recently, within the last few months, I read somewhere about someone who did just what you are asking about - mounting another bootable partition with windows on it as the hard drive to a VM running in a linux. The problem he had was with the licensing. The windows installation kept asking him to register it every time he booted the VM after having run it directly and vice versa. He went round and round with MS about it. Their position was that he needed 2 licenses. As to the legal side, even God doesn't what the law "is" until the courts have mangled it and decided which shades of red and green are meant by black and white, but he showed that by literal interpretation of the wording of the license he WAS in compliance to run it that way with only ONE license, but the outrageous thing was that regardless of the legal question the MS techs were wrong TECHNICALLY and showed no comprehension of their error when it was explained to them. Two licenses does NOT fix the problem. Shows you the kind of "look it up and give prepared answer #768" TV watching morons they have working at "tech support" for MS. The guy did figure out a hack to make it work. I don't remember the details but the hack wasn't extensive. Something on the order of a small batch file that ran at startup. Sorry I can't tell you where I saw that but now that you know it CAN be done you can sic google on it. I think I read it in some geek blog. Pretty sure it wasn't here. If I run across it again I'll try to remember to post a link here.


I've read a little bit about it, and with Virtual Box particularly it seems stressful and hard to accomplish(but what isn't with Ubuntu and Microsfot these days). My primary objective is to alleviate myself of the hassle of logging in and out all the time for simple tasks like watching Netflix or playing a game, though the latter is probably not possible anyway, which is OK to me, I don't play enough to care. But, I also read that it's possible to potentially damage your OS by doing this, and I don't potentially want to take that chance if it's possible. So, given that information is VMware Workstation the way for me to go?

---

### Post by davidvandoren on 2012-03-25
go to the virtualbox website and make sure you download the version with usb support.

Install windows XP on it if you have a cd. 

Else, if you have a full version of windows 7 install that one.

In the virtualbox settings share a folder with your guest system either XP or windows  7.
Point the shared folder to the windows partition you wish to access. 

Don't forget to enable 2 and 3D support for the guest system and to install the virtual additions in your guest system also.


For your original question 

I think Wayland Display Server will be able to do that in the future. 
But I am not sure if I understand the Wayland Display Server implication correctly.

---

### Post by Dreamer Fithp Apprentice on 2012-03-25
> **davidvandoren said:**
> go to the virtualbox website and make sure you download the version with usb support.

Install windows XP on it if you have a cd. 

Else, if you have a full version of windows 7 install that one.

In the virtualbox settings share a folder with your guest system either XP or windows  7.
Point the shared folder to the windows partition you wish to access. 

Don't forget to enable 2 and 3D support for the guest system and to install the virtual additions in your guest system also.


For your original question 

I think Wayland Display Server will be able to do that in the future. 
But I am not sure if I understand the Wayland Display Server implication correctly.

I think there is potential to confuse here.  To make it explicit, the solution above is an ALTERNATIVE to what OP requests, not a way to do what he is trying to do. I did a google search for  +run +windows +partition +from +vm +in +linux (I didn't actually enter the +s -- they are implicit and ixquick startpage google results add them explicitly on the result page) and I found LOTS of hits that do address exactly what OP is asking about, running an EXISTING windows partition (meaning the running the actual working software, the same actual files on the same actual hard disk space, not just accessing the partition contents as data and not creating a second virtual installation just for the VM which would waste disk space and not have the same advantages) from a VM in linux. I can see this approach will have real advantages. If you bookmark something in a web browser or change some setting while using the Windows in VM, those changes will still be there when you boot into the Windows partition directly and vice versa. I like this idea. I think I'll try it as soon as I get another hard drive.

---

