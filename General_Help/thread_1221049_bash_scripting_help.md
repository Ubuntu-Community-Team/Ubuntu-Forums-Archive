---
title: "bash scripting help"
date: 2009-07-23
forum: General Help
---

### Post by yeleek on 2009-07-23
Hi,

Need some help please. This script outputs a good 'whatever' and then the current cpu and memory usage on separate lines.  I'd like all 3 to be on the printed on the same line.  How can I do this?

Thanks

```

#!/bin/bash
time=$(date +%H)
name=$( echo $LOGNAME | sed 's/^./\u&/' )
#echo $name
#echo $time

if [ "$time" -lt 12 ]
then
	echo "Good Morning" $name
	ps aux|awk 'NR > 0 { s +=$3 }; END {print "CPU usage currently at "s"%"}' 
	ps aux|awk 'NR > 0 { s +=$4 }; END {print "Memory usage currently at "s"%"}'
elif [ "$time" -lt 18 ]
then
	echo "Good Afternoon" $name
	ps aux|awk 'NR > 0 { s +=$3 }; END {print "CPU usage currently at "s"%"}' 
	ps aux|awk 'NR > 0 { s +=$4 }; END {print "Memory usage currently at "s"%"}'

elif [ "$time" -lt 24 ]
then
	echo "Good Evening" $name
	ps aux|awk 'NR > 0 { s +=$3 }; END {print "CPU usage currently at "s"%"}' 
	ps aux|awk 'NR > 0 { s +=$4 }; END {print "Memory usage currently at "s"%"}'
fi
```

---

### Post by bacil on 2009-07-23
How about ?

```

#!/bin/bash
time=$(date +%H)
name=$( echo $LOGNAME | sed 's/^./\u&/' )
#echo $name
#echo $time
cpu=`ps aux|awk 'NR > 0 { s +=$3 }`
mem=`ps aux|awk 'NR > 0 { s +=$4 }`

if [ "$time" -lt 12 ]
then
	echo "Good Morning" $name
	echo "CPU: $cpu Memory: $mem"
elif [ "$time" -lt 18 ]
then
	echo "Good Afternoon" $name
	echo "CPU: $cpu Memory: $mem"
elif [ "$time" -lt 24 ]
then
	echo "Good Evening" $name
       echo "CPU: $cpu Memory: $mem"
fi
```

---

### Post by wojox on 2009-07-23
```
#!/bin/bash
time=$(date +%H)
name=$( echo $LOGNAME | sed 's/^./\u&/' )
cpu=$( ps aux|awk 'NR > 0 { s +=$3 }; END {print "CPU usage currently at "s"%"}' )
mem=$( ps aux|awk 'NR > 0 { s +=$4 }; END {print "Memory usage currently at "s"%"}' )

#echo $name
#echo $time

if [ "$time" -lt 12 ]
then
	echo "Good Morning" $name $cpu $mem
	
elif [ "$time" -lt 18 ]
then
	echo "Good Afternoon" $name $cpu $mem

elif [ "$time" -lt 24 ]
then
	echo "Good Evening" $name $cpu $mem
	
fi
```

---

### Post by yeleek on 2009-07-24
Thanks very much for the replies - thats great.

---

