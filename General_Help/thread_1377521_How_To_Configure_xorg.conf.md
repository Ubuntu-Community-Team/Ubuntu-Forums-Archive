---
title: "How To: Configure xorg.conf"
date: 2010-01-10
forum: General Help
---

### Post by phenest on 2010-01-10
Ok. Its been asked many times "Is there a tool to help me configure the xorg.conf to make it easier?", or to that effect. So, here it is.

This is a bash script intended to aid everyone, novice and expert alike, to create a xorg.conf file from scratch without needing any prior knowledge except for creating and running bash scripts.

It basically works by providing you with a menu. You select an option from that menu depending on what you want to do.

An example: You have no xorg.conf file and would like to build one that has the nvidia driver setup. Choose option 6 (Add line to Section) and you will be given a list of possible options to add. Look for the nvidia driver and enter the corresponding number on the left. The script will add that line to the correct Section for you. If the Section does not exist, it will create that too. Heck, if the xorg.conf file doesn't exist, it'll make one of those as well.

One thing to bear in mind: this will only create/edit a xorg.conf file that is in the same directory as this script. This is so it doesn't mess with the one you're currently using. If you want to edit the one in /etc/X11, then you will need to make a copy and use that instead.

One thing this tutorial does not teach, is how to use the terminal, but I will give as much precise information as I can.

Off we go then. Create an empty document in your /home folder called xorg.sh and paste this into it:
```
#!/bin/bash

options=('Monitor' '\tIdentifier\t"Configured Monitor"' 'Monitor' '\tOption\t"RandRRotation"\t"On"' 'Screen' '\tIdenifier\t"Configured Screen"' 'Screen' '\tMonitor\t"Configured Monitor"' 'Screen' '\tDevice\t"Configured Video Device"' 'Screen' '\tDefaultDepth\t24' 'Module' '\tLoad\t"glx"' 'Device' '\tIdentifier\t"Configured Video Device"' 'Device' '\tDriver\t"nvidia"' 'Device' '\tOption\t"NoLogo"\t"False"' 'Dummy' '\tOption\t"Something"')

xorg() {
	IFS=$'\n'
	cat xorg.conf
	unset $IFS
}

list() {
	xc=(`xorg`)
	l=0
	while [ $l -lt ${#xc[@]} ]; do
		li=${xc[$l]}
		[ ${li:0:7} == "Section" ] && echo $li
		let l++
	done
}

new() {
	xc=(`xorg`)
	l=0
	while [ $l -lt ${#xc[@]} ]; do
		[ ${xc[$l]} == "Section \"$1\"" ] && echo -e "Section \"$1\" already exists" && return
		let l++
	done
	echo -e "Adding Section \"$1\""
	echo -e "Section \"$1\"\nEndSection" >> xorg.conf
}

delete() {
	xc=(`xorg`)
	l=0
	while [ $l -lt ${#xc[@]} ]; do
		[ ${xc[$l]} == "Section \"$1\"" ] && break
		let l++
	done
	[ $l -eq ${#xc[@]} ] && echo -e "Section \"$1\" not found" && return
	echo -e "Deleting Section \"$1\""
	rm xorg.conf
	n=0
	while [ $n -lt $l ]; do echo ${xc[$n]} >> xorg.conf; let n++; done
	while [ ${xc[$n]} != "EndSection" ]; do let n++; done
	let n++
	while [ $n -lt ${#xc[@]} ]; do echo ${xc[$n]} >> xorg.conf; let n++; done
}

sections() {
	n=0
	l=0
	while [ $n -lt ${#options[@]} ]; do
		echo -e "$l\t"${options[$n]}"...\t"${options[$((n+1))]}
		let n+=2
		let l++
	done
}

show() {
	xc=(`xorg`)
	l=0
	while [ $l -lt ${#xc[@]} ]; do
		[ ${xc[$l]} == "Section \"$1\"" ] && break
		let l++
	done
	[ $l -eq ${#xc[@]} ] && echo -e "Section \"$1\" not found" && return 0
	[ -z $2 ] && echo -e "\t"${xc[$l]}
	let l++
	r=$l
	n=0
	while [ ${xc[$l]} != "EndSection" ]; do
		[ -z $2 ] && echo -e "$n\t"${xc[$l]}
		let l++
		let n++
	done
	[ -z $2 ] && echo -e "\t"${xc[$l]} || [ $2 == "l" ] && r=$l
	return $r
}

remove() {
	show $1 $2 1
	l=$?
	xc=(`xorg`)
	l=$(($l+$2))
	n=0
	echo -e "Removing line $2 from Section \"$1\": ${xc[$l]}"
	rm xorg.conf
	while [ $n -lt ${#xc[@]} ]; do
		[ $n != $l ] && echo ${xc[$n]} >> xorg.conf
		let n++
	done
}

add() {
	dv=${options[$(($1*2))]}
	op=${options[$(($1*2+1))]}
	show $dv "l"
	l=$?
	[ $l -lt 1 ] && new $dv && show $dv "l" && l=$?
	echo -e "Adding$op\nto Section \"$dv\""
	xc=(`xorg`)
	rm xorg.conf
	n=0
	while [ $n -lt $l ]; do
		echo ${xc[$n]} >> xorg.conf
		let n++
	done
	echo -e $op >> xorg.conf
	while [ $n -lt ${#xc[@]} ]; do
		echo ${xc[$n]} >> xorg.conf
		let n++
	done
}

[ ! -f xorg.conf ] && echo "Creating new empty xorg.conf file" && echo -e "# This was created using the xorg.sh script\n# found at ubuntuforums.org\n# This script was written by phenest\n#\n" >> xorg.conf
echo -en "1. List Sections in xorg.conf\t2. Add new Section\n3. Remove Section\t\t4. Show Section contents\n5. Remove line from Section\t6. Add line to Section\nChoose: "
read a
case $a in
	1)	list;;
	2)	echo -n "Enter Section name to add: "; read b; new $b;;
	3)	echo -n "Enter Section to remove: "; read b; delete $b;;
	4)	echo -n "Enter Section name: "; read b; show $b;;
	5)	echo -n "Enter Section name: "; read b; echo -n "Enter line no. "; read c; remove $b $c;;
	6)	sections; echo -n "Which of these to add: "; read b; add $b;;
esac
```
...and save it. Then you can either use the script to create a new xorg.conf (which it does automatically when it starts if one does not exist), or you can copy the one from /etc/X11 if it exists:
```
cp /etc/X11/xorg.conf xorg.conf
```
When you're done, copy it back to /etc/X11:
```
sudo cp xorg.conf /etc/X11/xorg.conf
```

This script is by no means perfect, but it does work. It not complete either, that is, there are many sections and options to add, so I have only provided the ones I use on my laptop. Please feel free to post as many options as possible so I can add them to this script. To add your own, the sections and option are added as:
'Section' 'Option' 'Section' 'Option' etc...
...into the options array. I've used \t for tabulation, but you could use spaces instead.

Have fun.

---

