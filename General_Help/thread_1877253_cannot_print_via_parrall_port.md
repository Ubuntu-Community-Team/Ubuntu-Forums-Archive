---
title: "cannot print via parrall port"
date: 2011-11-07
forum: General Help
---

### Post by then_dude on 2011-11-07
hello people

i got a problem. 

i have a ubuntu 10.04 with a 2.6.38.12 pae kernel. 

i got a pci parrell port card

printer: hp 6l. 

when i print something the documents are pending and processing and never i got any page out of the printer. 

can somebody help me ? 
thanks

---

### Post by dcstar on 2011-11-08
> **then_dude said:**
> hello people

i got a problem. 

i have a ubuntu 10.04 with a 2.6.38.12 pae kernel. 

i got a pci parrell port card

printer: hp 6l. 

when i print something the documents are pending and processing and never i got any page out of the printer. 

can somebody help me ? 
thanks

Very doubtful, the latest official kernel for 10.04 is 2.6.32-35 so if you use other kernels you are basically on your own.

Boot up off an official kernel and see if it works.

---

### Post by then_dude on 2011-11-09
thanks  well the problem was that at that time it was the only configuration on which my hardware would run stable.   i got an sandy bridge and use the on board video card.   maybe i should switch to ubunut 11.04 and hope everthing works fine out of the box  a little question, if i download drivers, do i need to select 10.04 ubuntu version, or do i have to choose the 11.04 because of the kernel ?   thanks

---

### Post by then_dude on 2012-01-12
hello people,

i tried some other things too. But i guess there must be a strange problem

i have run live cd's : ubuntu 10.04, linux mint 11, linux mint 12, Wattos,

all could print immediatly with via the parallell port to the hp 6l. But when i installed the OS on my harddrive, the printed pages are being processed and pending.... nothing happens. 

i thought that maybe during the install there were new updates download... SO i installed some OS again but without network connection: what happens: the same again: documents keep on pending ? 

WHAT on EARTH could it be that from a live cd everything works great, but when installed things go wrong ? that's just way beyond my beginners-brain

please help 
[SIZE=1]thanks a lot
greetz
[/SIZE]

---

### Post by dcstar on 2012-01-16
> **then_dude said:**
> 
.........
WHAT on EARTH could it be that from a live cd everything works great, but when installed things go wrong ? that's just way beyond my beginners-brain


Live CDs do not (usually) use things like propriety video drivers, so possibly when you do a real install these drivers are installed and are incompatible with your PCI parallel port card.

See if you have BIOS options to change the PCI resources the card uses.

---

### Post by then_dude on 2012-01-18
thanks dcstar,

i have checked the bios, but nothing shows. 

1)is there a way to install the live cd without any update or propietery drivers ? 
2)how can i un-install them ? (the propietery drivers ? )

pitty that it is this much hassle to get a printer to work. 

now i'm working on a live cd... (but it is very fast, :-)  )

---

### Post by dcstar on 2012-01-19
> **then_dude said:**
> thanks dcstar,

i have checked the bios, but nothing shows. 

1)is there a way to install the live cd without any update or propietery drivers ? 
2)how can i un-install them ? (the propietery drivers ? )

pitty that it is this much hassle to get a printer to work. 

now i'm working on a live cd... (but it is very fast, :-)  )

You can make a Live USB that may be quicker that a Live CD, and you can use "Persistence" so it keeps changes and works a bit more like a real install.

There could well be a kernel boot string to make the installed system work with your hardware like the Live CD but it may be difficult to find the actual thing that is causing the problem.

Do a web search for the "noapic" boot string option and see if you can try things like that to get your Parallel Port going.

---

### Post by Flysafe on 2012-02-18
I'm not sure if this will help you directly but I had the exact same problem trying to install HP-5p. Printer would be recognized when I ran add printer, installed driver but then all that would happen is get message "processing" and no output. This was with a PCI add on parallel port card. Running 11.10. I then installed the ATI FGLRX additional video driver and deleted the printer and added again. This time I got a HPLIP line when I added the printer location and not just /dev/lp0. Now the location is device=/dev/parport0. I tried using this location manually since I had this same location running 10.04 but that wouldn't work manually. Must be some conflict with video driver and parallel port. Sorry I can't be more technical and give you any more detail on how to search for your parallel port conflict.

---

