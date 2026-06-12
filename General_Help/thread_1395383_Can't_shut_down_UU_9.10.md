---
title: "Can't shut down UU 9.10"
date: 2010-01-31
forum: General Help
---

### Post by tommark on 2010-01-31
I have a Dell Latitude D610, installed Ubuntu 9.10 with wubi and Win XP professional. I had only one problem booting which was fixed immediately by meierfra, but now the Ubuntu won't shut down. The final message is "ubuntu 9.10 login", then the screen freezes.
Oddly when I restart from Ubuntu it shuts down enough to reboot into either Windows or back into Ubuntu. To shut down from Ubuntu I'm now holding down the start switch until the machine stops. effective but inelegant.
Thank you very much, whoever you are.
Tom Markham

---

### Post by audiomick on 2010-01-31
Hi.
I don't know what is wrong, I'm sorry.
This command should shut you down. If it doesn't, then something is getting hung up.
```
sudo shutdown -P now
```

---

### Post by tommark on 2010-02-03
Thank you. The matter is now moot. UU won't boot. (poetic that, if exasperating)
But, if I understand your message, I'll need to use the terminal to shut down in future. This seems a bit of a pain in the a.. for this much-touted GUI.

---

### Post by sideaway on 2010-02-03
you could just write a script, put it on your desktop and double click it to shutdown. However, that's just a work around. Wubi... I do not advise you install via wubi...

---

