---
title: "EAC under 10.04 not working"
date: 2011-02-23
forum: General Help
---

### Post by jamesisin on 2011-02-23
I have just installed EAC (Exact Audio Copy) under WINE on a newly built 10.04 system.  I get Access Denied errors when I attempt to start EAC.  Not sure what I'm doing wrong here, but I'd like to get it working correctly (I had it working fine on my previous 8.10 machine).

A little help?

---

### Post by mc4man on 2011-02-23
Don't use eac anymore, but i suspect the 1.0 version could be an issue (as is wine's crappy drive detection

You may want to try the 0.99pb5 version instead.
(it also may be beneficial to use an fstab entry/static mountpoint for your drive, though not sure if needed

Otherwise the wine subforum would be a better place for your post, (as far as the 1.0 version.

(the only thing I use wine for anymore is Imgburn and there I switch the I/O to ASPI_WNASPI32.DLL so as to keep wine out of the drive dection altogether.

---

### Post by stchman on 2011-02-23
You don't need EAC.  I have been ripping my CDs to .mp3, .ogg, .flac, etc. using Sound Juicer for years.

[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

The whole point of running Ubuntu is to use applications that are native to it.  Does one get Mac OS X and then try to run Windows Media Player on it?  No!!  Using Ubuntu as a stable platform for Windows apps is not a good idea.  Remember, it is something of a minor miracle that WINE can run Windows apps.

---

### Post by jamesisin on 2011-02-23
mc4man - Thanks.  Rolling back to 0.99pb5 seemed to do the trick.  Now just have to polish the installation and I'm back in business.

stchman - Normally I'd say something like "preachin to the choir, man" but since Ubuntu dropped (the now seemingly un-maintained) Grip there isn't a solid choice for assured accurate and error-free ripping.  I originally chose Grip because SoundJuicer was producing audible errors in my FLAC library.  That's a show-stopper.  I've looked a bit at Ruby Ripper but found that it's too young and clunky to satisfy me.  EAC has long been the *de facto* standard for accurate ripping.

---

### Post by stchman on 2011-02-23
> **jamesisin said:**
> mc4man - Thanks.  Rolling back to 0.99pb5 seemed to do the trick.  Now just have to polish the installation and I'm back in business.

stchman - Normally I'd say something like "preachin to the choir, man" but since Ubuntu dropped (the now seemingly un-maintained) Grip there isn't a solid choice for assured accurate and error-free ripping.  I originally chose Grip because SoundJuicer was producing audible errors in my FLAC library.  That's a show-stopper.  I've looked a bit at Ruby Ripper but found that it's too young and clunky to satisfy me.  EAC has long been the *de facto* standard for accurate ripping.

You must be doing some ultra sensitive audio work.  I rip my CDs all the time in VBR MP3 using LAME and they sound fantastic.

---

### Post by jamesisin on 2011-02-23
Mp3?  Fantastic?  Not possible.

---

### Post by stchman on 2011-02-24
> **jamesisin said:**
> Mp3?  Fantastic?  Not possible.

I cannot tell an audio difference(my ears) in the VBR MP3s and the original CD itself.

---

### Post by jamesisin on 2011-02-24
Can we agree there is a vast gulf between "acceptable" and "fantastic"?

---

### Post by stchman on 2011-02-25
For my ears, the VBR MP3 and the original CD are indistinguishable.  Granted I don't have studio quality audio equipment.

I will agree that 128K MP3s suck immensely.  If I don't have access to LAME I use 256K algorithm for ripping CDs.

I have people tell me "why use all that extra disc space?".  For me I CAN tell a difference between 128K MP3 and VBR or 256K MP3.  I rip my audio until I cannot tell the difference between the original and the copy.  256K or VBR work for me in that aspect.

---

### Post by jamesisin on 2011-02-25
Disc space is cheap enough now it's easy for me to have 700 GB of FLAC on a server here at home.  Why compromise?

I even installed RockBox on my iPod (old 60 GB hard drive).

I will say that it can be very difficult to pin point an articulable difference between a high bit-rate lost format file and a lossless file, but listening fatigue is much higher with lost formats.  And if there is no reason to compromise...

---

### Post by sieve on 2011-03-08
> **mc4man said:**
>  i suspect the 1.0 version could be an issue.

You may want to try the 0.99pb5 version instead.

This is true.  v1.0 does not install correctly. Apparently some people could get it to work by manually registering certain .dll files, but I tried and couldn't.  So I uninstalled v1.0 and installed v0.99pb5 and that worked fine.

Same problem same solution with 10.10.

---

