---
title: "Does Virtual box (windows) use Linux or Windows hardware drivers?"
date: 2010-08-20
forum: General Help
---

### Post by Nick_Jinn on 2010-08-20
So.....I am assuming that if you are connected to the internet in Linux you will be using the LINUX drivers for your wireless card, not the windows drivers for wireless, correct?

What about audio drivers? When does virtual box use Linux hardware drivers and when does it require that you install the drivers to your virtual box windows?

---

### Post by mike555 on 2010-08-20
If your running in VB then your using the host systems drivers (adapted by VB)

---

### Post by Ginsu543 on 2010-08-20
Your "wireless card," "audio", "video," etc. inside VirtualBox are all software emulations sitting between the Windows guest OS and the LInux host OS. So technically you are using the Linux host drivers but VirtualBox is "translating" them so your Windows guest thinks it's seeing the hardware.

---

### Post by Nick_Jinn on 2010-08-21
So I dont actually need to install the audio or wireless card drivers in the virtual OS as long as its working in Linux?

---

### Post by TNT1 on 2010-08-21
> **Nick_Jinn said:**
> So I dont actually need to install the audio or wireless card drivers in the virtual OS as long as its working in Linux?

Correct.

---

### Post by Nick_Jinn on 2010-08-21
You people are awesome. Thank you for being here to answer my never ending stream of questions at all hours of the day or night.

---

