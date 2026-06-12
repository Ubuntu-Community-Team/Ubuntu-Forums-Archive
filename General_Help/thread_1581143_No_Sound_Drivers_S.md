---
title: "No Sound Drivers :S"
date: 2010-09-24
forum: General Help
---

### Post by ardit ,A, on 2010-09-24
Hello.
I can't hear hear anything at my pc on my headsets :S

I had my drivers on XP and I have CD now (for XP,7 and Vista) 

My drivers: **ViA Technologies.**

How to install...?

and. I try '**Hardware Drivers**' but says:
*_No proprietary drivers are in use in this system_*

---

### Post by lkjoel on 2010-09-24
> **ardit ,A, said:**
> Hello.
I can't hear hear anything at my pc on my headsets :S

I had my drivers on XP and I have CD now (for XP,7 and Vista) 

My drivers: **ViA Technologies.**

How to install...?

and. I try '**Hardware Drivers**' but says:
*_No proprietary drivers are in use in this system_*
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by ardit ,A, on 2010-09-25
> **lkjoel said:**
> Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

Nope that didn't help me!
Didn't work :S

---

### Post by lkjoel on 2010-09-25
Go to Post-Fix your sound! and download the script into your homedir.
Then type this into a Terminal Window:
```
cd ~
chmod +x CPanel.sh
./CPanel.sh osspart1
# RESTART COMPUTER NOW
./CPanel.sh osspart2
./CPanel.sh -r
```

---

### Post by ardit ,A, on 2010-09-25
> **lkjoel said:**
> Go to Post-Fix your sound! and download the script into your homedir.
Then type this into a Terminal Window:
```
cd ~
chmod +x CPanel.sh
./CPanel.sh osspart1
# RESTART COMPUTER NOW
./CPanel.sh osspart2
./CPanel.sh -r
```

Im using Ubuntu 10.04 LTS

When I type: chmod +x CPanel.sh TERMINAL says:
chmod: cannot access `CPanel.sh': No such file or directory

Is this right file: CPanel.download when I download In Post-Fix is this file not CPanel.sh :S

---

