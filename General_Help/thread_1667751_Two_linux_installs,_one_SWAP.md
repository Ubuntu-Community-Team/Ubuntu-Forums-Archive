---
title: "Two linux installs, one SWAP?"
date: 2011-01-15
forum: General Help
---

### Post by CrimsonBizarre on 2011-01-15
I already have a ubuntu install on my computer, alongside a windows install. I'm going to add an archlinux install as well. I already have a SWAP for my ubuntu install; do I have to create another for arch, or can I get them both to use the same one?

Thanks in advance.

---

### Post by Nickjpost on 2011-01-15
Three OS on one machine? I would personally put archlinux on an external if possible, but you need a separate swap

---

### Post by CrimsonBizarre on 2011-01-15
> **Nickjpost said:**
> Three OS on one machine? I would personally put archlinux on an external if possible, but you need a separate swap
I'm going to remove ubuntu later, but at the moment I need both. And thanks for answering my question.

---

### Post by Jerry N on 2011-01-15
> **Nickjpost said:**
> Three OS on one machine? I would personally put archlinux on an external if possible, but you need a separate swap

I don't know anything about archlinux but certainly the various distributions of Ubuntu and Mint share a swap file and I would expect that to be true about almost any Linux distribution.  

I have installed two different Linux distributions on the same HD with Windows without difficulty.  I have also installed two different Windows distributions (XP, Win7) on a drive along with Ubuntu.

Jerry

---

### Post by CrimsonBizarre on 2011-01-15
> **Jerry N said:**
> I don't know anything about archlinux but certainly the various distributions of Ubuntu and Mint share a swap file and I would expect that to be true about almost any Linux distribution.  

I have installed two different Linux distributions on the same HD with Windows without difficulty.  I have also installed two different Windows distributions (XP, Win7) on a drive along with Ubuntu.

Jerry
Good to hear, thanks for that.

---

### Post by Nickjpost on 2011-01-16
> **CrimsonBizarre said:**
> Good to hear, thanks for that.
If you use software-suspend/hibernate it may be an issue. Ram is saved to swap in that circumstance, and you could potentially lose quite a bit of data if you brought up another distro after suspending.
Better safe than sorry is how I roll, but Jerry is right, you could.

---

### Post by Jerry N on 2011-01-16
> **Nickjpost said:**
> If you use software-suspend/hibernate it may be an issue. Ram is saved to swap in that circumstance, and you could potentially lose quite a bit of data if you brought up another distro after suspending.
Better safe than sorry is how I roll, but Jerry is right, you could.

Since we are talking about multiboot, wouldn't the required reboot to bring up another OS wipe out whatever you have saved in the swap partition anyhow?  

Jerry

---

