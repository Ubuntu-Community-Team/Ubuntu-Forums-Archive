---
title: "Nvidia driver install...can't get it to work..."
date: 2011-03-25
forum: General Help
---

### Post by RallyDarkstrike on 2011-03-25
Hey folks, I am hoping somebody can give me a little assistance, because I am lost...

I'm not a Linux newbie, per-se, but I have been tinkering with it in VMs for a few years now. However, last night, when I was updating my backup WinXP machine, the Windows install decided to corrupt itself so I thought "Hey, I'll try Ubuntu!"

Now...at the moment, I have it installed and working ok, but I've been trying since last night to get the Nvidia drivers working and no matter what I do the OS either won't use them or it won't boot to X, just the terminal. The system is a 1.5ghz Athlon 1800+ with 512mbs of RAM, and a 64mb Nvidia Quadro2 Pro video card on a 20gb HDD.

I've tried at least 6 different methods I've found to install drivers (many of them differing from each other, so I have no idea which way is right...) through searching on Google. As it stands at the moment, I have used the "sudo apt-get purge nvidia*" command to get rid of anything Nvidia-related to start from scratch. Also, I had read somewhere to uninstall the nouveau drivers as they conflict, so I have also run "sudo apt-get --purge remove xserver-xorg-video-nouveau" as well.

I've tried installing drivers from the Synaptics Manager as well (specifically the 96 drivers as I read elsewhere they are what apply to this card). Could somebody kindly point me to a method they KNOW should work as all the ones I've tried seem to have failed...or give me a step by step guide on how to sort this out? :( I thank anybody many times over in advance!!! :)

---

