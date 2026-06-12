---
title: "Make noip start during boot or login"
date: 2009-12-22
forum: General Help
---

### Post by SSovine on 2009-12-22
I am running 9.10 Karmic Koala.  I am hosting a personal web site from my computer using noip.  What I would like to do is make noip2 start when my system starts.  I have tried setting Ubuntu to automatically login to my username and setting noip2 as a Startup Application, but that didn't work.  I think this is possibly because noip2 requires super-user privileges. 

If I could get noip2 to start on system start, this would be best.  Could this be done using upstart? Also, would I be correct in calling noip2 a service?

---

### Post by SSovine on 2009-12-22
Also, I found this script in the readme.first documentation for noip2:

#######################################################
    #! /bin/sh
    # . /etc/rc.d/init.d/functions    # uncomment/modify for your killproc
    case "$1" in
        start)
        echo "Starting noip2."
        /usr/local/bin/noip2
        ;;
        stop)
        echo -n "Shutting down noip2."
        killproc -TERM /usr/local/bin/noip2
        ;;
        *)
        echo "Usage: $0 {start|stop}"
        exit 1
    esac
    exit 0
    #######################################################

Could this be modified to work on my system?  

I appreciate any help!

---

### Post by SSovine on 2010-02-02
Bump

---

