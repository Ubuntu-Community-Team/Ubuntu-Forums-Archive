---
title: "Windows Dual Boot?"
date: 2011-06-15
forum: General Help
---

### Post by AMcKee on 2011-06-15
Hello Everyone, 

I am trying to put a Ubuntu/Windows 7 dual boot on my computer, as Ubuntu doesn't like my graphics card...
However, whenever I try to burn an official Windows ISO to use with my (original and legal) key, ubuntu gives me errors. I tried burning it with a windows computer @ 1x speeds and it still didn't work...
It shows the files on the disk when I browse it in ubuntu, but the install on a separate partition just either
   a) Stalls at 0%
   b) Gives me an error then quits
I don't want to have to pay to order install disks, as none came with my computer purchase.
So my main question is, can I either:
1. Get some install disks free
2. Get the system files for all of windows, and mount them on my partition manually
3. Get it to work some other way.
I would really like to get this working, because my $200 graphics card is 100% incompatible with linux, and without it, I can barely play MINECRAFT on the lowest video settings... I have an i5 and 6GB of ram...

Specifically, I need Windows 7 Home Premium x64 for my key to work.
If anyone knows a way to do this, please let me know. I am a massive linux noob, and would really appreciate some help!

Thanks

Andrew McKee

---

### Post by HunkirDowne on 2011-06-15
I'm easily confused.

> **AMcKee said:**
> Hello Everyone, 

I am trying to put a Ubuntu/Windows 7 dual boot on my computer, as Ubuntu doesn't like my graphics card...

If Ubuntu doesn't like your graphics card, why would you want to install it?

> **AMcKee said:**
> However, whenever I try to burn an official Windows ISO to use with my (original and legal) key, ubuntu gives me errors. I tried burning it with a windows computer @ 1x speeds and it still didn't work...

Are you trying to run Windows in a virtual machine?  If Windows is already installed, why would you need to have an installation ISO?

When running multiple operating systems on the same computer, and at least one of those operating systems is Windows, it is best practice to install Windows first and then install your GNU/Linux distro(s).

> **AMcKee said:**
> I don't want to have to pay to order install disks, as none came with my computer purchase.

My last three PC purchases came without installation media.  However, the earliest of the three came with an image on a bootable DVD.

Since then I make recovery DVDs in case I mess up in general, but specifically prior to installing Ubuntu or some other GNU/Linux distro.

> **AMcKee said:**
> So my main question is, can I either:
1. Get some install disks free

I don't think so, at least not legally.  But IIRC, they only cost about $15-20 from your OEM (recovery disks, but should be installable to bare HDD).

> **AMcKee said:**
> 2. Get the system files for all of windows, and mount them on my partition manually

This might work, but with the way Windows is structured with Junction Points and the like, you would have to be quite crafty and I think it would be a laborious manual operation.  Especially nowadays (not like Windows 3.1 days) Windows is best served freshly installed and thinking it is the only operating system on board.

If you actually do get this option to work for you, let me know.  

Personally, I would leave Windows where it is and partition around it, install Linux, and hack grub.d if os-prober doesn't sufficiently dope the config so that Windows is properly chainloaded.

---

### Post by Mark Phelps on 2011-06-16
> **AMcKee said:**
> Hello Everyone, 

I am trying to put a Ubuntu/Windows 7 dual boot on my computer, as Ubuntu doesn't like my graphics card...

What make/model is your graphics card?  If you don't know, you should do the following:
1) Boot into Ubuntu from a LiveCD
2) Open a terminal and enter "lspci"
3) Look for the line containing "VGA"
4) Post that information back here.

If you have one of the older "legacy" ATI cards (NOT one of the newer HD 3x/4x/5/x6/x7x carda), you won't be able to get any new ATI drivers as ATI dropped support for those cards years ago.  You will be stuck using the default drivers.

If that's the case, it makes no sense that you're still trying to do an Ubuntu install.

---

