---
title: "Script question"
date: 2011-01-11
forum: General Help
---

### Post by sidmaster1 on 2011-01-11
This is the scipt:

#!/bin/bash

is_alive_ping()
{
  ping -c 1 $1 > /dev/null
  [ $? -eq 0 ] && echo Node with IP: $i is up
}

for i in 192.168.1.{1..120}
do
is_alive_ping $i & disown

done

---------------------------------------------------------------------
 
I need to know how to get this bash script to not echo the prompt
string in the midst of it's procedure here. And it does not want
to exit properly after execution, you have to press a key.

This is the output:

root@linux:/home/sid/code# ./net-ping.sh
Node with IP: 192.168.1.1 is up
root@linux:/home/sid/code# Node with IP: 192.168.1.100 is up
Node with IP: 192.168.1.103 is up
Node with IP: 192.168.1.102 is up
Node with IP: 192.168.1.105 is up

It would it to look like this:

root@linux:/home/sid/code# ./net-ping.sh
Node with IP: 192.168.1.1 is up
Node with IP: 192.168.1.100 is up
Node with IP: 192.168.1.103 is up
Node with IP: 192.168.1.102 is up
Node with IP: 192.168.1.105 is up


Thanks Everyone,

-Sid

---

### Post by bodhi.zazen on 2011-01-11
Remove the $ and disown or write the output to a file for later review.

---

### Post by hawkmage on 2011-01-11
I assume that you are using the disown command to background the pings to speed up the response.  That is also causing your problem.  By putting the pings into the background they are all forked off and detached from your terminal input.  This allows you to get your prompt back before all of your pings have sent their output.

---

### Post by sidmaster1 on 2011-01-11
That's a quick fix. Thanks for the help.
Guess I should have used that way to write to the screen in the first place huh?
Thanks very much for the help!

---

### Post by sidmaster1 on 2011-01-11
Thanks, guess I didn't understand the concept like I thought.
You all are great, Thanks for your help!

---

