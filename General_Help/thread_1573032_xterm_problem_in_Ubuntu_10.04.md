---
title: "xterm problem in Ubuntu 10.04"
date: 2010-09-12
forum: General Help
---

### Post by tdnghia89 on 2010-09-12
Hi, I am new to Linux. When I run a Borealis application mytest with command 'runtest mytest', the 'locale not supported by Xlib' error comes up:

nghiatran@nghiatran-desktop:~/borealis/test/simple$./runtest mytest
xterm -T Borealis@127.0.0.1:15000 -geometry 80x10+20+600 -e ../..//src/src/borealis -d 127.0.0.1:15000
One processing node (Borealis) started.
Warning: locale not supported by Xlib, locale set to C
Starting mytest
Mytest started
nghiatran@nghiatran-desktop:~/borealis/test/simple$ xterm -T mytest -geometry 200x30+200+30 -e .//mytest
Warning: locale not supported by Xlib, locale set to C

There should be two windows opening. However I only see them appear and quickly quit. Does anybody know how to solve this problem. I really appreciate your help.

---

### Post by tdnghia89 on 2010-09-12
upz!

---

### Post by tdnghia89 on 2010-09-12
Using locale, I got this result :

LANG=en_SG.utf8
LC_CTYPE="en_SG.utf8"
LC_NUMERIC="en_SG.utf8"
LC_TIME="en_SG.utf8"
LC_COLLATE="en_SG.utf8"
LC_MONETARY="en_SG.utf8"
LC_MESSAGES="en_SG.utf8"
LC_PAPER="en_SG.utf8"
LC_NAME="en_SG.utf8"
LC_ADDRESS="en_SG.utf8"
LC_TELEPHONE="en_SG.utf8"
LC_MEASUREMENT="en_SG.utf8"
LC_IDENTIFICATION="en_SG.utf8"
LC_ALL=


Does anybody know what is wrong ?

---

### Post by itcotbtoemik on 2010-09-12
There's three places to look - xterm itself, library dependencies
and borealis.  If you have one window up, then it's likely in the
third of those.  The locale problem is likely a missing shared
library used by xterm.  I seem to recall reading reports that
this may be libSM or libICE.

---

### Post by tdnghia89 on 2010-09-12
This is the contest of the runtest script:

```
 # Modify this variable to 1 or 2 if you want to see more debug messages
export LOG_LEVEL="2"

if [ $# -lt 1 ]
then
    echo "To run the single site application type: runtest mytest"
    echo "To run the distributed application type: runtest mytestdist"
    echo "... and when you want to stop everything type: runtest stop"
    exit 0
fi
    
# What to start
what=$1

# --------------------------------------------------
IP="127.0.0.1"

# Looking for BOREALIS_HOME environment variables 
# These variables give the top level location of all the source code. If they are not
# defined, assign them some reasonable defaults
BOREALIS_HOME=${BOREALIS_HOME:-"../../"}
APPS_HOME="./"

# Set the port numbers 
HEAD_PORT=35000
BOREALIS_PORT1=15000
BOREALIS_PORT2=17000

# --------------------------------------------------
# Everything else below should get set automatically
# --------------------------------------------------
BOREALIS_SRC_HOME=${BOREALIS_HOME}/src/src

case "${what}" in 

    # --------------------------------------------------
    # Basic targets
    # --------------------------------------------------
    head)
        echo "Starting the global catalog (Head)..."
        BINDING=${IP}:${HEAD_PORT}
        eval echo "xterm -T HEAD@${BINDING} -geometry 80x10+20+200 -e ${BOREALIS_HOME}/tool/head/BigGiantHead"
        xterm -T HEAD@${BINDING} -geometry 80x10+20+200 -e sh -c "${BOREALIS_HOME}/tool/head/BigGiantHead 2>&1 |tee head-${BINDING}.log"  &
        echo "Global catalog (Head) started."
        ;;

    borealis)
        echo "Starting one processing node (Borealis)"
        BINDING=${IP}:${BOREALIS_PORT1}
        if [ $# -gt 1 ]
        then
            BINDING=$2       # Some other IP:port combination
            OTHER_OPTIONS=$3 # There might be no other options
        fi
        eval echo "xterm -T Borealis@${BINDING} -geometry 80x10+20+600 -e ${BOREALIS_SRC_HOME}/borealis -d ${BINDING} ${OTHER_OPTIONS}"
        xterm -T Borealis@${BINDING} -geometry 80x10+20+600 -e sh -c "${BOREALIS_SRC_HOME}/borealis -d ${BINDING} ${OTHER_OPTIONS} 2>&1 |tee borealis-${BINDING}.log" &
        echo "One processing node (Borealis) started."
        ;;

    mytestapp)
        echo "Starting mytest"
        eval echo "xterm -T mytest -geometry 200x30+200+30 -e ${APPS_HOME}/mytest 2>&1 |tee mytestout.log" &
        xterm -T mytest -geometry 200x30+300+20 -e sh -c "${APPS_HOME}/mytest 2>&1 |tee mytest.log" &
        echo "Mytest started"
        ;;




```

Based on this script, there should be 2 xterm windows opening but they just flash up and disappear. I also the Borealis installation has no problem. Maybe something is missing.

---

### Post by tdnghia89 on 2010-09-12
I also cannot find the /usr/X11R6/include/X11 directory. It seems that this directory does not exist in Ubuntu 10.04. Is it related to my problem ?

---

### Post by tdnghia89 on 2010-09-12
I think I just found the cause of the problem. The mytest.log says: 
/home/nghiatran/borealis/test/simple/.libs/lt-mytest: error while loading shared libraries: libNMSTL.so.0: cannot open shared object file: No such file or directory

It is strange because libNMSTL.so.0 file is in /home/nghiatran/install_nmstl/lib and I have export this directory to LD_LIBRARY_PATH. Does anybody know how to fix this ?

---

### Post by itcotbtoemik on 2010-09-13
If Ubuntu has installed xterm with setuid permissions, then
the system unsets LD_LIBRARY_PATH.  If that's the case, you
can work around that by making the "xterm -e" run a script that
sets LD_LIBRARY_PATH, and in turn passes its arguments to run
whatever you need, e.g.,

#!/bin/sh
LD_LIBRARY_PATH={whatever} "$@"

---

