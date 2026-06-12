---
title: "Linux Equivalant to &quot;Ping -a&quot; in Windows"
date: 2009-11-27
forum: General Help
---

### Post by IAmNotAUser on 2009-11-27
I wasn't sure where to put this, I hope it's in the right place to get some support.

I regularly use the command

```
ping -a <HOSTIP>
```to resolve the host name of the computer receiving the ping request.

I've been trying to find a linux equivalant of this command, and the best I have found is host.

However, when I do
```
host 192.168.0.3
```

I get the following output
```
3.0.168.192.in-addra.arpa. not found: 3(NXDOMAIN)
```

Is there another way to do get the result, or how to make host work properly?

---

### Post by whoop on 2009-11-27
nslookup

---

### Post by dcstar on 2009-11-27
> **IAmNotAUser said:**
> 
........
However, when I do
```
host 192.168.0.3
```

I get the following output
```
3.0.168.192.in-addra.arpa. not found: 3(NXDOMAIN)
```

Is there another way to do get the result, or how to make host work properly?

Unless you are accessing a DNS system with that **internal** IP address in it, then that is exactly what should be returned.

---

### Post by diesch on 2009-11-27
What result do you want?

---

### Post by 1337H4x0r on 2009-11-28
This is exactly what should be happening if you are using DSN

---

### Post by jamesisin on 2009-11-28
I ran both ping [IP] and ping -a [IP] from my XP test machine.  The output of both commands was identical.  What is it you are trying to accomplish?

---

### Post by IAmNotAUser on 2009-11-28
I am trying to resolve the host name of the receiving computer.

The outputs from "ping" and "ping -a" are not the same

```
Microsoft Windows [Version 6.1.7600]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\Doug>ping 192.168.0.4

Pinging 192.168.0.4 with 32 bytes of data:
Reply from 192.168.0.4: bytes=32 time=29ms TTL=128
Reply from 192.168.0.4: bytes=32 time=12ms TTL=128

Ping statistics for 192.168.0.4:
    Packets: Sent = 2, Received = 2, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 12ms, Maximum = 29ms, Average = 20ms
Control-C
^C
C:\Users\Doug>ping -a 192.168.0.4

Pinging Doug-PC [192.168.0.4] with 32 bytes of data:
Reply from 192.168.0.4: bytes=32 time=1ms TTL=128
Reply from 192.168.0.4: bytes=32 time=1ms TTL=128

Ping statistics for 192.168.0.4:
    Packets: Sent = 2, Received = 2, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 1ms, Maximum = 1ms, Average = 1ms
Control-C
^C
```Notice that the ping -a output has "pinging Doug-PC" in it. That's what I'm trying to get. I do not have actual DNS records set up in the router, I'm trying to get to find a command to return the name of the computer (Doug-PC, Doug-Ubuntu, Doug-Laptop as appropriate) in the output.

Using "nslookup 192.168.0.6" (Doug-Laptop) gave me

```
Server    192.168.0.1
Address:    192.168.0.1#53

** server can't find 6.0.168.192.in-addr.arpa.: NXDOMAIN
```so I don't think that's what I'm after. I'm basically trying to get it to return the name of the computer that is set at install.

---

### Post by diesch on 2009-11-28
You need to either setup a DNS record or have an entry in /etc/hosts to get the DNs names corresponding to an IP address.

If Windows has other ways to resolve IP addresses that may work using Samba in some way.

---

### Post by IAmNotAUser on 2009-11-28
I understand that if I want to query the name servers, however Windows is able to get the computer to respond with its name when it receives a ping, I was hoping Linux would be able to as well.

I don't want to set up DNS records, as this is designed to be deployed in a new network in order to build that record listing up. Setting up DNS records pretty much contradicts that as I don't know the names of the computers, hence I am querying them with the "ping -a" command.

---

### Post by jamesisin on 2009-11-28
Ah, I see.  You are dealing with an issue on the ping'd machine (and not the pinging machine).  You ought be able to alter your recipient machine to offer up that information.  I tested one of google's servers with -a (74.125.67.100) and it responded with its host name (I'm assuming it's a RH server).

---

### Post by diesch on 2009-11-28
Windows seems to do that using *NetBIOS name resolution*. I guess to can get the names for system that support this using *smbclient* - but it's only supported on Windows systems or other systems using Samba.
Maybe asking another question about *NetBIOS name resolution* gets you more detailed answers about that.


The best you can do is to try both NetBIOS and DNS name resolution and be prepared that some IP address can't be resolved.

---

### Post by Mazin on 2009-11-28
I think I understand what you are looking for.  You want to, given a local IP address, find out the Windows name associated with it, right?  Like, if I name my Windows computer "foo" and its IP is 192.168.1.101, then looking up 192.168.1.101 will return "foo"?

