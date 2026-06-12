---
title: "Ping Script, Timer 15 Seconds? Need help."
date: 2011-08-04
forum: General Help
---

### Post by Joseph889 on 2011-08-04
```
#!/bin/bash
while true; do
date=`date +"%y-%m-%d"`
time=`date +"%OH-%M-%S"`
varone=1
total=99.9
pingms=`ping -c 1 25.25.25.25 | grep time=.* | sed 's/.*time=\(.*\)\s.*/\1/'`
echo $pingms
if [ $(echo "$pingms > $total"|bc) -eq 1 ]
then
errors=$((errors+varone))
echo Found error: $pingms
echo Error $errors/3
fi
ping -c 1 25.25.25.25 >/dev/null 2>&1 
if [ "$?" = "1" ] 
then
errors=$((errors+varone))
echo Found error: Timeout
echo Error $errors/3
fi
if [ "$errors" = 3 ]
then
sendemail (arguments hidden for privacy)
errors=0
echo "$date $time   Ping Error 100ms+ / Timeout" >> /logs-custom/service-pingtest.txt
fi
sleep 1
done
```Now basically, if 3 errors occur, it emails me. My problem is one can happen at 1:00AM, another at 3AM, and another at 6PM, and then it would email me.

What I want to do is have it send me the email if I get 3 errors within a window of 15 seconds.

So basically, let's say the first error is at 2:00:23AM, next at 2:00:25AM, and 2:00:29AM, then it would send me an email, but not at 1:00AM, another at 3AM, and another at 6PM.

Thanks guys for help, hope to hear from you soon.

---

### Post by zero2xiii on 2011-08-04
Hay,

Im still a noob in scripting, but I do have a sugestion.

Test the time stamps. Take a sample of the time stamps, each on a counter (say counter 1, 2 and 3)... And for each individual error state you test for, let it read the time into that var, then just before the email stage, test the 3 values to see if the seconds are less than or equal to 15... if it is not, skip and reset the other counters?

Just what came to mind as to how I would have approached it..

---

### Post by Joseph889 on 2011-08-04
> **zero2xiii said:**
> Hay,

Im still a noob in scripting, but I do have a sugestion.

Test the time stamps. Take a sample of the time stamps, each on a counter (say counter 1, 2 and 3)... And for each individual error state you test for, let it read the time into that var, then just before the email stage, test the 3 values to see if the seconds are less than or equal to 15... if it is not, skip and reset the other counters?

Just what came to mind as to how I would have approached it..

Any idea how I would go about doing this, preferably in code?

Just a bit confused.

---

### Post by fdrake on 2011-08-04
i would use the unix time system (the time in secs since 1970)
check the code I may have forgot something.
```
#!/bin/bash
while true; do
 cat > log.txt
 date=`date +"%y-%m-%d"`
 time=`date +"%OH-%M-%S"`
 varone=1
 total=99.9
 pingms=`ping -c 1 25.25.25.25 | grep time=.* | sed 's/.*time=\(.*\)\s.*/\1/'`
 echo $pingms
 if [ $(echo "$pingms > $total"|bc) -eq 1 ]
 then
  date +%s >> log.txt 
 fi
 ping -c 1 25.25.25.25 >/dev/null 2>&1 
 if [ "$?" = "1" ] 
  then
  date +%s >> log.txt
  errors=$((errors+varone))
  echo Found error: Timeout
  echo Error $errors/3
 fi
i=1;
 tail -3 log.txt | while read line; 
   do
     line_$i=$line
     i=$i+1
   done
difference=$(($line_3-$line_1))
if [$difference =< 15]
then
sendemail (arguments hidden for privacy)
errors=0
echo "$date $time   Ping Error 100ms+ / Timeout" >> /logs-custom/service-pingtest.txt
fi
sleep 1
done
```

---

