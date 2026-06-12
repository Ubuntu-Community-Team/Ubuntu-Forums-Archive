---
title: "Lightdm and Nvidia conflict?"
date: 2012-04-03
forum: General Help
---

### Post by Strinnityk on 2012-04-03
Hello everyone, 
the problem I got is, as tittle says a problem with the latest Nvidia drivers and Lightdm.

I'm new to Ubuntu and as I recently installed it (2 days ago) I was trying to update the Nvidia drivers hoping it would allow Ubuntu to detect my display (in the displays menu it says it's unknown).

The thing is that I install correctly the driver (or at least I think I do) but as Nvidia auto-configures xorg.conf setting Nvidia as default I don't get to see the gui; but in the other side if I delete that file so Lightdm becomes default again it shows me the gui but it doesn't detect the Nvidia driver nor detects my screen.

Apart from that, when I boot Ubuntu (I gotta do it from recovery mode->resume) can't boot it normally, I get to login in the TTY not with the gui, thing that doesn't happen if I set lightdm as default (deleting xorg.conf if Nvidia it's default).

I am running Ubuntu x64 11.10

P.S.: My apologies for my bad English.

---

