---
title: "Run as a Daemon"
date: 2010-05-07
forum: General Help
---

### Post by berzerke on 2010-05-07
I'm working with the Lucene-search extension for mediawiki. Part of the running procedure is I have to run the daemon lsearchd (java app). However, the only example given involves running it from the command line. I need it to start up automatically when the server reboots as a daemon. How do I get it to run as a daemon?

I've tried daemon switches (--daemon and -daemon), but neither worked and the docs are silent on this.

---

### Post by berzerke on 2010-05-08
Searching through some docs for an old version of the extension turned up an init script. Here are the instructions for anyone else who has this problem:

Copy the lucene-search directory to /usr/local/lucene-search. Then add the following init script to /etc/init.d (be sure to make it executable).

```

#!/bin/sh -e
### BEGIN INIT INFO
# Provides:             lsearchd
# Required-Start:       $syslog
# Required-Stop:        $syslog
# Default-Start:        2 3 4 5
# Default-Stop:         1
# Short-Description:    Start the Lucene Search daemon
# Description:          Provide a Lucene Search backend for MediaWiki
### END INIT INFO

test -x /usr/local/lucene-search/lsearchd || exit 0

OPTIONS=""
if [ -f "/etc/default/lsearchd" ] ; then
        . /etc/default/lsearchd
fi

. /lib/lsb/init-functions

case "$1" in
  start)
    cd /usr/local/lucene-search
    log_begin_msg "Starting Lucene Search Daemon..."
    start-stop-daemon --start --quiet --oknodo --chdir /usr/local/lucene-search --backgro$
    log_end_msg $?
    ;;
  stop)
    log_begin_msg "Stopping Lucene Search Daemon..."
    start-stop-daemon --stop --quiet --oknodo --retry 2 --chdir /usr/local/lucene-search $
    log_end_msg $?
    ;;
  restart)
    $0 stop
    sleep 1
    $0 start
    ;;
  reload|force-reload)
    log_begin_msg "Reloading Lucene Search Daemon..."
    stat-stop-daemon --stop -signal 1 --chdir /usr/local/lucene-search --exec /usr/local/$
    log_end_msg $?
    ;;
  status)
    status_of_proc /usr/local/lucene-search/lsearchd lsearchd && exit 0 || exit $?
    ;;
  *)
    log_success_msg "Usage: /etc/init.d/lsearchd {start|stop|restart|reload|force-reload|$
    exit 1
esac

exit 0

```

---

### Post by ramianaziba21 on 2010-05-08
This site is more   appropriate to publish some of the article. This article is one of the best   and great in this site. I like this post and sharing some of my close friend.

---

### Post by ojintoad on 2011-02-10
It looks as if the forum may have ended up cutting off parts of this script.  Do you have a reference to the original thread that features the script or can you repaste the script in some way where the script stays intact?

I'm in the middle of attempting to complete the lines myself and will post if I get it done.

---

