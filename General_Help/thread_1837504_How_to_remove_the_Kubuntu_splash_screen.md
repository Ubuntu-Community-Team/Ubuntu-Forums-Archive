---
title: "How to remove the Kubuntu splash screen"
date: 2011-09-01
forum: General Help
---

### Post by linuxuser12345 on 2011-09-01
Hi, I once had Kubuntu installed on my system through Ubuntu, but something went wrong and it caused the system to freeze a lot, so I removed Kubuntu, but the splash screen stayed. Is there any way I can revert my splash screen back to the original Ubuntu one?

I am running Ubuntu 11.04 "Natty Narwhal"

---

### Post by oldos2er on 2011-09-02
Try ```
sudo dpkg-reconfigure gdm
```

---

### Post by linuxuser12345 on 2011-09-04
I just tried that and it didn't help one bit! :(
Any ideas??

---

### Post by linuxuser12345 on 2011-09-05
Is there any way I can just replace the Kubuntu splash screen with the Ubuntu splash screen?

---

### Post by moorhead98 on 2011-09-05
> **linuxuser12345 said:**
> Is there any way I can just replace the Kubuntu splash screen with the Ubuntu splash screen?
There are a couple of programs. What I would recommend would be Plymouth Manager. It can change splash screens, and install newer, more awesome ones as well. Another good one is Zorin splash screen manager.
Also, Alternatives Configuraor can change it in like three clicks

---

### Post by sisco311 on 2011-09-05
If you don't want to install Plymouth Manager, then run:
```

sudo update-alternatives --config default.plymouth
sudo update-initramfs -u

```

---

### Post by oldos2er on 2011-09-05
> **linuxuser12345 said:**
> I just tried that and it didn't help one bit! 
Any ideas??

What happened exactly? Is the package gdm installed?

---

### Post by linuxuser12345 on 2011-09-05
Okay, I figured it out! I typed in "Plymouth Themes" in the Ubuntu Software Center and deleted anything relating to Kubuntu. The problem is fixed! :)

Thanks

---

