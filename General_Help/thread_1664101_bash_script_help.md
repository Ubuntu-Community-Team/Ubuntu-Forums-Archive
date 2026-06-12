---
title: "bash script help"
date: 2011-01-10
forum: General Help
---

### Post by brandonhon on 2011-01-10
i am trying to make the following script download at random times. i thought if i added a line where a random number was picked and then added to a variable say rTME and then call sleep $rTME it would work. instead it just sleeps indefinitely. any suggestions, here is what i have so far.

```
#servs - list of proxy servers
SERVS=`cat servs`
#number of seconds for random sleep
TME=14401

for i in $SERVS
	do
		#pick a random number from TME
		let "rTME = $RANDOM % $TME"
		
		#i - server picked from list, export to wget proxy setting
		export http_proxy=$i
		
		#wget - util to download from web -t 2 tries @ serv -T 90 timeout
        wget -t 2 -T 90 --proxy http://youlinkhere.zip
        
        #sleep rTME
        sleep $rTME
done

```

---

### Post by TeoBigusGeekus on 2011-01-10
> **brandonhon said:**
> 
```

		let "rTME = $RANDOM % @TME"

```

Shouldn't that be
```
let "rTME = $RANDOM % $TME"
```

---

### Post by brandonhon on 2011-01-10
oops my mistake, that is what i have in my code. still for some reason it sleeps indefinitely.

---

### Post by TeoBigusGeekus on 2011-01-10
Have you checked the value of rTME before invoking the sleep command?
Comment out the sleep line and put
```
echo $rTME
```
instead to see the resulting value.

---

### Post by brandonhon on 2011-01-10
i have and rTME is always an integer between the value specified in TME. here is an example of the output using:

```
echo "ip is: $i\nsleep time is: $rTME\n\n"
```


ip is: 173.22.192.161:8085
sleep time is: 83


ip is: 98.212.33.73:8088
sleep time is: 13162


ip is: 160.79.35.27:80
sleep time is: 5009


ip is: 208.66.145.233:8080
sleep time is: 5276

---

### Post by TeoBigusGeekus on 2011-01-10
For example, when I run
```
#!/bin/bash
TME=14401
let "rTME = $RANDOM %$TME"
echo $rTME
```
the first value I get is 13423, which is 13423/3600~4hours.
Are you sure you've waited for that long?

---

### Post by brandonhon on 2011-01-10
i always check the time the last down load ended and then go from there. so if the last download ended at 13:48.39 then it should start a new download at roughly 17:48.39. it never does for some reason, it just hangs.

---

### Post by brandonhon on 2011-01-11
curious, but does bash have a timeout. or does sleep have a maximum. i can't find anything about either. just don't know why my code isn't working.

---

