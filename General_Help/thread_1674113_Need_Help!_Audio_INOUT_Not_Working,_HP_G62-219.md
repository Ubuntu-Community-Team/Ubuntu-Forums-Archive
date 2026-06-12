---
title: "Need Help! Audio IN/OUT Not Working, HP G62-219"
date: 2011-01-23
forum: General Help
---

### Post by simon174 on 2011-01-23
Hello All,

I have been following this forum for a very long time as a guest, and it has been extremely helpful, so thank you to everyone for your kind support. You have helped a lot more people than you think!

My problem is that I just used Wubi to install Ubuntu! It's going so great! Except for one thing. My laptop audio features are not working. If I plug in a pair of headphones, then it does, but from the speakers, no luck. Some basic info. about my set up are as follows:

```

Version KernelLinux 2.6.32-27-generic (x86_64) Compiled#49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 C LibraryGNU C Library version 2.11.1 (stable) Default C CompilerGNU C Compiler version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)  DistributionUbuntu 10.04.1 LTS
Computer Processor2x Pentium(R) Dual-Core CPU       T4500  @ 2.30GHz Memory3021MB (1371MB used) Operating SystemUbuntu 10.04.1 LTS 

Date/TimeSat 22 Jan 2011 04:54:23 PM EST Display Resolution1366x768 pixels OpenGL RendererUnknown X11 VendorThe X.Org Foundation 
Multimedia Audio AdapterHDA-Intel - HDA Intel

```I am very new to Ubuntu, but am learning fast. If anymore info. is needed, please instruct me as to how to retrieve it, and will post it right away. My speakers are Altec-Lansing if that has any significance. Thank you very much everyone, I really look forward to using Ubuntu to maximum potential.

**2801I (ICH9 Family) HD Audio Controller**

cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ID 270
Codec: LSI ID 1040
Codec: Intel G45 DEVCTG


Regards,

Simon

---

### Post by hanciong on 2011-02-02
I have the same problem like you. I have HP G62 100SL. The sound doesn't work. after updating ALSA, the sound  works..... for a while. After some other update (from update manager),  the sound doesn't work again. why is this? and then if I run firefox,  other video programs seem don't work (for example like VLC or totem).  The movie I play there just doesn't play. In order for them to work, I  must close  firefox first. how to fix this? Thanx a lot

---

