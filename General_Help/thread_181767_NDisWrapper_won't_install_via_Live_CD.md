---
title: "NDisWrapper won't install via Live CD"
date: 2006-05-24
forum: General Help
---

### Post by Glass Casket on 2006-05-24
So I booted up the Ubuntu live CD to get my wireless card (Linksys WMP53GS) working! So since I wouldnt be able to download it, I put the latest version of ndiswrapper on my USB key. So I booted up and extracted all the files onto my desktop. I moved into that new directory, just like the instructions said. But when I tried going any command which started with 'make' via terminal, it told me that 'make' wasen't a valid command.

Does that mean that getting my card under the live CD is a no go? And according to the wireless cards which are compatible with Ubuntu, my showed up.

Thanks!

---

### Post by DarthMandeep on 2006-05-25
The problem with the Ubuntu livecd (at least the new Dapper one) is that it doesn't contain ndiswrapper-utils, which is what you need to install to use ndiswrapper.

The file you downloaded is the source for ndiswrapper, and building source requires you to download a package called "build-essential" and the right headers for the kernel version you're using. You can't do that very easily without a network connection, making the whole thing a chicken-and-egg problem.

My advice is to ignore the source package, and download the ndiswrapper-utils package from the Ubuntu site using a computer/os that has a net connection and bring it over to your Ubuntu system and install it using "sudo dpkg -i name-of-package"

Here's a link [http://packages.ubuntulinux.org/breezy/misc/ndiswrapper-utils](http://packages.ubuntulinux.org/breezy/misc/ndiswrapper-utils)

I noticed that the text mode install CD for Dapper includes ndiswrapper-utils, though the liveCD does not. Frustrating.

By the way, if all you want is a Linux liveCD that includes ndiswrapper so you can use it for web browsing without an install, you may want to look at Mepis. Last time I used it, it included ndiswrapper and the drivers needed for my WMP54GS and other cards by default, no install or config needed. Also included various plugins like Sun Java and Flash, making it better suited for a web browsing liveCD than the Ubuntu equiv. 

Not trying to say one is better than the other, I use Ubuntu.

---

### Post by _linux_ on 2006-05-25
Ubuntu already has ndiswrapper, so all you need is some other packages. Go [here]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto") for instructions on how to set it up.

---

