---
title: "inactivity reset / reboot for custom kiosk"
date: 2010-04-27
forum: General Help
---

### Post by rightmind on 2010-04-27
What I really need is for a guru out there to help me with this script that after it reboots after the idle time exceeds the threshold. I am aware of all the kiosk software out there, but my work wants my current build to have inactivity. They do not want me to start form scratch :(
Thank you

```
echo "Start of inactive.shl"

threshold=25
log=/home/patron/sidle.log
userid=patron
inactive=`who -a | grep $userid | cut -c 45-46 | sed 's/ //g'`

if [ "$inactive" != "" ]; then

echo "Idle time is: " $inactive

if [ "$inactive" -gt "$threshold" ]; then
echo "Threshold met so issuing shutdown command"
/sbin/shutdown -r now
else
echo "Bellow threshold"
fi
else
echo "Idle time is: 0"
fi

echo "Ending"
```

---

