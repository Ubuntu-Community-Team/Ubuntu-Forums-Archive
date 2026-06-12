---
title: "Probable new user WINE questions"
date: 2010-10-16
forum: General Help
---

### Post by HarryCromsfelder on 2010-10-16
I'm probably going to switch to Ubuntu soon but I had a few questions first. I use a wireless adapter that requires a CD installation, but it's only compatible with Windows. Will I be able to install it with WINE? Also does WINE come with Ubuntu or would i have to download it? Obviously that could cause a problem if I cant install the adapter to connect to the internet.

Also, could I install a game on Linux using WINE? I've been dying to play some Diablo but I don't know if it's compatible.

If it matters, the adapter is a Belkin N150 Wireless USB adapter.

Thanks for your help.

---

### Post by yetiman64 on 2010-10-16
> **HarryCromsfelder said:**
> I'm probably going to switch to Ubuntu soon but I had a few questions first. I use a wireless adapter that requires a CD installation, but it's only compatible with Windows. Will I be able to install it with WINE? Also does WINE come with Ubuntu or would i have to download it? Obviously that could cause a problem if I cant install the adapter to connect to the internet.

Also, could I install a game on Linux using WINE? I've been dying to play some Diablo but I don't know if it's compatible.

If it matters, the adapter is a Belkin N150 Wireless USB adapter.

Thanks for your help.

1. You will not need the wireless cd under Ubuntu. Ubuntu has the necessary modules for wireless usually and if it doesn't you can install the necessary Windows drivers using ndiswrapper in Ubuntu (not with Wine though). Try the live cd and if wireless works there it is fully supported and no need for ndiswrapper.

2. You have to install Wine from the repositories yourself but is not needed for your wireless at all. Use the software centre or synaptic or the terminal for installing. Being new in Ubuntu the software centre is probably your best bet.

Test your hardware first by using the live cd (try without installing) and try to setup the wireless under that.

Edit: you can also google for "ubuntu hardware compatibility list + belkin N150" to check the suitability of your particular adapter.

---

