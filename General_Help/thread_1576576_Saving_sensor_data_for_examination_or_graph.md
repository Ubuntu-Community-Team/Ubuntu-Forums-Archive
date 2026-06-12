---
title: "Saving sensor data for examination or graph"
date: 2010-09-17
forum: General Help
---

### Post by fig_wright on 2010-09-17
I was looking for some simply program to save the data produced by lm-sensors or gkrellmd in order to produce graphs and look for potential problems, but couldnt find any. So I wrote a shell-script that works quite well by transforming the output of "sensors" into a table for graphing, and thought it might be useful to others...

I quickly found that the output from sensors is erratic and subject to large noise, and so needs a degree of averaging to be used properly. In the script, shell variables can be set that cause the script to average every written reading for ITER times over INTERVAL seconds. Other than that remember to set the right log directory.

You'll probably tell me now that there's some other software that does this, in which case please do tell :-/ ... Also, happy to receive improvements to it!

```
#!/bin/bash
#=============================================================================
# Script:          save_sensors.sh
# ----------------------------------------------------------------------------
# Script Purpose:  Records sensors data
# ----------------------------------------------------------------------------
# Called by:       User/boot/login
# ----------------------------------------------------------------------------
# Requires:        sensors, sed, cut, tr, date, awk
# ----------------------------------------------------------------------------
# Arguments:       None
# ----------------------------------------------------------------------------
# Script History:
# Ver:  Date:           Author:         Change:
# 1.00  31/08/10        Fig Wright        Initial release
#=============================================================================

# ----------------------------------------------------------------------------
# Set up globals
THIS=$(basename $0)
VER="1.00"
LOGFILE="/root/logs/$(date +%Y%m%d%H%M)sensors.log"
# INTERVAL is the time waited between sensor readings
# ITER is the number of readings to average each data line over
INTERVAL=3
ITER=4
# Set desired output lines from sensors output
START_LINE=3
END_LINE=14
LINES=$((END_LINE-START_LINE+1))

# Start logging

echo "LOG Start $THIS - "$(date) > $LOGFILE

# Trap non-normal exit signals: 1/HUP, 2/INT, 3/QUIT, 15/TERM, ERR
# This lets us know which log files recorded crashes, as they wont have a
# termination line. Try [grep -c LOG *sensors.log] in your logdir to see

trap "echo LOG End $THIS - $(date) >> $LOGFILE; exit" 1 2 3 15 ERR

# Print header row to log

HEADER=$(sensors | sed -n "$START_LINE,${END_LINE}p;$(($END_LINE+1))q" | cut -d":" -f1 | tr "\012" " ")

echo "Timestamp "$HEADER >> $LOGFILE

# Loop LINES-1 times, creating the zero row

ZERO_ROW="0 "
for (( i = 1 ; i < $LINES ; i++ )); do
    ZERO_ROW=$ZERO_ROW"0 "
done

# Loop forever or until we are terminated

while true; do

    SUM_ROW=$ZERO_ROW

# Loop ITER times, waiting INTERVAL seconds each time

    for (( j = 0 ; j < $ITER ; j++ )); do

        sleep $INTERVAL

# Get the sensor data into a row

        DATA_ROW=$(sensors | sed -n "$START_LINE,${END_LINE}p;$(($END_LINE+1))q" | tr -s " " | cut -d" " -f2 | tr "Â°C+\012" " ")

# Add it to the counting row, dividing by the number of iterations

        SUM_ROW=$(echo ${SUM_ROW}${DATA_ROW} | awk -v iter=$ITER '{
                                x = NF/2
                                for (i = 1; i <= x; i++)
                                    printf $i + $(i+x) / iter " "
                                }')

    done

# Write averaged data line to log

    echo $(date +%Y%m%d%H%M%S)" "$SUM_ROW >> $LOGFILE

done

```

---