### Post by ojintoad on 2011-02-10
Found it: [http://www.mediawiki.org/wiki/Extension_talk:Lucene-search#LSearch_Daemon_Init_Script_for_Ubuntu]("http://www.mediawiki.org/wiki/Extension_talk:Lucene-search#LSearch_Daemon_Init_Script_for_Ubuntu")

---

### Post by John Ericson on 2011-07-27
This is the correct URL: [http://www.mediawiki.org/wiki/Extension_talk:Lucene-search/archive/2009#LSearch_Daemon_Init_Script_for_Ubuntu](http://www.mediawiki.org/wiki/Extension_talk:Lucene-search/archive/2009#LSearch_Daemon_Init_Script_for_Ubuntu)
 
I also improved some more on the script. I'll include it here in case anyone else needs it:
 
```

#!/bin/sh -e
### BEGIN INIT INFO
# Provides:             lsearchd
# Required-Start:       $syslog
# Required-Stop:        $syslog
# Default-Start:        2 3 4 5
# Default-Stop:         1
# Short-Description:    Start the Lucene Search daemon
# Description:          Provide a Lucene Search backend for MediaWiki. Copied by John Ericson from: http://ubuntuforums.org/showthread.php?t=1476445
### END INIT INFO

# Set to install directory of lucense-search. For example: /usr/local/lucene-search-2.1.3
LUCENE_SEARCH_DIR="/usr/local/lucene-search-2.1.3"

# Set username for daemon to run as. Can also use syntax "username:groupname" to also specify group for daemon to run as. For example: me:me
RUN_AS_USER=""

OPTIONS=""

test -x $LUCENE_SEARCH_DIR/lsearchd || exit 0

test -n "$RUN_AS_USER" && CHUID_ARG="--chuid $RUN_AS_USER" || CHUID_ARG=""

if [ -f "/etc/default/lsearchd" ] ; then
        . /etc/default/lsearchd
fi

. /lib/lsb/init-functions

case "$1" in
  start)
    cd $LUCENE_SEARCH_DIR
    log_begin_msg "Starting Lucene Search Daemon..."
    start-stop-daemon --start --quiet --oknodo --chdir $LUCENE_SEARCH_DIR --background $CHUID_ARG --exec $LUCENE_SEARCH_DIR/lsearchd -- $OPTIONS
    log_end_msg $?
    ;;
  stop)
    log_begin_msg "Stopping Lucene Search Daemon..."
    start-stop-daemon --stop --quiet --oknodo --retry 2 --chdir $LUCENE_SEARCH_DIR $CHUID_ARG --exec $LUCENE_SEARCH_DIR/lsearchd
    log_end_msg $?
    ;;
  restart)
    $0 stop
    sleep 1
    $0 start
    ;;
  reload|force-reload)
    log_begin_msg "Reloading Lucene Search Daemon..."
    stat-stop-daemon --stop -signal 1 --chdir $LUCENE_SEARCH_DIR $CHUID_ARG --exec $LUCENE_SEARCH_DIR/lsearchd
    log_end_msg $?
    ;;
  status)
    status_of_proc $LUCENE_SEARCH_DIR/lsearchd lsearchd && exit 0 || exit $?
    ;;
  *)
   log_success_msg "Usage: /etc/init.d/lsearchd {start|stop|restart|reload|force-reload|status}"
   exit 1
esac

exit 0

```

---

### Post by Anti_Climax on 2013-01-28
I've fixed a spelling error in the previous post of this script. Be sure to specify the LUCENE_SEARCH_DIR and RUN_AS_USER variables. The default path for Lucene Search on my 12.04LTS install was /usr/local/search/ls2. 

```

#!/bin/sh -e
### BEGIN INIT INFO
# Provides:             lsearchd
# Required-Start:       $syslog
# Required-Stop:        $syslog
# Default-Start:        2 3 4 5
# Default-Stop:         1
# Short-Description:    Start the Lucene Search daemon
# Description:          Provide a Lucene Search backend for MediaWiki. Copied by John Ericson from: http://ubuntuforums.org/showthread.php?t=1476445
### END INIT INFO

# Set to install directory of lucense-search. For example: /usr/local/lucene-search-2.1.3
LUCENE_SEARCH_DIR="/usr/local/lucene-search-2.1.3"

# Set username for daemon to run as. Can also use syntax "username:groupname" to also specify group for daemon to run as. For example: me:me
RUN_AS_USER=""

OPTIONS=""

test -x $LUCENE_SEARCH_DIR/lsearchd || exit 0

test -n "$RUN_AS_USER" && CHUID_ARG="--chuid $RUN_AS_USER" || CHUID_ARG=""

if [ -f "/etc/default/lsearchd" ] ; then
        . /etc/default/lsearchd
fi

. /lib/lsb/init-functions

case "$1" in
  start)
    cd $LUCENE_SEARCH_DIR
    log_begin_msg "Starting Lucene Search Daemon..."
    start-stop-daemon --start --quiet --oknodo --chdir $LUCENE_SEARCH_DIR --background $CHUID_ARG --exec $LUCENE_SEARCH_DIR/lsearchd -- $OPTIONS
    log_end_msg $?
    ;;
  stop)
    log_begin_msg "Stopping Lucene Search Daemon..."
    start-stop-daemon --stop --quiet --oknodo --retry 2 --chdir $LUCENE_SEARCH_DIR $CHUID_ARG --exec $LUCENE_SEARCH_DIR/lsearchd
    log_end_msg $?
    ;;
  restart)
    $0 stop
    sleep 1
    $0 start
    ;;
  reload|force-reload)
    log_begin_msg "Reloading Lucene Search Daemon..."
    start-stop-daemon --stop -signal 1 --chdir $LUCENE_SEARCH_DIR $CHUID_ARG --exec $LUCENE_SEARCH_DIR/lsearchd
    log_end_msg $?
    ;;
  status)
    status_of_proc $LUCENE_SEARCH_DIR/lsearchd lsearchd && exit 0 || exit $?
    ;;
  *)
   log_success_msg "Usage: /etc/init.d/lsearchd {start|stop|restart|reload|force-reload|status}"
   exit 1
esac

exit 0

```Save the text into /etc/init.d/lsearchd and be sure to mark it executable. The daemon  can now be started and stopped with manual calls to init.d/lsearchd. Issue  the following command to configure ubuntu to automatically run the  script on startup.

```

sudo update-rc.d lsearchd defaults

```This should take care of the issue of this init.d script appearing to be non-functional for many.

---

