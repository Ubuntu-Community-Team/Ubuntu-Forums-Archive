---
title: "Login Screen Resolution Too Big"
date: 2012-04-29
forum: General Help
---

### Post by No1StoppedMe on 2012-04-29
Can someone point me in the right direction here. Of course I'm new to Ubuntu but I haven't been able to find a straight answer to this question.

How do you change the resolution of your login screen?

nVidia X Server settings and the display settings allow me to change the resolution of my screen once logged into Ubuntu however they do not adjust the display on the login screen that appears after GRUB. 
I'm using a 32" Sharp Aquos TV as my monitor and because it's only a 2nd gen of the Aquos's it doesn't have built in screen resolutions adjustment settings on the TV itself so I'm stuck trying to find a solution within Ubuntu. This is a small problem but it's driving me nuts not being able to solve it. I've tried Ubuntu Tweak but it doesn't allow me to adjust the resolution of the long in screen. 

Any help would be appreciated. Thanks.

---

### Post by pqwoerituytrueiwoq on 2012-04-29
for 720p try 1366x768
for 1080p try 1920x1080

i suggest you set it using nvidia settings and save to config file

if you need to edit the size manually
open /etc/X11/xorg.conf it will be near the end

---

### Post by No1StoppedMe on 2012-04-29
> **pqwoerituytrueiwoq said:**
> for 720p try 1366x768
for 1080p try 1920x1080

i suggest you set it using nvidia settings and save to config file

if you need to edit the size manually
open /etc/X11/xorg.conf it will be near the end

Jesus! I had it set to 1280x720. Problem solved. Wow. 3 months of frustration solved. Thanks. Who knew that making the resolution bigger would solve me problem. lol

---

