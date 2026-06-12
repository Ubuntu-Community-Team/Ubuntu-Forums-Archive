---
title: "Conky change text based on if from script"
date: 2010-03-25
forum: General Help
---

### Post by yeleek on 2010-03-25
Hi,

My conky file declares a color association with this

color5 green

and then after TEXT has this line

```
ISC: ${execi 60 /home/ben/scripts/isc.sh}
```

the isc.sh file has this

```
#!/bin/bash
curl http://isc.sans.org/infocon.txt | sed 'y/abcdefghijklmnopqrstuvwxyz/ABCDEFGHIJKLMNOPQRSTUVWXYZ/' > /tmp/isc

read STATUS < /tmp/isc

if [[ $STATUS == "GREEN" ]]; then
	echo "\${color5}"$STATUS     #GREEN
elif [[ $STATUS == "YELLOW"  ]]; then
	echo "\${color6}"$STATUS   #YELLOW
elif [[ $STATUS == "ORANGE"  ]]; then
	echo "\${color7}"$STATUS   #ORANGE
elif [[ $STATUS == "RED"  ]]; then
	echo "\${color8}"$STATUS  #RED
else echo "\${color9}"$STATUS     #BLUE

fi
```

What gets displayed on the screen when conky runs is 
ISC: ${color5}GREEN

Why is it not displaying GREEN in the green colour?  If I manually type ${color5}GREEN into .conkyrc its fine.

Any ideas?

Thanks

---

### Post by yeleek on 2010-03-25
Fixed it - conky needs execpi not execi.

---

