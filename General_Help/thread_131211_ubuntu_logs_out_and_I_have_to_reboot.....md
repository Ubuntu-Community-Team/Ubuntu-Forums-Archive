---
title: "ubuntu logs out and I have to reboot...."
date: 2006-02-16
forum: General Help
---

### Post by ttallos on 2006-02-16
ubuntu logs out and I have to reboot to get back into the system. This is mildly annoying. I looked in the system logs and they said something about  gconfd not reading or somthing. I could not log back in and had to reboot two or three times now. This is not a cronic problem but happens once or twice a day. I have a RAID 5 array with 160GB HDD the array is 320GB the array is clean. Hope this is fixable??

---

### Post by eylisian on 2006-02-16
can you get that parting shot error message? the one about gconf complaining about something...

---

### Post by ttallos on 2006-02-16
Here I have enclosed a screenshot. Hope it helps it is the user log file. A little history. I built this machine new. Rebooting always seems to cure it so far. Last night when it crashed at 11:45pm I was playing sirtet all of the sudden the screen went blank and then I was at the login screen and when I tried to log in again it just went to the brown screen and froze but I could move the mouse. After a minute or two I just rebooted. Thanks for any input you can give.

---

### Post by eylisian on 2006-02-16
hmmmm. when the freeze happens could you switch to console 1 ( ctrl + alt + F1 ) and login as the default user (or the username w/ issues) issue;
```
xinit -- :1
```
This should start another xsession with a small shell emulator, issue;
```
`which gnome session`
```
See if you get any errors spit back at you, if there are any post them.

---

### Post by ttallos on 2006-02-16
Aahhhh you seem to be a rocket scientist. I just want to be a rocket scientist. This problem only has happened 3 times in the last few days. I will do that trick you told me and repost the next time it happens. This morning it booted and is running just fine. I am going to run this machine all day every day just to try to stress it. Thanks for the additional troubleshooting tips. I really appriecate your help as I am new to ubuntu.

---