### Post by Joseph889 on 2011-08-04
> **fdrake said:**
> i would use the unix time system (the time in secs since 1970)
check the code I may have forgot something.
```
#!/bin/bash
while true; do
 cat > log.txt
 date=`date +"%y-%m-%d"`
 time=`date +"%OH-%M-%S"`
 varone=1
 total=99.9
 pingms=`ping -c 1 25.25.25.25 | grep time=.* | sed 's/.*time=\(.*\)\s.*/\1/'`
 echo $pingms
 if [ $(echo "$pingms > $total"|bc) -eq 1 ]
 then
  date +%s >> log.txt 
 fi
 ping -c 1 25.25.25.25 >/dev/null 2>&1 
 if [ "$?" = "1" ] 
  then
  date +%s >> log.txt
  errors=$((errors+varone))
  echo Found error: Timeout
  echo Error $errors/3
 fi
i=1;
 tail -3 log.txt | while read line; 
   do
     line_$i=$line
     i=$i+1
   done
difference=$(($line_3-$line_1))
if [$difference =< 15]
then
sendemail (arguments hidden for privacy)
errors=0
echo "$date $time   Ping Error 100ms+ / Timeout" >> /logs-custom/service-pingtest.txt
fi
sleep 1
done
```

Thanks, I'll test that soon.

---

### Post by bodhi.zazen on 2011-08-04
I suggest you use a loop.

As it seems this is a learning experience I shall not write it for you, but rather give you a hint.

