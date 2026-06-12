---
title: "Laptop locks, not running warm"
date: 2009-09-07
forum: General Help
---

### Post by Enk on 2009-09-07
Hi

My laptop have latelly been locking up, and I am not sure were to start to find the cause. 

I've tried to install sensors to check CPU-temperature, but none have worked. Though I have noticed that the computer doesn't lock up only when it is hot (that is, when it feels really hot), it also lock while only running a few programs.

I use Firefox with flashblock so it doesn't take up to much CPU.

---

### Post by khelben1979 on 2009-09-07
If there's a hardware problem and you have warranty left for it you should send it for repairs. If it's software related, it could be that your kernel don't like your hardware, then you could try with another version of Ubuntu or compile your own kernel.

Also here's a couple of questions:
1. Is this the result of a fresh install of Ubuntu? 
2. What Ubuntu version?
3. And what are the hardware specifications for this laptop?

---

### Post by Enk on 2009-09-07
Hi, thanks for reply.

1. No, I have been using this computer for 2-3 months without problems.

2. I am running Xubuntu 9.04

3. [http://www.mipmap.org/downs/lshw.html](http://www.mipmap.org/downs/lshw.html)

---

### Post by Enk on 2009-09-09
bump:confused:

---

### Post by P4man on 2009-09-09
Try adding "noapic" and/or "nolapic" (without quotes) to your kernel parameters. If you dont know how to add those, have a look here:
[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

If that doesn't help, you could try a more radical solution of adding "acpi=off"

---

