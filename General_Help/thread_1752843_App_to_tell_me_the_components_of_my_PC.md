---
title: "App to tell me the components of my PC"
date: 2011-05-08
forum: General Help
---

### Post by maghoxfr on 2011-05-08
Hi, I'm going to an extremely lazy day, so looking through all my drawers to find the manuals of my PC is not an option. I would like to know if there's an app that told me what's inside my computer. I know some of the parts, but others like the MB I can't remember the exact model. I know there's lots and lots of dust as well :P.

I think ubuntu comes with one app like that preistalled but I should have deleted it because I just can't find it.

Thank you very much

---

### Post by oldfred on 2011-05-08
These will list a lot of details:

To save it as a file use
sudo lshw > hw.txt

HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

udevadm info --export-db > file.txt
Similarly, if you run
sudo dmidecode > bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

---

### Post by ~Plue on 2011-05-08
/Edited out

---

### Post by maghoxfr on 2011-05-08
> **oldfred said:**
> These will list a lot of details:

To save it as a file use
sudo lshw > hw.txt

HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html

udevadm info --export-db > file.txt
Similarly, if you run
sudo dmidecode > bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.
 I must be doing something wrong because the last two commands didn't return anything. But this one 

```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.htm
```
did, and it was waht I was looking for. Thank you very much. If there's a GUI version I would love it. If not I'm cool because I got wht I needed.

Thanks again!

---

### Post by ~Plue on 2011-05-08
Might as well try to post something useful this time..

> **maghoxfr said:**
> If there's a GUI version I would love it. If not I'm cool because I got wht I needed.

Search the software center for "hardinfo". Once installed, you can access it from the applications >> system tools

Hope that helps

---

### Post by oldos2er on 2011-05-08
> **maghoxfr said:**
>  If there's a GUI version I would love it. If not

**lshw-gtk**

---

### Post by yetiman64 on 2011-05-08
> **maghoxfr said:**
> I must be doing something wrong because the last two commands didn't return anything.....
Look in your users home folder for bios.txt and file.txt. The commands given will have created the 2 files there but it won't be apparent from the terminal output.

---

