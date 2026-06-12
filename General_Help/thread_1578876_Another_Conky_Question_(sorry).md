---
title: "Another Conky Question (sorry)"
date: 2010-09-21
forum: General Help
---

### Post by thefallofroy on 2010-09-21
Just a quick one, as you can see from my screenshot I want to have both the storage space of vista and ubuntu displayed. Clearly I am not using the right code to display the vista info but ubuntu is just fine. Is this possible? Is it possible to display how much space is used/free in my windows partition even though I'm using wubi?

---

### Post by VCoolio on 2010-09-21
In this part
```
${fs_used /} of ${fs_size /}
```
the / is the path to the folder or partition you want to be checked. You need to point that to your windows partition, like
```
${fs_used /media/disk} of ${fs_size /media/disk}
```
Run 'mount' in a terminal to see what path you need.

---

### Post by thefallofroy on 2010-09-21
> **VCoolio said:**
> In this part
```
${fs_used /} of ${fs_size /}
```
the / is the path to the folder or partition you want to be checked. You need to point that to your windows partition, like
```
${fs_used /media/disk} of ${fs_size /media/disk}
```
Run 'mount' in a terminal to see what path you need.

Here is a screenshot after i put mount in the terminal. Which one do I need? I tried both /dev/sda2 and /dev/loop0, they both give me the same info, and even though its diff from what ubunutu is, I dont think thats right. Because I know for a fact that I have WAY more than 300 KB out of 1.47 GB...

---

### Post by VCoolio on 2010-09-21
At least you don't want anything starting with /dev; that is where the hardware is found. It is mounted to something elsewhere (called the mountpoint, which is what you need here), but it seems wubi handles things differently and I'm not sure. Try /host. Also, I assume you can browse your windows stuff in a file manager; check what path is mentioned there.

---

### Post by thefallofroy on 2010-09-21
There, I got it. It was /host/Windows, I should've known xD thanks for helping me clarify.

---

