---
title: "bash hell , removing &quot; from a strings"
date: 2009-06-28
forum: General Help
---

### Post by xpd259 on 2009-06-28
im writing a bash script and i'm stuck

the out put of a dialog menu is

echo $select
"foo" "bar" "lemon" cheese"

while I need
$foo $bar $lemon $cheese

and very new to bash scripting and i've no idea how to do this :(
any help would be fantastic 




```
dialog --backtitle "Enable / Disable Tags" \
		--no-cancel --title "CHECKLIST BOX" \
	        --checklist "Hi, blah blah fill me in" 25 61 15 \
        	"$CITY"  "$CITY_TAG" off \
         	"$COPYRIGHT"    "$COPYRIGHT_TAG" off \
        	"Orange" "Yeah, that's juicy." off \
        	"Chicken"    "Normally not a pet." off \
        	"Cat"    "No, never put a dog and a cat together!" off\
        	"Fish"   "Cats like fish." off \
        	"Lemon"  "You know how it tastes." on 2> $tempfile2

	retval=$?

	enable=`cat $tempfile2`

echo $enable
```

---

