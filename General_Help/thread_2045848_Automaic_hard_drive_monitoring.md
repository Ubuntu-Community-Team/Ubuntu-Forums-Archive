---
title: "Automaic hard drive monitoring"
date: 2012-08-22
forum: General Help
---

### Post by 8301 on 2012-08-22
Hello

I am planning to build a simple home server using spare SATA drives. This server will be put away some where, where it will be dark and cold, and the only connection is made by SSH and via command line.

One thing that worries me is that my drives is getting old, aprox. 5 years in operation, and I don't want to get at visit from an hard drive angel while the drives are in operation.  

Is there a way to monitor the drives, software wise, so I can receive a warning message that the drives need to be replaced before I begin "loose" data?

I know that nothing is bullet proof but I want to be as preventive as possible from hard drive crashes.

Br

---

### Post by dino99 on 2012-08-22
if that SATA drive support S.M.A.R.T commands (and it might) then the package smartmontools is what you need.

---

### Post by mikechant on 2012-08-22
SMART data monitoring is definitely worth doing - but it's not really enough - I've read that maybe 50% of hard drive failures happen with no SMART warning at all, and there is no foolproof way to predict these failures. 

You have to work on the assumption that you can loose all your data at any time without warning, and take appropriate backup measures.

---

