---
title: "dzen2 status bar script"
date: 2009-07-23
forum: General Help
---

### Post by rennis250 on 2009-07-23
Hello,

I am trying to combine a few scripts for dzen2 that I found on the dzen2 wiki.  One was written for bash and the other for zsh, and I might have slipped up in combining and converting everything to a single bash script.  In any event, the problem is not with dzen2, as the script itself does not run properly.  I'm not too keen on bash scripting, but just wondering if anyone had any insight.

```
#!/bin/sh
 
#colors, fonts, pixel setup
BG=#39587f  # dzen backgrounad
FG=#999  # dzen foreground
W=150     # width of the dzen bar
GW=50      # width of the gauge
GFG=#999  # color of the battery gauge
MAINFG=#999 # main foreground color
GH=7       # height of the gauge
GBG=#333  # color of gauge background
X=1080       # x position
Y=1036    # y position
FN='fixed' # font

#battery setup 
STATEFILE='/proc/acpi/battery/BAT0/state' # battery's state file
INFOFILE='/proc/acpi/battery/BAT0/info'   # battery's info file
 
LOWBAT=25        # percentage of battery life marked as low
LOWCOL='#ff4747' # color when battery is low

#time intervals
BATT_INT=5      # time interval in seconds
DATE_INT=1    # date interval
CPU_INT=1    # cpu interval
VOLUME_INT=1    # volume interval
WIRE_INT=3    # wireless interval
ETH_INT=3    # ethernet interval
TIME_INT=1    # main interval
 
#icon path
DZEN_ICONPATH=/home/rennis250/Desktop/dzen2-0.8.5/bitmaps

#date format
DATE_FORMAT='%A, %d.%m.%Y %H:%M:%S'
 
#functions for various stuff
fdate() {
    date +$DATE_FORMAT
}

#fcpu_usage() {}

#setup initializations
DATECOUNTER=$DATE_INT
BATTCOUNTER=$MAIL_INT
CPUCOUNTER=$CPU_INT
VOLUMECOUNTER=$VOLUME_INT
WIRECOUNTER=$WIRE_INT
ETHCOUNTER=$ETH_INT

#start looping!!
while true; do

    if [$DATECOUNTER -ge $DATE_INT]; then
        PDATE=$(fdate)
        DATECOUNTER=0
    fi

    if [$BATTCOUNTER -ge $BATT_INT]; then
        # look up battery's data
        BAT_FULL=`cat $INFOFILE|grep design|line|cut -d " " -f 11`;
        STATUS=`cat $STATEFILE|grep charging|cut -d " " -f 12`;
        RCAP=`cat $STATEFILE|grep remaining|cut -d " " -f 8`;
 
        # calculate remaining power
        RPERCT=`expr $RCAP \* 100`;
        RPERC=`expr $RPERCT / $BAT_FULL`;
 
        # change color if warning is necessary
        if [ $RPERC -le $LOWBAT ]; then GFG=$LOWCOL; fi

        PBATT='^fg($GFG)^i(${DZEN_ICONPATH}/battery.xpm)^p(3)${RPERC}'

        BATTCOUNTER=0
    fi

#    if [$CPUCOUNTER -ge $CPU_INT]; then
#        PCPU=""
#        CPUCOUNTER=0
#    fi
#
#    if [$VOLUMECOUNTER -ge $VOLUME_INT]; then
#        PVOLUME=""
#        VOLUMECOUNTER=0
#    fi
#
#    if [$WIRECOUNTER -ge $WIRE_INT]; then
#        PWIRE=""
#        WIRECOUNTER=0
#    fi
#
#    if [$ETHCOUNTER -ge $ETH_INT]; then
#        PETH=""
#        ETHCOUNTER=0
#    fi

#    print "$PBATT $PCPU $PVOLUME $PWIRE $PETH ^fg(${MAINFG})${PDATE}^fg()"
    print "$PBATT"

    DATECOUNTER=$((DATECOUNTER+1))
    BATTCOUNTER=$((BATTCOUNTER+1))
    CPUCOUNTER=$((CPUCOUNTER+1))
    VOLUMECOUNTER=$((VOLUMECOUNTER+1))
    WIRECOUNTER=$((WIRECOUNTER+1))
    ETHCOUNTER=$((ETHCOUNTER+1))

    sleep $TIME_INT;
done


```And here is the error that it produces on my machine:

```
./dzen_script.sh: 110: [1: not found
[: 110: missing ]
Warning: unknown mime-type for "" -- using "application/octet-stream"
Error: no such file ""
./dzen_script.sh: 110: [2: not found
./dzen_script.sh: 110: [1: not found
Warning: unknown mime-type for "" -- using "application/octet-stream"
Error: no such file ""
./dzen_script.sh: 110: [3: not found
./dzen_script.sh: 110: [2: not found
Warning: unknown mime-type for "" -- using "application/octet-stream"
Error: no such file ""


```Thanks for any help,
Rob

---

