---
title: "need help with  missing LSB information"
date: 2011-11-23
forum: General Help
---

### Post by bittug on 2011-11-23
i had this script added i get this error any help please


update-rc.d: warning: /etc/init.d/fslb missing LSB information



#!/bin/bash

case "$1" in
        start)
                echo "Starting Fireshare Load Balancer..."
                /usr/fslb/restart
                echo "Done!"
                ;;
        stop)
                echo "Stopping Fireshare Load Balancer..."
                /usr/fslb/stop
                echo "Done!"
                ;;
        restart|reload|force-reload)
				/usr/fslb/restart
                echo "Done!"
                ;;
        *)
                echo "Usage: /etc/init.d/fslb {start|stop|restart|reload}"
                exit 1
esac
exit 0

---

### Post by jpeegill on 2012-01-30
i request u plz give the link where u laod software
"fireshare load balancer"

---

### Post by catafesta on 2012-12-11
plis link for  Fireshare Load Balancer

---

### Post by rnerwein on 2012-12-11
> **bittug said:**
> i had this script added i get this error any help please


update-rc.d: warning: /etc/init.d/fslb missing LSB information



#!/bin/bash

case "$1" in
        start)
                echo "Starting Fireshare Load Balancer..."
                /usr/fslb/restart
                echo "Done!"
                ;;
        stop)
                echo "Stopping Fireshare Load Balancer..."
                /usr/fslb/stop
                echo "Done!"
                ;;
        restart|reload|force-reload)
                /usr/fslb/restart
                echo "Done!"
                ;;
        *)
                echo "Usage: /etc/init.d/fslb {start|stop|restart|reload}"
                exit 1
esac
exit 0
hi 
is this not windows stuff ?
give me the output of: file fslb

---

