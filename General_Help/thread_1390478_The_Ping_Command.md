---
title: "The Ping Command"
date: 2010-01-25
forum: General Help
---

### Post by Jackp90 on 2010-01-25
I am pinging google and sending the output to a text file via the command:

```
ping google.com >> ping
```

But I want to only want to view connections that have a time greater than 400ms how would I do that.

I tried piping it trough grep with a number like so:

```
ping google.com |grep #
```

But that didn't work so after a google search I figured that I would start a new thread.

Thank you for the help and sorry if I posted this in the wrong section.

---

### Post by n0dix on 2010-01-25
You can do a bash script for that!

---

### Post by Jackp90 on 2010-01-25
> **n0dix said:**
> You can do a bash script for that!

I am not really well versed in programing in bash is there a place that you would suggest that I start (e.g. a site that talks about some things that I would need to know to start writing a script that will coincide with what I need.

---

### Post by t4thfavor on 2010-01-25
Here is a perl script tha should work (I have nothing over 400ms away)

Save it, mark it executable, and run it like

sudo ping.pl [www.google.com](www.google.com)

if you want to add a count to it, I can teach you how to do that.


```

 use Net::Ping;
 $host = $ARGV[0];
 
    # High precision syntax (requires Time::HiRes)
 $p = Net::Ping->new("icmp");
 $p->hires();
 ($ret, $duration, $ip) = $p->ping($host, 5.5);
 if (1000 * $duration >= 400){
	 printf("$host [ip: $ip] is alive (packet return time: %.2f ms)\n", 1000 * $duration)
 }else{
	 #do nothing else
 }
 #printf("$host [ip: $ip] is alive (packet return time: %.2f ms)\n", 1000 * $duration)
 if $ret;
 $p->close();

```

It's way possible with bash, and awk, Im just not that good today, and perl makes it easier.

---

### Post by mr clark25 on 2010-01-26
well, i have developed something. i think its bash scripting, but I'm not sure.

here it is:
```

ping google.com -c 1 -i 0.25 -w 4.0 >a
echo "6 a">b
wc -l a >c
diff b c || diff b c >RESULTS.txt
./ping

```

it is also in the attached document (should be executable)
if RESULTS.txt ever shows up, the ping took longer than 4 seconds.

---

