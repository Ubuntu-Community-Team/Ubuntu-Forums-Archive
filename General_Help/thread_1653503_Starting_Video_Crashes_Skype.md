---
title: "Starting Video Crashes Skype"
date: 2010-12-27
forum: General Help
---

### Post by djwrmp on 2010-12-27
Hi Guys,
ubuntu 10.10
skype 2.1.0.81
Logitech usb cam

Have tested video with cheese works fine
Have tested cam with chat sites seems to work.

I can skype people, text and voice call, and can watch their video but as soon as I enable my cam Skype crashes.

I have searched everywhere and see a lot of people have the same issue but can't find an answer.

Can anyone help?

Regards
DJ

---

### Post by djwrmp on 2010-12-27
bump

---

### Post by ksparks33 on 2011-02-07
Did you find a solution? I have the exact same problem.

---

### Post by botWi on 2011-02-23
bump

has anyone found a solution?

---

### Post by botWi on 2011-02-24
I finally resolved this

command xdriinfo showed that there is no video driver loaded
I started googling why my driver is not loaded and found that Intel graphic drivers were disabled in Ubuntu because of freeze bugs
I enabled driver manually and now skype works well :)

[https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus)

---

