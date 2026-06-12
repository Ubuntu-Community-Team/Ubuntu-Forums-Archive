---
title: "Scheduling a script to run does not happen."
date: 2011-03-23
forum: General Help
---

### Post by Silvernail on 2011-03-23
I can not get 'crontab' to work.
Below is the results of 'crontab -e':
```

10 * * * * /usr/bin/sigrot
0 18 * * 5 /usr/bin/tff-meeting-mail.sh
36 19 * * * /home/dave/wakeup

```

Line 1 works properly and has for 2 years or more.

Line 2 worked 1 time and never again. The code snippet is rather long but I will post anyway.
```

#!/bin/bash
whichmonth=$(date | awk -F" " '{print$2}')
if [ $whichmonth = 'Jan' ]; then
	whichFri=22;
elif [ $whichmonth = 'Feb' ]; then
	whichFri=19;
elif [ $whichmonth = 'Mar' ]; then
	whichFri=25;
elif [ $whichmonth = 'Apr' ]; then
	whichFri=22;
elif [ $whichmonth = 'May' ]; then
	whichFri=27;
elif [ $whichmonth = 'Jun' ]; then
	whichFri=24;
elif [ $whichmonth = 'Jul' ]; then
	whichFri=22;
elif [ $whichmonth = 'Aug' ]; then
	whichFri=26;
elif [ $whichmonth = 'Sep' ]; then
	whichFri=23;
elif [ $whichmonth = 'Oct' ]; then
	whichFri=21;
elif [ $whichmonth = 'Nov' ]; then
	whichFri=25;
elif [ $whichmonth = 'Dec' ]; then
	whichFri=24;
fi
thisFri=$(date | awk -F" " '{print$3}')
if [ "$thisFri" = "$whichFri" ]; then
	echo "send email";
	cd /home/dave/tffrobot/
	./meeting-send.sh
	exit 0
fi
	echo "not today";
exit 0

```

Line 3 worked once and never again.
```

mplayer /media/seagate_/CarolinaChocolateDrops/memphis-breaddown-02.mp3

```

I can call both './meeting-send.sh' and './wakeup from a terminal and they work as expected.
Can anyone see what I am doing wrong? Is there more/different information I need to provide.

Any help will be appreciated.
Thanks in advance.
Dave

---

### Post by DaithiF on 2011-03-24
capture stdout and stderr output from the jobs to a logfile so you can see whats happening inside the scripts, in particular any error messages.  also echo out the contents of variables that important to its execution ... e..g whichFri, thisFri, etc.

10 * * * * /usr/bin/sigrot
0 18 * * 5 /usr/bin/tff-meeting-mail.sh > /home/dave/tff.log 2>&1
36 19 * * * /home/dave/wakeup  > /home/dave/wakeup.log 2>&1

---

### Post by Silvernail on 2011-03-25
Thanks for taking the time to reply.

Some day I hope to get all my stupidity used up.

In both scripts I forgot to check spelling and syntex.

Everything works fine now.

Thanks again.
Dave

---