If so, then `nmblookup` might help.  Since Windows names are specific to Windows' zeroconf service (this would not work with Apple's Bonjour/Avahi zeroconf!), they are managed with the Samba suite.  Keep in mind that these names are WINS names and not DNS names (different tools for different realms).

Try running

```
$ nmblookup -A 192.168.1.101
```

and see if it prints out what you need.  You'll probably have to use some scripting magic to pull out the right info, but I assume you're already doing that with `ping -a`.

I found this by first finding this [perl script]("http://www.perlmonks.org/?displaytype=displaycode;node_id=;123764") that does exactly the reverse of what you need.  The manpage for `nmblookup` will have more detail.

Please let me know if this works or not.

---

### Post by 5BallJuggler on 2009-11-28
Try this:-

```
sudo nmap 192.168.1.*
```

It works for me.

to give just what you are after, you need a bit more code

```
sudo nmap 192.168.1.* | grep "192.168" | sed 's/Interesting ports on //g' | sed 's/All .* scanned ports on //g' | cut -d')' -f1 | sed 's/.home (/ /g

```

---

### Post by jamesisin on 2009-11-28
If the above is all you are seeking then you could just run nslookup [IP.adrs.of.machine] and (provided it is getting DHCP from something on your network which is in your DNS list) it will return the local name of the machine.

I looked over the ping man page and don't see anything that might emulate the Windows -a option.  (I thought perhaps the verbose argument but alas no.)

So, I guess you are seeking two solutions: a) have ping responses include host name information and b) find a utility which pings in a manner which requests host name information.

---

### Post by dcstar on 2009-11-28
> **diesch said:**
> Windows seems to do that using *NetBIOS name resolution*. I guess to can get the names for system that support this using *smbclient* - but it's only supported on Windows systems or other systems using Samba.
Maybe asking another question about *NetBIOS name resolution* gets you more detailed answers about that.


The best you can do is to try both NetBIOS and DNS name resolution and be prepared that some IP address can't be resolved.

Install **winbind**

---

### Post by IAmNotAUser on 2009-11-28
> **Mazin said:**
> I think I understand what you are looking for.  You want to, given a local IP address, find out the Windows name associated with it, right?  Like, if I name my Windows computer "foo" and its IP is 192.168.1.101, then looking up 192.168.1.101 will return "foo"?

Yes, that's exactly what I was attempting to do. Sorry if I didn't explain it to begin with everyone, posting that output of -a in my original post would have probably helped to make it clear to begin with.

> **Mazin said:**
> If so, then `nmblookup` might help.  Since Windows names are specific to Windows' zeroconf service (this would not work with Apple's Bonjour/Avahi zeroconf!), they are managed with the Samba suite.  Keep in mind that these names are WINS names and not DNS names (different tools for different realms).

Try running

```
$ nmblookup -A 192.168.1.101
```and see if it prints out what you need.  You'll probably have to use some scripting magic to pull out the right info, but I assume you're already doing that with `ping -a`.

I found this by first finding this [perl script]("http://www.perlmonks.org/?displaytype=displaycode;node_id=;123764") that does exactly the reverse of what you need.  The manpage for `nmblookup` will have more detail.

Please let me know if this works or not.

I figured that it wasn't a DNS record it was looking up, but I couldn't for the life of me find a reference to what the actual name was (which I now know as WINS), thanks everyone, especially Mazin and diesch, for edging me in the right direction.

Yes, the scripting part is definitely no issue to me, I can handle that once I found the right output. :P

It looks like nmblookup does exactly what I wanted it to, this is the output I get from it:
```
Looking up status of 192.168.0.4
    DOUG-PC         <00> -         M <ACTIVE> 
    WORKGROUP    <00> - <GROUP> M <ACTIVE> 
    DOUG-PC         <20> -         M <ACTIVE> 
    WORKGROUP    <1e> - <GROUP> M <ACTIVE> 

    MAC Address = 00-50-8D-BF-11-F0
```which is the correct computer name, and also contains the ip address in the output, which is excellent! Thanks a lot. :D

> **5BallJuggler said:**
> Try this:-

```
sudo nmap 192.168.1.*
```It works for me.

to give just what you are after, you need a bit more code

```
sudo nmap 192.168.1.* | grep "192.168" | sed 's/Interesting ports on //g' | sed 's/All .* scanned ports on //g' | cut -d')' -f1 | sed 's/.home (/ /g

```

I couldn't get your command to run, I get a new line and > response, as if it's waiting for my input, also doing a regular sudo nmap does not print out the computer name at any point, so any further manipulation of the output will be pointless, surely?

However, as I mentioned, I think nmblookup is the response I've been hoping for. Tried it against 2 of my Windows machines I have available atm, and it responded as hoped to both of them. 

Thanks for the replies everyone! I've tried to reply to the other posts in this thread with helpful info in case someone else finds this thread in the future for a slightly difference purpose.

---

