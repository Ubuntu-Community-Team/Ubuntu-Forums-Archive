---
title: "Seriously needs help!"
date: 2010-12-17
forum: General Help
---

### Post by Bamboon on 2010-12-17
Ok, I know I'm a noob so don't slaughter me now, all right?

I recently bougt an Asus N61DA with Windows 7. I decided to install Ubuntu alongside Windows, so I made the Ubuntu CD, just like it said. Then I inserted the CD and restarted the computer. I started the installer (ubuntu 10.10 64-bit) and chose the option where it says "install ubuntu alongside other operating systems", or something like that. So, the installation started, but then I lost the internet connection, and the installation stopped. I re-connected the computer, but the installation still wouldn't continue. I restarted the computer and then nothing happened. I've restarted it several times, but still nothing happens. I've inserted the Windows recovery CD, but it doesn't work. Any ideas what I should do?

---

### Post by tshep03 on 2010-12-17
Is your computer set to boot from the cd?

---

### Post by doperative on 2010-12-17
> **tshep03 said:**
> Is your computer set to boot from the cd?

"the installation started, but then I lost the internet  connection, and the installation stopped"

I don't understand how losing the Internet connection would affect the installation, can you even boot from the Ubuntu CD?

---

### Post by Bamboon on 2010-12-17
> **tshep03 said:**
> Is your computer set to boot from the cd?

I don't know. I think something happened when I restarted the computer before the installation was finished.

---

### Post by Bamboon on 2010-12-17
> **doperative said:**
> "the installation started, but then I lost the internet  connection, and the installation stopped"

I don't understand how losing the Internet connection would affect the installation, can you even boot from the Ubuntu CD?

I could at first. But after I restarted it, it won't boot from the Ubuntu CD anymore, and the Windows recovery CD doesn't work either.

---

### Post by mmsmc on 2010-12-17
check your BIOS boot options make sure its set to boot from your harddrive

---

### Post by matt-fender on 2010-12-17
It's times like this when DVD roms decide to go pop lol

---

### Post by Bamboon on 2010-12-17
> **mmsmc said:**
> check your BIOS boot options make sure its set to boot from your harddrive

Great, thanks! Now I can boot from the Ubuntu CD. The Windows recovery DVD still doesn't work, though, so it looks like I have to buy another license. How could Windows be uninstalled just because I restarted the computer before the Ubuntu installation was finished?

---

### Post by tshep03 on 2010-12-17
Windows is still there. Finish the Ubuntu install and reboot.

---

### Post by cgroza on 2010-12-17
Windows was not deleted, after you finish the installation, you should be given the option at boot.

---

### Post by kgarbutt on 2010-12-17
The same thing happened to my son. He installed Ubuntu 10.10 onto his computer and Ubuntu deleted a hidden boot/recover folder. He had to buy recovery discs from HP. You probably did the same thing. Do a web search to see if your computer has one of those hidden partitions.

---

### Post by Bamboon on 2010-12-18
Ok, I tried to start the installation now. I got two error messages. "Cannot allocate protected mode pages" and "you need to load the kernel first". Anyone know what these two mean and how to fix them?

---

### Post by Bamboon on 2010-12-18
> **kgarbutt said:**
> The same thing happened to my son. He installed Ubuntu 10.10 onto his computer and Ubuntu deleted a hidden boot/recover folder. He had to buy recovery discs from HP. You probably did the same thing. Do a web search to see if your computer has one of those hidden partitions.

But wouldn't this hidden partition even show up when I right-click on computer and go to manage? It was a small partition there with 20 GB, and C (where Windows was located) at about 160 GB and D at about 300 GB. I deleted D cause it was empty and transferred everything to C, so it was roughly 440 GB large and then started the Ubuntu installation. Could Ubuntu have overrided the 20 GB partition?

---

### Post by jingaling on 2010-12-18
Hey,

Looks like the Ubuntu installation hadn't finished so therefore GRUB hadn't been setup correctly. Here's a bit of computer 101 for you (sorry if i am teaching granny to suck eggs here!).

All Operating Systems (OS) have what's called a boot sector, in windows this is called the MBR (Master Boot Record) and in Linux its called the GRUB loader (GRand Uniformed Boot Loader). These systems tell the computer which OS to boot to. When you install ubuntu along side windows, GRUB takes over as the boot sector (MBR is still there though - GRUB is just the daddy), so, if the installation does not complete properly and GRUB isn't configured then you will not be able to boot either OS.

YOUR WINDOWS INSTALLATION IS FINE - YOU JUST NEED TO GET PAST GRUB AND TO THE MBR.

Here's what I would do:

1) Download a bootable partition editor (gparted is good, free and simple to use - do a google search for the download link).
2) Burn gparted to a disk and boot your computer from it.
3) Once gparted it running delete all the linux partitions leaving just the main windows 7 NTFS partition and the windows 7 100MB system reserved partition.
4) Apply the changes and re-boot.
5) Windows should now boot as linux/GRUB are gone.
6) BACKUP YOUR WINDOWS OS!!! (Windows image backup should be fine)
7) Try to install ubuntu again whilst disconnected from the internet (you can connect and install updates once ubuntu is installed).
8)Fall in love with open source technology (ubuntu) and get rid of that crappy, virus ridden, crashing all the time Microsoft OS :)

I hope this helps, if not then please feel free to drop me a personal message and I will do what I can to help.

Jing

---

### Post by Bamboon on 2010-12-18
Ok, I've burned gparted unto a CD, but it won't start. How do I get it to start? Do I need to do something in BIOS again?

---

### Post by Bamboon on 2010-12-19
No one knows how to get gparted to work?

---

### Post by mwl128340 on 2010-12-19
do you have the live cd for ubuntu? if you boot into the live cd there should be gparted in system>admin

---

### Post by Bamboon on 2010-12-19
Never mind, I just had to press F8 for gparted to start. From there it was easy and I now have both Ubuntu and Windows installed. Thanks to everyone for your help, especially jingaling who introduced me to gparted. Keep up the good work guys:D

---

