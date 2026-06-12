---
title: "So, I lost my white Ubuntu logo shutdown screen; how do you get it back?"
date: 2010-03-09
forum: General Help
---

### Post by kelvin.illa on 2010-03-09
I could think of two reasons that may have caused this: (1) I installed "kubuntu-desktop" recently which I then deleted almost immediately; (2) I installed "startUp-manager," and tinkered a little with it. I'm not sure about the latter since it does say it manages--most likely only--the start-up.

Help, please. And thanks.

---

### Post by dcstar on 2010-03-09
> **kelvin.illa said:**
> I could think of two reasons that may have caused this: (1) I installed "kubuntu-desktop" recently which I then deleted almost immediately; (2) I installed "startUp-manager," and tinkered a little with it. I'm not sure about the latter since it does say it manages--most likely only--the start-up.

Help, please. And thanks.
Reinstall the ubuntu-desktop package, or try:
```
sudo update-initramfs -u -k all
```

---

### Post by kelvin.illa on 2010-03-09
> **dcstar said:**
> Reinstall the ubuntu-desktop package, or try:
```
sudo update-initramfs -u -k all
```

The appearance of the shutdown screen, had always been unsure. I was  afraid that I lost it completely this time; I thought I lost it after  several times of not seeing it. But the shutdown screen showed when I shut  down after posting this. Anyway, I'll still try to use your  solution--maybe I could keep my shutdown screen permanently.

I don't have "ubuntu-desktop" installed, so I what I used instead was  your code.

Thanks, David.

---

### Post by kelvin.illa on 2010-03-12
After typing that command, the black background, white Ubuntu logo shutdown screen doesn't ever show anymore--ever. No worries, though, it's purely aesthetic. But I do still wish it wasn't that way.

---

