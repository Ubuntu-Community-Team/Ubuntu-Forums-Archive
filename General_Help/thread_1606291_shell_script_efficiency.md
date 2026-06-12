---
title: "shell script efficiency"
date: 2010-10-26
forum: General Help
---

### Post by hobbyhack on 2010-10-26
I am helping someone who needs get lots of data from netstat and sort through it.  The existing script seems very inefficient.

Here is a portion of the current script:
```

echo "Total connections:"
netstat -an | grep -c 37.4080
echo "Established sessions:" 
netstat -an | grep ESTABLISHED | grep -c 37.4080
echo "Close Wait"
netstat -an | grep CLOSE_WAIT | grep -c 37.4080
echo "Last Acknowledgement"
netstat -an | grep LAST_ACK | grep -c 37.4080 
echo "Finish wait"
netstat -an | grep FIN_WAIT | grep -c 37.4080

```This actually goes on for a long time with a ton more of the same.  It seems to me running netstat 20 different times isn't very efficient.  However I am having issues pulling the netstat results into a variable that I can use.  I tried:
```

NETSTAT_RESULTS=`netstat -an`

```However, this somehow brings all the results in as a single line.  I thought about dumping the results to a file and then greping the file but I am afraid it is going to actually read the file every time which also doesn't seem efficient.

I use python a lot and I realize I could do this quickly and efficiently in python or perl but any suggestions on doing this in a shell script?

Thanks

---

### Post by Boondoklife on 2010-10-26
Try this:

```

#!/bin/bash
NETSTAT_RESULTS=`netstat -an`

echo 'Total connections:'
echo "$NETSTAT_RESULTS"
echo 'Established sessions:'
echo "$NETSTAT_RESULTS" | grep 'ESTABLISHED'
echo 'Close Wait'
echo "$NETSTAT_RESULTS" | grep 'CLOSE_WAIT'
echo 'Last Acknowledgement'
echo "$NETSTAT_RESULTS" | grep 'LAST_ACK'
echo 'Finish wait'
echo "$NETSTAT_RESULTS" | grep 'FIN_WAIT'

```Works for me

---

### Post by CharlesA on 2010-10-26
I'd suggest using $(...) instead of `...` in the above script to make it easier to nest and whatnot. It's not really *needed* but it helps make it cleaner. :)

---

### Post by Boondoklife on 2010-10-26
> **CharlesA said:**
> I'd suggest using $(...) instead of `...` in the above script to make it easier to nest and whatnot. It's not really *needed* but it helps make it cleaner. :)

Yea that is what I normally do, but wanted to stay close to what was already there =]

---

### Post by sisco311 on 2010-10-26
Try awk, something like:
```
netstat -an | \
grep 37.4080 | \
awk '{ tot++ } /ESTABLISHED/{ est++ } /CLOSE_WAIT/{ clo++ } \
END {print est" "tot" "clo}'
```

---

### Post by Boondoklife on 2010-10-26
This is why I love bash, and programming in general, so many ways to do the same thing!

---

### Post by lavinog on 2010-10-26
Why do you grep 37.4080?

Although sisco311's code is likely to be better, you could also grep out the unneeded data first:
```

#!/bin/bash
NETSTAT_RESULTS=$(netstat -an|grep -e 'ESTABLISHED' -e 'CLOSE_WAIT' -e 'LAST_ACK' -e 'FIN_WAIT')

echo 'Total connections:'
echo "$NETSTAT_RESULTS"
echo -n 'Established sessions :'
echo "$NETSTAT_RESULTS" | grep -c 'ESTABLISHED'
echo -n 'Close Wait :'
echo "$NETSTAT_RESULTS" | grep -c 'CLOSE_WAIT'
echo -n 'Last Acknowledgement :'
echo "$NETSTAT_RESULTS" | grep -c 'LAST_ACK'
echo -n 'Finish wait :'
echo "$NETSTAT_RESULTS" | grep -c 'FIN_WAIT'


```

---

### Post by Boondoklife on 2010-10-26
Actually sisco's code just gives you a count at the end not the actual data.

---

### Post by sisco311 on 2010-10-26
> **lavinog said:**
> Why do you grep 37.4080?


