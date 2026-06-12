---
title: "windows 7 no boot"
date: 2011-10-05
forum: General Help
---

### Post by dhulagu on 2011-10-05
I have installed ubnuntu 11.04 alongside windows 7. Now I cannot get windows 7 to boot. It goes straight to ubuntu 11.04. It shows the message "over range" on startup.  How can I correct this, I don't want to lose all my stuff on windows.

---

### Post by garvinrick4 on 2011-10-05
In ubuntu open a terminal (ctrl/alt/t)
```
sudo update-grub
```
If that does not do it.
show me the output of:
```
sudo fdisk -l
```
```
sudo parted -l
```
Lower case L on both of them.

---

### Post by mikejonesey on 2011-10-05
so many have issues with this... I may create a gui program for this at some point... or at least a hench bash...

```
sudo apt-get instal os-prober
sudo os-prober
update-grub2
```

does what?

what were the symptoms / scenario around the disappearance? an update or partitioning...

---

### Post by mikejonesey on 2011-10-05
@garvinrick4

beat me to it lol...

---

### Post by garvinrick4 on 2011-10-05
> so many have issues with this... I may create a gui program for this at some point... or at least a hench bash...
Been done drs305:
[HOWTO: Grub Customizer - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=10340183#post10340183")

---

