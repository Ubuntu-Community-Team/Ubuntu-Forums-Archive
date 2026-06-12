---
title: "How do I know if I'm running 32 or 64 bit natty?"
date: 2011-05-22
forum: General Help
---

### Post by kimangroo on 2011-05-22
Basically I just installed Natty on my new laptop. It's got an i5 with 4GB ram and so I guess it's 64bit.

I kind of forgot about that when I installed Natty off the live cd and was wondering how do I know if I've installed 32 or 64 bit version?

If I've got a 32 bit am I missing out on much (other than a couple of hundred megabytes of ram?)

Also can I easily upgrade from 32 to 64?

Thanks for any help.

---

### Post by Autodave on 2011-05-22
What was the name of the ISO that you used?

---

### Post by amauk on 2011-05-22
in a terminal, run```
uname -m
```i686 = 32bit
x86_64 = 64bit

---

### Post by Autodave on 2011-05-22
> **kimangroo said:**
> Basically I just installed Natty on my new laptop. It's got an i5 with 4GB ram and so I guess it's 64bit.

I kind of forgot about that when I installed Natty off the live cd and was wondering how do I know if I've installed 32 or 64 bit version?

If I've got a 32 bit am I missing out on much (other than a couple of hundred megabytes of ram?)

Also can I easily upgrade from 32 to 64?

Thanks for any help.


To answer your other question, unless you are doing major spreadsheats or something VERY CPU intensive, I would stick with the 32 bit.  More programs are available for the 32 bit.  I have tried both version 10.10 32 and 64 bit and could not see any discernable difference in speed between them in any program.

---

### Post by oldos2er on 2011-05-22
> **kimangroo said:**
> Also can I easily upgrade from 32 to 64?
  

You would need to do a fresh install.

There are only a couple programs I'm aware of that are 32-bit only; Skype and acroread (Adobe Acrobat PDF Reader). If you have 64-bit hardware, in my opinion you should use 64-bit software.

---

### Post by kimangroo on 2011-05-23
Thanks, it seems I am using 64 bit after all.

Does 32 bit software not run on 64 bit? Or does it just not take advantage of the extra bits?

How about drivers and stuff like that? I'm having some problems with my installation right now and was wondering whether it could have anything to do with the 64 bit/32 bit conflict?

---

### Post by oldos2er on 2011-05-24
You can run 32-bit apps on 64-bit Ubuntu by installing ia32-libs.

> How about drivers and stuff like that? I'm having some problems with my  installation right now and was wondering whether it could have anything  to do with the 64 bit/32 bit conflict?

If you give all the details of the problem (which hardware? which drivers? etc.) I'm sure someone could help.

---

### Post by bpb_21 on 2011-05-24
> **Autodave said:**
> To answer your other question, unless you are doing major spreadsheats or something VERY CPU intensive, I would stick with the 32 bit.  More programs are available for the 32 bit.  I have tried both version 10.10 32 and 64 bit and could not see any discernable difference in speed between them in any program.


When you say "More programs are available for the 32 bit," does that mean that the 64 bit OS version can't run 32 bit applications?

I just switched my main production machine over to Ubuntu 11.04, x64, and have had no regrets although I am rather new using this daily as my main machine.  But, I ask because I'm coming from the Windows world where x64 versions of that OS can run 32 bit applications.  Is Ubuntu not the same way?

I don't want to miss out on anything if there isn't a discernable speed difference and there is more software available.

---

### Post by pakidevil on 2011-05-24
uname -a

---

### Post by linuxinstalledfromhdd on 2011-05-24
> **bpb_21 said:**
> When you say "More programs are available for the 32 bit," does that mean that the 64 bit OS version can't run 32 bit applications?

I just switched my main production machine over to Ubuntu 11.04, x64, and have had no regrets although I am rather new using this daily as my main machine.  But, I ask because I'm coming from the Windows world where x64 versions of that OS can run 32 bit applications.  Is Ubuntu not the same way?

I don't want to miss out on anything if there isn't a discernable speed difference and there is more software available.

Yes there are more 32-bit debian package software installations than 64-bit.   It's just easier to work with sometimes with drivers that only have 32-bit support.  I recommend 32-bit for a more stable system too.  It depends on what you need.

---

### Post by wildmanne39 on 2011-05-25
> **kimangroo said:**
> Basically I just installed Natty on my new laptop. It's got an i5 with 4GB ram and so I guess it's 64bit.

I kind of forgot about that when I installed Natty off the live cd and was wondering how do I know if I've installed 32 or 64 bit version?

If I've got a 32 bit am I missing out on much (other than a couple of hundred megabytes of ram?)

Also can I easily upgrade from 32 to 64?

Thanks for any help.
Hi, I have been running 64 bit for three years and I have never had a problem, even adobe is 64 bit now, but I have alway's used the open source flash and it works great I have never tried to install a program that was only for 32 bit,it might be true in the windows world but in ubuntu I have not found that to be the case.

