---
title: "Help on convert RHEL script to Debian (Ubuntu)"
date: 2010-02-19
forum: General Help
---

### Post by Milleman on 2010-02-19
Hi guys,

Need some minor help with converting a daemon script (in /etc/init.d) for RHEL into a Ubuntu version. Ubuntu doesn't recognize the "daemon" command in following script:

```

daemon --user ${USER} "/usr/bin/${SVNAME} ${OPTIONS}"
RETVAL=$?
[ $RETVAL = 0 ] && touch /var/lock/subsys/${SVNAME}
echo

```

What is the Debian equivalent to "daemon"?

/Mill

---

