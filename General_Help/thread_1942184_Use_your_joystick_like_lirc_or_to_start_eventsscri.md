---
title: "Use your joystick like lirc or to start events/scripts"
date: 2012-03-17
forum: General Help
---

### Post by frenchn00b on 2012-03-17
Hi,

I would like to share this possibility to use your joystick with a limited number of packages : only joystick.

here is the code 


```


#!/bin/sh


killall -e jstest 
killall -e jstest 
killall -e jstest  -9 

	

	jstest  --event /dev/input/js0  > $HOME/.js0input & 
	
	
	while [ 1  ] ; do 
	
		JSTAIL=`tail -n 1  $HOME/.js0input` 
		JSVALUE=`  echo "${JSTAIL}" | awk -F "value " ' { print $NF } ' `
		JSBUTTON=`  echo "${JSTAIL}" | awk -F "number " ' { print $2 } ' | awk  -F "," ' { print $1 } '`

		if [  "$JSTAIL_LAST" != "$JSTAIL" ] && [ "$JSVALUE"  != "0" ]   ; then 
			echo "$JSTAIL   -   Value $JSVALUE   -  $JSBUTTON"   
			[ -f  /usr/bin/aplay ]   && aplay -q $HOME/.fvwm/sounds/popup.wav
			
			[ $JSBUTTON -eq 0 ]  && echo "Button 0"  && mplayer $HOME/.fvwm/sounds/numbers/0.wav

			
			
		fi 
	
		JSTAIL_LAST="$JSTAIL"
	done

killall -e jstest 
killall -e jstest 
killall -e jstest 



```

With this script you can start scanning for instance or use it into crontab -e with @REBOOT.

Enjoy coding

---

