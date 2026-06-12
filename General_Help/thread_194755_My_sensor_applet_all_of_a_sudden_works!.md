---
title: "My sensor applet all of a sudden works!"
date: 2006-06-11
forum: General Help
---

### Post by OfficeLinebacker on 2006-06-11
So it always used to say "no sensors selceted" on the applet area and I just wrote it off.  I forget everything I went through but it just didn't work as easily as say MBM works on Windows.

So anyway My Ubuntu box (Dapper 6.06) was just sitting unused for a while.  Then I hooked my KVM and did a wuick sudo apt-get update, sudo apt-get upgrade, and then rebooted, and when it came back up, voila!

Super happy...now I can get to overclockin'!

---

### Post by Jason_25 on 2006-06-11
Maybe 
```

acpi -t

```
works for you?  It doesn't require lm-sensors and has always worked for me.

To overclock, I boot into the live cd, run sprime and update with that command when I want to see the CPU temp.

---

