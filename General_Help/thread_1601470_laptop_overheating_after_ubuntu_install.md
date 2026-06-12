---
title: "laptop overheating after ubuntu install?"
date: 2010-10-20
forum: General Help
---

### Post by supadupadad1 on 2010-10-20
I had given a quick tutorial at school on how to install ubuntu on a computer. One of my classmates came to me this morning and told me that after successfully installing linux his computer shut off. it installed fine. His disk popped out and he restarted  and was able to log in and was navigating around fine. he restarted again to log into windows and was unable because the computer kept shutting off. Same thing when he logged into ubuntu. He waited 20 minutes and was able to use both operating systems fine and no issues after that. I was trying to find an application to monitor the temp of his comuter. I found wmsensors but how do you run it? Any help would be appreciated. I would hate for him to have a bad first impression of linux from the start.

---

### Post by Hippytaff on 2010-10-20
Might this be the kind of thing your looking for
[http://www.bradtrupp.com/ubuntu-cpu-temperature.html](http://www.bradtrupp.com/ubuntu-cpu-temperature.html)
 
also I know some people have been having trouble with overheating with 10.10, possibly a bug

---

### Post by TBABill on 2010-10-20
Which version did he install? I believe the default CPU Frequency Scaling setting is now ondemand, which lowers to about half the CPU's full performance frequency until system demand requires higher, then it jumps up until not needed again. I think in Karmic and before you have to enable it manually. That's an option to help control CPU frequency, but video card heat is another issue altogether. That is normally fixed with the right proprietary driver. Has he installed his video driver if it is available?
 
+1 for Hippytaff's comment about a possible bug if it's 10.10. Many users experiencing higher heat than 10.04 LTS (although 10.04 released with a bug that ran really hot as well but was quickly fixed).

---

