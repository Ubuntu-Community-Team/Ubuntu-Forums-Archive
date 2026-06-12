---
title: "Weird behavior"
date: 2009-11-30
forum: General Help
---

### Post by suby-luby on 2009-11-30
All,

I have a double boot system (Ubuntu and Windows). I wanted to resize my Ubuntu partition. The only way I was able to was by deleting the swap partition, resize the partitions, and recreate the swap.

The problem now is that everytime I try to log in to my Ubuntu, it kicks me out.

Something is wrong with X Window, because when I do shell login, I am able to do so successfully.

Can anyone please tell me what's going on?

I really need to get to my data so please help me if you know.

Thanks a million

---

### Post by utnubuuser on 2009-12-01
Tried updating grub?
> sudo update-grub

---

### Post by suby-luby on 2009-12-01
> **utnubuuser said:**
> Tried updating grub?

I did, and it did not fix the problem.

Please help!!

---

### Post by DGortze380 on 2009-12-01
> **suby-luby said:**
> All,

I have a double boot system (Ubuntu and Windows). I wanted to resize my Ubuntu partition. The only way I was able to was by deleting the swap partition, resize the partitions, and recreate the swap.

The problem now is that everytime I try to log in to my Ubuntu, it kicks me out.

Something is wrong with X Window, because when I do shell login, I am able to do so successfully.

Can anyone please tell me what's going on?

I really need to get to my data so please help me if you know.

Thanks a million

Boot your recovery kernel and select XFix

---

### Post by suby-luby on 2009-12-01
> **DGortze380 said:**
> Boot your recovery kernel and select XFix

I tried that, it did not fix it. Here is the strange part though.

When I login using a console application as a root, and then issue startx, it works just fine.

However, when I login, again using a console, as a regular user, and issue startx, it tries and then fails.

It shows a message saying window number is 2 while its supposed to be 1 (or something to the effect).

I have no clue, why this weird behavior.

Any tips are appreciated.

---

### Post by khelben1979 on 2009-12-01
Try: ```
startx -- :1
```

---

