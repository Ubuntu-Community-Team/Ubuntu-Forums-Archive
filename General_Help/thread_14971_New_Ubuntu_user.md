---
title: "New Ubuntu user"
date: 2005-02-11
forum: General Help
---

### Post by caiphn on 2005-02-11
Hi, I downloaded the warty-release-live-i386, and burned the image. I put the CD in, and noticed that it gave me the option to install a few apps, with a nice menu. The reason I mention this is I don't think there is a problem with the way I burned the CD.

I use an AMD 1800+ Processor.
Asus V8420 Video Adaptor.
Asus A7N8X Motherboard.
(2) 256 stick of Samsung Memory

Not really sure what else is important. Anyway, I boot up the CD, and I get the menu with the various options. (I tried four of them) When I try to do the parity check or whatever the error checking is, the screen just goes black. CRC Check? Can't remember which one it is. If I just let it boot up, this happens.



MP-BIOS BUG: 8254 timer
not connected to IO-APIC

audit (1108001840.998:0): initialized


I am a complete newbie, so I'm not sure what to try from here.
I'm using some relatively unknown (to me at least) but up until now it seemed to be quite reliable media, "Hypermedia CD-Recordable", I don't know if a corny name warrants crappy media or not. It's a CD-R, and I burned it at 52x.

---

### Post by clparker on 2005-02-11
That's the live CD, dont mess with the live cd, hell it really isn't ubuntu, it's a knoppix cd with an 'ubuntu' feel. Get the real deal and install it.

---

### Post by caiphn on 2005-02-11
I see. I'm totally new to Linux so I just randomly picked a Live CD after I was reading a review at slashdot, and I was just trying to get it up and running as I've never even seen it before. Thought maybe there was something I could try doing other than just installing.

---

### Post by Jad on 2005-02-11
you will have to download the Installation CD
[http://releases.ubuntu.com/warty/](http://releases.ubuntu.com/warty/)

---

### Post by caiphn on 2005-02-11
Right, I understand that I can't use the Live CD, it's just I thought maybe someone would be able to assist me with my current problem. I will start the installation download now, I'm going to have to repartition this drive first.

---

### Post by Jad on 2005-02-11
sure thing
while downloading please read 
[http://pw1.netcom.com/~kmself/Linux/FAQs/partition.html](http://pw1.netcom.com/~kmself/Linux/FAQs/partition.html)
also read [http://www.UbuntuGuide.org/](http://www.UbuntuGuide.org/)

---

### Post by caiphn on 2005-02-11
Just tried to Gnoppix live CD, I got the exact same error message, although the audit # was different..

MP-BIOS BUG: 8254 timer not connected to IO-APIC..

Will this become an issue when I do the actual install? I've read a good portion of that second link at work.  I will give it another look through before installing.

---

### Post by caiphn on 2005-02-12
Doing a google search for the error message I was receiving was far from helpful unfortunately. I've heard that Linux errors actually mean something instead of the typical gibberish Windows errors, so I was wondering if there was some sort of website someone could direct me to so I could research this error or at least get some sort of definition for it.. it seems as though the audit number changes each time, I'd also like to find out what this refers to. I typically wouldn't ask this sort of question but I have had no luck finding this information on my own. ](*,)  Any input is welcome, thanks!

---

### Post by alastair on 2005-02-12
Some sort of BIOS bug. You could try disabling APIC (interrupts) when you boot. 

You can do this by passing the option "noapic" on the boot command line.  

You should be able to access the boot command line, and change it,  using one of the help (F?) keys after booting the CD.

Alternatively, try the "hoary" live-cd (it is newer and might work around this).

---

### Post by caiphn on 2005-02-14
Thanks, I believe I tried all of the boot options you could select with the cursor keys, but if that is not one of the options than perhaps that is the issue. I will also try the newer Live CD, I appreciate the input! I'll post how it goes for me.

---

### Post by trivialpackets on 2005-02-14
[QUOTE=caiphn]Thanks, I believe I tried all of the boot options you could select with the cursor keys, but if that is not one of the options than perhaps that is the issue. I will also try the newer Live CD, I appreciate the input! I'll post how it goes for me.[/QUOTE]
 I have this issue on my HP notebook with the io apic.  When I install the warty install version, when it brings up your grub loader, you press 'e', go to the line with all of the boot options, and press 'e' again, enter 'noapic' as instructed above, press return, then press 'b' and it should disable this and run through without issue.  Assuming all goes well, when you get it up, sudo gedit /boot/grub/menu.list and add the noapic so that you don't have to type that in each time that you login.  Good luck.

---

### Post by caiphn on 2005-02-14
Great, I'm not sure what you mean by 'sudo gedit /boot/grub/menu.list' but of course more reading and experimenting will get me through that. I'm a 100% Linux newb so... I'm going to search around for some FAQs right now so I have something to read while at work regarding sudo commands and whatnot. Sorry for the ignorance and I appologize if I made anyone roll their eyes.  :smile:

---

### Post by caiphn on 2005-02-14
I appologize if this is the incorrect forum to be posting this, I didn't see anything that said 'super noobs click here'. I was reading through the partition FAQ that was posted earlier by Jad, and the term SUID keeps coming up. I went to webopedia but it doesn't explain exactly what it means. Just curious so I can have a better understanding of what I'm reading.\

Or perhaps I need to find a partitioning FAQ which is more geared towards beginners..

--EDIT--

Woah, checking out the FAQ section in the forum, I see there are a plethora of links for me to read up on. I'll try to take some of this in before I continue to ask silly questions, found a great general Linux FAQ.

---

### Post by misGnomer on 2005-02-15
Caiphn, if the "old" Warty-live doesn't work for you, it might be a good idea to try one of the more recent (and frequent) Hoary or Gnoppix live CDs which come with a more recent kernel (2.6.10.x) with updates that may fix your problem. Your Gnoppix disc, if recent, should work fine after a little editing of boot parameters.

Alastair already told you how to interrupt the boot process using F keys to get to the boot menus and commandline where you can edit the boot parameters. You need to add "noapic" there so that the system will boot in legacy IRQ mode.

On some systems ACPI needs to be switched off as well, using "acpi=off" (or acpi=ht" as a less drastic measure?).

Eric's tip to do "sudo gedit /boot/grub/menu**.lst**" (not **.list**) to add the "noapic" boot parameter works with an installed version of Linux as the changes are saved to disk, but under live session the changes are wiped out at the next reboot and don't therefore do any good.

Also google for "A7N8X noapic linux" or replace "A7N8X" with the main chipset model (the culprit here) on your motherboard to find out more.

---

