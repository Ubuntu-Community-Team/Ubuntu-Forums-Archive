---
title: "My Ubuntu has collapsed!"
date: 2009-12-22
forum: General Help
---

### Post by shabani23 on 2009-12-22
Pls all help me, how do I update my Ubuntu in the condition before broke up! If anyone can tell me the code how to update it, it would be very helpful. thanks all!

---

### Post by synapsys on 2009-12-22
> **shabani23 said:**
> Pls all help me, how do I update my Ubuntu in the condition before broke up! If anyone can tell me the code how to update it, it would be very helpful. thanks all!

We might need a little more info than that in order to help.....

What happened?

---

### Post by shabani23 on 2009-12-22
> **synapsys said:**
> We might need a little more info than that in order to help.....

What happened?

I was using it normaly, and than it got stuck I restarted it, but now it goes only in comand prompt, so I tried to switch with ctrl+alt+f7 but it doesn't switch. How do I update everything from the last time I was using it? I don't have an Ubuntu cd here because I would have reinstalled it. 

Thanks for your help.

---

### Post by synapsys on 2009-12-22
what does your command prompt look like?

grub>      ?

---

### Post by shabani23 on 2009-12-22
> **synapsys said:**
> what does your command prompt look like?

grub>      ?

it is black and just waiting for a command! I tried sudo apt get update, but doesn't accept that command. it is just like when your screen doesn't work and than you try to download the drivers from command prompt.

---

### Post by synapsys on 2009-12-22
So there is no boot menu and no chance to boot into recovery mode?

---

### Post by shabani23 on 2009-12-22
> **synapsys said:**
> So there is no boot menu and no chance to boot into recovery mode?

I think there is boot menu, but I don't know how it goes, because I didn't use Ubuntu for a long time.

---

### Post by Conzo on 2009-12-22
Use your Install Disc ( live )  THen do the sudo grub update restart and should be fine

---

### Post by synapsys on 2009-12-22
> **Conzo said:**
> Use your Install Disc ( live )  THen do the sudo grub update restart and should be fine

I think you mean

```
sudo update-grub
```

I don't think he has a live cd.

---

