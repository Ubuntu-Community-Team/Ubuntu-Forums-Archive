---
title: "New Nvidia driver .... 386 all good - K7 no screens?"
date: 2006-02-26
forum: General Help
---

### Post by OldGaf on 2006-02-26
Hi all,

I have installed the latest Nvidia drivers under Kubuntu 5.10 - 2.6.12.10-386 with no problems on my AMD box. But now when I try to run under 2.6.12.10-K7 I get no GUI. When I try to startx I get a no screens message.

I ran dpkg-reconfigure xserver-xorg with no error, but still the same problem.

Does anyone have any ideas ?

---

### Post by Sutekh on 2006-02-26
[QUOTE=OldGaf]Hi all,

I have installed the latest Nvidia drivers under Kubuntu 5.10 - 2.6.12.10-386 with no problems on my AMD box. But now when I try to run under 2.6.12.10-K7 I get no GUI. When I try to startx I get a no screens message.

I ran dpkg-reconfigure xserver-xorg with no error, but still the same problem.

Does anyone have any ideas ?[/QUOTE]
You will need to grab the linux-restricted modules for your k7 kernel to keep the nvidia drivers working.

```
sudo apt-get install linux-k7
```Will grab the k7 kernel (which you already have) and restricted modules (which you need) in one go.

---

