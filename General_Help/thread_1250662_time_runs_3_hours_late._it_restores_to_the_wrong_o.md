---
title: "time runs 3 hours late. it restores to the wrong one after restart."
date: 2009-08-26
forum: General Help
---

### Post by chriskin on 2009-08-26
my time settings seem a little off : every time i restart i have to set it myself to the real time - it always shows 3 hours earlier than normal.

can you tell me how i can make it stay the way it should be?

---

### Post by tjwoosta on 2009-08-26
this page should help
[https://help.ubuntu.com/community/UbuntuTime]("https://help.ubuntu.com/community/UbuntuTime")

If you are by chance dual booting with windows it probably means ubuntu is set to use UTC and windows is set to use localtime. If windows was installed first it would set the bios clock use localtime as well, then when you are rebooting ubuntu it could be just reverting back to the bios clock.

The fix for that problem would be on the page I linked under "Multiple Boot Systems Time Conflicts"

---

### Post by tuxxy on 2009-08-26
Ubuntu will assume that the system clock is set to UTC.  To stop you having to change the time in Ubuntu at every bootup you should open a terminal and enter this command

```
sudo gedit /etc/default/rcS
```

Now a text file will open, you should locate the following line 

```
UTC=yes
```

Change this to No, like below;

```
UTC=no
```

Now save the file and it should be fine.

---

### Post by chriskin on 2009-08-26
> **tjwoosta said:**
> this page should help
[https://help.ubuntu.com/community/UbuntuTime]("https://help.ubuntu.com/community/UbuntuTime")

If you are by chance dual booting with windows it probably means ubuntu is set to use UTC and windows is set to use localtime. If windows was installed first it would set the bios clock use localtime as well, then when you are rebooting ubuntu it could be just reverting back to the bios clock.

The fix for that problem would be on the page I linked under "Multiple Boot Systems Time Conflicts"

but i never had any problem with the time the last 3 years i dual boot , so why now? and i never actually boot into windows if it changes anything 

i will check the link , thanks

---

### Post by chriskin on 2009-08-26
> **tuxxy said:**
> Ubuntu will assume that the system clock is set to UTC.  To stop you having to change the time in Ubuntu at every bootup you should open a terminal and enter this command

```
sudo gedit /etc/default/rcS
```

Now a text file will open, you should locate the following line 

```
UTC=yes
```

Change this to No, like below;

```
UTC=no
```

Now save the file and it should be fine.

just checked, it Is at no :S

---

### Post by kerry_s on 2009-08-26
in administration-> time & date
unlock it
click on manual
select keep synchronized


heres what that looks like.

---

### Post by Dullstar on 2009-08-26
I seem to recall there being a time zone selection.  Am I wrong?  If there's a time zone selection, make sure it's on the right zone!

---

### Post by chriskin on 2009-08-26
> **kerry_s said:**
> in administration-> time & date
unlock it
click on manual
select keep synchronized


heres what that looks like.

i tried that, but only "manually" works, the other one asks every time to install ntp, it installs it, then asks again. i'll search for a solution tomorrow, i have to go now

thanks everyone

---

### Post by kerry_s on 2009-08-26
> **chriskin said:**
> i tried that, but only "manually" works, the other one asks every time to install ntp, it installs it, then asks again. i'll search for a solution tomorrow, i have to go now

thanks everyone

forgot about that little bug, after it installs you got to close it & open it again. so if its already been installed it should be available when you open it now.

---

### Post by chriskin on 2009-08-27
> **kerry_s said:**
> forgot about that little bug, after it installs you got to close it & open it again. so if its already been installed it should be available when you open it now.

thanks, time is in sync now :)

---

