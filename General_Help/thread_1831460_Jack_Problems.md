---
title: "Jack Problems"
date: 2011-08-23
forum: General Help
---

### Post by nitro7 on 2011-08-23
Greetings, 

Jack will not start up in realtime mode from QT Jack Control. Here is some outputs that may help

```
cat /etc/issue
Ubuntu 10.04.3 LTS \n \l

```

Jack Control Error
```
12:58:16.080 Startup script...
12:58:16.085 artsshell -q terminate
sh: artsshell: not found
12:58:16.491 Startup script terminated with exit status=32512.
12:58:16.491 JACK is starting...
12:58:16.492 /usr/bin/jackd -dalsa -dhw:0 -r48000 -p256 -n2
jackd 0.118.0
Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
Please check your /etc/security/limits.conf for the following lines
and correct/add them:
  @audio          -       rtprio          100
  @audio          -       nice            -10
After applying these changes, please re-login in order for them to take effect.
You don't appear to have a sane system configuration. It is very likely that you
encounter xruns. Please apply all the above mentioned changes and start jack again!
12:58:16.537 JACK was started with PID=3828.
12:58:16.636 JACK was stopped with exit status=255.
12:58:18.650 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

```
group
teenhorizons adm dialout cdrom audio plugdev lpadmin admin sambashare rivendell
```

```
 cat /etc/security/limits.conf | grep -v "#"


@audio          -       rtprio          100
@audio          -       nice            -10
@audio          -       memlock         unlimited

```

```
cat /etc/security/limits.d/audio.conf | grep -v "#"
@audio   -  rtprio     99
@audio   -  memlock    unlimited

```

```
 ulimit -l -r
max locked memory       (kbytes, -l) unlimited
real-time priority              (-r) 99

```

Any help greatly appreciated.
Clint

---

