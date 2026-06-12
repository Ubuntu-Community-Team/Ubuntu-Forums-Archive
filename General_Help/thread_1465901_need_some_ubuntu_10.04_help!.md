---
title: "need some ubuntu 10.04 help!"
date: 2010-04-29
forum: General Help
---

### Post by lopezman on 2010-04-29
Hi, im lopezman

me, and my brother are somewhat bad Ubuntu user.
here is some basic information, we are both using acer laptops (aspire 5315-2153)i have no idea what that means :D
so if you need any info on the laptops the acer website can tell you more than i can.

as you all know the new ubuntu 10.04 has been released, my brother and i started to upgrade it through the update manager.
while installing it the update manager got stuck on memtest86+ image found : /boot/vmlinuz-2
so some how got past that point and rebooted; upon rebooting there was no option to boot windows the computer tried to boot ubuntu.
the booting got stuck, and said grub panic.
btw that is what happend to my brothers computer 

i stoped my updater when i got stuck on memtest86+ image not found stuff.
i am now to afraid to turn off my computer.

so my questions are:
1.is it alright to turn off my computer?
2.anyway to help my bro, is there any way to help my bro's comp?
3.most important one is...:-k how do i get into these situations???

also me, and my bro were dual booting with windows vista not sure if i said that before

---

### Post by clhsharky on 2010-04-29
HI lopezman

1- Don't shut off computer yet

Go to 'applications/accessories/terminal' click

copy/paste this code

```
sudo update-grub
```

in terminal.

It will ask for your password.
Type your password hit enter.
 
"you wont see your password being enter'd but it is"

It takes a little bit of time for grub to update, 1 or 2 minutes.
If you get any errors tell us what they are.
If no errors, you can reboot.

Sharky

---

### Post by lopezman on 2010-04-30
alright, so i typed sudo update-grub into the terminal, and now it is saying
"found linux image: /boot/vmlinuz-2.6.32-21-generic" over and over agian.

---

