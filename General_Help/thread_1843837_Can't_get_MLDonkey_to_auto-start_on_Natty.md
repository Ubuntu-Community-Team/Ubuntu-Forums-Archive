---
title: "Can't get MLDonkey to auto-start on Natty"
date: 2011-09-14
forum: General Help
---

### Post by megacrypto on 2011-09-14
Im trying to make mldonkey 3.1.0 auto-start when my system boots. I used to have a script that does that but with the upgrade of both ubuntu (from 10.04) and mldonkey (from 3.0.1) this script does not work anymore.

This was the script:
```

#! /bin/sh
# Written by Lorenz Bauer
# Feel free to redistribute / modify
set -e

. /lib/lsb/init-functions

if [ -f /etc/default/mldonkey ]; then
   . /etc/default/mldonkey
fi

BINARY="/usr/bin/mlnet"
if [ ! -x "$BINARY" ]; then
   log_failure_msg "MLDonkey executable not found!"
   exit 0
fi

if [ ! -n "$MLNET_DIR" ]; then
   MLNET_DIR="/home/user/.mldonkey"
fi

if [ ! -d "$MLNET_DIR" ]; then
   log_failure_msg "Directory '$MLNET_DIR' doesn't exist!"
   exit 0
fi

case "$1" in
  start)
   log_begin_msg "Starting MLDonkey core..."

   local MLNET_ARGS=""
   if [ -n "$MLNET_USER" ]; then
      MLNET_ARGS="-run_as_user $MLNET_USER"
   fi

   local SSD_ARGS=""
   if [ -n "$MLNET_GROUP" ]; then
      SSD_ARGS="-g $MLNET_GROUP"
   fi

   MLDONKEY_DIR="$MLNET_DIR" start-stop-daemon --start --pidfile "$MLNET_DIR/mlnet.pid" --exec "$BINARY" -b $SSD_ARGS -- -pid "$MLNET_DIR" $MLNET_ARGS || log_end_msg 1
   log_end_msg 0
   ;;
  stop)
   log_begin_msg "Stopping MLDonkey core..."
   start-stop-daemon --stop --oknodo --pidfile "$MLNET_DIR/mlnet.pid" || log_end_msg 1
   log_end_msg 0
   ;;

  restart)
   log_begin_msg "Restarting MLDonkey core..."
   $0 stop 2>&1 > /dev/null || log_end_msg 1
   sleep 1
   $0 start 2>&1 > /dev/null || log_end_msg 1
   log_end_msg 0
   ;;

  *)
   log_success_msg "Usage: $0 {start|stop|restart}"
   exit 1
esac

exit 0

```

and this is how i got it to work:
```

sudo rm /etc/init.d/mldonkey-server
sudo cp mldonkey-server /etc/init.d
sudo chmod +x /etc/init.d/mldonkey-server
sudo update-rc.d mldonkey-server start 98 2 3 4 5 . stop 20 0 1 6 .

```

and this is how i installed mldonkey:
```

sudo apt-get install ssh cvs ocaml-nox ocaml-native-compilers
cvs -d:pserver:anonymous@cvs.savannah.nongnu.org:/sources/mldonkey co -P mldonkey
cd mldonkey
./configure
make
sudo make install

```

as per the instructions on their page [[http://mldonkey.sourceforge.net/CompilationProblems#Installation_instructions_for_Ubuntu](http://mldonkey.sourceforge.net/CompilationProblems#Installation_instructions_for_Ubuntu)]

help will be very much appreciated ... thanks

---

