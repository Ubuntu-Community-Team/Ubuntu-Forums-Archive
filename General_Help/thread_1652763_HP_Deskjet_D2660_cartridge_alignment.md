---
title: "HP Deskjet D2660 cartridge alignment"
date: 2010-12-25
forum: General Help
---

### Post by elsenator on 2010-12-25
OS: Ubuntu 10.10

I've been trying to get my HP DeskJet D2660 printer to work for a while now, but I am having several problems that I can't seem to get around.

For the driver I have 2 options. The hpijs (hplip) or the hpcups driver. Neither of them work properly.

The HPLIP driver and control software keeps telling me that the stuff I print has printed correctly, but my printer does nothing. It just sits there laughing at me whilst I get popups on my monitor telling me that the print job start and completes.
I have successfully printed the print head calibration paper and aligned them as told by the HP software, but after I have done so, it just goes back to sleep. Nothing prints, not even the test page. I can't understand why it prints the calibration sheet just fine and then, afterwards, it won't print anything else but tells me everything prints fine.

The HPCUPS driver works just fine, but it has these really bad shadows on everything I print caused by incorrect alignment of the print heads. There seems to be no option of correcting this using the HPCUPS driver.

So, what I have is a HPLIP driver which allows me to calibrate but won't print, and a HPCUPS driver which prints just fine, but won't allow me to calibrate.

Any input on this problem will be greatly appreciated.

My HPLIP driver version: 3.10.6 (official from Ubuntu)
I've also tried downloading and installing the latest (3.10.9), but with no luck. Prints calibration just fine, then nothing else.

---

### Post by elsenator on 2010-12-25
I've now tried manually installing all versions of HPLIP all the way down to 3.9.12.

It seems that this error is in fact a bug in the hplip 3.10.x printing software/drivers since 3.9.12 actually works. The **huge** letdown is that 3.9.x won't use the black cartridge *at all*. So all blacks gets printed in this mushy brown. So, not really a solution for me.

Anyways, I guess there ain't much to do about this other than wait for HPLIP to fix it. I will see if I can file a bug report on it, but at the moment their official website is down.

Lastly, I am still very much interested in any input you guys might have on this issue.

---

