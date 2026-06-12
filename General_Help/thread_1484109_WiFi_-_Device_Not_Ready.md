---
title: "WiFi - Device Not Ready"
date: 2010-05-15
forum: General Help
---

### Post by Bradj47 on 2010-05-15
I just got an ASUS EEE PC and installed Ubuntu Lucid Netbook Remix. But now I can't get the WiFi to work. When I click on the networking icon in the top left corner it shows that I'm connected to the wired network **auto eth0**. But underneath that where it says **Wireless Netwokrs** it says **wireless is disabled**. Then when I enable it using **Fn+F2** it either says **disconnected** or **device not ready**. I know there should be a list of wireless networks there. When Windows 7 was installed on this thing it could see my neighbor's networks and everything. Why can't Ubuntu? Do I need a driver or something?

---

### Post by Bradj47 on 2010-05-15
bump

---

### Post by harrismc on 2010-05-30
Hi, I'm having the same issue with the asus eeepc 1005HA (royal blue model).

The issue started when I had Karmic Koala but it was more sporadic. After upgrading to Lucid, the problem has only gotten worse. 

To get it to work now, I have to boot to windows XP, turn the wifi radio on and off using the keyboard shortcut, then connect to the wifi network, then restart into ubuntu and turn the wifi on and off with the keyboard shortcut, and then sometimes it works. If that doesn't work, I try to turn the wifi on and off again using keyboard shortcut, the eeepc tray, and restart /etc/init.d/networking. Sometimes this works.

I have tried installing wicd and madwifi-ng but this hasn't affected the problem.

Does anyone have any other ideas or suggestions?

Edit:
Created a Launchpad bug here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/587498](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/587498)

---

