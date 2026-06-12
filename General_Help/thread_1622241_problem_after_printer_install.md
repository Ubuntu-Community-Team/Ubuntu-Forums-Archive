---
title: "problem after printer install"
date: 2010-11-15
forum: General Help
---

### Post by Willardv on 2010-11-15
Hi everyone;
 
I'm a newbie who has flirted with Ubuntu a few times in the past.
 
I've recently installed Kubuntu 10.10 on my Acer Aspire One ZG5 netbook. Everything works pretty well and I'm enjoying it so far.
 
One problem - I have a Lexmark S405 inkjet printer - for which I installed drivers the other day. The install goes fine and the printer does work - but upon next boot, there is an error loading Kate - and then some sort of script editor pops up.
 
Uninstalling the driver package seems to fix the error message but it's back upon re-install. Didn't have this with my Ubuntu VM on my desktop. The printer does still work.
 
How to fix?

---

### Post by Willardv on 2010-11-15
Update - here is the text that Kate displays:

########################################################################
#             (c) Copyright 2009 Lexmark R&D Corporation               #
#                        All rights reserved                           #
########################################################################
#                                                                      #
#  This command lists the model names, queues, uri's and USB numbers   #
#  of printers that are supported and/or attached.                     #
#                                                                      #
########################################################################
fname=~/.lxk_session
pname=~/.lxk_session_pid
lname=/tmp/.lxk_session_$USER
if [ -n "$DBUS_SESSION_BUS_ADDRESS" ]; then
   echo $DBUS_SESSION_BUS_ADDRESS > $fname
   if [ -f $lname ]; then
       rm -rf $lname
   fi
   cp $fname $lname
   chmod ugo+r $lname
   chown $USER:bin $lname
elif [ -f $fname ]; then
    pid=`cat $pname`
    pidfromps=`ps aux | grep -m 1 -E "^$USER.*dbus-daemon.*session.*" | grep -v "grep" | awk '{print $2}'`
    if [ -z "$pidfromps" ]; then
        eval `dbus-launch --sh-syntax --exit-with-session`
        echo $DBUS_SESSION_BUS_ADDRESS > $fname
        echo $DBUS_SESSION_BUS_PID > $pname
        if [ -f $lname ]; then
           rm -rf $lname
        fi
        cp $fname $lname
        chmod ugo+r $lname
        chown $USER:bin $lname
    elif [ $pid -ne $pidfromps ]; then
        rm -rf $fname
        rm -rf $pname
        rm -rf $lname
    else
        if [ -f $lname ]; then
           rm -rf $lname
        fi
        cp $fname $lname
        chmod ugo+r $lname
        chown $USER:bin $lname
    fi
elif [ -z "$BUS_SESSION_BUS_ADDRESS" ]; then
   eval `dbus-launch --sh-syntax --exit-with-session`
   echo $DBUS_SESSION_BUS_ADDRESS > $fname
   chmod ugo+r $fname
   echo $DBUS_SESSION_BUS_PID > $pname
   if [ -f $lname ]; then
       rm -rf $lname
   fi
   cp $fname $lname
   chmod ugo+r $lname
   chown $USER:bin $lname
fi


Here is a screenshot of the error:

---

