---
title: "Ubuntu freezes after several minutes of use"
date: 2010-08-02
forum: General Help
---

### Post by ravenhawk82 on 2010-08-02
Hello! I am a new ubuntu user, and have just installed ubuntu on my second laptop. However, this one is giving me some grief. After several minutes, it completely locks up. No mouse, keyboard, anything. Just frozen solid. I had some issues installing it, and got around them by checking something like "nolacpi" and "noacpi" with the live cd, but now I don't know how to re enable those options. I'm fairly new at this, so simplistic speaking helps. I'm quite computer savvy, but am still learning how linux works. Thanks in advance!

For refrence, this is the system specs:
HP Pavilion Zx5000
Pentium 4 3.06GHz
ATI Mobility Radeon 9200 GPU
1GB RAM
60GB IDE Hard drive

---

### Post by Maverick_Meerkat on 2010-08-02
Greetings,

ACPI seems to be a real problem for us laptop users! It seems that your Power Management settings may be causing the lock up. That was an issue for lots of laptop users. Suspend and hibernate seems to lock the system up. This seems to be a bug. Only solution I have found it to not use suspend or hibernate features. Additionally, the screensaver settings may or may not contribute to the problem.

1. On the desktop drop down menu navigate System>Preferences>Power Management

Adjust settings from there.

2. In the terminal/CLI
```
sudo apt-get install sysv-rc-conf

sudo sysv-rc-conf
```

Make certain that in the row "acpi-supp$" columns 2,3,4,5 have an X under them and all others are blank.

Make certain that in the row "acpid" all columns are blank.

3. In the desktop drop down menu navigate System>Preferences>Startup Applications

Make certain that Power Management checkbox IS selected.

BTW additional Power Settings are available thru Ubuntu Tweak. Get it here: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/) 

Hope this helps you out!

---

### Post by ravenhawk82 on 2010-08-02
In order to better see what was going on, I booted the live CD again, and found that I had used "noapic" and "nolapic", not acpi like I thought. Oops... any idea how to get those?

---

### Post by Maverick_Meerkat on 2010-08-02
> **ravenhawk82 said:**
> In order to better see what was going on, I booted the live CD again, and found that I had used "noapic" and "nolapic", not acpi like I thought. Oops... any idea how to get those?

[http://wiki.linuxquestions.org/wiki/APIC](http://wiki.linuxquestions.org/wiki/APIC)

So I assume using gedit to configure /etc/default/grub 

to

apic=on

and

lapic=on

Then in terminal/CLI

sudo update-grub

Maybe reboot to be safe

Will solve the problem.

---

