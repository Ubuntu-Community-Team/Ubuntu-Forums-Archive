---
title: "boot script gets killed"
date: 2009-09-11
forum: General Help
---

### Post by cameramanager on 2009-09-11
Hi

i'm trying to let a application start when booting...
i've got a sym link in /etc/init.d

i've used update-rc.d name defaults 90 to make it start during the boot.

when i boot the script start the program as it should do, however the program is killed a few seconds after it's started.

However when i call the script manually later on the program starts as it is supposed to

I've used exactly the same code on a debian server and there it worked.

Has anyone any idea what might cause this problem?

---

### Post by cameramanager on 2009-09-12
bump

---

### Post by akakingess on 2009-09-12
Just a stab in the dark, but I believe (I'm not in front of my Ubuntu machine right now)  that under the System menu in either Administration or Preferences there is a Startup Applications choice, would that work for you or have you already tried it?

---

### Post by cameramanager on 2009-09-12
tried that, the problem ain't that the program doesn't start, but it gets killed for some reason.

I've changed the program that has to be started to a really simple program that justs prints the time every 100 ms. in i log in and use the initscript to start the program it keeps running, however once it is started during boot, it gets killed within 4 sec.

initscript:

startServer)
    echo -n "starting server"

    touch $SERVER_PID
    chown $SERVER_USER:$SERVER_USER $SERVER_PID
    
    if start-stop-daemon --test --start --pidfile "$SERVER_PID" \
        --user $SERVER_USER --startas "$JAVA_EXE" \
        >/dev/null; then
        
        cd $SCRIPT_DIR
        cp=$(ls $LIB_DIR/*.jar | tr [:space:] ":")
        includes=$cp$MAIN_JAR

        su -p -s /bin/sh $SERVER_USER \
            -c "export LD_LIBRARY_PATH=/home/innovista/server/jprofiler4/bin/linux-x86; ulimit -n 50000; $JAVA_EXE -cp $includes $STARTUP_ARGUMENTS $MAIN_CLASS > $LOG_FILE & echo \$! > $SERVER_PID"
        echo " started."
    
    else
        echo ' (server already running).'
    fi

---

### Post by cameramanager on 2009-09-12
Cleaned up the initscript a bit, so only the really needed is left,
i close the standard out and error in the program, and close the input now in the initscript

startServer)
#    echo -n "starting server"

    touch $SERVER_PID
    chown $SERVER_USER:$SERVER_USER $SERVER_PID
    
#    if start-stop-daemon --test --start --pidfile "$SERVER_PID" \
#        --user $SERVER_USER --startas "$JAVA_EXE" \
#        >/dev/null; then
        
        cd $SCRIPT_DIR
        cp=$(ls $LIB_DIR/*.jar | tr [:space:] ":")
        includes=$cp$MAIN_JAR

        su -p -s /bin/sh $SERVER_USER \
            -c "$JAVA_EXE -cp $includes $STARTUP_ARGUMENTS $MAIN_CLASS <&- > $LOG_FILE & echo \$! > $SERVER_PID"
#        echo " started."
    
#    else
#       echo ' (server already running).'
#    fi
    ;;

the script still works when called manualy, but at boot time its runs for 3 sec, then gets killed

---

