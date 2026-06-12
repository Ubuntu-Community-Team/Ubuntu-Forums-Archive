---
title: "Zenity script progress bar"
date: 2010-04-09
forum: General Help
---

### Post by j_arquimbau on 2010-04-09
Hello,

Could someone help me adding a working progress bar to the following secure-deleting script?
```

#!/bin/bash

if [ "$1" = "" ]; then
   exit
fi

zenity --question --title "Borrado Seguro" --text "¿Está seguro de que desea eliminar definitivamente los archivos y/o carpetas? Esta operación puede tardar dependiendo del tamaño de los archivos."
if [ $? = 0 ]; then
   while [ "$1" != "" ]; do
	ans=$(zenity --scale --title "Borrado Seguro" --text "Elija un nivel de seguridad de borrado" --min-value=0 --max-value=3 --value=3 --step 3);echo $ans
	if [ $ans = 0 ]; then
	\rm \-r -v "$1"	
	\rm \-r -v "$1~"
	exit
	fi
		
	if [ $ans = 1 ]; then
	wipe -f -c -r -Q3 -P50 "$1"
	wipe -f -c -r -Q3 -P50 "$1~"
	exit
	fi

	if [ $ans = 2 ]; then
	wipe -f -c -r -Q7 -P50 "$1"
	wipe -f -c -r -Q7 -P50 "$1~"
	exit
	fi

	if [ $ans = 3 ]; then
	wipe -f -c -r -P50 "$1"
	wipe -f -c -r -P50 "$1~"
	exit
	fi
	
	shift 
   done
fi

```

Thank you!

---

### Post by kerry_s on 2010-04-09
why not just add a "zenity --info" before the exit?

example:
zenity --info --text="This drive is finished"
or with time out:
zenity --info --text="Wipe Complete" --timeout="5"

---

### Post by j_arquimbau on 2010-04-09
> **kerry_s said:**
> why not just add a "zenity --info" before the exit?

example:
zenity --info --text="This drive is finished"
or with time out:
zenity --info --text="Wipe Complete" --timeout="5"

That is a good idea,I'm going to try it now. Thank you!

Any way, I'd like a progress bar as the wiping action takes too much time with large files, so you can get an idea of how much time is left... Any idea at this point?

---

### Post by kerry_s on 2010-04-09
well according to the man page it should be as simple as:
\rm \-r -v "$1"	| zenity --progress --pulsate

but that would mean for each command.
better you just rewrite it to call it once, no matter the selected.

---

### Post by j_arquimbau on 2010-04-10
> **kerry_s said:**
> well according to the man page it should be as simple as:
\rm \-r -v "$1"	| zenity --progress --pulsate

but that would mean for each command.
better you just rewrite it to call it once, no matter the selected.

With that command I just get a bar which stays at 0% and doesn't increase...

---

