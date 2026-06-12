---
title: "Getting a program to loop"
date: 2010-01-13
forum: General Help
---

### Post by tom.swartz07 on 2010-01-13
Hi all,

I have a script that changes my background to a real-time satellite shot of the earth.

Heres the script:
```
#!/bin/bash

cd ~/.gnome2/
while [  1 ]; do
	COUNTER=0
	while [  $COUNTER -lt 60 ]; do
		wget http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg -O world.jpg
		temp=$(stat -c%s world.jpg)
		if [[ $temp > 1000 ]]
			then 	rm world_sunlight_Wallpaper.jpg
				mv world.jpg world_sunlight_Wallpaper.jpg
				break
		fi
		sleep 5
        	let COUNTER=COUNTER+1 
	done
	sleep 300
done
```

For some reason, it will not repeat after the set 300 seconds (5 minutes).
How do I get it to loop properly?

---

### Post by falconindy on 2010-01-13
Works fine for me... you might want to check your limits.conf (maybe in /etc/security/) to make sure that there's no hard limit on the amount of time a script can be executing before its killed by the OS.

Other possibility: might just be a matter of opentopia throttling you for hitting that URL too often thinking you're a bot (and you sort of are).

Also, minor cleanup if you don't mind...
```
#!/bin/bash

cd ~/.gnome2/
while [[ 1 ]]; do
	COUNTER=0
	while [[ COUNTER=$[ $COUNTER + 1 ] -lt 60 ]]; do
		wget http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg -O world.jpg
		if [[ $(file world.jpg | grep JPEG) ]]; then
			mv world.jpg world_sunlight_Wallpaper.jpg
			break
		fi
		sleep 5
	done
	sleep 300
done
```

---

### Post by tom.swartz07 on 2010-01-13
> **falconindy said:**
> Works fine for me... you might want to check your limits.conf (maybe in /etc/security/) to make sure that there's no hard limit on the amount of time a script can be executing before its killed by the OS.

Other possibility: might just be a matter of opentopia throttling you for hitting that URL too often thinking you're a bot (and you sort of are).

Also, minor cleanup if you don't mind...
```
#!/bin/bash

cd ~/.gnome2/
while [[ 1 ]]; do
	COUNTER=0
	while [[ COUNTER=$[ $COUNTER + 1 ] -lt 60 ]]; do
		wget http://www.opentopia.com/images/cams/world_sunlight_map_rectangular.jpg -O world.jpg
		if [[ $(file world.jpg | grep JPEG) ]]; then
			mv world.jpg world_sunlight_Wallpaper.jpg
			break
		fi
		sleep 5
	done
	sleep 300
done
```

You might have a point about it getting throttled.... Perhaps i could change it to every 15 minutes. 

Thanks a ton Falconindy. I appreciate the cleanup!

---

