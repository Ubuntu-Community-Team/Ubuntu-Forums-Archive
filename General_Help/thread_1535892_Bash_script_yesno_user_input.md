---
title: "Bash script yes/no user input"
date: 2010-07-21
forum: General Help
---

### Post by J V on 2010-07-21
Trying to make a bash script that will ask a user weather they want to do something or not: Need to invert the boolean on the until loop and get the second if to use "And" syntax (Just for the sake of learning)```
loop=true
until !$loop; do
    echo -n "Do you want to block advertisements and potential malware with a hosts file? [y/n] "
    read input
    if [ -n "`echo "$input" | grep -i [ny]`" ]; then # If theres a y or n in the answer
        if [ -n "`echo "$input" | grep -i y`" -a -n "`echo "$input" | grep -i n`" ]; then # If theres a y but no n
            echo "Bingo"
        fi
    loop=false #Finish the loop no matter which answer
    fi
echo -n ""
done
```

---

### Post by J V on 2010-07-23
bump

---

### Post by prodigy_ on 2010-07-23
I use the following if I need a simple y/n choice: ```
#!/bin/sh

f_Choice () {
  # Reads and interprets a single keypress.
  OLD_STTY=$(stty -g)
  stty -icanon iuclc -echo min 1 time 0
  while	:
  do
	U_ANSWER=$(dd bs=1 count=1 2>/dev/null)
	case $U_ANSWER in
	  $1|$2) 
		printf "%s\n" "$U_ANSWER" 
		RET_VAL=0
		test x"$U_ANSWER" = x"$2" && RET_VAL=1
		stty "$OLD_STTY"
		return $RET_VAL
		;;
	  *)
		;;
	esac
  done
}
```
And then **f_Choice y n** will totally ignore anything except "Y", "N" or "Ctrl+C". Obviously, "Y" returns 0, and "N" returns 1.

---

### Post by J V on 2010-07-23
That's nice but I'm looking for something a bit simpler...

Would you know how to use negative booleans (Found, needed a space) :
```
! $bool
```And use 'and' in an if statement? (Also needed a space, bash is so sensitive...)```

if [[ -n "`echo "$input" | grep -i y`"]] && [[-n "`echo "$input" | grep -i n`" ]];
```

---

