---
title: "No command line"
date: 2010-12-07
forum: General Help
---

### Post by ttalin on 2010-12-07
About two months ago I upgraded my dual boot Linux-x86-64 Vista from Heron to 10.04 Lucid. Initially everything worked fine including wireless etc. Once I accidentally changed a few /etc permissions which caused a problem, but fixed it going into recovery mode. For the past weeks, I only used the windows. Over the weekend I tried logging into Ubuntu, the gnome would not come up. So, I went into recovery mode and typed "sudo apt-get update && sudo apt-get upgrade" which also went through. However, after that I lost the recovery options. I had used that command very successfully in the past. Right now, I have no command line that would allow me to type something. I was wondering if there are any keys Alt+Del + something that would give me a prompt I can work with. I'm totally baffled as to how this can happen. Any help would be appreciated I'm counting on special keys?? Thanks in advance.

---

### Post by matt_symes on 2010-12-07
Hi

Open a terminal and type  

sudo update-grub

See if this brings the option back in the grub menu (I think that is what you are asking)

Kind regards

---

