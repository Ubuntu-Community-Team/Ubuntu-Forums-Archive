---
title: "xfce4-session-logout --halt not working correctly?"
date: 2010-11-30
forum: General Help
---

### Post by LuniTux on 2010-11-30
Hello,

I have an Xubuntu 9.10 Computer that is set to shutdown at a specific time. If I type ```
xfce4-session-logout --halt
``` from the terminal the computer correctly shuts down. The problem is that I want the computer to shutdown via bash script, but when I run the script (using --halt or --reboot), the computer does **logs out** and **does not** shutting down. How can I get the script to shutdown using xfce4-session-logout?

Thanks in advance,

---

### Post by conradin on 2010-11-30
Ok, its not bash, its expect, but it will do what you want automatically. I think your current set up might be failing because to shut down you need to be root. (just a guess)

```

#!/usr/bin/expect
spawn sudo -i
expect ":"
send "MY_Password\r"
expect "#"
send "shutdown -h now\r"
interact

```

---

### Post by ajgreeny on 2010-11-30
From "man shutdown"

> **shutdown** arranges for the system to be brought down in a safe way.  All logged-in users are notified that the system is going down and, within the last five minutes of TIME, new logins are prevented.

       TIME may have different formats, the most common is simply the word 'now' which will bring the  system  down  immediately.   Other valid formats are +m, where m is the number of minutes to wait until shutting down and hh:mm which specifies the time on the 24hr clock.

       Once TIME has elapsed, shutdown sends a request to the init(8) daemon to bring the system down  into the appropriate runlevel.

       This is performed by emitting the runlevel(7) event, which includes the new runlevel in the RUNLEVEL  environment variable as well as the  previous  runlevel  (obtained  from  the  environment  or  from /var/run/utmp)  in  the  PREVLEVEL variable.  An additional INIT_HALT variable may be set, this will contain the value HALT when bringing the system down for halt and POWEROFF when bringing the  system down for power off.

If you **always** want the machine to shutdown at 11.00pm you could add the following line to /etc/rc.local just above the "exit 0" line:-
```
shutdown -h 23:00
``` and i think that would do it for you; not quite a script as such, but it still uses bash as far as I'm aware.

---

### Post by LuniTux on 2010-11-30
I want to be able to shutdown using the xfce4-session-logout command because root is not needed. I know that i can
```
sudo crontab -e
0 23 * * * shutdown -h now
```
but i would prefer
```
crontab -e
0 23 * * * xfce4-session-logout --halt
```
if possible.

I'm just confused why script logs out but direct through terminal shuts down. both are being run without **sudo**. Could the permissions of the file be effecting it?```
ls -l
-rwxr--r-- 1 lcluser lcluser 205 2010-11-30 10:32 autohalt.sh
```

---

### Post by LuniTux on 2010-11-30
well this is odd, now the computer is only logging out ```
xfce4-session-logout --halt
``` . I dont think I changed anything so im not sure why... I will continue to see if there are any solutions

---

### Post by LuniTux on 2010-11-30
It appears to be a bug based on what Im seeing on google

[http://www.google.com/search?hl=en&q=%22xfce4-session-logout+--halt%22+not+working&aq=f&aqi=&aql=&oq=&gs_rfai=]("http://www.google.com/search?hl=en&q=%22xfce4-session-logout+--halt%22+not+working&aq=f&aqi=&aql=&oq=&gs_rfai=")

---

