---
title: "Colorize Text in Konversation"
date: 2010-11-19
forum: General Help
---

### Post by vis.15 on 2010-11-19
Here is a simple script that I created to colorize the text in Konversation. 

```

#!/bin/bash

Server=$1
Target=$2

i=2 #start at $3
argv=("$@")
sp=" "
tn=$#

while [ $i -le $tn ]; do
	text=$text$sp${argv[$i]}
	let i=i+1
done

text=`echo ${text:1}` #remove begging space

#Colors
ccode= #0x03 Color code
White=0 #0x03 0
Black=1 #0x03 1
DkBl=2 #Dark blue x03 2
Green=3 #03 03
Red=4 #03 04
Maroon=5 #03 05

text_len=`echo ${#text}`
i=$text_len
j=0
colorn=2

while [ $i -gt 0 ]; do
	char=`echo ${text:$j:1}` #text:position:length
	let j=j+1
	color_num=`expr $colorn % 16` # mod 16
	
	if [ "$color_num" == "0" ] | [ "$color_num" == "1" ]; then #No white or black
		color_num=2
	fi

	case "$char" in
  	[a-zA-Z]*) #If Letter
  		ctext=$ctext$ccode$color_num$char$ccode$color_num
  		let colorn=colorn+1
  	;;
	*)
		if [ "$char" == "" ]; then 
			char=" "
		fi
		ctext=$ctext$char
	;;
	esac
	
	let i=i-1
done

qdbus org.kde.konversation /irc say $Server "$Target" "$ctext"

```

Notes: When using a question mark (?) konversation turns the question mark into the script's name. When using an asterisk konversation turns it in to all the scrips in the scripts directory.

---

