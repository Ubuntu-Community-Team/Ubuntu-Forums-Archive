---
title: "unable to send messages to remote computer using notify-send"
date: 2010-08-01
forum: General Help
---

### Post by adityavpratap on 2010-08-01
Hi,
I am running Ubuntu 10.10 on two of my laptops. I want to send message from one of them to the other using notify-send. I have connected to the remote laptop using ssh as -
$ ssh -X 192.168.1.x

after entering the appropriate password the ssh connection to the remote laptop is established. Then I enter the following commands -
$ DISPLAY=:0.0
$ export DISPLAY
$ XAUTHORITY=~/.Xauthority
$ export XAUTHORITY
$ sudo -u username /usr/bin/notify-send "Hello" (where username is the username on the remote system)
after which I get the following message -
[I]libnotify-Message: Unable to get session bus: /bin/dbus-launch terminated abnormally with the following error: No protocol specified
Autolaunch error: X11 initialization failed.[/I]

I have been breaking my head on this for a long time now but there is no further progress. Any suggestions?

Thanking in advance,

---

### Post by Primefalcon on 2010-08-01
Do you have the same problem if you just do this after sshing in

```
export DISPLAY=:0; notify-send "hi there"
```

---

### Post by adityavpratap on 2010-08-03
Sorry for the delay in responding. I tried as you suggested and got the following output -
```

libnotify-Message: Unable to get session bus: /bin/dbus-launch terminated abnormally with the following error: No protocol specified
Autolaunch error: X11 initialization failed.

```

---

### Post by jamesisin on 2012-02-12
I get that same dbus error.  Did you ever make any progress with this?

---

