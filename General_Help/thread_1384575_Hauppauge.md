---
title: "Hauppauge"
date: 2010-01-18
forum: General Help
---

### Post by Rick1971 on 2010-01-18
my TV capture card wont even get recognized

it my Windows machine it works fine

but here in Ubuntu 9.10 it does nothing
it i an older WinTv 150 non-PVR
it has the 878 chipset

any suggestions?

---

### Post by fragos on 2010-01-18
Your TV card is recognized and an appropriate drive loaded for it. There will however be no applications for TV until you install them. In a terminal window run "lsmod |grep tv". You will see either bttv or ivtv in the output. If bttv install tvtime and you'll be up in no time. For ivtv you may need to install mythtv which I'm unfamiliar with.

---

### Post by Rick1971 on 2010-01-18
excellent!

it works well

just gotta figure out how to get better picture quality 
then i will set up DVR


thanks

---

### Post by [S2] on 2010-01-18
> **Rick1971 said:**
> my TV capture card wont even get recognized

it my Windows machine it works fine

but here in Ubuntu 9.10 it does nothing
it i an older WinTv 150 non-PVR
it has the 878 chipset

any suggestions?

sure. just install kaffeine. it's an excellent tv app.

---

### Post by saedelaere on 2010-01-26
> **'[S2] said:**
> sure. just install kaffeine. it's an excellent tv app.

Since when does Kaffeine support TV-cards with BT878 chipset?

---

