---
title: "Run a command at startup"
date: 2011-05-22
forum: General Help
---

### Post by jardo on 2011-05-22
hi there!
i need to run this command at the boot of computer 
```
hdparm -B 255 /dev/sda
```

i saved  this command in the file /etc/rc.local
but i don't know why...it doesnt work, so i have to run it after boot from terminal..here there is the content of the file:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
iwconfig wlan0 rate 11M
hdparm -B 255 /dev/sda
exit 0
```

what's wrong?:confused:

---

### Post by m_duck on 2011-05-22
Did you "change the execution bits"? Run the following in terminal to see the output, and if there is no 'x' in the left group of the output, you just need to make the file executable.
```
ls -l /etc/rc.local
```
And to make it executable if it isn't:
```
chmod +x /etc/rc.local
```You'll probably need root privileges to make it executable - if that is the case, prefix the chmod command with ***sudo***.

---

### Post by jardo on 2011-05-22
first of all...thanks for the help!
here there is the output of the command you said me to type:
```
-rwxr-xr-x 1 root root 352 2011-05-21 12:35 /etc/rc.local
```

uhm...i need to run the second command you suggested me? i see some x in the output:)

---

### Post by m_duck on 2011-05-22
Ok, it's executable then... So it *should* work :p Have you tried a reboot to see if it does since running the chmod command?

Do either of the commands work, or do they both not work? And do they work when you run the from the terminal once booted?

---

### Post by jardo on 2011-05-22
i restarted after running chmod...but it's the same....the other command about the rate of wlan connection works fine....
the hdparm command works properly just if i run it from terminal...:confused:

---

### Post by lithopsian on 2011-05-22
Something else may be messing with your power settings later in the boot process and overriding the hdparm command.  The obvious candidate would be part of your screen saver which generally includes power management features.  Executing hdparm after the screensaver has been initialised would then stick.

---

### Post by sisco311 on 2011-05-22
Edit the /etc/hdparm.conf file and add something like:
```

/dev/disk/by-id/<symlink-to-sda> {
   apm = 255
}
```

---

### Post by jardo on 2011-05-22
> **sisco311 said:**
> Edit the /etc/hdparm.conf file and add something like:
```

/dev/disk/by-id/<symlink-to-sda> {
   apm = 255
}
```

i copied what u suggested me in that file...and i tried also with 
```
/dev/sda {
   apm = 255
}
```

but it didn't help...maybe i write with wrong syntax?
disk/by-id/<symlink-to-sda> with what i should change? sorry but im a bit newbie in ubuntu :D

---

### Post by jardo on 2011-06-13
i still have this issue...how can i run a command at startup for hdparm???? :(

---

### Post by Arteymis on 2011-06-13
The really best way I know is to first open "Application on start up" and then press "add" so you can write your own commands on start-up.

EDIT : I've just read on boot of the computer... This fix might not be appropriated then..

---

