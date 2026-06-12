---
title: "photoprint broken on 12.04?"
date: 2012-06-25
forum: General Help
---

### Post by korben88 on 2012-06-25
I do concealed firearms permits, and was using photoprint to print off passport sized photos. I lliked it because I could just highlight all the students pics from the day, and it would print them 4 to a 4x6 photo page.

I upgraded to precise, and now photoprint will not open. does anyone know when this will be fixed? or alternatively another efficient way to do multiple passport photos?


Thank you,
Troy

---

### Post by raja.genupula on 2012-06-25
actually an application launching problems can be found  by launching it from the terminal . so try to open it from terminal .

like ```
<app_name> 
```so we can find out what are the errors causing the issue , :)

---

### Post by prshah on 2012-06-25
> **korben88 said:**
> I upgraded to precise, and now photoprint will not open. does anyone know when this will be fixed? 

This problem occurs because photoprint is "hard-linked" (hard coded) to use libgutenprint 2, whereas Precise carries ver 3.

You can easily fix this by using the command```
sudo ln -s /usr/lib/x86_64-linux-gnu/libgutenprint.so.3 /usr/lib/x86_64-linux-gnu/libgutenprint.so.2
```

(This is for 64-bit, replace with suitable path changes for 32 bit).

This creates a link (file) named libgutenprint.so.2 that simply links to the existing libgutenprint.so.3


Please post back here with results / problems.

> **raja.genupula said:**
> 
like ```
gksu <app_name> 
```

Photoprint does not require root permissions. Please stop blindly advising people to run programs as root / superuser.


Regards,

---

### Post by korben88 on 2012-06-26
Thank you prshah. That worked great. Photoprint opened  but it didn't want to [RIGHT][/RIGHT]print. I had to go to work, and didnt have time to mess with it though. If I can't get it i'll post a new thread.

---

### Post by prshah on 2012-06-26
> **korben88 said:**
> Thank you prshah. That worked great. Photoprint opened  but it didn't want to [RIGHT][/RIGHT]print. I had to go to work, and didnt have time to mess with it though. If I can't get it i'll post a new thread.

Photoprint opens and prints after I have made the above change (and only this change) on my system.

Is your printer an Epson? I had to re-install the printer after upgrade to 12.04 from 11.10. Can you check if anything else prints?

---

### Post by korben88 on 2012-06-26
The printer is an HP, I can print from libreoffice, and txt files. But when I try to print from photoprint the print cue comes up and say processing for a minute then switches to held.

I've let it sit in that state for 20 or so minutes with no change.

---

### Post by davidvandoren on 2012-06-26
Open Photoprint

Go to print setup 

Output 
Print queue: select your model
Printer Model: select Adobe and PostScrips level 2

This should work but with less options though.

---

### Post by korben88 on 2012-06-27
David, those were the setting already..
 I finally had a chance to play around with it, and If print with any of the shortcut settings it will print just fine, but when  I switch to custom and set the paper size to 4x6, thats when it will not print

---

### Post by prshah on 2012-06-27
> **korben88 said:**
> switch to custom and set the paper size to 4x6, thats when it will not print

Do you have any "tray" options (may also be called feed)? You can check the cups configuration page ( [http://localhost:631](http://localhost:631) ). This will also show you reasons why your job is "held".

---

### Post by korben88 on 2012-06-28
Iirc there are 2 tray options. I don't remember the names, but can check when I get home.

---

