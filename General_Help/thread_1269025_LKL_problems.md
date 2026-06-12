---
title: "LKL problems"
date: 2009-09-17
forum: General Help
---

### Post by Anonymity on 2009-09-17
I installed LKL today and it was working then my comp messed up (was unable to use keyboard at all) had to restart and now I get

scott@desktop:~$ sudo lkl -k /usr/share/lkl/keymaps/us_km -o /home/`echo $USER`/Desktop/log.log -l &
[1] 3572
scott@desktop:~$ sudo lkl -k /usr/share/lkl/keymaps/us_km -o /home/`echo $USER`/Desktop/log.log -l &
[2] 3574

[1]+  Stopped                 sudo lkl -k /usr/share/lkl/keymaps/us_km -o /home/`echo $USER`/Desktop/log.log -l
scott@desktop:~$ 

[2]+  Stopped                 sudo lkl -k /usr/share/lkl/keymaps/us_km -o /home/`echo $USER`/Desktop/log.log -l
scott@desktop:~$ 

how do I fix it? im using Jaunty Jackie btw

---

### Post by majdi on 2009-11-15
Hi I successfully installed it on 8.04.3 and had no problems with my keyboard. I started it by running the following command;

```
sudo lkl -k /usr/share/lkl/keymaps/us_km -o /var/log/lkl.log -l &
```

I got the message;

```
Started to log port 0x60. Keymap is /usr/share/dock/lkl/us_km. The logfile is /var/log/lkl.log
```

But there was no log file created and I checked to see if lkl is running and it was.

I tried a re-boot but now I get 

```

sudo lkl -k /usr/share/lkl/keymaps/us_km -o /var/log/lkl.log -l &
[1] 6871

[1]+ Stopped

```

Not sure why this is happening, any fix for this?

---

### Post by majdi on 2009-11-16
Anyone???

---

### Post by dictum9 on 2009-12-26
> **majdi said:**
> 

```
sudo lkl -k /usr/share/lkl/keymaps/us_km -o /var/log/lkl.log -l &
```I got the message;

```
Started to log port 0x60. Keymap is /usr/share/dock/lkl/us_km. The logfile is /var/log/lkl.log
```But there was no log file created and I checked to see if lkl is running and it was.


lkl -l -k /usr/share/lkl/keymaps/us_km -o /tmp/file.out 

I got the same thing, the same command but no output file is created. Why is that?

---

