---
title: "measure internet connectivity"
date: 2010-01-26
forum: General Help
---

### Post by YigalB on 2010-01-26
Lately, my internet connection stops for several minutes and then re-connects. Since there are few issues to debug here (router, modem, ADSL, internet provider), I would like first to measure the failure rate.

Is there a utility or script that will do the following: Wake every 1-2 minutes, verify a certain web page is available (doesn't matter which). If it fails: dump a line to a log file and get back to sleep. If OK - get back to sleep.

Is there such a utility? 
If not - can someone help me with writing such a script?

Thanks
Yigal

---

### Post by ibuclaw on 2010-01-26
You mean like: [http://www.speedtest.net/](http://www.speedtest.net/) 
?

---

### Post by t4thfavor on 2010-01-26
You want to setup a cron job that runs something like this

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

look here for more info
[http://perldoc.perl.org/Net/Ping.html](http://perldoc.perl.org/Net/Ping.html)

and it would be pretty easy to add file logging to this.


Also this is something I wrote for pinging remote hosts, and emailing if the host is down, Im not sure if it still works or not, but your free to use it. PS it's a perl file (.pl)

And if you want it hacked down a bit to be more cron oriented instead of an actual daemon, I can help with that too, just PM me.

---

### Post by YigalB on 2010-01-26
> **tinivole said:**
> You mean like: [http://www.speedtest.net/](http://www.speedtest.net/) 
?
no - this will measure what is the speed at a given moment. I am looking for something that will record the connectivity over time.
 Thanks!

---

### Post by YigalB on 2010-01-26
> **t4thfavor said:**
> You want to setup a cron job that runs something like this

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

look here for more info
[http://perldoc.perl.org/Net/Ping.html](http://perldoc.perl.org/Net/Ping.html)

and it would be pretty easy to add file logging to this.


Also this is something I wrote for pinging remote hosts, and emailing if the host is down, Im not sure if it still works or not, but your free to use it. PS it's a perl file (.pl)

And if you want it hacked down a bit to be more cron oriented instead of an actual daemon, I can help with that too, just PM me.

This looks great - I will need some help to set it up. Thanks!

---

