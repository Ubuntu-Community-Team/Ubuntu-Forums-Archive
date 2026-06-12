---
title: "Swap File relocation (to save ssd life span)"
date: 2010-05-22
forum: General Help
---

### Post by Chareos on 2010-05-22
Hi guys,

strange question I got.
I'm feeling short in RAM on my 1GB netbook with latest Kubuntu running.
The only shortcoming here is lack of RAM. Chromium eats it up literally. So, I'm thinking of a swap file.

Note, I didn't create a swap partition at install-time, cause I'm sensible to possible SSD wearing (even knowing that's unlikely).


So I came up with an ipothetical solution:

- every 5 boot, at startup create a new swap file and mount it
- delete the old swapfile

This way, every 5 boot I'd get the swapfile relocated, and SSD wearing much more leveled.

Is there a way to do so ?
Any of you would be able / have easy hints for me to follow to try and set up this ?


Many thanks

---

### Post by Chareos on 2010-05-22
I studied a little, made up my mind, and decided that relocating swapfile every cold boot is good enough for me (I power off my netbook once per week, and live a lot with suspend/resume).

I added 
```
dd if=/dev/zero of=/swapfileNEW bs=1M count=**128**
rm /swapfile
mv /swapfileNEW /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile

```
to /etc/rc.local

and it seems to work fine.
On SSD, the boot time increase is barely noticeable (for **128** MB)

---

