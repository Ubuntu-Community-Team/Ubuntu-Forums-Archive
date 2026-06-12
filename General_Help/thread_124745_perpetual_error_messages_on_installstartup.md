---
title: "perpetual error messages on install/startup"
date: 2006-02-02
forum: General Help
---

### Post by sumday on 2006-02-02
Right, so i'm trying to install breezy from the installation CD. 

The first time, after having copied the packages to the hard drive, and asking me to take the CD out and reboot, i began to notice some error messages. I believe the installer was about 60% of the way through, and the following error message appeared:

[4294860.250000] hci_usb_isoc_rx_submit: hci0 isoc rx submit failed urb dd2c6614 err -28 

this appeared twice during the installation underneath the progress bar. It didn't look like it should be there, but it stayed there, i think, till the end.

I googled it, and it appears to be related to bluetooth. My computer has an internal bluetooth adapter, but i never use it. So would removing that get rid of this error message? I didn't build this computer, and i don't know where the bluetooth adapter is, so i'd rather not have to remove it.


anyway, on this installation, i had various problems with graphics drivers, sound cards, and a bunch of other stuff, so i decided to give it another go and do it right from the start.

So this morning i repeat what i did above, and got the same error message. but some more appeared around the 90% mark, and all of a sudden, there was a torrent of error messages where the ubuntu installer should have been. They just kept on coming thick and fast.

The error messages went by so quickly that i didn't have a chance to note down any of them until it settled onto the following

[429xxxx.xxxxxx] usb 5-8 clear tt 1 (92b2) error -71

the 'xxxx's denote rapidly changing numbers. The number was increasing by around 1-2 integers a second. the 'error -71' was different earlier on in the stream of error messages. I believe it started out much lower, and settled on 71 eventually.

So my entire screen was full of these error messages with no sign of them stopping, so i rebooted. When it got to the bit where the X sever should kick in and take you to the login screen, i got the same perpetual error message thing. It just didn't stop. 


That's when i got bored and came here. Can anyone help?

---

### Post by el3ktro on 2006-02-02
Hi,
I'll try to help, but I need some more info. What kind of motherboard, processor & chipset does your computer use? During install, do you have any USB devices connected? Are you installing from an USB CD drive?

As a first step, try disabling all USB stuff in the BIOS if possible.


Tom

---

