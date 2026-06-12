---
title: "ubuntu as router?"
date: 2006-02-23
forum: General Help
---

### Post by freemanen on 2006-02-23
Is it possible to have a computers that is connected to a third and then the third is connected to the internet?

---

### Post by steve.horsley on 2006-02-23
Yes. This is generally known as IP masquerating. I've never done it, so don't know what's involved, abu a google for "linux ip masquerading" should turn up quite a lot. 

I do know that it is all configured by using iptables, which is a command-line interface to the Linux packet filter. This is rather tricky to drive, and a number of graphical firewall configuration utilities have been made to simplify the configuration - they all just write scripts for iptables. The most common one mentioned in this forum is firestarter. I have previously used guarddog (firewall) and know it has a companion called guidedog that is specifically for configuring IP masquerading. There are many others.

---

### Post by lamego on 2006-02-23
You can read it [here]("http://www.ubuntuforums.org/showthread.php?t=91370") .

---

