---
title: "System time changes"
date: 2010-11-10
forum: General Help
---

### Post by drkarasheed on 2010-11-10
[FONT=Tahoma][SIZE=3][COLOR=Blue]I have 3 hard disks on my PC
I have Windows 7, Windows XP, and Ubuntu10.10 on each one of them.
On being with Ubuntu, and decides to shift to one of the Windows versions, by changing the First hard disk boot priority, the system time time simply changes by 12 hours when  Windows is booted.
I have to manually correct this time change on Windows. I have tried my best to see this not happening on the Ubuntu settings. But all settings seem to be correct. Please advise[/COLOR][/SIZE][/FONT]
[email]drkarasheed@gmail.com[/email]

---

### Post by sohlinux on 2010-11-10
> **drkarasheed said:**
> [FONT=Tahoma][SIZE=3][COLOR=Blue]I have 3 hard disks on my PC
I have Windows 7, Windows XP, and Ubuntu10.10 on each one of them.
On being with Ubuntu, and decides to shift to one of the Windows versions, by changing the First hard disk boot priority, the system time time simply changes by 12 hours when  Windows is booted.
I have to manually correct this time change on Windows. I have tried my best to see this not happening on the Ubuntu settings. But all settings seem to be correct. Please advise[/COLOR][/SIZE][/FONT]
[email]drkarasheed@gmail.com[/email]

[SIZE="4"]I had a similar issue some time ago which I never figured out so I installed [dimension4]("http://www.thinkman.com/dimension4/download.htm") which automatically corrects the time over tcp, its freeware[/SIZE]

---

### Post by DeMus on 2010-11-10
If the 12 hours difference is the difference in time you have between local time and GMT then it is easy to explain.
Probably in Ubuntu you use GMT and a location so the system can calculate your local time. In Windows you probably use only local time. The problem is the BIOS of your computer. You have only one BIOS and therefore only one system time.
Either change the time in Ubuntu from GMT to local (or vice versa) or do this in Windows. This makes the computer use the same time in both OS'es.

---

### Post by Mark Phelps on 2010-11-10
Not picking on Ubuntu ... but if the time is wrong when you boot INTO Windows, after being in Ubuntu, then Ubuntu is changing the clock, not Windows.

This is probably because Ubuntu is set to use UTC by default.

To turn that off, do the following in Ubuntu:
1) Open a terminal
2) Enter the command "gksudo gedit /etc/default/rcS"
3) Find the line that has the UTC variable
4) Change the value from yes to no
5) Save the file
6) Reboot

---

