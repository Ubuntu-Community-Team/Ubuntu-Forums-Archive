---
title: "LSBInitScripts"
date: 2011-11-18
forum: General Help
---

### Post by brodos1 on 2011-11-18
Hi
I am trying to figure out how I can make a dependency for a sevice (daemon) to start.
I am running transmission-daemon witch is dependent of a nfs share being mounted before it starts.

My default runlevel is 2 and I want to edit my /etc/init.d/transmission-daemon script to be dependent of nfs being mounted.

from what I have read I can do this by editing this part of the init.d script:

#!/bin/sh -e
### BEGIN INIT INFO
# Provides: transmission-daemon
# Required-Start: $local_fs $remote_fs $network
# Required-Stop: $local_fs $remote_fs $network
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Start or stop the transmission-daemon.
### END INIT INFO


Could I use something like this?

#!/bin/sh -e
### BEGIN INIT INFO
# Provides: transmission-daemon
# Required-Start: $local_fs $remote_fs $network **$portmap**
# Required-Stop: $local_fs $remote_fs $network **$portmap**
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: Start or stop the transmission-daemon.
### END INIT INFO

As you see I added the portmap as a dependency, Is this correct?

Also, after I have made the changes shold I use update-rc.d mydaemon defaults or insserv mydaemon

Should I also remove the # ?

All help is appriciated :D

Btw, I am mounting the nfs filsystem via fstab.

---

### Post by mamruoc on 2011-11-29
I'm in the same situation.

I my memories serves me correct (been approx. 3 weeks since last attempt), nfs should be mounted in a nfs-mount.sh or something like that, this way it will be possible to use the $remote_fs.

---

