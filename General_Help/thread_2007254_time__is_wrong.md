---
title: "time  is wrong"
date: 2012-06-20
forum: General Help
---

### Post by winzip on 2012-06-20
$date   ----> This prints Local Time .  time  is wrong.  how do I  change this time ?

I am using  ubuntu server ...no GUI.

---

### Post by surfer on 2012-06-20
this should work:

```
$ sudo dpkg-reconfigure tzdata
```

your system time should be set to UTC time. to keep it synchronized you can use ntpdate (on startup) or ntp (permanently).

---

### Post by winzip on 2012-06-20
> **surfer said:**
> this should work:

```
$ sudo dpkg-reconfigure tzdata
```your system time should be set to UTC time.
.
 
UTC time is correct.

> 

to keep it synchronized you can use ntpdate (on startup) or ntp (permanently).What  does *ntpdate *do ?

---

### Post by alon L on 2012-06-20
sync your machine time with NTP servers.
[https://help.ubuntu.com/8.04/serverguide/NTP.html](https://help.ubuntu.com/8.04/serverguide/NTP.html)

---

### Post by philinux on 2012-06-20
> **winzip said:**
> UTC time is correct.

What  does *ntpdate *do ?

Check if the package ntp is installed if not install it.

It syncs time with ntp servers.

---

### Post by winzip on 2012-06-21
> **philinux said:**
> Check if the package ntp is installed if not install it.



I guess its not installed.

**$dpkg -s ntp**
Package `ntp' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.


[COLOR=Red]Please note my ubuntu server is not internet connected[/COLOR].  ..so  I  dont think this will help.

---

### Post by winzip on 2012-06-21
you know in file   */etc/timezone*  I see two  time

Local Time <----[COLOR=Red]This is wrong [  A ][/COLOR]

UTC Time <---- [COLOR=Blue]This is correct [ B][/COLOR] ...it shows our local time .


But when I  command

**$date** <----this [COLOR=Red][COLOR=Black]prints[/COLOR]  [A] i.e Local Time[/COLOR]  which is wrong.

---

### Post by winzip on 2012-06-21
comments please

---

### Post by dcottingham on 2012-06-21
I'm a bit confused at this point. What do you get from "cat /etc/timezone"?

---