[http://www.cyberciti.biz/faq/bash-while-loop/](http://www.cyberciti.biz/faq/bash-while-loop/)

---

### Post by Joseph889 on 2011-08-04
> **fdrake said:**
> i would use the unix time system (the time in secs since 1970)
check the code I may have forgot something.
```
#!/bin/bash
while true; do
 cat > log.txt
 date=`date +"%y-%m-%d"`
 time=`date +"%OH-%M-%S"`
 varone=1
 total=99.9
 pingms=`ping -c 1 25.25.25.25 | grep time=.* | sed 's/.*time=\(.*\)\s.*/\1/'`
 echo $pingms
 if [ $(echo "$pingms > $total"|bc) -eq 1 ]
 then
  date +%s >> log.txt 
 fi
 ping -c 1 25.25.25.25 >/dev/null 2>&1 
 if [ "$?" = "1" ] 
  then
  date +%s >> log.txt
  errors=$((errors+varone))
  echo Found error: Timeout
  echo Error $errors/3
 fi
i=1;
 tail -3 log.txt | while read line; 
   do
     line_$i=$line
     i=$i+1
   done
difference=$(($line_3-$line_1))
if [$difference =< 15]
then
sendemail (arguments hidden for privacy)
errors=0
echo "$date $time   Ping Error 100ms+ / Timeout" >> /logs-custom/service-pingtest.txt
fi
sleep 1
done
```

Tested it, it returned this error:

```
./testping2.sh 
41.9
./testping2.sh: line 25: line1=: command not found
./testping2.sh: line 25: line1+1=: command not found
./testping2.sh: line 25: line1+1+1=: command not found
./testping2.sh: line 28: -: syntax error: operand expected (error token is "-")

```

I think the error is from: ```
difference=$(($line_3-$line_1))
``` with the "-". Line 28.

---

### Post by fdrake on 2011-08-04
> **Joseph889 said:**
> Tested it, it returned this error:

```
./testping2.sh 
41.9
./testping2.sh: line 25: line1=: command not found
./testping2.sh: line 25: line1+1=: command not found
./testping2.sh: line 25: line1+1+1=: command not found
./testping2.sh: line 28: -: syntax error: operand expected (error token is "-")

```

I think the error is from: ```
difference=$(($line_3-$line_1))
``` with the "-". Line 28.

my bad. 
change this i=$i+1  to this i=$(($i+1))

---

### Post by Joseph889 on 2011-08-04
> **fdrake said:**
> my bad. 
change this i=$i+1  to this i=$(($i+1))

Now it returns this:

```
./testping2.sh 
42.4
./testping2.sh: line 25: line_1=: command not found
./testping2.sh: line 25: line_2=: command not found
./testping2.sh: line 25: line_3=: command not found
./testping2.sh: line 28: -: syntax error: operand expected (error token is "-")
```

---

### Post by fdrake on 2011-08-04
i am a litle bit out of shape with bash: I changed the errors try it now and let me know

```
#!/bin/bash
while true; do
 cat >> log.txt
 date=`date +"%y-%m-%d"`
 time=`date +"%OH-%M-%S"`
 varone=1
 total=99.9
 pingms=`ping -c 1 25.25.25.25 | grep time=.* | sed 's/.*time=\(.*\)\s.*/\1/'`
 echo $pingms
 if [ $(echo "$pingms > $total"|bc) -eq 1 ]
 then
  date +%s >> log.txt 
 fi
 ping -c 1 25.25.25.25 >/dev/null 2>&1 
 if [ "$?" = "1" ] 
  then
  date +%s >> log.txt
  errors=$((errors+varone))
  echo Found error: Timeout
  echo Error $errors/3
 fi
i=1;
 tail -3 log.txt | while read line; 
   do
     "line_$i"=$line
     i=$(($i+1))
   done
difference=$(($line_3-$line_1))
if (("$difference" =< 15))
        then
sendemail (arguments hidden for privacy)
errors=0
echo "$date $time   Ping Error 100ms+ / Timeout" >> /logs-custom/service-pingtest.txt
fi
sleep 1
done
```

---

### Post by Joseph889 on 2011-08-04
> **fdrake said:**
> i am a litle bit out of shape with bash: I changed the errors try it now and let me know

```
#!/bin/bash
while true; do
 cat > log.txt
 date=`date +"%y-%m-%d"`
 time=`date +"%OH-%M-%S"`
 varone=1
 total=99.9
 pingms=`ping -c 1 25.25.25.25 | grep time=.* | sed 's/.*time=\(.*\)\s.*/\1/'`
 echo $pingms
 if [ $(echo "$pingms > $total"|bc) -eq 1 ]
 then
  date +%s >> log.txt 
 fi
 ping -c 1 25.25.25.25 >/dev/null 2>&1 
 if [ "$?" = "1" ] 
  then
  date +%s >> log.txt
  errors=$((errors+varone))
  echo Found error: Timeout
  echo Error $errors/3
 fi
i=1;
 tail -3 log.txt | while read line; 
   do
     "line_$i"=$line
     i=$(($i+1))
   done
difference=$(($line_3-$line_1))
if (("$difference" =< 15))
        then
sendemail (arguments hidden for privacy)
errors=0
echo "$date $time   Ping Error 100ms+ / Timeout" >> /logs-custom/service-pingtest.txt
fi
sleep 1
done
```

```
./testping2.sh 
42.9
./testping2.sh: line 25: line_1=: command not found
./testping2.sh: line 28: -: syntax error: operand expected (error token is "-")

```

Can I contact you via AIM or something, it would make your help a lot easier and faster? If you don't want to that's fine.

---

### Post by fdrake on 2011-08-04
i am trying the script but i don't get your error (i get a sendmail error because i did not put any argument)

```
$ ./test.sh
./test.sh: line 31: syntax error near unexpected token `arguments'
./test.sh: line 31: `sendemail (arguments hidden for privacy)'
```

---

### Post by Joseph889 on 2011-08-04
> **fdrake said:**
> i am trying the script but i don't get your error (i get a sendmail error because i did not put any argument)

```
$ ./test.sh
./test.sh: line 31: syntax error near unexpected token `arguments'
./test.sh: line 31: `sendemail (arguments hidden for privacy)'
```

Well, I changed ```
cat > log.txt
``` to ```
echo "" >> log.txt
``` because if I used cat it would sit there until the script was stopped.

Any ideas?

---

### Post by fdrake on 2011-08-04
> **Joseph889 said:**
> Well, I changed ```
cat > log.txt
``` to ```
echo "" >> log.txt
``` because if I used cat it would sit there until the script was stopped.

Any ideas?

that's weird.. i don't get any of you errors and i am using the same script from my last post. Are you sure u have cat installed?
```

which cat
```

---

### Post by Joseph889 on 2011-08-04
> **fdrake said:**
> that's weird.. i don't get any of you errors and i am using the same script from my last post. Are you sure u have cat installed?
```

which cat
```

```
/bin/cat
```

This is weird. Do you have any packages that are necessary to run this script?

---

### Post by fdrake on 2011-08-04
test this if works...

---

### Post by Joseph889 on 2011-08-04
> **fdrake said:**
> test this if works...

Same error. All I know is that this string is a problem.

```
"line_$i"=$line
```

---

### Post by fdrake on 2011-08-05
> **Joseph889 said:**
> Same error. All I know is that this string is a problem.

```
"line_$i"=$line
```

new script

---

