---
title: "screen 'froze' just before login"
date: 2009-08-22
forum: General Help
---

### Post by I_PRODUCTIONS on 2009-08-22
my screen 'freezes' just before the login screen it looks like a black banner at the top with green ubuntu logos over it and the rest of the screen is white with odd pixels of either green on pinky -purple i am currently running off the disc. I want to know: Is this something to worry about? & how do i fix this? any help please, thanks.

O.S: UBUNTU 9.04 
Computer: Asus Vento M9 
Myself: puzzled :confused:



PLZ CHECK PAGE TWO

---

### Post by majed on 2009-08-22
I'd say first thing to do is to copy any data that u have to another disk or to an external drive..

Second step can be anything between trying to fix the problem and reinstalling the whole system!

---

### Post by sandyd on 2009-08-22
seems like a problem w/ your graphix drivers
could you post your video card model please?

if you don't know it, you can press     Ctrl-Alt-F1wihle the screen is frozen. Then login and type in
[/code]
lspci
[/code]
find your videocard in that mess of numbers and words and your set.

---

### Post by I_PRODUCTIONS on 2009-08-23
@carlee yeah i tried the ctrl+alt+F1 didn't work just remained frozen and sorry i don't know what it is thanks anyway and also

 @majed i can't copy my stuff as i don't have an external hard drive and also via disk i don't have the privilages to copy most of my stuff i found the folder of where it is but just can't copy it 

thanks for your help

by the way it's before log-in screen it's just after the bar loading thing after choosing the O.S. (I have dual boot), when it comes up 'frozen' then the only thing i can do is turn off the computer via the power button

---

### Post by P4man on 2009-08-23
go in to the grub menu (you may have to press "escape") while grub loads.
Then select the first line with something like "ubuntu kernel 2.6.2xxx -generic". press "e" to edit. 

Then select the probably third line, line which looks most like:

kernel	/boot/vmlinuz-2.6.28-15-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro quiet splash 

press "e" again to edit. remove the splash and quiet at the end so you get:

kernel	/boot/vmlinuz-2.6.28-15-generic root=UUID=0e5317cf-1aa2-4b20-9ffa-f17c41f48f37 ro 

then press "b" to boot.

It wont solve any problem, but you'll get output which will help us further finding the cause.

---

### Post by I_PRODUCTIONS on 2009-08-23
@P4man yeah, I just tried that and I got the same sorta screen only the 'banner' is slightly more squashed up thanks for your input.

---

### Post by TeoBigusGeekus on 2009-08-23
Boot up with live cd. Once Ubuntu has loaded, go to Programs->Accessories->Terminal. You are now in the terminal. Type
```
lspci > ~/Desktop/pciinfo
```
to list your pci devices and save them in a file on your desktop.
Post us the file to see what your graphic card is.

---

### Post by P4man on 2009-08-23
> **I_PRODUCTIONS said:**
> @P4man yeah, I just tried that and I got the same sorta screen only the 'banner' is slightly more squashed up thanks for your input.

You must have done something wrong, unless Im terribly wrong heh. Without those switches, you should see no ubuntu logo or banner at all, only text ?

---

### Post by I_PRODUCTIONS on 2009-08-23
@[U]P4man neither one of us can be blamed it's my computer thanks anyway 

@TeoBigusGeekus thanks that looked like it would work but every time i entered it (copied it then pressed enter) it would have the 'ubuntu@ubuntu:~$' thing on the next line so i don't think any action was done

thanks for your help i know this is kinda getting frustrating all over a graphics card[/U]

---

### Post by TeoBigusGeekus on 2009-08-23
> **I_PRODUCTIONS said:**
> 
@TeoBigusGeekus thanks that looked like it would work but every time i entered it (copied it then pressed enter) it would have the 'ubuntu@ubuntu:~$' thing on the next line so i don't think any action was done

Have you checked your desktop? You should see a file called pciinfo.
If not, just type 
```
lspci
```
and post us the outcome.

---

