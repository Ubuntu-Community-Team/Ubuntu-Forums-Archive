---
title: "problem with init.d script"
date: 2012-02-21
forum: General Help
---

### Post by MacUsers on 2012-02-21
Dear all,

I'm having a problem running this init.d script, named *sendwol*, which just sends a WOL magic-packet at the time boot to wake up my NAS (also Ubuntu oneiric server). 

```
#!/bin/sh
#
### BEGIN INIT INFO
# Provides:       sendwol
# Required-Start: $remote_fs $local_fs
# Required-Stop:  $remote_fs $local_fs
# Default-Start:  2 3 4 5
# Default-Stop:   0 1 6
# Short-Description: Send WOL to mserv 
### END INIT INFO
#
. /lib/lsb/init-functions

do_start() {
    wol=`which wake-on-lan`
    if [ "$?" -eq 0 ]; then
        $wol mserv
    else
        echo "wake-on-lan not installed"
    fi
    exit
}

do_stop() {
    echo "Action not supported"
    exit
}

case "$1" in
  start )
        do_start
        ;;
  restart|reload|force-reload )
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
  stop )
        do_stop
        ;;
  * )
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

exit 0

```I've already created all the required Sys-V links:

```
# ls -l /etc/rc?.d/* | grep sendwol | awk '{OFS=" ";print $8,$9,$10}'
/etc/rc0.d/K20sendwol -> ../init.d/sendwol
/etc/rc1.d/K20sendwol -> ../init.d/sendwol
/etc/rc2.d/S20sendwol -> ../init.d/sendwol
/etc/rc3.d/S20sendwol -> ../init.d/sendwol
/etc/rc4.d/S20sendwol -> ../init.d/sendwol
/etc/rc5.d/S20sendwol -> ../init.d/sendwol
/etc/rc6.d/K20sendwol -> ../init.d/sendwol

```But it's not working at all. 
_wake-on-lan _is a python script, which works just fine by itself and it works also just fine if I run this init script manually:
```
# /etc/init.d/sendwol start
```but not doing anything during the booting. I'm completely clueless here. Does anyone understand what am I doing wrong? Thanks in advance for your help. Cheers!!

---

### Post by Cheesehead on 2012-02-21
(oops - erroneous post)

---

### Post by MacUsers on 2012-02-22
Just to add the info that, couple of my other init.d scripts works just fine but I cannot make this one work. So any help/suggestion would be appreciated. Cheers!!

---

