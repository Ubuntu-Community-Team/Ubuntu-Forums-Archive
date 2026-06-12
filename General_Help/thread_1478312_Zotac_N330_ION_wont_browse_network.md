---
title: "Zotac N330 ION wont browse network"
date: 2010-05-09
forum: General Help
---

### Post by ep1centre on 2010-05-09
As per title, my Zotac N330 ION wont browse the network, i just installed Ubuntu 10.04 and everything seems to work fine including internet access however it will not let me browse the network either through the "network browser" or through the "connect to server" feature!

The network is a windows based Samba network and it has always worked with ubuntu before on other computers however this is the 1st time I'm installing ubuntu on my Zotac motherboard.

So far i've tried a few things by reading up on the internet, including reloading the ntfs "config" changing the workgroup name from the default "workgroup" to my network's actual workgroup (which i'd never had to do before and it has always worked in the past) i tried connecting through the "connect to server" feature without success, i tried connecting using both the 10.04 and the 9.10 live CD feature also without success, and i've even switched off the Nvidia ION hardware drivers just in case that was creating any issues, i restarted the system between every one of these fixes i also tryed restarting my router... and meanwhile my other (older, stardard) PC with ubuntu 9.10 on remains able to browse the network without problems.

Every time i try to browse the net i get the following error message "Unable to mount location Failed to retrieve list from server" - i also noticed that before the ubuntu splash screen shows at start up there's a quick flash of a black screen with an error message saying something about how ubuntu is unable to probe SMB2 i can't get the error code and the full message as it flashes too quickly to read and take notes.

I'm gonna do a fresh install just so my attempts at fixing it don't get in the way of any instructions you give me!

This is really frustrating can anyone please help?



Thank you.

---

### Post by ep1centre on 2010-05-09
Ok i've just done a clean install and it's working, i'm now afraid of installing anything else in case it stops working but i need the graphics drivers or else it wont play videos properly =(

I will try to start with the "software updates" and i wont touch the Nvidia ION drivers and see how i get on... i'll report back!

---

### Post by navic on 2010-05-12
Glad you got your network browsing back.  I have a Zotac ION with Ubuntu also and I've experienced large file copying problems - If I copy day a TV season folder (~8gb, 24 files) from the local hard drive to a USB drive, it just sits there and never finishes.  Nautilus just goes zombie, have to reboot the manually.  Was wondering if you've tried copying large files to external volumes and experienced this problem?

I know it's the ION platform because I've installed Ubuntu on other desktops (AthlonX2, P4, Core2Quad, etc) and performed large copies to the same external hard drive and it works fine.... only freezes on the ION.

---

