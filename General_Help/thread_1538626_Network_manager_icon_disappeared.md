---
title: "Network manager icon disappeared"
date: 2010-07-25
forum: General Help
---

### Post by shadewalker on 2010-07-25
Hello everyone,
I am new to ubuntu Linux. I am using Ubuntu 10.04 Lucid Lynx 32 bit version alongside my Windows OS.I wanted to enable my DHCP configuration in my modem.So I did what was to be done from Windows and when I switched to Linux, I found DHCP enabled connection not working in Linux and also the network manager icon had vanished from the systray.I have now switched off DHCP and wanted to revert back to my original settings but still no network manager icon is there.
Please, can anybody help me with this?
Thanks in advance,
shadewalker.

---

### Post by AlphaLexman on 2010-07-25
Make sure NetworkManager is running:
```
ps aux | grep NetworkManager
```

---

### Post by Ocxic on 2010-07-25
hit "alt-F2" and run "nm-applet"
that will get network manager back.

---

