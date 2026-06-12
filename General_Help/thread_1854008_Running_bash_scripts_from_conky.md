---
title: "Running bash scripts from conky"
date: 2011-10-03
forum: General Help
---

### Post by layr on 2011-10-03
What's the deal with it? If the script is simply executed - everything works. When it's ran via conky using
```
${execi 60 sh ~/.scripts/script1.sh}
```
conky finds everything wrong.

Bash script:
```
#/bin/bash
# Set startup values:
delete_loop=1
current_mins=$(date -u "+%M")
current_hours=$(date -u "+%H")
if [ $current_hours = 00 ];then
   current_hours=24
fi
metar_hours_pre=$(cat ~/.conky/METAR/.EETU.txt)
metar_hours=$(echo $metar_hours_pre|cut -c12-13)

# The script itself:

if [[ $(echo {50..59}) =~ $current_mins ]] && (( 10#$metar_hours == $((10#$current_hours-1)) )) || ! [ 10#$current_hours = 10#$metar_hours ] && ! (( 10#$metar_hours == $((10#$current_hours-1)) ));then
	if ping -c 1 www.google.com > /dev/null 2>&1;then
		curl -s 'http://weather.noaa.gov/pub/data/observations/metar/stations/EETU.TXT' > ~/.conky/METAR/.EETU.txt
		metar_hours_pre=$(cat ~/.conky/METAR/.EETU.txt)
		metar_hours=$(echo $metar_hours_pre|cut -c12-13)
		if ! [[ $(echo {50..59}) =~ $current_mins ]] && (( 10#$metar_hours == $((10#$current_hours-1)) )) || [ 10#$current_hours = 10#$metar_hours ]; then
			> ~/.conky/METAR/.new_EETU.dat
		else
			rm ~/.conky/METAR/.new_EETU.dat
		fi
		> ~/.conky/METAR/.connection_check_EETU.dat
	else
		if [ -f ~/.conky/METAR/.connection_check_EETU.dat ]; then 
		    delete_loop=0
		fi	
		if [ $delete_loop = 0 ]; then
			   echo "No connection." > ~/.conky/METAR/.EETU.txt
			   rm ~/.conky/METAR/.connection_check_EETU.dat
			   rm ~/.conky/METAR/.new_EETU.dat
			   delete_loop=1
		fi
	fi
fi
```
And error:

```
/home/laur/.scripts/METAR_scripts/EETU.sh: 39: [[: not found
/home/laur/.scripts/METAR_scripts/EETU.sh: 39: arithmetic expression: expecting EOF: "10#17-1"
/home/laur/.scripts/METAR_scripts/EETU.sh: 39: [[: not found
/home/laur/.scripts/METAR_scripts/EETU.sh: 39: arithmetic expression: expecting EOF: "10#17-1"
rm: cannot remove `/home/laur/.conky/METAR/.new_EETU.dat': No such file or directory

```
Seems as if those long lines won't go through. I read others found solution by putting variables between quotation marks, but that didn't work for me.

---

### Post by sisco311 on 2011-10-03
sh is NOT bash. In Ubuntu, sh is a symlink to dash.

---

### Post by layr on 2011-10-03
Again you are correct. Luckily (or not) bash and dash are quite similar, i have been running multiple scripts using sh command:D

Btw, does the ! statement have to be always inside brackets? It seems as sometimes it may be in front of brackets, other times function wouldn't work if ! wasn't inside.

e.g. if ! [[ $var1 == $var2 ]] || [[ ! $var3 == $var4 ]]

Edit: finally found - ! has to be INSIDE the brackets.

---

