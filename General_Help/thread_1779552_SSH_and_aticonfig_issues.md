---
title: "SSH and aticonfig issues"
date: 2011-06-10
forum: General Help
---

### Post by DJeX on 2011-06-10
Hello, I have ssh installed on a Ubuntu box and I want to run a script I wrote remotely through ssh. The script accesses aticonfig and returns the information requested ex. temp, fan speed, clock speed.

If I log into the Ubuntu box with "ssh 192.168.0.120 -l username" and run the script it works fine but when I go to run the script like this "ssh username@192.168.0.120 bash /home/username/script.sh temp 0" aticonfig throws this error:

```
aticonfig: This program must be run as root when no X server is active
```

I'm not sure why this is any different than logging in and running the script. I know in order to run aticonfig you need to run it from the current logged in X org account.

I need it to run with "ssh username@192.168.0.120 bash /home/username/script.sh temp 0" so I can log the results in a database on my web server.

Can any one help?

If it helps this is my script:
```
#!/bin/bash
 
if [ "$1" = "" ]
then
        echo "Usage: $0 <command> <gpu #>"
        echo "Commands:"
        echo "  temp - get gpu temperature in C"
        echo "  load - get gpu load in %"
        echo "  clock- get current clock in MHz"
        echo "  all  - get temp/load/clock for adapter #"
        echo "GPU # - this is the adapter number that you would use with aticonfig"
fi
 
COMMAND=$1
GPU=$2
SUDO="sudo -u djex"
ATICONFIG="$SUDO /usr/bin/aticonfig"
 
if [ "$COMMAND" = "temp" ]
then
        X=`$ATICONFIG --odgt --adapter=$GPU | grep Temperature | awk '{print $5}'`
        X=${X/\.*}
        echo $X
elif [ "$COMMAND" = "fan" ]
then
        X=`$ATICONFIG --pplib-cmd "get fanspeed $GPU" | grep 'Fan Speed' | awk '{gsub(/%/,"",$4); print $4}'`
        X=${X/\.*}
        echo $X
elif [ "$COMMAND" = "load" ]
then
        X=`$ATICONFIG --odgc --adapter=$ATICONFIG_ADAPTER_ID | grep 'GPU load' | awk '{gsub(/%/,"",$4); print $4}'`
        X=${X/\.*}
        echo $X
elif [ "$COMMAND" = "core-clock" ]
then
        X=`$ATICONFIG --odgc --adapter=$ATICONFIG_ADAPTER_ID | grep 'Current Clocks' | awk '{print $4}'`
        X=${X/\.*}
        echo $X
elif [ "$COMMAND" = "mem-clock" ]
then
	Y=`$ATICONFIG --odgc --adapter=$ATICONFIG_ADAPTER_ID | grep 'Current Clocks' | awk '{print $5}'`
	Y=${Y/\.*}
        echo $X
elif [ "$COMMAND" = "all" ]
then
        X=`$ATICONFIG --odgt --adapter=$GPU | grep Temperature | awk '{print $5}'`
        X=${X/\.*}
        echo "TEMP for $GPU is $X C"
        X=`$ATICONFIG --odgc --adapter=$ATICONFIG_ADAPTER_ID | grep 'GPU load' | awk '{gsub(/%/,"",$4); print $4}'`
        X=${X/\.*}
        echo "LOAD for $GPU is $X %"
	X=`$ATICONFIG --pplib-cmd "get fanspeed $GPU" | grep 'Fan Speed' | awk '{gsub(/%/,"",$4); print $4}'`
        X=${X/\.*}
	echo "FAN SPEED for $GPU is $X %"
	X=`$ATICONFIG --odgc --adapter=$ATICONFIG_ADAPTER_ID | grep 'Current Clocks' | awk '{print $4}'`
        X=${X/\.*}
	Y=`$ATICONFIG --odgc --adapter=$ATICONFIG_ADAPTER_ID | grep 'Current Clocks' | awk '{print $5}'`
	Y=${Y/\.*}
        echo "Current Clock for Adapter $GPU is Core: $X MHz Memory: $Y MHz"
elif [ "$COMMAND" = "adapters" ]
then
        $ATICONFIG --lsa
fi
```

---

