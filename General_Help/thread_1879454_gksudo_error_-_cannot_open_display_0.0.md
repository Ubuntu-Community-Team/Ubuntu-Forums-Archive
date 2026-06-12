---
title: "gksudo error - cannot open display: :0.0"
date: 2011-11-11
forum: General Help
---

### Post by ut_nubu on 2011-11-11
Hi, 
I used to run applications such as gedit as a different user by using the command
gksudo -u username gedit
without any problem. After installing lamp on Ubuntu 11.04 64bit this command line results now in the following error message:
cannot open display::0.0

other programmes like gnucash show the following error message:
An error occurred while creating the directory: .gnucash
Please correct the problem and restart GnuCash.
The reported error was 'Permission denied' (errno 13).

I would appreciate if anyone could help me to get gksudo running again.

Thanks a lot.

---

### Post by lechien73 on 2011-11-11
If you run:

```
echo $DISPLAY
```

from the terminal window, what is the output?

---

### Post by ut_nubu on 2011-11-12
Thanks for your reply. Running:  'echo $DISPLAY' gives:
:0.0

---

