---
title: "Installing HASP HL key on 10.04"
date: 2011-02-14
forum: General Help
---

### Post by Azon on 2011-02-14
Ok so I am trying to see if I could get this working on 10.04. I have tried using Wine for my Windows application and all I need to do is get .Net framework and runtime working, I have tried the latest firmware for the key, I have also tried mono for framework but I cannot get that working. 

Any tips?

---

### Post by An Sanct on 2011-02-14
In my experience Hasp hardware keys are a nuisance. Even under windows, they need kernel drivers, so making it run under WINE would be a little miracle (IMHO).

You can try to make HASP use Linux drivers, Ubuntu version is listed here in the official page [http://www3.safenet-inc.com/support/hasp/enduser.aspx](http://www3.safenet-inc.com/support/hasp/enduser.aspx)
thus making the software run under WINE and hasp under the control of Ubuntu. That should work normally.

PS. To make HASP clear, its a USB keygen/calculator, that responds to random input with software predicted output, checked via hardware results, if they match, the license is okay. So software under Wine should invoke hasp and get the answer (maybe some dll tweaking will be needed)

ps2 ... [http://kb.x-formation.com/questions/197/How+do+I+use+a+HASP+dongle+with+an+Ubuntu+operating+system%3F](http://kb.x-formation.com/questions/197/How+do+I+use+a+HASP+dongle+with+an+Ubuntu+operating+system%3F)

---

