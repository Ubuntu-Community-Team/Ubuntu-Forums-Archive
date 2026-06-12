---
title: "xorg.conf wrong"
date: 2010-10-18
forum: General Help
---

### Post by DelusionalX on 2010-10-18
Hi guys,

After a lot of trying and fresh **Ubuntu 10.10** installs (2 to be exact) I finally found what (I think) is causing my nvidia driver issues.

What I did:

- Fresh 10.10 install
- updated
- installed nvidia-current through terminal
- made xorg.conf using "sudo nvidia-xconfig" (gave error that is didn't exist and created a new one)

Then normally I would have to restart X to make the magic happen...
Well, it happened and now I'm at a tty1 terminal on boot.

I can delete my xorg.conf file and boot to my (low res) desktop.

When I'm at the tty1 terminal and type "startx" it gives me an error describing it can't find the nvidia driver stated in the xorg.conf file.

I wanted to install the official nVidia drivers but I can't boot into recovery (hangs on initialisation).

My question now is: has anyone been able to get the nvidia drivers working in 10.10 and how did he/she do it?

Thanks,
also, first post.

---