My guess is that 4080 is a port number and 37 is the last part of an IP address.

> **Boondoklife said:**
> Actually sisco's code just gives you a count at the end not the actual data.

Exactly what the original script does.

---

### Post by Boondoklife on 2010-10-26
Actually I think the OP wanted the data, not just a count, but I could be wrong and it would be far from the first time =]

I'm a little baffled about the .4080 too as this is the layout of netstat at least on my box:
```
 tcp       13      0 10.0.1.12:57335         10.0.1.30:139           CLOSE_WAIT
```

Note the ':' instead of a '.'

---

### Post by lavinog on 2010-10-26
grep -c 37.4080 just gives the count

---

### Post by Boondoklife on 2010-10-26
> **lavinog said:**
> grep -c 37.4080 just gives the count

Ahh now that explains it, never bothered to use that switch :P

---

### Post by sisco311 on 2010-10-26
> **Boondoklife said:**
> 

Note the ':' instead of a '.'

Yep, but in a grep PATTERN, the period . matches any single character.

---

### Post by hobbyhack on 2010-10-26
Thanks for all the replies.  I probably should have included more of the code because we are actually separating a few different IPs as well as other ports as well with other netstats.  I was not kidding when I said he had 20 netstats and actually I just counted and there are 32.

The 37.4080 is making sure it just grabs port 4080 from just one of the IPs.  We also have another netstat looking at 42.4080 for example.  It also helps ignore all the stuff in the bottom of the netstat -an result that they didn't want anyway.

I especially like sisco311's solution for  this and think I could probably use it to get down to just one netstat by matching 2 things (IP.port and status) on each line.

Looks like I will be spending tomorrow morning with awk.

Thanks!!!

---

### Post by hobbyhack on 2010-10-26
> **CharlesA said:**
> I'd suggest using $(...) instead of `...` in the above script to make it easier to nest and whatnot. It's not really *needed* but it helps make it cleaner. :)

Cool.  I will look into that.

> **Boondoklife said:**
> Try this:

```

#!/bin/bash
NETSTAT_RESULTS=`netstat -an`

echo 'Total connections:'
echo "$NETSTAT_RESULTS"
echo 'Established sessions:'
echo "$NETSTAT_RESULTS" | grep 'ESTABLISHED'
echo 'Close Wait'
echo "$NETSTAT_RESULTS" | grep 'CLOSE_WAIT'
echo 'Last Acknowledgement'
echo "$NETSTAT_RESULTS" | grep 'LAST_ACK'
echo 'Finish wait'
echo "$NETSTAT_RESULTS" | grep 'FIN_WAIT'

```Works for me

When I try this I get the entire results back as a single line stored in the variable.

---

### Post by CharlesA on 2010-10-26
That's the problem with storing a load of text in a variable.

I don't really know a way around it.

---

### Post by hobbyhack on 2010-10-30
> **sisco311 said:**
> Try awk, something like:
```
netstat -an | \
grep 37.4080 | \
awk '{ tot++ } /ESTABLISHED/{ est++ } /CLOSE_WAIT/{ clo++ } \
END {print est" "tot" "clo}'
```

Thank you!!!

awk is perfect and an amazing tool.

