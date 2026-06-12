---
title: "ATI graphics driver help"
date: 2009-11-14
forum: General Help
---

### Post by sr.vinay on 2009-11-14
Here's the thing:
I've got Karmic Koala. I downloaded the latest ATI driver for my graphics card. I activated the graphics driver(proprietary) in the "ubuntu" way, which is to go to hardware drivers and then activate it from there. My desktop started running really, really slow! Do I need to do something other than the above mentioned process to run my gfx card properly?
Because, it's really annoying when KUbuntu does what Windows should do(crash).
And by the way, when I tried restoring the graphic settings to previous settings (The Xorg.conf file) I got a totally blurred screen!

---

### Post by undecim on 2009-11-14
What kind of graphics card do you have? Go to a terminal and type "lspci| grep VGA" and post the result

---

### Post by sr.vinay on 2009-11-15
I've got an ATI HD 4350 ( It also said 1:00.0 VGA compatible RV710 ATI Technologies)

---

### Post by Mark Phelps on 2009-11-15
The best source of detailed info on ATI driver issues is the Phoronix forums -- suggest you go there for the details.

But, from what I read recently, the new ATI restricted drivers are encountering all kinds of problems in Ubuntu 9.10, especially the ATI catalyst 9.10 drivers.  Rumours are that the Catalyst 9.11 beta drivers work a lot better -- but they're not out yet.

In the interim, to get a useful display back, you could remove the ATI drivers and replace them with the open source drivers using the instructions in the link below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

