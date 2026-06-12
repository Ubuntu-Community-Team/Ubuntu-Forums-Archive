---
title: "OpenOffice in EyeOS on Ubuntu Server"
date: 2009-10-20
forum: General Help
---

### Post by tee4cute on 2009-10-20
I'm running ubuntu server 8.04 with the lastest eyeOS (I downloaded in the morning). My problem is that I can't open .doc file in eyeOS. Firstly, eyeOS display that I've to install openoffice first. So, I installed it by following the steps provided in wiki (here : [http://wiki.eyeos.org/Setting_Up_Office_Linux]("http://wiki.eyeos.org/Setting_Up_Office_Linux")). Then I open eyeOS and .doc file in desktop. It shows me blank ~.~. I'm finding the solutions all day. Please help!!!

Steps I proceeded.

-Follow the steps in wiki

-After following the steps in wiki. I got error "cannot open X11's SecurityPolicy file". So I installed the X11 packages and this error was solved.

-Now, I've got some errors while executing xvfb.sh command :

Starting Virtual Framebuffer 'fake' X server for OpenOffice in eyeOS...

expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc

I'm not sure that this error relates to failure in opening openoffice in eyeOS.

Thanks for advance.

---

### Post by tee4cute on 2009-10-20
any idea please?

---

### Post by ubun_two on 2009-10-20
Just a thought.

What version of OpenOffice are you trying to use?  The wiki you pointed says it has to be 2.x.

---

### Post by tee4cute on 2009-10-20
Firstly, I installed openoffice 3.0. Now, I've tried openoffice 2.4.1 but nothing's better. (also blank page when opening .doc)

---

### Post by danielrs on 2009-11-23
Unfortunately eyeos requires OpenOffice 2.x :(

I think that I have seen someone with a problem similar to yours on the eyos forums (forums.eyeos.org). If you can't find the post, you can start a new topic and surely someone will help you ;)

---

