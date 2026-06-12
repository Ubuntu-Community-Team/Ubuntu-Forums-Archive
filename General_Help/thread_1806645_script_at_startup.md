---
title: "script at startup?"
date: 2011-07-17
forum: General Help
---

### Post by pua06 on 2011-07-17
salmo allikm warhmat allah wabrakato
i   tried to make script startup  when booting but no response 

this steps that i did, i made it in my pc and work but in another  pc can't work

 that i did in details
   1-i make script check.sh put in /home/ubuntu
   2-i make symbolic link because i make program auto start and i gave script
   priority less than this program
   sudo ln -sf /home/ubuntu/check.sh  etc/rc5.d/S70check.sh
   3-i go to session startup and put
   Name  check
   commend /home/ubuntu/check.sh

 i don't know why can't see this script as start when booting
thanks so much

---

### Post by Toz on 2011-07-18
It's not really clear what you are trying to accomplish. You appear to be trying to place the script in the rc5.d directory which indicates that you want the script to run on system startup, but then it looks like you are also trying to run it from xfce's user-specific autostart. Does this script need to be run at system startup or at the user login level?

If at system startup, then I suggest:
1. move file to /usr/local/bin
2. make sure file is executable
3. remove link in /etc/rc5.d
4. add line to /etc/rc.local just before "exit 0" to execute the script
```
.....
/usr/local/bin/check.sh
exit 0
```

If at user startup, then:
1. remove link in /etc/rc5.d
2. make sure file is executable
3. keep entry in xfce autostart

---

### Post by pua06 on 2011-07-18
> **Toz said:**
> It's not really clear what you are trying to accomplish. You appear to be trying to place the script in the rc5.d directory which indicates that you want the script to run on system startup, but then it looks like you are also trying to run it from xfce's user-specific autostart. Does this script need to be run at system startup or at the user login level?

If at system startup, then I suggest:
1. move file to /usr/local/bin
2. make sure file is executable
3. remove link in /etc/rc5.d
4. add line to /etc/rc.local just before "exit 0" to execute the script
```
.....
/usr/local/bin/check.sh
exit 0
```If at user startup, then:
1. remove link in /etc/rc5.d
2. make sure file is executable
3. keep entry in xfce autostart

thanks
really that in details what i want to do i have program motion and want this program be startup when booting i did it from gui 
and it start when system booting 
there was a script that need to start it after motion startup so i put the script in rc5.d 
and make priority less than motion
already i made script executable within
properties and permission
you understand me ?
keep entry in xfce autostart[??????????????

---

### Post by Toz on 2011-07-18
So, you have 2 scripts that need to run. One called **motion** that needs to start first, then a second one called **check.sh** that is dependent on the first one starting. Both need to start at system boot and both scripts are   marked executable.

If so, I would put them both in /usr/local/share and edit the **/etc/rc.local** file before the "exit 0" statement, like:
```

/usr/local/bin/motion
/usr/local/bin/check.sh
exit 0
```

If you need to wait some time before starting the second script (to let some initiation happen with first script), you could prefix the second statement with a sleep command like:
```
/bin/sleep 5s && /usr/local/bin/check.sh
```

---

### Post by pua06 on 2011-07-18
> **Toz said:**
> So, you have 2 scripts that need to run. One called **motion** that needs to start first, then a second one called **check.sh** that is dependent on the first one starting. Both need to start at system boot and both scripts are marked executable.
 
If so, I would put them both in /usr/local/share and edit the **/etc/rc.local** file before the "exit 0" statement, like:
```

/usr/local/bin/motion
/usr/local/bin/check.sh
exit 0
```
 
If you need to wait some time before starting the second script (to let some initiation happen with first script), you could prefix the second statement with a sleep command like:
```
/bin/sleep 5s && /usr/local/bin/check.sh
```
 
thanks
 
motion is program not script

---

