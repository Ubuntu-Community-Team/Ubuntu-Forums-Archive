---
title: "Scanner isn't working"
date: 2011-12-04
forum: General Help
---

### Post by mindrifter on 2011-12-04
Hello, I've encountered something weird with my scanner. I don't know if the software somehow got corrupted or anything like that, but my scanner isn't working any more. I use simple scan, and when I try to scan something, the waiting circle thing comes up for a couple minutes then it displays this message ```
[SIZE="4"]**Failed to scan**[/SIZE]

[SIZE="3"]Unable to start scan[/SIZE]
``` I tried switching usb ports to see if the port was faulty and that didn't help. I also tried using it on another family member's laptop that runs windows 7 and it worked. Can anyone please tell me what's wrong and how to fix it? Thankyou.

---

### Post by mindrifter on 2011-12-04
* Update

I reinstalled the simple scan package, some SANE packages and some hp clients, and it's still doing the same thing.

---

### Post by oldtimer7777 on 2011-12-04
> **mindrifter said:**
> * Update

I reinstalled the simple scan package, some SANE packages and some hp clients, and it's still doing the same thing.

Well try to figure out what made it stop working... 

Did you run an update or upgrade anything since the last time you remember it working? 

Have you made any changes to your system that might have caused this to happen?  Did you installing anything new?  Did you upgrade your entire system from an older version?

---

### Post by mindrifter on 2011-12-05
The computer was just being used as it normally is and it stopped working. I don't think anything happened to trigger a malfunction. I updated the computer after it wasn't working to see if that would fix it, but it didn't. I'd try running it in the terminal but I'm still a little new to linux and I don't know how to tell it to scan through the terminal.

---

### Post by SteveDee on 2011-12-06
> **mindrifter said:**
> ...I'd try running it in the terminal but I'm still a little new to linux and I don't know how to tell it to scan through the terminal....

Assuming you are running Lubuntu, for any application that would normally run via a menu, just find the menu entry and right-click on the application. The Properties option will show you the application command you need.

For Simple Scan type in a terminal:-
```

simple-scan

```
...and remember, all commands are case sensitive.

---

