---
title: "How to add my other Linux to boot menu?"
date: 2011-03-19
forum: General Help
---

### Post by SpectrumDT on 2011-03-19
Hello. 

I used to run Fedora 13 on my PC. Recently I have installed Kubuntu 10.10 alongside it. But now Kubuntu has overwritten my Fedora boot loader so I cannot boot Fedora.

Is it possible to restore my Fedora boot options and add them to the boot loader menu that Kubuntu uses (either directly or by chaining to a second boot loader)? 

Thanks in advance.

---

### Post by burton247 on 2011-03-19
What version of GRUB have you got on your MBR?

---

### Post by mr.farenheit on 2011-03-19
try updating grub in terminal

---

### Post by SpectrumDT on 2011-03-19
> **burton247 said:**
> What version of GRUB have you got on your MBR?

Thanks for the reply. grub-install says this:

```
spectrum@spectrum-P55-USB3:~$ grub-install -v
grub-install (GRUB) 1.98+20100804-5ubuntu3
spectrum@spectrum-P55-USB3:~$ 
```

---

### Post by TeoBigusGeekus on 2011-03-19
Try
```
sudo update-grub
```
to see if grub can auto detect your fedora partitions.

---

### Post by SpectrumDT on 2011-03-20
> **TeoBigusGeekus said:**
> Try
```
sudo update-grub
```
to see if grub can auto detect your fedora partitions.

Yes, that worked. Thanks a lot. :)

---

### Post by TeoBigusGeekus on 2011-03-20
You're welcome; don't forget to mark the thread as solved.

---

