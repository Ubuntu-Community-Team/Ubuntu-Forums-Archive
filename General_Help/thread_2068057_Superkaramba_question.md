---
title: "Superkaramba question"
date: 2012-10-08
forum: General Help
---

### Post by Statia on 2012-10-08
I have a nice Superkaramba theme called sysmaloon (it's a bit like Conky) that I have been tweaking to suit my needs and hardware.
As I have an Asus motherboard that is not really supported by lm-sensors, I don't get voltages or fan speeds. Instead I've been putting in some other system info.
On one line, it displays the CPU clocks. I have a dual core, hyperthreading CPU, so there are four values.
The strange thing is that this:

```
cat /proc/cpuinfo | grep MHz | awk '{print $4}' | cut -c -4 | paste -sd " "
```works in bash, but not in Superkaramba. Does anyone have an idea why not? Does Superkaramba use a different shell to parse its themes?

I solved it with:

```
cat /proc/cpuinfo | grep MHz | awk '{print $4}' | cut -c -4 |  xargs -I {} echo {}  | xargs echo"
```A bit more clunky, but it works.
Still curious why the other one does not work though.

---

### Post by Statia on 2012-10-09
Maybe a good time for a bump.

---

