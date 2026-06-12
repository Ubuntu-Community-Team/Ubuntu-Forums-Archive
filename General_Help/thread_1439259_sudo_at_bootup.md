---
title: "sudo at bootup"
date: 2010-03-26
forum: General Help
---

### Post by dDaYb on 2010-03-26
Hello,
I want deluged and deluge-web started at boot but not under root. So that all downloaded files are owned by not root, but user sm
I made a script /etc/init.d/m

```

#! /bin/sh
# /etc/init.d/m

case "$1" in
  start)
    echo "Starting script M "
    sudo -S -b -u sm deluged
    sudo -S -b -u sm screen -S deluge2 -d -m deluge-web -q
 *)
    echo "Usage: /etc/init.d/m {start}"
    exit 1
    ;;
esac

exit 0

```

and added it
```
sudo update-rc.d m defaults 98 02
```

but it doesn't start, why?

---

### Post by sisco311 on 2010-03-26
Check out the /etc/init.d/skeleton for an example script.

Try to start/stop the daemon with start-stop-daemon:
```
start-stop-daemon --start --user username:group --exec ...
```


Or write an Upstart job:
[http://upstart.ubuntu.com/getting-started.html](http://upstart.ubuntu.com/getting-started.html)

---

