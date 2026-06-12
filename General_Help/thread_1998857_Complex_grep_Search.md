---
title: "Complex grep Search"
date: 2012-06-07
forum: General Help
---

### Post by smackheid on 2012-06-07
Hello all,

My Ubuntu server obtains a text log file every half hour with following naming convention:

LogFile-YYYY-MM-DD-HHMM

each log contains entries like this:

00000,City,,AA0000,,1,,0,DD-JUN-12,
00000,City,,AA0000,,2,,0,DD-JUN-12,
00000,City,,AA0000,,3,,0,DD-JUN-12,

I'm looking to write a grep that will search for a string within files no more than 24 hours old for the value AA0000,,1/2/3 etc, the AA0000 varies and the 1 can be 1-5.

Neither of the below lines work properly as when grep does match the string, it only matches first few characters. 

egrep M0145??2  LogFile-`date +%Y-%m-%d -d "yesterday"`*
egrep "AB0040,,2"  LogFile-`date +%Y-%m-%d -d "yesterday"`*

Any tips or pointers would be greatly appreciated.

Thanks in advance
Smackheid

---

### Post by steeldriver on 2012-06-07
you can use the [...] regex syntax to denote a range of possible characters

[0-9]                       any single decimal digit
[0-9]+                     one or more decimal digits

e.g. (you will need to specify how the AA varies if you want to get further)

```
egrep "AA[0-9]+,,[0-5]" LogFile-`date +%Y-%m-%d -d "yesterday"`
```or

```
grep "AA[0-9]\+,,[0-5]" LogFile-`date +%Y-%m-%d -d "yesterday"`
```

---

### Post by smackheid on 2012-06-07
Thanks for your input Steeldriver.

I'll expand the scenario a bit as I hadn't really made my objective clear at first.

The logs are collected 48 times a day. Each log file contains a list of nodes which alarm during the last half hour. 

There are 12700+ nodes on the network and each node has up to 5 access points :shock:

I'm looking to count the number of times each node and access point appears in the previous days 48 logfiles. I also use a list of nodes as search criteria.

so it would look like this:
AA0000,,1: (count)
AA0000,,2: (count)
AA0001,,1: (count)

Below is what I have so far, but it's not returning anything useful :(

```

#!/bin/bash

rm /var/opt/projects/deadcell/scripts/test/countout

cat nodefile  | while read NODE
do

echo "$NODE Sector 1" >> /deadcell/scripts/test/countout
find /deadcell/files/DeadCell-`date +%Y-%m-%d -d "yesterday"`* | xargs egrep -c "$NODE,,1" >> /deadcell/scripts/test/countout

echo "$NODE Sector 2" >> /deadcell/scripts/test/countout
find /deadcell/files/DeadCell-`date +%Y-%m-%d -d "yesterday"`* | xargs egrep -c "$NODE,,2" >> /deadcell/scripts/test/countout

echo "$NODE Sector 3" >> /deadcell/scripts/test/countout
find /deadcell/files/DeadCell-`date +%Y-%m-%d -d "yesterday"`* | xargs egrep -c "$NODE,,3" >> /deadcell/scripts/test/countout

echo "$NODE Sector 4" >> /deadcell/scripts/test/countout
find /deadcell/files/DeadCell-`date +%Y-%m-%d -d "yesterday"`* | xargs egrep -c "$NODE,,4" >> /deadcell/scripts/test/countout

echo "$NODE Sector 5" >> //deadcell/scripts/test/countout
find /deadcell/files/DeadCell-`date +%Y-%m-%d -d "yesterday"`* | xargs egrep -c "$NODE,,5" >> /deadcell/scripts/test/countout

done


```

---

### Post by codemaniac on 2012-06-07
Find the logs modified in the last 24 hours and grep your string . 
> find . -mtime 0   # find files modified between now and 1 day ago

Something like below 

```
find /deadcell/files/DeadCell -mtime 0 | xargs egrep "$NODE,,1"
```

---

### Post by codemaniac on 2012-06-07
You can refine your search by providing a part of the name of the log file .
Do you maintain any naming convention of the log file ?

If so please provide that to find with -name switch .

The below would search the string "$NODE,,1" in only those filenames having "LogFile" as substring and modified within last 24 hours .

```
find /deadcell/files -name "*LogFile*" -mtime 0 | xargs egrep "$NODE,,1"
```

---

### Post by steeldriver on 2012-06-07
yes it's definitely your 'find' that is the problem

if all the files are in /deadcell/files/ there's really no need to use find, you could just loop over the directory list (ls) and cat the output i.e.

```
for LOG in $(ls /deadcell/files/DeadCell-`date +%Y-%m-%d -d "yesterday"`*)
do 
    egrep -c "$NODE,,1" $LOG >> ...
    egrep -c "$NODE,,2" $LOG >> ...
done

```

---

### Post by codemaniac on 2012-06-07
> **steeldriver said:**
> yes it's definitely your 'find' that is the problem

if all the files are in /deadcell/files/ there's really no need to use find,


But what if the OP has thousands of files in this directory having timestamp spanning several years .

Here he is only bothered about the files that are recently been modified .

---

### Post by smackheid on 2012-06-08
Again guys, thank you all very much for the input here. I'm truly amazed at how cooperative the Linux community can be.

So, the output from the grep -c looks like this:

DeadCell-2012-06-06-1705:1
DeadCell-2012-06-06-1735:1
DeadCell-2012-06-06-1805:1
DeadCell-2012-06-06-1835:1

Is there a way to do the total count for each entry?

Thanks

---

### Post by codemaniac on 2012-06-09
> **smackheid said:**
> Again guys, thank you all very much for the input here. I'm truly amazed at how cooperative the Linux community can be.

So, the output from the grep -c looks like this:

DeadCell-2012-06-06-1705:1
DeadCell-2012-06-06-1735:1
DeadCell-2012-06-06-1805:1
DeadCell-2012-06-06-1835:1

Is there a way to do the total count for each entry?

Thanks
Are you looking for the total number of matches or matches for a single entry .
grep -c would count the number of matches in a particular file and lists on the righmost column , in your case it is all 1 .

---

### Post by smackheid on 2012-06-10
As there will only be 1 access point/node combination in each file, it will only ever show as 1 or 0. There are 48 files in a day, so I'd be looking to count the number of times each specified node/access point combination appears in the previous day's 48 files.

Thanks
Smackheid

---

### Post by Vaphell on 2012-06-10
you can capture numbers alone and simply add the result of current iteration to the counter. Grep -h skips 'filename:' part so you get clean numbers.

```
n=0
for log in ...
do
  i=$( grep -hc ... "$log" )
  (( n=n+i ))
done
```
or knowing that there is max 1 match
```
for log in ...
do
  if grep -q ... "$log"
  then
    (( n++ ))
  fi
done
```


```
for LOG in $(ls /deadcell/files/DeadCell-`date +%Y-%m-%d -d "yesterday"`*)
```
we don't do that. Ls is for visual feedback purposes and is not to be parsed, built-in globbing is for that.
all-caps vars are not cool either, you risk overwriting some environmental variable by accident (they are all-caps by convention).
```
for log in /deadcell/files/DeadCell-$(date +%Y-%m-%d -d "yesterday")*
```

---

### Post by smackheid on 2012-06-27
Hi all,

Thanks for all your input to this thread. That code to count worked a treat. 

Watch this space for my next question :p

Thanks again
SmackHeid

---

