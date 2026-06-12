---
title: "Pre Runlevel 6 script"
date: 2010-08-05
forum: General Help
---

### Post by pacmac on 2010-08-05
Hi all;

I need to delay the reboot scripts in /etc/rc6.d for 10 seconds with all services and terminal sessions remaining active including ttyS0, which is a serial terminal being used to interact with a micro controller. The micro-controller queries the run level with who -r and if it receives a runlevel of 6 will branch off into a routine to handle the reboot.

I have added a script (pre-shutdown) to /etc/init.d with a link in rc6.d, K01pre-shutdown as follows:

#! /bin/sh
## give time for micro to determine run level.
sleep 10

This runs before all but the syslogd script, and does delay the reboot as expected, however as soon as the reboot command is issued from another session, all sessions appear to end and the micro-controller is unable to communicate with ttyS0 to issue the who -r command and read the reply.

How can I prevent the killing of the terminal sessions on reboot to allow sufficient time for the micro to poll the runlevel ?

Thanks

---

### Post by pacmac on 2010-08-06
Hmmm.

I have edited the init.d script as follows:

```

#! /bin/sh
## give time for PIC to determine run level.
sleep 5
echo -e '\0002 reboot \0003' > /dev/tty
sleep 5
echo -e '\0002 reboot \0003' > /dev/tty
sleep 5
echo -e '\0002 reboot \0003' > /dev/tty
sleep 5
echo -e '\0002 reboot \0003' > /dev/tty
sleep 5
echo -e '\0002 reboot \0003' > /dev/tty
sleep 5
echo -e '\0002 reboot \0003' > /dev/tty

```

and although all of the pauses appear to work, nothing is displayed on the terminal.

Any ideas on how I can delay the killing of the terminal sessions to allow time for some additional commands to be sent before shutdown ?

Thanks

---

### Post by chopinhauer on 2010-08-06
> **pacmac said:**
> 
This runs before all but the syslogd script, and does delay the reboot as expected, however as soon as the reboot command is issued from another session, all sessions appear to end and the micro-controller is unable to communicate with ttyS0 to issue the who -r command and read the reply.


Ubuntu doesn't use the System V init process, but [Upstart](http://upstart.ubuntu.com/) an event-based init daemon. Therefore whenever the "runlevel 6" event is emitted many scripts (configured in the /etc/init directory or /etc/event.d for older Ubuntu releases) start simultaneously. Only the legacy init scripts are started one after another.

You should probably configure your script to run on the "runlevel 6" signal and reconfigure the others to run when your script has finished ("on stopped <your_scripted>").

---

### Post by pacmac on 2010-08-06
Hi;

Thanks for helping.

If I understand you correctly, upstart reads through /etc/init and decides whether to run a related script in /etc/init.d based on the runlevels set in the /etc/init/*.conf files ?

But what i'm not sure about is this:
> 
configure your script to run on the "runlevel 6" signal and reconfigure the others to run when your script has finished
Are you saying that I need to edit every /etc/init/*.conf file's runlevel where the script is configured to stop on runlevel 6 i.e. 

stop on runlevel [!2345] 
change to 
stop on runlevel [!23456]

and then call each modified script from a new /etc/init/*.conf file is set to stop on runlevel [!2345] so I would end up with:
```

/etc/init/pre-reboot.conf
stop on runlevel [!2345] 
on stopped script
  exec /etc/init.d/pre-reboot
  exec /etc/init.d/rc
end script

```

---

### Post by chopinhauer on 2010-08-06
I would do something like: you replace the lines
```
stop on runlevel [06]
stop on runlevel [!2345]
```with
```
stop on stopped pre-reboot
```and in /etc/init/pre-reboot.conf something like:
```

start on runlevel [!2345]

exec /etc/init.d/pre-reboot

```

This way your script will be executed first and everything will wait until it stops.

---

