---
title: "how do you start cups  ?"
date: 2011-07-03
forum: General Help
---

### Post by gandaran on 2011-07-03
cups is disabled by default on backtract 5 (kubuntu 10.04), I can start the service running this command
```
/etc/init.d/cups start
```
but I would like cups to load at start up always, I'm sure the fix is just some file editing but don't know which.
thanks

---

### Post by mikejonesey on 2011-07-03
as it's already in the init.d it's easy to add to the rc.d

you want it to run in level 2 3 4 5

ubuntu strains normal run level is 2

```
update-rc.d cups add
update-rc.d cups start 20 2 3 4 5 . stop 20 0 1 6
```

---

### Post by gandaran on 2011-07-03
didn't work
```
root@bt:~# update-rc.d cups add
update-rc.d: warning: cups start runlevel arguments (none) do not match LSB Default-Start values (2 3 4 5)
update-rc.d: warning: cups stop runlevel arguments (none) do not match LSB Default-Stop values (1)
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
       update-rc.d [-n] <basename> disable|enable [S|2|3|4|5]
                -n: not really
                -f: force

The disable|enable API is not stable and might change in the future.
root@bt:~# update-rc.d cups start 20 2 3 4 5 . stop 20 0 1 6
update-rc.d: warning: cups stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (1)
update-rc.d: error: start|stop arguments not terminated by "."
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | SS KK]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
       update-rc.d [-n] <basename> disable|enable [S|2|3|4|5]
                -n: not really
                -f: force

The disable|enable API is not stable and might change in the future.
root@bt:~# 

```

---

### Post by gandaran on 2011-07-04
fixed by removing purge cups completely and then re-install.

---

