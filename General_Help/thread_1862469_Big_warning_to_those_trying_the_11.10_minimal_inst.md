---
title: "Big warning to those trying the 11.10 minimal install..."
date: 2011-10-16
forum: General Help
---

### Post by OneXero on 2011-10-16
I don't know exactly what part of it messed me up, so I'll list it in detail:

I downloaded the ~25 MB minimal ubuntu install iso.

I used the pendrive bootable usb tool and selected 11.10 ubuntu from the list, and chose the mini iso.

It installed, and I tried to boot into it. When I did, I got "Cannot find Linux Kernel."

I then restarted and unplugged. Now it was grub rescue>.

At this point I make a windows recovery CD and try to boot into that. It works, but can't detect my hardware anymore, or my windows installation, after popping up and telling me that it found an error in my boot files (which it couldn't repair because it couldn't find the hard drive or the windows installation).

So I mulled around for a few hours and finally resolved to use the recovery command line (that apparently COULD detect the hard drive) and I copied over my data to an external hard drive. I had to completely format the hard drive and install Ubuntu (Full) to get things working again...(to even get that to work I had to create my own partitions).

**So yeah. Don't do what I did.** Also, if you don't believe me/ have a computer to spare. 

Duplicate my steps and tell me what the hell happened! 

BTW: I called my samsung tech support and he was completely baffled "It shouldn't work this way" -- "Samsung Recovery should be able to boot." --- He wanted me to send it in for repair...Yeah right.

---

### Post by OneXero on 2011-10-16
Oh and I guess props to Ubuntu install, the windows reinstall wouldn't let me do jack. Kept popping up with errors, in line with the previous problem. But with Ubuntu all I had to do was manage the partitions and create my own swap space and it stopped giving the "Cannot write bootloader" error! So three cheers for that...

---

