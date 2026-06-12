---
title: "MFC 440CN printer/scanner"
date: 2011-05-05
forum: General Help
---

### Post by SDRED on 2011-05-05
How do I get the scanner part of my printer to work?  I thought once the driver for the printer was installed that everything would work.

---

### Post by plucky on 2011-05-05
> **SDRED said:**
> How do I get the scanner part of my printer to work?  I thought once the driver for the printer was installed that everything would work.

You have to go [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html) and download the correct .deb file driver for your printer and install.Also follow all the steps in the installation instructions.

Good Luck

---

### Post by walt.smith1960 on 2011-05-05
Yes the printer & scanner are almost treated like separate machines.  Download the scanner software and install it after the preparatory steps.  Be sure you have either CSH or TCSH installed--you can check that in Synaptic package manager.  You don't *have* to install the scan key tool right away if you don't want to.  I have two Brother MFDs networked and there's one step that has to be done from the command line for networked machines.  ```
brsaneconfig(2-3-4 as required) -a  name=(name  your  device)  model=(model  name)  ip=xx.xx.xx.xx 

```This doesn't apply to USB connections.

---

### Post by doubtful wisdom on 2011-05-08
SODRED, how did you get the MFC-440CN printer to work?  I have been trying to get it running for days, with no success.  It printed and scanned in for years under previous versions of Ubuntu.  Not now.  The printer is seen, but drivers are not found.  Yes, I have installed drivers from Synaptic.

Your scanner (should) work with the Brother instructions, although I cannot get it to work now either.  Scanner not seen.

I guess we both need help and maybe some luck.  I am many hours and 2 fresh installs of 11.04 trying to get the MFC-440CN to work.  FRUSTRATED!!!!!

---

### Post by walt.smith1960 on 2011-05-09
Do you have drivers from Synaptic and drivers from Brother both? If so, I wonder if you're having some sort of conflict. I've installed Brother MFC-6490CW drivers in 11.04 both 32 bit and 64 bit with no issues.

---

