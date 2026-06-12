---
title: "opencl not detecting multiple gpus"
date: 2012-07-01
forum: General Help
---

### Post by joshpunb on 2012-07-01
My goal is to have opencl setup on my computer for research work and be  able to use 3 gpus and a cpu for computing. Is there something I am  missing regarding setting up opencl on ubuntu 11.04 to have my system  recognize multiple gpus. (3 x HD6950).

My installation steps were as follows from a fresh install:
1.  Download and install catalyst 12.6. I followed the installation  instructions provided by amd for installing on a linux system then used  command "sudo aticonfig -f --initial --adapter=all".
2.  Download and install AMD-APP-SDK-v2.7.

Using  the command clinfo only recognizes my cpu and 1 of 3 gpus. Is there  another step that I am missing, such as setting up xorg.conf? If so then  what am I missing and how would I go about fixing it?

---

### Post by joshpunb on 2012-07-04
anyone?

---

