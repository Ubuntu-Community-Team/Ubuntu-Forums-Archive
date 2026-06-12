---
title: "Ping with timestamp and logging"
date: 2011-09-19
forum: General Help
---

### Post by mykrob on 2011-09-19
I know how to redirect a ping to a textfile, but I am having trouble getting the timestamp to work. 

If i run   ping yahoo.com    it works, all packets are sent and received.

If i run   ping -T tsonly yahoo.com, i get this:

```

ping myk@lenovoLaptop:~$ ping -T tsonly yahoo.com
PING yahoo.com (98.137.149.56) 56(124) bytes of data.
^C
--- yahoo.com ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4032ms

```

How do I properly format the command to get a timestamp logged on each iteration, or every specified time period?

Thanks,

---

### Post by Bodsda on 2011-09-19
> **mykrob said:**
> I know how to redirect a ping to a textfile, but I am having trouble getting the timestamp to work. 

If i run   ping yahoo.com    it works, all packets are sent and received.

If i run   ping -T tsonly yahoo.com, i get this:

```

ping myk@lenovoLaptop:~$ ping -T tsonly yahoo.com
PING yahoo.com (98.137.149.56) 56(124) bytes of data.
^C
--- yahoo.com ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4032ms

```How do I properly format the command to get a timestamp logged on each iteration, or every specified time period?
Thanks,

I'm not on my Ubuntu machine at the moment, but what happens if you use the -v option as well?

Thanks,
Bodsda

---

### Post by Paddy Landau on 2011-09-19
I think you need to use a server that supports the command. Consider the two following commands:
```
*[COLOR=Navy]ping -c 1 -T tsonly **www.yahoo.com**[/COLOR]*
PING eu-fp3.wa1.b.yahoo.com (87.248.112.181) 56(124) bytes of data.

--- eu-fp3.wa1.b.yahoo.com ping statistics ---
1 packets transmitted, 0 received, 100% packet loss, time 0ms
``````
*[COLOR=Navy]ping -c 1 -T tsonly **ntp2.ja.net**[/COLOR]*
PING ntp2.ja.net (193.62.22.98) 56(124) bytes of data.
64 bytes from ntp2.ja.net (193.62.22.98): icmp_seq=1 ttl=243 time=78.7 ms
TS:     44451473 absolute
    3607327
    -3604481
    -1
    -4
    30
    1968342
    -1968366
    4
Unrecorded hops: 2


--- ntp2.ja.net ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 78.713/78.713/78.713/0.000 ms

```

---

### Post by mykrob on 2011-09-19
so is there a way to have it ping any server of my choosing and simply log what time the ping request was sent? I need to run a long term ping at a site and having that time stamp will greatly help with troubleshooting so we can see how much time is passed between certain points.

Thanks.

---

### Post by Paddy Landau on 2011-09-19
Sorry, I don't know the answer to that. Experiment with the various ping options and see what you can come up with.

---

### Post by Lampi on 2011-09-19
that's sth traceroute will more likely be of service:

```
traceroute [-U,I,T] -z 11 [target]
```

-U will send UDP packages
-I will send ICMP packages
-T will send TCP packages

read the manpage fur full details, IIRC you need sudo privileges for some of the parameters, same goes for several ping parameters (flood etc)

---

### Post by Lars Noodén on 2011-09-19
You can use the **-D** option.  It will give you the [unix timestamp](http://www.unixtimestamp.com/).

```
$ ping -c 3 **-D** google.com
PING google.com (209.85.148.105) 56(84) bytes of data.
[1316435881.681957] 64 bytes from fra07s07-in-f105.1e100.net (209.85.148.105): icmp_req=1 ttl=54 time=59.3 ms
[1316435882.681945] 64 bytes from fra07s07-in-f105.1e100.net (209.85.148.105): icmp_req=2 ttl=54 time=57.7 ms
[1316435883.683967] 64 bytes from fra07s07-in-f105.1e100.net (209.85.148.105): icmp_req=3 ttl=54 time=55.7 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2005ms
rtt min/avg/max/mdev = 55.760/57.601/59.326/1.458 ms
```

---

### Post by Azdour on 2011-09-19
Hi,

I was never able to get ping to give me a timestamp. The -D option does not exist for ping under Ubuntu 10.04.

In the end I wrote a script that output the time, then did a single ping:

```
ping -c 1 <some website>
```

The script would run every so often and output to a log file. That way I could see what time of day the ping failed.

---

### Post by Lars Noodén on 2011-09-19
Here is something in perl which converts the UNIX timestamps to something readable:

```

#!/usr/bin/perl

use strict;
use warnings;

my $ping=qq(/bin/ping -D www.google.com);

open (PING,"$ping |" )
  or die("Could not open $ping: $!\n");

while ( my $line = <PING>) {
   my @line = split(/\s/, $line);
   my $time = shift( @line );
   next unless ( $time =~ s/[\[\]]//g );

   my ($sec,$min,$hour,$mday,$mon,$year) = localtime($time);

   $mon++; $year += 1900;
   $time = printf("%d-%02d-%02d %02d:%02d:%02d ",$year,$mon,$mday,$hour,$min,$sec);

   unshift ( @line, $time );
   print join(" ", @line),qq(\n);
}
close (PING);
exit (0);

```

---

### Post by Lars Noodén on 2011-09-19
> **Azdour said:**
> Hi,

I was never able to get ping to give me a timestamp. The -D option does not exist for ping under Ubuntu 10.04.

I just checked under Oneiric and -D is there, so this should work for you under Oneiric.  It is also present under Natty.  I'm not sure that you can get a backport of just ping for 10.04.  Who'd have thought that after all this time that [ping](http://ftp.arl.mil/mike/ping.html) is under active development?

---