### Post by I_PRODUCTIONS on 2009-08-23
[U]@TeoBigusGeekus Oh there we go damb windows in the way- i'm prone to this sorta thing ... well here we are i posted it all just in case... (i couldn't bother looking through it plus i don't know what half of these mean ... ok all of them)

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 10)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

this was all there was in pciinfo file
[/U]

---

### Post by I_PRODUCTIONS on 2009-08-24
AHEM! above is the PCinfo

---

### Post by P4man on 2009-08-24
Im not too sure how to install/configure X for intel onboard video, so until someone else chimes in, ill tell you how to revert to vesa graphics, which is far from ideal, but at least might give you your desktop back.

Boot your machine in recovery console (second option in grub menu).

The type 

```
sudo nano /etc/X11/xorg.conf
```

(note the uppercase X in in X11)

Find the section "device" that contains a "driver" line, and looks somewhat like this
```

Section "Device"
	Identifier	"Generic Video Card (or intel Gxx whatever videocard)"
	Driver		"intel"
EndSection
```

Let us know what driver is in there now, and change it to "vesa", so you get:
```

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
EndSection

```

press control +x and then Y to save.

reboot.

---

### Post by I_PRODUCTIONS on 2009-08-24
@P4man Where do i type this i go into grub menu then select the recovery mode (second one in the list not of the recovery modes) then i get a box with a list of things what one do i select or where do i type? (sorry i'm a new to this)

---

### Post by P4man on 2009-08-24
a box with a list of things? 

Lets try again. boot the machine. If needed, press escape to get the grub menu which will look much like this:

[IMG]http://thegabfather.files.wordpress.com/2008/09/grub4kt.jpg[/IMG]

(its an old one, but you get the idea).

Select *ubuntu whatever kernel **(recovery mode**)* there and press ENTER.

then you should be greeted by a command prompt where you can log in, and enter the commands I wrote above.

---

### Post by I_PRODUCTIONS on 2009-08-24
@P4man i select that but this pops up

sorry i had to do it with a camera

---

### Post by P4man on 2009-08-24
sorry,my bad, I forgot about that menu. Select the "root shell" there. Then you got a prompt where you can enter the commands I put higher up.

---

### Post by I_PRODUCTIONS on 2009-08-24
@P4man this happens (i scrolled down a bit) should i just add the line

---

### Post by P4man on 2009-08-24
yeah, then just add 

```
Driver "vesa"
```

in the device section

---

### Post by I_PRODUCTIONS on 2009-08-24
@P4man tried that rebooted and got the banner thing again

this is not going well

---

### Post by P4man on 2009-08-24
no, thats definately not good. If you're sure you are using the vesa driver, and your screen is corrupted like that, Im beginning to wonder if its not a hardware problem.

when did this start? Did you run windows or another version of ubuntu without problems before trying out jaunty (assuming you have jaunty now)? Or did jaunty used to work, and suddenly you started getting this graphical corruption?

I cant tell from the pics if its a laptop or PC, but could you try to connect another screen ?

---

### Post by I_PRODUCTIONS on 2009-08-24
@P4man oh sorry its a PC and i have another screen from a Packard bell imedia 4605 

it started the day i made this thread and i'm not sure what caused it but before it happened i was testing out the screen session capture thing and it froze so i restarted then i got the banner thing (i should of mentioned this earlier)

---

### Post by P4man on 2009-08-24
well, duh, im also confusing a few threads. You can boot from the live cd, and everything works there, so its not likely a hardware issue. Running out of idea's though :(

---

### Post by I_PRODUCTIONS on 2009-08-26
new screen of the error this morning slightly larger and had blue bars in the white bit

---

### Post by I_PRODUCTIONS on 2009-08-27
I just got on to one of my friends and he's saying it's to do with GNOME this 'error'

GNOME IS BROKEN

WHAT TO DO (doesn't fix it but you get your files and avert the problem): 
i am now shrinking my partition
and installing ubuntu on the remainder space left
 so then i can copy all of my files to the new partition

---

