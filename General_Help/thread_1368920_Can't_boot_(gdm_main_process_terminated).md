---
title: "Can't boot (gdm main process terminated)"
date: 2009-12-31
forum: General Help
---

### Post by Sardien on 2009-12-31
Hi all,

Running 9.04 - did a bunch of updates today (including what it said was a "partial upgrade") and now it won't boot.

It shows the Ubuntu logo briefly and then returns to this screen and stays there:

```

Boot from (hd0,0)..<snip>
Starting up ...
init: gdm main process (562) terminated with status 1
```

I searched the forums & Googled but didn't find anything:(

How do I fix this please?

Thanks a lot! :D

---

### Post by john newbuntu on 2009-12-31
Check if you have adequate space in your home directory.  Type "df -Th" on the command line and see if the "USE" column shows anything close to 100%.
If not, please look at the following logs: /var/log/Xorg.0.log, /var/log/syslog and /var/log/messages to see anything abnormal at the time when the failure happened.

---

### Post by Sardien on 2010-01-01
> **john newbuntu said:**
> Check if you have adequate space in your home directory.  Type "df -Th" on the command line and see if the "USE" column shows anything close to 100%.
If not, please look at the following logs: /var/log/Xorg.0.log, /var/log/syslog and /var/log/messages to see anything abnormal at the time when the failure happened.

Thanks.
Unfortunately I can't even get into the console.
I try ctrl+alt+F[1-7] but never get a login prompt. 
Tried booting in Recovery Mode but also don't get a login prompt. :\

What should I do?

---

### Post by Sardien on 2010-01-02
*bump*

anyone? please :) ?

---

### Post by john newbuntu on 2010-01-03
Follow steps 1 through 9 in the link below to boot into a single user mode:
[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)
You can then check the older logs to see what went wrong.

Once you are logged in, do:
sudo dpkg-reconfigure gdm

Finally, you could try and run:
sudo init 2
to get into your regular mode of operation.

---

