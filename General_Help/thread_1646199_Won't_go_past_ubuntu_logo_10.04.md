---
title: "Won't go past ubuntu logo 10.04"
date: 2010-12-15
forum: General Help
---

### Post by Headhoncho6123 on 2010-12-15
Hi, I am running ubuntu 10.04 and I disabled KMS for radeon  by running

echo options radeon modeset=0 | sudo tee /etc/modprobe.d/radeon-kms.conf

 When I rebooted it just stalled at a screwed up ubuntu logo so I booted into recovery mode and typed in

echo options radeon modeset=1 | sudo tee /etc/modprobe.d/radeon-kms.conf

To no avail. Where I got the code from it said that I could remove and kms would be enabled so I ran

rm /etc/modprobe.d/radeon-kms.conf 

Well right now I am back on the other partition with 9.04 coming to yall for help. I'm not too skilled with ubuntu but I have been running it for a while.

---

