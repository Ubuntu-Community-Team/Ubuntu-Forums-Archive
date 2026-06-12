---
title: "Ububtu 12.04 freeze on battery"
date: 2012-05-17
forum: General Help
---

### Post by najdorfchess on 2012-05-17
Hi all. I own a dell 15r laptop and I recently install ubuntu 12.04 64-bit to make use of the entire 8gb ram. Everything runs great and im slowly started to like the unity interface especially the hud which I hated in previous releases, one problem I keep facing is that it keeps freezing when running on battery  power especially when I adjust the screen brightness. Everything becomes unresponsive and I have to abruptly power off the computer and restart it. 
And im using the latest version of kernel and my system is Upto date. 
Anyone knows what the problem could be? Any suggestions? 

Thanks

---

### Post by Erik1984 on 2012-05-17
Does this also happen when you run Ubuntu from the live CD? If so then you might try to do another live session with the boot option 'acpi=off' to see if that makes any difference. [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by najdorfchess on 2012-05-17
Haven't considered checking livecd. But I really don't want to reinstall my OS. I only recently removed everything and did a clean install after Ubuntu 12.04 final beta had some issues, as soon as LTS version got released. So tell me if anything else I could try/ test. Or does it have to do with the latest kernel, one thing I can do is run the older version (one version before, the one that came with the LTS version) and see if I have similar issues. Any other suggestions?

---

### Post by Erik1984 on 2012-05-18
I don't know much about hardware and power issues but I'm only suggesting a boot option, not reinstalling. Just use the Live CD to see if the boot option has any effect w/o reinstalling. If the boot option works you could set it for the already installed Ubuntu.

---

### Post by najdorfchess on 2012-05-18
What boot options? Can you explain?

---

### Post by Erik1984 on 2012-05-18
> **najdorfchess said:**
> What boot options? Can you explain?

'acpi=off' that option can sometimes fix issues with power management (like a machine not properly shutting down). So it was just a suggestion you could try. If you apply that boot option on a Live session it's only temporary to test it out. I can't  explain boot options better than they did in this article:[ https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

---

### Post by aaronmountain on 2012-05-18
Ubuntu 12.04 had got lot of bugs and issues with non pae devices. So generic pae files are to be downloaded which can solve your problem though. At the startup, on grub loader, just run the ubuntu, run the ubuntu in generic pae mode( recovery mode) and it will be in your very low resolution mode. This is what I am doing to check whether if it is not a graphic issue. Then just enter the command $ sudo apt-get install linux-headers-generic-pae and check wether now it runs successfully.

__________________
Love skiing [here]("http://www.luckymountainhome.com/copper_mountain_real_estate/")

---

### Post by gpalarea on 2013-02-01
I was having the "freeze on battery power" too on my old HP Compaq nx6310, but a bios update to the laptop seems to have fixed it.

---

