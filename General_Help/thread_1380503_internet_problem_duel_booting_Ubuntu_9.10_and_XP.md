---
title: "internet problem duel booting Ubuntu 9.10 and XP"
date: 2010-01-13
forum: General Help
---

### Post by Trumpet19019 on 2010-01-13
I recently duel booted ubuntu and xp. Ubuntu works great and the internet works fine, but when I boot up xp it won't find an internet connection, and will only give me the option of using dial-up. Does anyone know what may be wrong with XP?

---

### Post by jm8254og on 2010-01-13
What do you get when you do an ipconfig under XP?  under Run type cmd then type ipconfig in the command prompt.  Do you get an IP?

---

### Post by Trumpet19019 on 2010-01-13
no i don't get an ip but i get one on ubuntu.

---

### Post by jm8254og on 2010-01-13
Try typing "ipconfig /renew" on the XP box and see what it says.  

I don't know if its the dualboot causing the issue rather something else.  When you say dual boot did you use Wubi installer or did you resize your partition and install Ubuntu beside XP?

---

### Post by tuan_b918 on 2010-01-13
Have you checked if the driver is there or not?

---

### Post by Trumpet19019 on 2010-01-14
how do i determine whether or not the computer has the right driver?

---

### Post by maxbarjr on 2010-01-14
Hi.  Right Click on My Computer and select Manage.  On the Computer Management dialogue box, click on Device Manager.  On the right Pane, find Network adapters.  Click on the + sign to expand it.  You should see your NIC under the Network adapters and there should be no yellow markings like question mark or exclamation point.  That means your NIC was recognized by XP.

Hope that helps.

---

### Post by Sef on 2010-01-14
Have yoiu checked your network to make sure it is set up for broadband?

---

### Post by Goveynetcom on 2010-01-14
I would check if the drivers are installed, then even if they are, reinstall them then check again. I have solved countless problems by just reinstalling something. Report back when you get any new info.

---

### Post by slooksterpsv on 2010-01-14
1. Yes Check to see if the driver is in Device Manager
1a It is: see if it's disabled in Device Manager (see 2)
1b It is NOT: Try add new hardware and see if it detects it. 

2. If its in device Manager see if it's enabled
2a It is enabled - check Network connections (see 3)
2b It is disabled - enable it

3. Is it in Network Connections in Control Panel
3a. Yes - is it disabled? See 4
3b. No - try removing the drive in device manager, reboot, then re add it.

4. Disabled in Network connections?
4a Reenable it
4b If enabled run the following command in command prompt

[PHP]
ipconfig /flushdns
ipconfig /release
netsh int ip reset reset.txt
netsh winsock reset catalog
[/PHP]

Restart computer, check connectivity. Does it work? Check manufactures website for Drivers, BIOS update, etc.

---

