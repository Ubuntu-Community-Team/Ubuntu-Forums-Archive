---
title: "Live CD Issue Lucid Lynx Final"
date: 2010-05-02
forum: General Help
---

### Post by Pernig on 2010-05-02
When i insert the Live CD, whether I choose memory test, try without installing or install Ubuntu, the computer seems to continue to load without a signal going to the monitor, as if a frequency or resolution unsupported by the card or monitor was chosen. 

I had a similar issue with 9.10, but this only happened after the system was installed when you got to the login screen. I can't find a 'safe graphics' option on this live CD as I could on Karmic. Are there any cheat codes I can use to enable some sort of safe graphics mode?

I am downloading the alternate installer now and going to try installing using this method. I've never done this before, do I have to setup a desktop myself using the command line with this?

My computer is an Asus M2N-SLI Deluxe motherboard with 2GB RAM, a GeForce 9600GT graphics card, and a DGM 23" 1920x1080 widescreen monitor connected via DVI.

Also I am installing the 64 bit version, although I don't reckon this is a 64 bit only issue.

Thanks in advance for your help.

---

### Post by givrix on 2010-05-02
I faced the same problem, and couldn't find any answer on the net.
So I tried some options with the F6 key : nomodeset restored the screen right while booting, but it finaly crashed on the purple background splash screen.

Then I tried using all options but initramfs couldn't reach the live cd then...

So the only solution for me was to remove my nvidia card and temporarily put an ati while installing.
Quite a challenge for a laptop user however.

I really suspect nouveau being the reason of this ....

---

### Post by Scunizi on 2010-05-02
Might be an SLI thing.. with my machine I have to modify the kernel boot line.. (live cd and after install) .. I add pci=nomsi .. after that all is well.. on boot of the live cd type F6 and you should be looking at the kernel line.. at the end where "quiet splash" is simply insert pci=nomsi before "quiet".  You may also have to add acpi=off.. but do one thing at a time.

---

