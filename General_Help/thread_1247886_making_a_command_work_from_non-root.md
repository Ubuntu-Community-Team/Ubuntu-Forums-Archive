---
title: "making a command work from non-root"
date: 2009-08-23
forum: General Help
---

### Post by linkxs on 2009-08-23
hi, this command:

```
echo 0 > /sys/class/leds/asus\:\:touchpad/brightness
```

turns off the LED's around my touchpad on my laptop. It doesn't work from sudo, but does work from root account. How would i make it be able to run from a non-root account? 

Thanks in advance

---

### Post by blueridgedog on 2009-08-23
Do you want the command to run every time the system boots or just when desired?  If you want it to run every time, you can place it at the end of /etc/init.d/rc.local.  It may work there.

---

### Post by linkxs on 2009-08-23
unfortunately, doesn't seem it worked.

---

### Post by loomsen on 2009-08-23
Hello.

sudo doesn't work because it works ;)

sudo's purpose is to temporary obtain admin rights for a user.

see:

> 
[COLOR="Red"]docter[~][/COLOR] echo $HOME
/home/docter
[COLOR="Red"]docter[~] [/COLOR]sudo echo $HOME
/home/docter
[COLOR="Red"]docter[~][/COLOR] su -c 'echo $HOME'
Password: 
/root


and 

> 
[COLOR="Red"]docter[~][/COLOR] sudo echo $(whoami)
docter
[COLOR="Red"]docter[~][/COLOR] su -c 'echo $(whoami)'
Password: 
root


---

### Post by linkxs on 2009-08-23
ahh, ok. that explains the sudo problem. so, i could do 

> su -c echo 0 > /sys/class/leds/asus\:\:touchpad/brightness

but then bootup will hang and wait for me to enter the root password, which clearly isn't an option.

---

### Post by loomsen on 2009-08-23
So, just to make sure I get you right, you want this command to be executed only once upon boot?

Then blueridgedog is right and the place to go is 
/etc/init.d/rc.local

For instance you could add something simple like

```

if [ -e /sys/class/leds/asus\:\:touchpad/brightness ];then
echo 0 > /sys/class/leds/asus\:\:touchpad/brightness
fi

```

This command will be executed after all boot processes finished, no need to use su -c on it.

If you want to alter the brightness from your running gnome session you'll need to use

```

su -c "echo 0 > /sys/class/leds/asus\:\:touchpad/brightness"
```

su : login as superuser
-c : specify a command to run (is: login as root, run command, logout)
and you'll have to put the command into quotes otherwise the > pipe would break your su privileges and you still wouldn't be able to write to /sys/cl...

---

