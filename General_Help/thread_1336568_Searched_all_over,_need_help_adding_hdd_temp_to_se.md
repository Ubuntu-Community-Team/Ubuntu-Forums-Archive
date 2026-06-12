---
title: "Searched all over, need help adding hdd temp to sensors-applet"
date: 2009-11-24
forum: General Help
---

### Post by dixie460 on 2009-11-24
Well, I tried everything that i could think of an searched for help too, but I just can't get sensors-applet to see the hard drive temp sensor on my Dell Inspiron 1545 laptop. I installed hddtemp, and when I go to the command line and sudo hddtemp /dev/sda it reports my harddrive temp just fine. When I open the Preferences section of sensors-applet and go to the Sensors tab, there's the acpi tree which when expanded shows THM which apparently is my CPU) and there's the libsensors tree which when expanded shows temp1, Core0, and Core1. How can I get it to let me add and enable my hard drive sensor?

Also, if anyone knows what temp1 might be, I would love to know. It's ain't my hard drive, I verified this my checking the drive temp from the command line and the output from that doesn't match anything reported in sensors-applet. To verify that, I put my hard drive in the freezer for a couple minutes (I know, thermal shock), put it back in, and none of the temperatures reported by sensors-applet had dropped. Checking from the command line showed that the drive was indeed 30 degrees cooler than what it had been before. Is temp1 my motherboard temp maybe?

Thanks!!

Andy

---

### Post by dcstar on 2009-11-24
> **dixie460 said:**
> Well, I tried everything that i could think of an searched for help too, but I just can't get sensors-applet to see the hard drive temp sensor on my Dell Inspiron 1545 laptop. I installed hddtemp, and when I go to the command line and sudo hddtemp /dev/sda it reports my harddrive temp just fine. When I open the Preferences section of sensors-applet and go to the Sensors tab, there's the acpi tree which when expanded shows THM which apparently is my CPU) and there's the libsensors tree which when expanded shows temp1, Core0, and Core1. How can I get it to let me add and enable my hard drive sensor?
........

```
gksudo gedit /etc/default/hddtemp
```

Make RUN_DAEMON="true", save and reboot.

---

### Post by dixie460 on 2009-11-25
Thanks, will try it when I get home today.

EDIT: It works great! Thanks for the help dcstar.

---

### Post by bludgard on 2010-12-28
> **dcstar said:**
> ```
gksudo gedit /etc/default/hddtemp
```Make RUN_DAEMON="true", save and reboot.


Worked great for me.:P

Thanks.

No rep?

+1

---

