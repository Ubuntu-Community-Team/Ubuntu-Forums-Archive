---
title: "USB microphone is not automatically used, despite sound preference setting"
date: 2010-01-25
forum: General Help
---

### Post by andersja on 2010-01-25
Hi all, I have an unusual problem you might be able to help with. 

I am supporting a user who has a USB microphone plugged in to a PCMCIA USB card in her laptop. 

At install time, I set it up (System -> Preferences -> Sound) to be used as the default input device and it worked fine every time the PC rebooted. 

As of about a week ago (some new security update auto installed?), the microphone is no longer set to default inpud device at boot and the user has to go to System -> Preferences -> Sound and select the device as input at every reboot. 

Can anyone help?

System info: HP nx6110 laptop running Ubuntu 9.10 (Karmic). USB mic is a generic device (fully recognized in Ubuntu, the problem is about whether it's working, just about its recognition as default input device at boot time)

---

### Post by andersja on 2010-01-26
Update: after a couple of boots of "forgetting" that it is/was the primary sound input, it has now been picked up at boot a couple of times. Bizarre? Race condition somewhere?

---

### Post by KayakJim on 2010-01-26
I have run into this on my 9.04 Jaunty 64-bit desktop running on my laptop.

I have found that opening a terminal and running alsamixer and then selecting the proper mic to be the default generally resolves the issue. 

I still need to do this every couple of weeks for some reason but at least it is an easy fix.

---

### Post by andersja on 2010-02-02
> **KayakJim said:**
> I still need to do this every couple of weeks for some reason but at least it is an easy fix.
Thanks for confirming I'm not the only one, KayakJim. Because the user I am supporting is remote I can't easily run the bug reporting wizard: would you mind raising a bug next time it happens to you? Feel free to reference this forum URL as "proof" it happens to more people than yourself... 

[https://help.ubuntu.com/community/ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")

---

