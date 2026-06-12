---
title: "Problems with btnx"
date: 2009-09-12
forum: General Help
---

### Post by slope on 2009-09-12
Sometimes I get problems with btnx. Mostly it is the scroll function that stop working. Reboot usually takes care of problems. 
But not always handy to do a boot in the middle of other jobs. SO I try to to use th btnx GUI from Applications -> System -> Btnx.

When I try to use the Restart Btnx button I get an error:
Failed to execute command: "/etc/init.d/btnx restart" Make sure btnx is installed correctly.

Well I have had all buttons adressed during setup so I know btnx is correct installed. And it worked yesterday and days before.

Ok so when I try to restart btnx from terminal I get this:
```
Restarting btnx : Button Extension - mouse button rerouter daemon
 btnx: Failed to kill previous btnx processes
btnx successfully stopped
 btnx: uinput modprobed successfully.
 btnx: Opening config file: /etc/btnx/btnx_config_Default
 btnx: Error: invalid arguments for command execution configuration option.
 btnx: You must specify at least one item: /path/to/executable_name
 btnx: Example: /usr/bin/gedit
 btnx: Then append optional arguments: /usr/bin/gedit --new-window /etc/btnx/btnx_config
 btnx: Fatal error in config_split_command. Exiting...
btnx failed to start during restart

```

Any tips?

Btw I am on 64 bit. Mouse is Logitech Mx Revolution.

---

### Post by P4man on 2009-09-12
AFAIK, btnx no longer works with current releases, and its not going to be fixed. To control the scroll wheel, you can still use revoco though. Have a look here:

[http://www.toosweettobesour.com/2009/05/13/logitech-mx-revolution-revoco-in-ubuntu-904-jaunty-click-to-click-even-after-a-resumewakeup/](http://www.toosweettobesour.com/2009/05/13/logitech-mx-revolution-revoco-in-ubuntu-904-jaunty-click-to-click-even-after-a-resumewakeup/)

---

### Post by slope on 2009-09-12
> **P4man said:**
> AFAIK, btnx no longer works with current releases, and its not going to be fixed. To control the scroll wheel, you can still use revoco though. Have a look here:

[http://www.toosweettobesour.com/2009/05/13/logitech-mx-revolution-revoco-in-ubuntu-904-jaunty-click-to-click-even-after-a-resumewakeup/](http://www.toosweettobesour.com/2009/05/13/logitech-mx-revolution-revoco-in-ubuntu-904-jaunty-click-to-click-even-after-a-resumewakeup/)

Np cause I am still in Hardy LTS. 
I will look into the link you gave.

Thx

---

