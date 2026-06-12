---
title: "PlayOnlinux freezes after trying to install starcraft2"
date: 2011-01-12
forum: General Help
---

### Post by LetsMugSanta on 2011-01-12
Yeah so I started up Playonlinx, go down to the starcraft 2 option and click apply or install and all it does is freeze up every time. Last time I installed starcraft 2 just through wine I had some in game issues that made it non playable.

Any ideas?

---

### Post by Nextgeneration on 2011-02-02
> **LetsMugSanta said:**
> Yeah so I started up Playonlinx, go down to the starcraft 2 option and click apply or install and all it does is freeze up every time. Last time I installed starcraft 2 just through wine I had some in game issues that made it non playable.

Any ideas?


I am having the same problem, mine has the option to update but It won't let me maby something to do with that.

---

### Post by Cyrushehe on 2011-02-03
hey go to playonlinux.com and download 3.3.8 that fixed mine

---

### Post by x C0MMAND0 x on 2011-02-03
Quick Way...

```

wget -q "http://deb.playonlinux.com/public.gpg" -O - | sudo apt-key add -
sudo wget http://deb.playonlinux.com/playonlinux_maverick.list -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

```

*Assuming you are on 10.10

---

### Post by Zalib on 2011-02-17
I know this is kinda digging up an old thread and thanks for the help. I'm having problems getting starcraft 2 under wine to work properly and I hope this will be a good alternative. Although I have to ask How reliable is Play on linux over using wine to run starcraft 2? Play on linux seems to me like a very weird and unprofessional program where as wine seems to have more people behind it you know? That's just my opinion anyways. I just would like to know the differences.

---

