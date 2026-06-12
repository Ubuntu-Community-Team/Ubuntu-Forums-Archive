---
title: "Ping several computers at a time"
date: 2012-05-24
forum: General Help
---

### Post by najdorfchess on 2012-05-24
Hi all. I want to ping several computers connected to my network simultaneously without going through them one at a time to find out if the system is alive or not in the network. I want to write a bash command to do it (preferably). To do this, below is the code I came up with: 

```

for host in (CAT ipaddresslist.txt)
ping -c 1 $host >/dev/null 2>&1 && echo "$host up and running" || echo "$host down"

``` 

where the ip address list is stored in the text file (lets say)

Is there a faster way to do it? Because this will take O(n) time since the code pings one by one plus the communication overhead of the network. I want to do it for several thousands of computers on my network and do it fast. Any suggestions? Anyone? 

Thanks in advance :)

---

### Post by papibe on 2012-05-24
Hi najdorfchess.

There are a couple of typical bash structures to do that.

Using a for:
```
for host in $(cat ipaddresslist.txt); do
    ...
done
```
Or better, using a while:
```
while read -r host; do
   ...
done < ipaddresslist.txt
```
As for the body of the loop, this would work:
```
if ping -c 1 $host &> /dev/null
then
    echo "$host up and running"
else 
    echo "$host down"
fi
```
Now this:
> **najdorfchess said:**
> I want to do it for several thousands of computers on my network and do it fast. Any suggestions? Anyone?

At first glance, it does not look like a very good idea, and would really recommend rethinking what you are doing.

The best way I can think of is doing it slowly, in intervals, so you don't overload the network.

For example:
```
while read -r host; do
    if ping -c 1 $host &> /dev/null
    then
        echo "$host up and running"
    else 
        echo "$host down"
    fi

    **[COLOR="Red"]sleep 10s[/COLOR]**

done < ipaddresslist.txt
```
That would make a 10 seconds pause after every trial.

I hope this helps, and tell us how it goes.
Regards.

---

### Post by diesch on 2012-05-24
Use nmap  with the *-sP*  option

---

### Post by najdorfchess on 2012-05-26
Thanks for your reply guys. I think nmap is a good way to do it. I found couple of other solutions too, by using 

1) fping
2) ARP protocol 

Both these basically send broadcast messages to all devices in network and invokes a reply from them confirming their existence on the network.

---

### Post by Habitual on 2012-05-26
[http://www.bournetoraiseshell.com/article.php/20120324121758738?query=ping](http://www.bournetoraiseshell.com/article.php/20120324121758738?query=ping)

---

### Post by najdorfchess on 2012-08-07
Thank you all

---

