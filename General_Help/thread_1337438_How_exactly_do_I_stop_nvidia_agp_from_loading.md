---
title: "How exactly do I stop nvidia_agp from loading?"
date: 2009-11-25
forum: General Help
---

### Post by joeljoel on 2009-11-25
How exactly do I stop nvidia_agp from loading so that nvagp will load?

It complains: "NVRM: not using NVAGP, an AGPGART backend is loaded!"

That backend would be nvidia_agp. But I don't know how to stop it loading.

Please help, I've been searching for hours.

Edit: Sorry, I'm using karmic.

---

### Post by Sam on 2009-11-25
Run in a terminal:```
gksudo gedit /etc/modprobe.d/blacklist
```

Add the line```
blacklist nvidia_agp
```

Save, close and reboot.

---

### Post by Kelly3030 on 2009-11-25
Not sure but...I recently saw another similar thread maybe it can help here....

[http://www.uluga.ubuntuforums.org/showthread.php?t=410745](http://www.uluga.ubuntuforums.org/showthread.php?t=410745)


:P Quikshiptoner.com

---

### Post by joeljoel on 2009-11-25
> **Sam said:**
> Run in a terminal:```
gksudo gedit /etc/modprobe.d/blacklist
```

Add the line```
blacklist nvidia_agp
```

Save, close and reboot.

I don't have '/etc/modprobe.d/blacklist', the closest I have is '/etc/modprobe.d/blacklist.conf'

So I added 'blacklist nvidia_agp' to '/etc/modprobe.d/blacklist.conf'.
I also created '/etc/modprobe.d/blacklist' and added 'blacklist nvidia_agp' to that as well.

Rebooted and nvidia_agp was still loaded.

> **Kelly3030 said:**
> Not sure but...I recently saw another similar thread maybe it can help here....

[http://www.uluga.ubuntuforums.org/showthread.php?t=410745](http://www.uluga.ubuntuforums.org/showthread.php?t=410745)

I also tried adding 'agpgart' to the two blacklist files above (although I don't think it's necessary according to the Nvidia driver notes) and both agpgart and nvidia_agp still loaded.

---

### Post by Sam on 2009-11-25
Oops that was right, it's blacklist.conf.

Run```
lsmod |grep nvidia_agp
```It will tell you which modules need nvidia_agp.

---

### Post by joeljoel on 2009-11-25
```
lsmod | grep nvidia_agp

nvidia_agp	6200	1
agpgart		34988	2 nvidia,nvidia_agp
```

---

### Post by Sam on 2009-11-25
What if you blacklist "nvidia" and "nvidia_agp" ?

---

### Post by joeljoel on 2009-11-25
With nvidia blacklisted as well, lsmod still lists both.

---

### Post by wojox on 2009-11-25
Put this in xorg.conf Device section ( section with Driver and Vendor name)

```
Option         "NvAgp" "0"
```

Save and reboot.

Might also try blacklisting this:

```
blacklist nvidia-agp
```

---

### Post by joeljoel on 2009-11-25
Thanks all for your help!

Turns out I'd done everything already except this:
```
update-initramfs -u
```

---

