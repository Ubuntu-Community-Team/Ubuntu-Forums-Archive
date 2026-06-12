---
title: "system info"
date: 2010-12-02
forum: General Help
---

### Post by mmsmc on 2010-12-02
how do you check your system information, such as available memory

---

### Post by I'mGeorge on 2010-12-02
you install some applications that does that for you like conky or some dockable apps. If you want something that could be executed in your terminal than hwinfo it's the one for you.

---

### Post by flipper T on 2010-12-02
system/administration/system monitor is a start

---

### Post by robert shearer on 2010-12-02
In a terminal...  (applications>accessories>terminal) and type...
```
top
```

---

### Post by czr114 on 2010-12-02
It depends whether you're looking to check once or check ongoing:

CLI: top
GUI: gnome-system-monitor
GUI Monitor Applet: Right click panel, add to panel, system monitor

---

### Post by Habitual on 2010-12-02
lshw

---

### Post by oldfred on 2010-12-02
If you want a HTML file:

HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

sudo dmidecode >bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

---

