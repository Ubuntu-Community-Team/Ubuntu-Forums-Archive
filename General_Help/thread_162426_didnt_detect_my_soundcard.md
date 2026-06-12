---
title: "didnt detect my soundcard"
date: 2006-04-19
forum: General Help
---

### Post by runefreak on 2006-04-19
ad1881 compaq presario 5020 worked with windows me doesnt work now need help

---

### Post by Sutekh on 2006-04-19
According to the Ubuntu Wiki, you should have support for that particular card.

[Ubuntu Wiki - Hardware Support - Sound Cards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards?highlight=%28ad%29%7C%281881%29%7C%28sound%29%7C%28card%29)

Can you try opening a terminal window and using this command
```
alsamixer
```
and adjust the speaker levels to see if you can hear sound.

There are commands that you can use to check that the sound card has been detected, I will try to find them.

Otherwise you can open the Device Manager (System -> Administration menu) and see if you can find the card in there.

---

### Post by runefreak on 2006-04-19
mark@ubuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
mark@ubuntu:~$
that is what i got there are no drivers for my card from the manufacturer
for linux

---

### Post by runefreak on 2006-04-19
can someone please help me?

---

