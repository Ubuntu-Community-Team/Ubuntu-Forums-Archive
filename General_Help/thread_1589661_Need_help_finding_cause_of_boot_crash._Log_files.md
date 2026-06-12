---
title: "Need help finding cause of boot crash. Log files??"
date: 2010-10-06
forum: General Help
---

### Post by defenestratos on 2010-10-06
Hello,
I was wondering whether there was any way to find out why my netbook is crashing occasionally when I boot. I am running Ubuntu 10.04 i686 edition with no other OSs installed. 
It gets sort of two thirds through the boot and then just sits there as if it is waiting for something with a black screen (No splash either).
Usually boot is very fast. It just completely fails sometimes.
Which log file should I look at to identify where my machine trips up? I really want to fix it because it is the LAST problem on an otherwise rock solid system!!
Thanks,

---

### Post by Quackers on 2010-10-06
You could try /var/log/boot

---

### Post by defenestratos on 2010-10-07
/var/log/boot yields 'Nothing has been logged yet.'
I guess that I should wait until the fault appears again and then check this log file. Do you have any other tips?
Thanks!

---

### Post by Quackers on 2010-10-07
Did you have a look at other files in there? var/log/kern.log, kern.log.1, last.log, messages, messages.1, syslog, user.log, xorg.log. Have a look at these after a slow boot event.

---

### Post by defenestratos on 2010-10-19
i couldn't really find anything outstanding but then it is all greek to me really. I have attached the logs as a tar.gz if anyone felt like looking through it. It is most frustrating to have to restart three times before I get into my system :(

---

