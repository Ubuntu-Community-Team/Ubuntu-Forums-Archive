---
title: "No Sound in 9.10 w/ twist"
date: 2010-04-07
forum: General Help
---

### Post by SherlockTKE on 2010-04-07
Great lords of Ubuntu, I have a problem, and I pray to thee to help.
As I have seen all across my research into the problem, many people are having difficulties with the "modem driver" and sound in 9.10 (especially on Asus computers). I have already tried looking into alsa drivers and the whatnot suggested in various threads to no avail. Being as my sound was working before the driver was installed, the modem driver being a problem is logical. So I should just hit up the System>Administration>Hardware Drivers tool and remove the Modem driver, right?
Herein lies my problem. I have installed that driver in the past, I remember doing so, yet it does not appear on the list of drivers installed, therefore it cannot be removed by my limited knowledge. Is there a way around this? 

My computer is an Asus M51SN and any questions are more than welcome.

Thank You.

---

### Post by duanedesign on 2010-04-07
SherlockTKE,
[This wiki page]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats") has many of the common Karmic sound problems. It includes how to identify them and their relevant workarounds. I hope this page is useful.

best of luck,
duanedesign
-
-

---

### Post by SherlockTKE on 2010-04-11
> **duanedesign said:**
> SherlockTKE,
[This wiki page]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats") has many of the common Karmic sound problems. It includes how to identify them and their relevant workarounds. I hope this page is useful.

best of luck,
duanedesign
-
-


Thank you Duanedesign! I figured out Timidity was the source of the problem blocking pulseaudio from working. Removed Timidity from synaptic and everything is working fine! I can finally use Ubuntu for all the media I want and stop using Win7!

---

