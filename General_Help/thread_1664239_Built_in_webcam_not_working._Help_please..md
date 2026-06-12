---
title: "Built in webcam not working. Help please."
date: 2011-01-10
forum: General Help
---

### Post by Aterruit on 2011-01-10
I installed skype today and was in the middle of a web convo, and then skype crashed. Since then, my cam has not worked at all. I've tried Cheese, camorama, guvcview, and none of them are working. They all display "device not found" 

Here is my lsusb turn out:


josh@josh-T-1625:~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
josh@josh-T-1625:~$ 


Any help would be greatly appreciated

---

### Post by jonbonjovi on 2011-01-10
Did you try to restart the O.S.? Is the webcam still not recognised? Hardware problem maybe? Try with a live CD...

---

### Post by Aterruit on 2011-01-10
I will try that right now.

---

### Post by Aterruit on 2011-01-10
Ok, so I restarted my computer and this is what happenned when i opened up cheese. It opened and ran fine, (almost) this time it didnt tell me that it could not find the device, however my camera did not start. So the program ran, but didnt work. Also, when i started cheese, after it ran for a couple of seconds my networking was disabled, and i had to restart my computer again. 

This is similar to what happened to me while using skype. I was in the middle of a convo, cam was working fine, cam messes up, skype crashes, boom no networking.  What's up with that?

---

### Post by jonbonjovi on 2011-01-10
Soo weird...have you tried those softwares on a live cd? Maybe your installation got corrupted.

---

### Post by Aterruit on 2011-01-10
Anyone out there got any ideas please? I'm lost on this one.

---

### Post by Aterruit on 2011-01-10
No I havent tried from a live CD yet. I was kind of hoping for a simpler solution, like removing the drivers for the webcam entirely, and then re-installing them. But i dont know how to do that.

---

### Post by no2498 on 2011-01-11
if the computer/program crash they do not turn off the cam the right way
skype leaves a icon up top that must be off too
thats why the restart helped
most lap tops you need to push key's to turn the cam on for the first time
programs take over after that

was just pointing

---

### Post by Aterruit on 2011-01-11
How Might I do that?

---

### Post by Aterruit on 2011-01-11
I disabled video completely in skype. then I restarted the program, and it said "no video devices detected" What Next?

---

### Post by no2498 on 2011-01-12
you need to see the light of the cam before it will start
try the fn+f4 at the same time


you may try this


click system, preferences
go down the list to multimedia systems selector, start it click video
try v4l and v4l2 click the bottom test button for each 1

---

### Post by Aterruit on 2011-01-14
Can somebody please help me? This is extremely frustrating.

---

### Post by always_niggles on 2011-01-22
Hi there,
it looks like I have the same or very similar issue.
When I open Skype, it opens ok and seems to be running ok BUT, when I try to use the build-in web-cam, my wireless network connection instantly switches off and the only way I can get the network connection back is by re-starting my laptop.
I have noticed that your network card is also a Realtek one, may this be the issue?

For info:
  Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  Bus 001 Device 003: ID 04f2:b022 Chicony Electronics Co., Ltd Gateway USB 2.0 Webcam
  Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Lets hope somebody can shed some light into the issue.

Thanks

---

### Post by no2498 on 2011-01-22
[http://www.google.com/search?client=opera&rls=en&q=04f2:b022+Chicony+Electronics+Co.,+Ltd+Gateway+USB+2.0+Webcam&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest](http://www.google.com/search?client=opera&rls=en&q=04f2:b022+Chicony+Electronics+Co.,+Ltd+Gateway+USB+2.0+Webcam&sourceid=opera&ie=utf-8&oe=utf-8&channel=suggest)


always_niggles

thats for you

---

