---
title: "disable/enable conky when on battery/AC bash script"
date: 2012-09-15
forum: General Help
---

### Post by kmilo8 on 2012-09-15
hello everyone!!!
I'm new to this and sorry if this was already asked and solved but I didn't find it.
ok, I want to make conky disable or enable depending if it's connected to AC or If it's on battery.
I got the idea from this site:

[http://www.techytalk.info/ubuntu-disable-enable-compiz-battery-ac-script/comment-page-1/#comment-14666](http://www.techytalk.info/ubuntu-disable-enable-compiz-battery-ac-script/comment-page-1/#comment-14666)

The thing is if i start conky from the terminal and disconect the AC adapter conky closes but if I plug it in, conky does not start.
this is where i have my bash:
/etc/pm/power.d/01-conky

#!/bin/bash

export DISPLAY=:0.0
if on_ac_power; then
    su -p -c 'notify-send -u critical -i "notification-message-IM" "On AC:  Turning desktop composition on"' warlock
    sleep 10
    su -p -c 'conky' warlock
   
else
    su -p -c 'notify-send -u critical -i "notification-message-IM" "On battery:  Turning conky off"' warlock
    sleep 1
    su -p -c 'killall -v conky' warlock
fi
 
exit 0
____________________
Ubuntu 12.04 64 bits
running on a dell inspiron n4050.

Any help would be great and I would really thankful.

---

### Post by Habitual on 2012-09-15
[http://ubuntuforums.org/showpost.php?p=6158865&postcount=2](http://ubuntuforums.org/showpost.php?p=6158865&postcount=2) may help.

---

### Post by kmilo8 on 2012-09-15
Thank you but that's not what I'm looking for.... My problem is not with conky itself,  it's with a bash to execute conky and to kill it automatically depending on if my laptop is plugged or unplugged from the AC adapter.
Thanks!

---

### Post by Toz on 2012-09-15
Try exporting the user's ~/.Xauthority file as well:

```
export XAUTHORITY="/home/user/.Xauthority"
```
...where /home/user/.Xauthority is the path to your actual .Xauthority file

---

### Post by kmilo8 on 2012-09-15
```
#!/bin/bash

export DISPLAY=:0.0
export XAUTHORITY="/home/warlock/.Xauthority"
if on_ac_power; then
    su -p -c 'notify-send -u critical -i "notification-message-IM" "On AC:  Turning desktop composition on"' warlock
    sleep 10
    su -p -c 'conky' warlock
   
else
    su -p -c 'notify-send -u critical -i "notification-message-IM" "On battery:  Turning conky off"' warlock
    sleep 1
    su -p -c 'killall -v conky' warlock
fi
```Thank you but it's still not working....
 Did i did it right?

---

### Post by Toz on 2012-09-16
How are you determining "on_ac_power"? Try tying into the existing PM_FUNCTIONS routines and try a script like this:

```

#!/bin/bash

. "${PM_FUNCTIONS}"

export XAUTHORITY="/home/warlock/.Xauthority"
export DISPLAY=":0"

case $1 in
    true) #laptop_mode_battery 
          su warlock -c 'notify-send -u critical -i "notification-message-IM" "On battery:  Turning conky off"' 
          sleep 1
          su warlock -c 'killall -v conky' 
          ;;
    false) #laptop_mode_ac 
          su warlock -c 'notify-send -u critical -i "notification-message-IM" "On AC:  Turning desktop composition on"' 
          sleep 10
          su warlock -c 'conky -d'
          ;;
    *)    ;;
esac

exit 0

```

---

### Post by kmilo8 on 2012-09-16
It's still not working and when I unplug it conky does not close.

```

if on_ac_power; then
    su -p -c 'notify-send -u critical -i "notification-message-IM" "On AC:  Turning conky on"' warlock
    sleep 10
    su -p -c 'conky' warlock
   

```

Thats where my problem is the "else" part works fine.

---

### Post by Toz on 2012-09-16
Try using the code I posted in post #6. I've tested it and it works.

---

### Post by kmilo8 on 2012-09-16
where does this bash go, I mean in what folder???

---

### Post by Toz on 2012-09-16
> **kmilo8 said:**
> where does this bash go, I mean in what folder???
I'm sorry, I thought that the code you posted in your original post was your code. Ok, try these steps (from a terminal window):
[LIST=1]
[*]Create the script to run when power state changes:
```
gksu gedit /etc/pm/power.d/zconky
```
[*]Copy and paste the following into the gedit window:
```
#!/bin/bash
U=<username>

. "${PM_FUNCTIONS}"

export XAUTHORITY="/home/$U/.Xauthority"
export DISPLAY=":0"

case $1 in
    true) #laptop_mode_battery 
          su $U -c 'notify-send -u critical -i "notification-message-IM" "On battery:  Turning conky off"' 
          sleep 1
          su $U -c 'killall -v conky' 
          ;;
    false) #laptop_mode_ac 
          su $U -c 'notify-send -u critical -i "notification-message-IM" "On AC:  Turning desktop composition on"' 
          sleep 10
          su $U -c 'conky -d'
          ;;
    *)    ;;
esac

exit 0
```
[*]Change the second line of that script and replace <username> with your login actual userid (make sure the case is correct).
[*]Save the file
[*]Make the file executable:
```
sudo chmod +x /etc/pm/power.d/zconky
```
[*]Test it (pull out the power cable and plug it back in). conky should quit on cable out and restart on cable in.
[*]If it doesn't work, you can get diagnostic information from the **/var/log/pm-powersave.log** log file. Feel free to post back the contents of that file.
[/LIST]

---

### Post by kmilo8 on 2012-09-16
it worked! but then after i rebooted i dont know what happend :(


```

/usr/lib/pm-utils/power.d/xfs_buffer true: not applicable.
Running hook /etc/pm/power.d/zconky true:
/etc/pm/power.d/zconky: line 2: syntax error near unexpected token `newline'
/etc/pm/power.d/zconky: line 2: `U=<warlock>'

/etc/pm/power.d/zconky true: Returned exit code 2.
Running hook /etc/pm/power.d/01_conky false:
Conky: $HOME environment variable doesn't exist
Conky: $HOME environment variable doesn't exist
*** glibc detected *** conky: malloc(): memory corruption: 0x0000000000a180e0 ***

```

---

