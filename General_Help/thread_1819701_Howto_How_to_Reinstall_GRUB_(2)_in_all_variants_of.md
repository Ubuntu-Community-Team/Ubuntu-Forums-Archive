---
title: "Howto: How to Reinstall GRUB (2) in all variants of Ubuntu - THE EASY WAY!"
date: 2011-08-06
forum: General Help
---

### Post by x-D on 2011-08-06
_**THE METHOD I'M ABOUT TO SHOW YOU CAN BE DONE FROM:**_

. A LIVE DISK/CD/DVD
. A LIVE USB
. ANY OTHER LIVE MEDIA
. AN INSTALLED VERSION OF UBUNTU (KUBUNTU, XUBUNTU, EDUBUNTU, UBUNTU, LUBUNTU, ETC, ETC)

The absolute EASIEST WAY, to (re)install GRUB is to use a little program   called Boot-Repair. It does all that work to do with commands in the   Terminal to reinstall GRUB for you, and it's really noob friendly, with a   simple GUI, that you merely have to indicate which OS you want as your   main Operating System etc, IF YOU WANT TO! This is all under advanced   options, but really, it's not so advanced, anyway to get Boot-Repair:[U][B]

Do this in the Terminal:[/B][/U]

```

sudo add-apt-repository ppa:yannubuntu/boot-repair

sudo apt-get update && sudo apt-get install -y boot-repair-ubuntu

```Now, run the program (search for it in Unity, or go to: System   ----> Administration ----> Boot Repair, in Gnome 2/ Classic Mode   in 11.04 Natty Narwhal)

Then, once the program is done reinstalling GRUB (should take at max 2 minutes), do this:

```

sudo update-grub

```This is probably not necessary, but it will just eradicate the potential for any errors, whatsoever!

_**Inf****o for this can be found by:**_

a) going to: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
b) messaging me here.

Hope this helped...

x-D :guitar:

---

