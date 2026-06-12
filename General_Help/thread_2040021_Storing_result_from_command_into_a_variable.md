---
title: "Storing result from command into a variable"
date: 2012-08-10
forum: General Help
---

### Post by bomberb17 on 2012-08-10
Hello,
I'm trying to implement a script that runs iperf, which measures bandwidth between a client and a server. A sample output looks like:

```

user1@ubuntu:~$ iperf -c 192.168.1.1 -P 1 -i 1 -p 5001 -f k -t 5
------------------------------------------------------------
Client connecting to 192.168.1.1 , TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.135.159 port 50309 connected with 192.168.1.1  port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 1.0 sec   256 KBytes  2097 Kbits/sec
[  3]  1.0- 2.0 sec   128 KBytes  1049 Kbits/sec
[  3]  2.0- 3.0 sec  0.00 KBytes  0.00 Kbits/sec
[  3]  3.0- 4.0 sec   128 KBytes  1049 Kbits/sec
[  3]  4.0- 5.0 sec  0.00 KBytes  0.00 Kbits/sec
[  3]  5.0- 6.0 sec  0.00 KBytes  0.00 Kbits/sec
[  3]  0.0- 9.3 sec   640 KBytes   561 Kbits/sec

```So this command runs a bandwidth test for a specific amount of time (-t option)
I want to take the result from the very last line (in the previous example, 561) and store it into a variable in my script. Based on that result I would run a bandwidth test for a specific file size, according to my previous result. E.g. if a is between 0 and 100, run iperf with -n 100000 (100Kbyte file) and so on.
Any help will be greatly appreciated!!

---

### Post by Zvlwab on 2012-08-10
```
VAR=`iperf -c 192.168.1.1 -P 1 -i 1 -p 5001 -f k -t 5`
for i in $VAR; do
    echo $i
done
```

---

### Post by bomberb17 on 2012-08-10
I don't think this helps, because the output might be variable (e.g. it might output one more or one less line). I was thinking of something about grep...

---

### Post by Vaphell on 2012-08-10
try```
n=$( iperf -c 192.168.1.1 -P 1 -i 1 -p 5001 -f k -t 5 | tail -1 | awk '{ print $(NF-1) }' )
```

---

