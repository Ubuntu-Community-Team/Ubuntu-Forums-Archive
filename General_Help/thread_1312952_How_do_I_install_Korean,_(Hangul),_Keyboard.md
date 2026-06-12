---
title: "How do I install Korean, (Hangul), Keyboard"
date: 2009-11-03
forum: General Help
---

### Post by stanni2 on 2009-11-03
Hi,
I'm new to Ubuntu and am trying to install the Korean Keyboard so my wife can use the computer. 
I've installed Ubuntu 9.10 and gone on System, Amdinistration, language support and installed Korean language. Then I logged out and back in again and am not able to bring up the korean keybord. How do I go about to activate the Hangul characters?

---

### Post by jesuisbenjamin on 2009-11-03
I found some information here: [https://launchpad.net/ubuntu/+source/scim-hangul/0.3.2-1](https://launchpad.net/ubuntu/+source/scim-hangul/0.3.2-1)

Some users in this forum are from Korea and write Hangul/Hanja. Hint: [http://ubuntuforums.org/showthread.php?t=640176](http://ubuntuforums.org/showthread.php?t=640176)

---

### Post by stanni2 on 2009-11-03
OK, I've found out how it is done:

In System, administration, language support switch to IBUS. Log out and back in again and then you should see a keyboard icon on the top task bar. then:

Right click on the keyboard icon in the notification area, choose
Preferences. Click on the Input Methods tab, select the desired input
method(s) from the combobox and click Add. Sort them if necessary.
Changes take effect immediately.

[https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/464060](https://bugs.launchpad.net/ubuntu/+source/ibus/+bug/464060)

---

