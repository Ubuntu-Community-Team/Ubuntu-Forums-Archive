---
title: "help deciphering developer-speak"
date: 2010-09-30
forum: General Help
---

### Post by discoross on 2010-09-30
Hi all,

I have a dell laptop with an i7. Windows runs it fine with little to no scaling. Ubuntu 10.0.4 LTS is very bad about keeping the temps down. I'm on powersave mode, and I set all my fans to full speed, but a simple make command will rocket my CPU to 97C and it powers off (or I power it off for safety). 

I came across this
[https://lists.ubuntu.com/archives/kernel-team/2010-January/008467.html](https://lists.ubuntu.com/archives/kernel-team/2010-January/008467.html)
which seems to acknowledge that i7 temps are high due to a bug when determining C2 latency. I can't figure out by going through the thread if they offer a fix (those look like some kind of diff patches), or if they are proposing a fix, or if the fix has been implemented, in which case where can I find it?

---

### Post by migs73 on 2010-09-30
If you have an Inspiron or a Latitude try the i8kutils package in synaptic. It has stuff for monitoring CPU temps and controlling fans speeds.

---

### Post by discoross on 2010-09-30
> **discoross said:**
>  I set all my fans to full speed, but a simple make command will rocket my CPU to 97C 
I have a studio. I can monitor temps and control fan speeds already

---

### Post by discoross on 2010-10-03
I updated to the 2.6.35 kernel and my temps are down, although I don't have an explanation other than that. However $make still boosts my temps up to 200F. 

I did notice that my fans, when set to "full power" never reach their actual full potential. In windows I'll have really loud fans for cpu-intensive things, but in ubuntu I get the medium level when I request the highest. So maybe there is something to your point, migs. 

is there a fan control for a studio system that actually brings my fans to the full power?

---