---

### Post by linuxinstalledfromhdd on 2011-05-25
You can run a PAE version of 32-bit that will use all of your extra memory.  Sometimes a user might need to install a printer driver/software that only exists as a 32-bit deb package install. And forcing doesn't allow it to run in 64-bit arch.  It really depends..  If I needed to use Citrix ICA or whatever, I would want a 32-bit system to configure and install the client for that. It's matter of preference and what you intend on using the system for eventually. I like to keep my options open in case that is something I may need to install in the future. :P

---

### Post by nemilar on 2011-05-25
You can see if you're running a 64 or a 32bit OS by the command:

```
uname -a
```

For example:

```
Linux stardust 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

The x86_64 indicates that it is 64bit.  32bit would say "i386" or "i686", usually.

You can see if a binary (library or executable) is 64 or 32 bit by using the "file" command:

```
jdeprizi@stardust /lib $ file /usr/lib/libgimp-2.0.so.0.600.11 
/usr/lib/libgimp-2.0.so.0.600.11: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped

jdeprizi@stardust /lib $ file /usr/lib32/libgtk-x11-2.0.so.0.2400.4 
/usr/lib32/libgtk-x11-2.0.so.0.2400.4: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped

```


In my experience, with Ubuntu/Linux there is never really any difference (from an ease-of-use perspective) between using a 64 and a 32 bit installation, until you start downloading things outside of the repositories, like Adobe Flash, Juniper Networks VPN software, etc...  Once you go into this realm, 32 bit is definitely easier, although I've always managed to get 64 bit working with some effort.

---

### Post by kimangroo on 2011-05-25
Ok at first I was worried that I had installed 32 bit instead of 64 and was "wasting" hardware as it were, but now that I've read the replies and realised that I have actually got 64 bit on, I'm regretting I didn't install 32 bit!!

Although I like ubuntu a lot and I use it more for my daily stuff, I really want stability and lack of problems over power (given that I tend to have to put more effort into getting ubuntu to work anyway).

I'm dual booting 64bit windows in order to make use of the discrete gfx in my laptop for games and other graphics intensive stuff, so I would have been happy to keep ubuntu 32 bit.

Anyway so far Skype seems to be working fine (someone said it was 32 bit) and flash via the ubuntu-restricted-extras is all working as well. The only thing I think might not be working is touchpad-indicator which someone else thought might be because of 32/64 bit problems.

EDIT ********************
While I've got people's attention, can I just ask on a completely unrelated note, is it not possible to use some of the "extra" buttons on modern laptops which boot fast stripped down os's for quick web access, or os's for recovery purposes, to independently launch either ubuntu or windows etc? I just think that would be so handy for dual booters!
I posted a thread about it [here]("http://ubuntuforums.org/showthread.php?t=1764312").

---

### Post by oldos2er on 2011-05-25
> **linuxinstalledfromhdd said:**
>   I recommend 32-bit for a more stable system too. 

In what manner has it been unstable for you? I have to admit I've never experienced instability that can be attributed solely to bitness.

---

### Post by bpb_21 on 2011-05-25
> **linuxinstalledfromhdd said:**
> You can run a PAE version of 32-bit that will use all of your extra memory. ...  I like to keep my options open in case that is something I may need to install in the future. :P

I agree with you on keeping options open.  You mention a PAE version of the 32 bit; where can you get that?  Is that an option in the alternate download CD/DVD?  I have used a few alternate install CDs but haven't ever paid attention to that option.

(And even better, can you "convert" a regular 32 bit install into a PAE version?  I'd imagine that would be the same answer as "converting" a 32 bit install to a 64 bit install - no - but thought I'd ask to make sure.)

---

### Post by bpb_21 on 2011-05-25
> **oldos2er said:**
> In what manner has it been unstable for you? I have to admit I've never experienced instability that can be attributed solely to bitness.

(Pardon the interruption and questions, I didn't realise the differences between 32/64 bit on Windows and 32/64 bit on Ubuntu.)

Could 32 vs 64 bit influence the way programs access hardware?  For example, would a 32 bit install potentially find a better (i.e. more compatible) driver for a wireless card or DVD burner?  (Assuming both otherwise work under 32 & 64 bit versions.)  By "more compatible" I mean not just working but interfacing better with 32 bit programs - like CD/DVD burners and wireless cards (that work out of the box with Linux) playing "nicely" with their respective applications.

---

### Post by oldos2er on 2011-05-25
Linux is not Windows, no matter the bitness.

I'm not a programmer, and certainly not a device driver developer, but I've never come across drivers for different architectures that work differently because of their architecture. That's an opinion though and worth what you paid for it.

The PAE kernel is installed automatically during a 32-bit Ubuntu installation if it detects you have 4 or more GB of RAM.

---

