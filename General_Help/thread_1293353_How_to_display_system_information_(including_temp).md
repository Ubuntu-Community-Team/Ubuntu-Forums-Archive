---
title: "How to display system information (including temp)"
date: 2009-10-16
forum: General Help
---

### Post by CharlesA on 2009-10-16
I was wondering how to display the system information after you login to a terminal.

It looks like this on a machine using KDE: 

```
System information as of Fri Oct 16 20:40:01 PDT 2009

  System load:  0.06              Swap usage:  0%     Users logged in: 1
  Usage of /:   3.1% of 71.05GB   Temperature: 46 C
  Memory usage: 50%               Processes:   125

  Graph this data and manage this system at https://landscape.canonical.com/

```This is how it looks on a different machine running Gnome:

```
  System information as of Fri Oct 16 20:40:02 PDT 2009

  System load: 0.2                Memory usage: 9%   Processes:       140
  Usage of /:  0.9% of 282.42GB   Swap usage:   0%   Users logged in: 1

  => /sync is using 88.3% of 1.34TB

  Graph this data and manage this system at https://landscape.canonical.com/

```

How do I get the one running on gnome to display the temperature? Also, is there a command to display this info at will (so to speak?).

Thanks!

---

### Post by bwang on 2009-10-17
Do you have the lm-sensors package installed?

---

### Post by CharlesA on 2009-10-17
Yup, lm-sensors is installed.

When I run "sensors" the temp info is displayed.

Unfortunately, the temp isn't displayed when I login via SSH

on the machine running KDE, lm-sensors isn't installed, but I get a temperature output when logging into ssh. :confused:

---

### Post by CharlesA on 2009-10-22
Still curious as to how to display the TEMP.

No such luck with my google-fu either. Meh. :-(

---

### Post by harmeet on 2009-11-16
The command you are looking for is -

landscape-sysinfo

```
harmeet@sip:~$ landscape-sysinfo 
  System load:  0.0               Swap usage:  0%     Users logged in: 1
  Usage of /:   2.5% of 34.90GB   Temperature: 57 C
  Memory usage: 7%                Processes:   101

  Graph this data and manage this system at https://landscape.canonical.com/
```

---

### Post by CharlesA on 2009-11-24
Thanks! Unfortunately that doesn't display the temp still. Oh well, not a huge deal. I know the box is only running at around 35C.

---

