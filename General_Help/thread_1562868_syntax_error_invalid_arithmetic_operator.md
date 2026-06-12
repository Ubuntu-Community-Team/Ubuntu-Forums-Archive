---
title: "syntax error: invalid arithmetic operator"
date: 2010-08-28
forum: General Help
---

### Post by defy on 2010-08-28
hi

i have this code
   
   > #!/bin/sh
#
# Simple init.d shell script that can to modified to fit your favorite distro
#
# All Rates are in Kbits, so in order to gets Bytes divide by 8
# e.g. 25Kbps == 3.125KB/s
#
# TC=/sbin/tc
# DNLD=64Kbit   # DOWNLOAD Limit
# DWEIGHT=6Kbit # DOWNLOAD Weight Factor ~ 1/10 of DOWNLOAD Limit
# UPLD=64KBit    # UPLOAD Limit
# UWEIGHT=6Kbit  # UPLOAD Weight Factor
# Filter id = {queue id Ex: 11,10} + {2 digits of the end of the ip address}
TC=/sbin/tc
Unit=KBit
Multiply=1
#Variable declaration -->
let DWN_RATE[3]=128*$Multiply
let UPL_RATE[3]=128*$Multiply 
#<-- Variable declaration
tc_start()
{
    #Download Queue -->
    $TC qdisc add dev eth2 root handle 11: cbq bandwidth 100Mbit avpkt 1000 mpu 64
    $TC class add dev eth2 parent 11:0 classid 11:3 cbq rate  ${DWN_RATE[3]}$Unit weight $((${DWN_RATE[3]}/10))$Unit allot 1514 prio 1  avpkt 1000 bounded
    $TC filter add dev eth2 parent 11:0 protocol ip handle 113 fw flowid 11:3
    #<-- Download Queue
    #Upload Queue -->
    $TC qdisc add dev eth0 root handle 10: cbq bandwidth 100Mbit avpkt 1000 mpu 64
    $TC class add dev eth0 parent 10:0 classid 10:3 cbq rate  ${UPL_RATE[3]}$Unit weight $((${UPL_RATE[3]}/10))$Unit allot 1514 prio 1  avpkt 1000 bounded
    $TC filter add dev eth0 parent 10:0 protocol ip handle 103 fw flowid 10:3
       }
tc_stop()
{
    $TC qdisc del dev eth2 root
    $TC qdisc del dev eth0 root
}
tc_restart()
{
    tc_stop
    sleep 1
    tc_start
}
tc_show()
{
    echo ""
    echo "eth2:"
    $TC qdisc show dev eth2
    $TC class show dev eth2
    $TC filter show dev eth2
    echo ""
    echo "eth0:"
    $TC qdisc show dev eth0
    $TC class show dev eth0
    $TC filter show dev eth0
    echo ""
}
case "$1" in
    start)
        echo -n "Starting bandwidth shaping: "
        tc_start
        echo "done"
        ;;
     stop)
        echo -n "Stopping bandwidth shaping: "
         tc_stop
         echo "done"
         ;;
    restart)
        echo -n "Restarting bandwidth shaping: "
        tc_restart
        echo "done"
         ;;
    show)
        tc_show
         ;;
    *)
        echo "Usage: /etc/init.d/tc.sh {start|stop|restart|show}"
         ;;
esac
exit 0

and i have thease Errors:

> ")syntax error: invalid arithmetic operator (error token is "
")syntax error: invalid arithmetic operator (error token is "
'etc/webmin/init/tc.sh: line 21: syntax error near unexpected token `
'etc/webmin/init/tc.sh: line 21: `tc_start()
and i dont know what should i do please help me

i'm sorry for my poor english

plz help me please

thanks , for your helps[IMG]http://ubuntuforums.org/images/icons/icon12.gif[/IMG]

---

