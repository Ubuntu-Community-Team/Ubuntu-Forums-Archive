---
title: "crash on shutdown"
date: 2012-02-19
forum: General Help
---

### Post by AUTOgod on 2012-02-19
hi guys.

i am desperately trying to get into linux, but it seems to be fighting me every step of the way.

im starting by trying to setup an unattended server and have managed to get wake-on-lan, samba, media sharing with minidlna, and vnc working, but just last night, after rtying to get vsftpd working (via a webmin module that refuses to show), i decided to shut down the system, only to find this morning, that it hasnt really shutdown.

it has instead frozen on the xubuntu splash screen, with the load bar stuck, and absolutely nothing happening.

this has happened before, and i switched to a different distro, but that gave me other issues. i would like to stay with ubuntu variants if possible.

any help will be much appreciated.

system info:
xubuntu 11.10
asus k8v
amd athlon 64 3400+ 2.2ghz
1.5GB ddr ram
geforce 4 mx4400
sda: toshiba 200GB SATA hdd
sdb: seagate 40GB SATA hdd

---

### Post by 2F4U on 2012-02-19
Did you look into the system log files? If it happened before and if you had problems with other distros, it may be a hardware issue. Do you recognize problems while the machine runs or just when it shuts down? Did you run a memtest program?

---

### Post by AUTOgod on 2012-02-19
> **2F4U said:**
> Did you look into the system log files? If it happened before and if you had problems with other distros, it may be a hardware issue. Do you recognize problems while the machine runs or just when it shuts down? Did you run a memtest program?

this problem doesnt happen with any other distro, and it works perfectly when its started and running. it starts perfectly and can run for days without issue.

it hasnt ever had any memory issues.

the log doesnt seem to have anything bad in it.

---

### Post by mardybear on 2012-02-19
Hi AUTOgod.

I have more of a workaround than a solution. My system used to hang when attempting to shutdown while logged in. I didn't want to spend days trying to figure it out so for me the solution was simply to logout first and then select shutdown from the login screen - powers down every time without fail.

This might be a hardware specific issue related to your desktop environment. I never did try take the time to try shutting down from different desktops - gnome vs kde vs xfce vs openbox.

Good luck,

mardybear

---

### Post by AUTOgod on 2012-02-26
> **mardybear said:**
> Hi AUTOgod.

I have more of a workaround than a solution. My system used to hang when attempting to shutdown while logged in. I didn't want to spend days trying to figure it out so for me the solution was simply to logout first and then select shutdown from the login screen - powers down every time without fail.

This might be a hardware specific issue related to your desktop environment. I never did try take the time to try shutting down from different desktops - gnome vs kde vs xfce vs openbox.

Good luck,

mardybear

well, that doesnt work, and also wouldnt be practical for a remote server.

also, using different hardware hasnt made any difference.

using a different desktop manager hasnt helped either (lxde)

---

