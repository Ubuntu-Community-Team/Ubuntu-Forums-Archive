---
title: "Dual Boot disappeared"
date: 2010-12-17
forum: General Help
---

### Post by badreligionxtc on 2010-12-17
I have Ubuntu 10.04 and Windows 7 installed on my laptop. I used to be able to dual boot both systems. While fixing the issue of my low resolution splash screen i may have changed something. when booting my computer i am no longer able to choose whether i want to boot windows or ubuntu. i just have a black screen for a few seconds. any help please?

---

### Post by trinitydan on 2010-12-17
Try opening a terminal and typing sudo update-grub.  Then reboot and it should be there.

---

### Post by wilee-nilee on 2010-12-17
> **badreligionxtc said:**
> I have Ubuntu 10.04 and Windows 7 installed on my laptop. I used to be able to dual boot both systems. While fixing the issue of my low resolution splash screen i may have changed something. when booting my computer i am no longer able to choose whether i want to boot windows or ubuntu. i just have a black screen for a few seconds. any help please?

Is this a wubi install, and can you remember the changes you made?

Were the changes outside of the menu-system-preferences monitor gui?

---

### Post by wilee-nilee on 2010-12-17
> **trinitydan said:**
> Try opening a terminal and typing sudo update-grub.  Then reboot and it should be there.


Black screen no boot at all.

---

### Post by trinitydan on 2010-12-17
> **badreligionxtc said:**
>  i just have a black  screen for a few seconds.


 > **wilee-nilee said:**
> Black screen no boot at all.

I guess I was under the assumption that after the few seconds it was booting Ubuntu.  Maybe I was mistaken?

---

### Post by wilee-nilee on 2010-12-17
> **trinitydan said:**
> I guess I was under the assumption that after the few seconds it was booting Ubuntu.  Maybe I was mistaken?


It is a rather vague description.;) no it actually boots into something; that would help.

---

### Post by badreligionxtc on 2010-12-17
Thanks for the help guys but do i feel like an idiot.... I just realized that when i fixed my splash screen i used StartUp-Manager. I realized that i changed my Timeout time to 0. thanks for the help and don't make fun of me too bad haha.

---

### Post by wilee-nilee on 2010-12-17
> **badreligionxtc said:**
> Thanks for the help guys but do i feel like an idiot.... I just realized that when i fixed my splash screen i used StartUp-Manager. I realized that i changed my Timeout time to 0. thanks for the help and don't make fun of me too bad haha.

ooooh 0 nah we all make mistakes .;)

---