Now I can get a report like this (IPs may look funny because i changed them):
```

Local port totals
    Port    Count     Recv-Q     Send-Q
   50000      252          0          0
   47001        2          0          0
    6080        4          0          0
    4080       34          0          0
      22       12          0        104

State totals
           State    Count     Recv-Q     Send-Q
      CLOSE_WAIT       19          0          0
     ESTABLISHED      540          0        104
      FIN_WAIT_2        4          0          0
          LISTEN       32          0          0
       TIME_WAIT        3          0          0

Local port by state
    Port            State    Count     Recv-Q     Send-Q
   50000      ESTABLISHED      252          0          0
   47001      ESTABLISHED        2          0          0
    6080       FIN_WAIT_2        4          0          0
    4080        TIME_WAIT        3          0          0
    4080      ESTABLISHED       12          0          0
    4080       CLOSE_WAIT       19          0          0
      22      ESTABLISHED       12          0        104

Local port by remote IP
    Port          Remote IP    Count     Recv-Q     Send-Q
   50000       42.38.98.238      123          0          0
   50000          127.0.0.1      129          0          0
   47001       42.38.98.238        2          0          0
    6080       56.78.34.254        4          0          0
    4080        47.58.39.39        6          0          0
    4080    204.110.163.167        9          0          0
    4080     192.68.113.132        6          0          0
    4080       174.46.32.70        2          0          0
      22       56.78.34.254       12          0        104

Local port by remote IP by state
    Port          Remote IP            State    Count     Recv-Q     Send-Q
   50000       42.38.98.238      ESTABLISHED      123          0          0
   50000          127.0.0.1      ESTABLISHED      129          0          0
   47001       42.38.98.238      ESTABLISHED        2          0          0
    6080       56.78.34.254       FIN_WAIT_2        4          0          0
    4080        47.58.39.39       CLOSE_WAIT        6          0          0
    4080    204.110.163.167        TIME_WAIT        3          0          0
    4080    204.110.163.167      ESTABLISHED        5          0          0
    4080     192.68.113.132       CLOSE_WAIT        6          0          0
      22       56.78.34.254      ESTABLISHED       12          0        104

Remote IP by state
         Remote IP            State    Count     Recv-Q     Send-Q
   204.110.163.167        TIME_WAIT        3          0          0
   204.110.163.167      ESTABLISHED        5          0          0
    192.68.113.132       CLOSE_WAIT        6          0          0
         127.0.0.1      ESTABLISHED      260          0          0
      56.78.34.254       FIN_WAIT_2        4          0          0
      56.78.34.254      ESTABLISHED       13          0        104
       47.58.39.39       CLOSE_WAIT        6          0          0
      42.38.98.238      ESTABLISHED      254          0          0

Remote IP totals
         Remote IP    Count     Recv-Q     Send-Q
   204.110.163.167        9          0          0
    192.68.113.132        6          0          0
      174.46.32.70        2          0          0
         127.0.0.1      260          0          0
      56.78.34.254       17          0        104
       47.58.39.39        6          0          0
      42.38.98.238      254          0          0

```Here is my script if anyone wants to use it. It needs some tuning to get the sorts right.  Just pipe netstat into it 'netstat -an | <awkscriptname>:
```

#!/usr/bin/awk -f

BEGIN {
# Establish arrays
    state_count[""]=0;
    local_count[""]=0;
    remote_count[""]=0;
    local_remote_count[""]=0;
    local_state_count[""]=0;
    remote_state_count[""]=0;
    local_remote_state_count[""]=0;
}

{

    # Test for valid input
    #ignore lines without 6 fields
    if (NF != 6) {
        # ignore
    
    #ignore lines w/o local and remote IP
    } else if ($4 == "*.*" && $5 == "*.*") {
        # ignore
    
    #awk everything else
    } else {

    # Name our fields
    recvq=$2;
    sendq=$3;
    
    #get just the server port
    split($4,a,".")
    if (a[5]) {
        local=a[5]
    } else {
        local=$4
    }
    
    #get just the remote address
    split($5,b,".")
    if (b[5]) {
        remote=b[1]"."b[2]"."b[3]"."b[4]
    } else {
        remote=$5
    }

    state=$6;

    # Populate count arrays
    # name[<local> <remote> <state>]<command>
    state_count["* " "* " state]++;
    local_count[local " * " "*"]++;
    remote_count["* " remote " *"]++;
    local_remote_count[local " " remote " *"]++;
    local_state_count[local " * " state]++;
    remote_state_count["* " remote " " state]++;
    local_remote_state_count[local " " remote " " state]++;

    # Populate receive queue arrays
    # name[<local> <remote> <state>]<command>
    state_recvq["* " "* " state]+=recvq;
    local_recvq[local " * " "*"]+=recvq;
    remote_recvq["* " remote " *"]+=recvq;
    local_remote_recvq[local " " remote " *"]+=recvq;
    local_state_recvq[local " * " state]+=recvq;
    remote_state_recvq["* " remote " " state]+=recvq;
    local_remote_state_recvq[local " " remote " " state]+=recvq;

    # Populate send queue arrays
    # name[<local> <remote> <state>]<command>
    state_sendq["* " "* " state]+=sendq;
    local_sendq[local " * " "*"]+=sendq;
    remote_sendq["* " remote " *"]+=sendq;
    local_remote_sendq[local " " remote " *"]+=sendq;
    local_state_sendq[local " * " state]+=sendq;
    remote_state_sendq["* " remote " " state]+=sendq;
    local_remote_state_sendq[local " " remote " " state]+=sendq;
    }
}

# Output the data
END {
    print "Local port totals";
    printf "%8s %8s %10s %10s\n", "Port", "Count", "Recv-Q", "Send-Q";  
    sort = "sort -rn"
    for (i in local_count) {
        if (local_count[i] > 1) {
            split(i,g," ")            
            printf "%8s %8s %10s %10s\n", g[1], local_count[i], local_recvq[i], local_sendq[i] | sort
        }
    }
    close(sort)

    print "\nState totals";
    printf "%16s %8s %10s %10s\n", "State", "Count", "Recv-Q", "Send-Q";  
    sort = "sort"
    for (i in state_count) {
        if (state_count[i] > 1) {
            split(i,g," ")            
            printf "%16s %8s %10s %10s\n", g[3], state_count[i], state_recvq[i], state_sendq[i] | sort
        }
    }
    close(sort)

    print "\nLocal port by state";
    printf "%8s %16s %8s %10s %10s\n", "Port", "State", "Count", "Recv-Q", "Send-Q";  
    sort = "sort -rn"
    for (i in local_state_count) {
        if (local_state_count[i] > 1) {
            split(i,g," ")            
            printf "%8s %16s %8s %10s %10s\n", g[1], g[3], local_state_count[i], local_state_recvq[i], local_state_sendq[i] | sort
        }
    }
    close(sort)

    print "\nLocal port by remote IP";
    printf "%8s %18s %8s %10s %10s\n", "Port", "Remote IP", "Count", "Recv-Q", "Send-Q";  
    sort = "sort -rn"
    for (i in local_remote_count) {
        if (local_remote_count[i] > 1) {
            split(i,g," ")            
            printf "%8s %18s %8s %10s %10s\n", g[1], g[2], local_remote_count[i], local_remote_recvq[i], local_remote_sendq[i] | sort
        }
    }
    close(sort)

    print "\nLocal port by remote IP by state";
    printf "%8s %18s %16s %8s %10s %10s\n", "Port", "Remote IP", "State", "Count", "Recv-Q", "Send-Q";  
    sort = "sort -rn"
    for (i in local_remote_state_count) {
        if (local_remote_state_count[i] > 1) {
            split(i,g," ")            
            printf "%8s %18s %16s %8s %10s %10s\n", g[1], g[2], g[3], local_remote_state_count[i], local_remote_state_recvq[i], local_remote_state_sendq[i] | sort  
        }
    }
    close(sort)

    print "\nRemote IP by state";
    printf "%18s %16s %8s %10s %10s\n", "Remote IP", "State", "Count", "Recv-Q", "Send-Q";  
    sort = "sort -rn"
    for (i in remote_state_count) {
        if (remote_state_count[i] > 1) {
            split(i,g," ")            
            if (g[2] == "*.*") {
                # ignore
            } else {    
            printf "%18s %16s %8s %10s %10s\n", g[2], g[3], remote_state_count[i], remote_state_recvq[i], remote_state_sendq[i] | sort
            }
        }
    }
    close(sort)

    print "\nRemote IP totals";
    printf "%18s %8s %10s %10s\n", "Remote IP", "Count", "Recv-Q", "Send-Q";  
    sort = "sort -rn"
    for (i in remote_count) {
        if (remote_count[i] > 1) {
            split(i,g," ")
            if (g[2] == "*.*") {
                # ignore
            } else {    
                printf "%18s %8s %10s %10s\n", g[2], remote_count[i], remote_recvq[i], remote_sendq[i] | sort
            }
        }
    }
    close(sort)
}

```There is a great site on awk here although I like the sort method I used better:
[http://www.grymoire.com/Unix/Awk.html](http://www.grymoire.com/Unix/Awk.html)

---

