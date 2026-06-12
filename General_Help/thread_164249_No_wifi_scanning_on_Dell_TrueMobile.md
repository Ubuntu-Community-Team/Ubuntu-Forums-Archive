---
title: "No wifi scanning on Dell TrueMobile"
date: 2006-04-22
forum: General Help
---

### Post by concreteclam on 2006-04-22
Hello all,

I recently installed Ubuntu Breezy on my Dell Latitude C610 laptop. While I'm not exactly a total newbie to Linux, I'm still pretty "new" to it.

Anyway, it picked up my Dell TrueMobile 1150 mini-PCI wifi card as a "unknown device" in the GNOME device manager. It's using the orinoco driver, which I've come to gather doesn't support scanning for SSIDs.

I know my router's config for my house, but it would be a lot nicer if I could get support for automatic scanning for SSIDs. Wifi-radar and programs like it report that scanning isn't supported.

I've figured out there's three possible solutions for my problem:
1. Install a patched version of the orinoco drivers.
2. Re-compile my kernel to the latest version.
3. Try and configure and use ndiswrapper.

I don't want to do #1 because I don't want to mess up my drivers, and #2 sounds a little scary, so I went ahead and tried #3. I downloaded the wifi drivers from Dell's website and extracted the exe through Wine. Then I used ndiswrapper to install the INF file to it, which worked. Now I don't know what to do. I'm guessing I somehow tell something to use ndiswrapper instead of the orinoco drivers? If so, I don't know how to do that, and lots of searches through these forums and reading man pages hasn't helped much.

Could someone please point me in the right direction? :)

Edit: Using ndiswrapper -l says that the driver is loaded. However, using ndisgtk, it shows the driver loaded, but also says: Hardware present: no
Uhh...

---

### Post by concreteclam on 2006-04-22
Okay, so I decided to ditch ndiswrapper and go with patching the orinoco file. I got the gz file, unpacked it, and whenever I try to run make, I get: 

Makefile:35: *** The kernel source is not configured.  Stop.

... what?

---

### Post by concreteclam on 2006-04-22
Replying to my thread here again, I decided to take the plunge and recompile the kernel. It updated orinoco to the latest version, and scanning works. Yay!

---

### Post by yanokwa on 2006-05-15
concreteclam, could you post some more detailed instructions on how to get this to work?

---

