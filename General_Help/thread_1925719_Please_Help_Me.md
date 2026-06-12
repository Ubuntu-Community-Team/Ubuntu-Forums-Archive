---
title: "Please Help Me"
date: 2012-02-15
forum: General Help
---

### Post by thisisme2 on 2012-02-15
Alright, so im new to Ubuntu, and i just downloaded the latest version from the homepage. I am running Ubuntu from Windows 7. When i get into Ubuntu it wont let me click on wireless networks when i click on the signal button. There is also a notification popping up telling me to intall the driver called "Broadcom STA wireless driver" BUT whenever i click install driver, it gives me an error message. Like i said im new to Ubuntu but THIS IS COMPLICATED.... can someone please give me a suggestion or something?

Thanks

---

### Post by mikewhatever on 2012-02-15
You need to connect an ethernet cable, then, when you click to install the driver, it will get downloaded and installed.

If you get error messages, post them!

---

### Post by wildmanne39 on 2012-02-15
Hi, to install the driver from additional drivers you need to be connected to the internet with a hard wire or other means, if you have a connection then please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by thisisme2 on 2012-02-15
> **mikewhatever said:**
> You need to connect an ethernet cable, then, when you click to install the driver, it will get downloaded and installed.

If you get error messages, post them!
i dont have an ethernet cable =s *facepalm*... ill post what the message says in a lil while

---

