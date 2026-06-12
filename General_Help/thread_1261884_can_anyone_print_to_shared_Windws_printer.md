---
title: "can anyone print to shared Windws printer?"
date: 2009-09-09
forum: General Help
---

### Post by rick71 on 2009-09-09
Is anyone able to print from a 9.04 machine to a USB ink-jet printer that is shared from a Windows XP machine?

I have not been able to get this to work in either 8.10 or 9.04.

Any info and/or help appreciated.

---

### Post by Claus7 on 2009-09-09
Hello, 

try this out:
[http://ubuntuforums.org/showthread.php?t=600670&highlight=print](http://ubuntuforums.org/showthread.php?t=600670&highlight=print)
It is a little bit old, yet it might help you.

Regards!

---

### Post by rick71 on 2009-09-09
Thanks for the reply... I have tried that before... no joy.

---

### Post by NoaHall on 2009-09-09
Yes I have. It works fine. If you can't see it, make sure it's shared.

---

### Post by rick71 on 2009-09-09
> **NoaHall said:**
> Yes I have. It works fine. If you can't see it, make sure it's shared.

It is shared. I can print to it from another XP machine. I can ping it. The machine shows up in smb://domain, but I can't connect to it. I keep getting the username/domain/password dialog whether I use a name or an IP.

---

### Post by rick71 on 2009-09-09
I added the printer using CUPS. I sued smb://10.166.195.55/HP9650 (smb://ip/printer name). I get "Connection failed: NT_STATUS_ACCESS_DENIED" from CUPS.

---

### Post by Claus7 on 2009-09-09
Hello,

there have ages since the last time I did that configuration. I saw the last post and comparing it with my old thread I see that you give 2 instead of 3 arguments. I think that you miss the name of the workgroup. Even if this is wrong, you do not loose too much and give it a try.

Regards!

---

### Post by rick71 on 2009-09-09
When I include the workdroup, I don't get as far in the process.

I created a share on that particular computer. I can't get to the share from my Ubuntu box, but I can from an XP box.

Tomorrow, I am going to try to ccreate shares on other Xp machines and see if I can get to them from the Ubunut box. If I can, I'll try sharing the printer from there.

---

