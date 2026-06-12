---
title: "GRUB wont show fedora partition on start up"
date: 2012-10-09
forum: General Help
---

### Post by ukballer1012 on 2012-10-09
I've spent countless hours trying to solve this with no luck. I tried ubuntu's boot repair but that still didn't work. It generated a report which you can find [here]("http://paste.ubuntu.com/1269882"). Hopefully there is enough information provided in that report to solve the issue but if you guys need more info I'll gladly respond. Thanks in advance.

---

### Post by dniMretsaM on 2012-10-09
Have you tried:
```
sudo update-grub
```

---

### Post by oldfred on 2012-10-10
+1 on dniMretsaM suggestion.

Fedora's default install usually uses LVM and grub has issues finding that. The work around was mounting it (and installing the lvm2 driver) before running the sudo update-grub. But it looks like you just installed to a ext4 partition with a separate /boot. Grub2's os-prober should find it. If not you can copy Fedora boot stanza to 40_custom.

---

