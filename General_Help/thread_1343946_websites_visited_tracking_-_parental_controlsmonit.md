---
title: "websites visited tracking - parental controls/monitoring"
date: 2009-12-02
forum: General Help
---

### Post by pabc on 2009-12-02
My son is about to get a laptop of his own for the first time - ie one not in a family room where we can watch him.

I've looked at a number of webfiltering options and the best I can find isnt great and to be honest I dont want to filter anything - I'd rather he knows it's all logged and to behave himself - else I'll apply the ban hammer!

I've looked at logging everything at the router level which is a pain but I can do it if I use 'another' laptop to receive the syslogs from the router and then look at them now and again.

But the ideal solution for me would be a daemon which just logged websites that the laptop visits - ie one designed for this so it does the dns look ups from the ips and just presents a txt file of when and where a user has visited?

I've had a look around in the repos and nothing stands out.

Does anyone have any ideas or other ways I could go about this?

---

### Post by kidders on 2009-12-03
Hi there,

It sounds like you're looking for something that would run on the laptop itself, which presents a problem, because that would mean your son couldn't have root access to his own machine. That aside, assuming you really are only interested in the web_sites_ (ie not URLs) visited, the simplest solution might be to use his firewall to log outgoing traffic on ports 80 & 443.

Of course, if your son is happy to forego root access to his laptop, you might as well use *its* syslog daemon to store requests logged by your router.

An alternative approach would be to use a transparent proxy, but since most web filters are basically proxies, I'm guessing you've ruled that idea out already.

I'm not sure that's very much help. It could be quite difficult to find a good way to track activity without involving a second computer.

---

### Post by StuartN on 2009-12-03
> **kidders said:**
> It sounds like you're looking for something that would run on the laptop itself

I had a trivial cron job on my teenager's computer to post the filtered output from netstat -al, along with a timed allowance imposed by the router. I am sure someone could turn the IP addresses into a meaningful log.

I also imposed a total access ban at the router whenever she abused the system, e.g. by Facebooking during homework.

Everything was by "consent", in the sense of accepting these rules or no access, and completely open (no snooping on content).

---

### Post by StuartN on 2009-12-03
Whilst sorting out an unrelated problem, I came across OpenDNS [https://www.opendns.com/start/](https://www.opendns.com/start/) which offers a Basic (i.e. free) account that offers a 2-week archive in its reporting function, plus web filtering, phishing protection and other goodies.

I don't know if Google Public DNS [http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/) will add any filtering or reporting features.

Of course anyone can bypass a DNS by inserting their own DNS addresses in Network Manager, unless you log and / or filter those addresses at the router (which is where the big stick rule comes in - mess with the settings and the router blacklists the kid's MAC address).

---

### Post by pabc on 2009-12-05
cheers for the ideas.

I've flashed my router with dd-wrt and set it logging to an old machine which I can log into and retrive the logs.

I wasn't planning to give him root access so I'll look at the simpler option of logging outgoing firewall traffic.

The idea of using his syslog to collect the router logs is excellent. It'll work whilst I'm only monitoring his laptop rather than everything.

I think WICD allows fixed IP on one connection and DHCP on others so he'll still be able to roam.

---

### Post by pabc on 2009-12-06
just incase anyone stumbles across this via search

I ended up setting up an iptables rule to log all output from all interfaces as log-level 7

```
sudo iptables -A OUTPUT -o + -j LOG --log-level 7 --log-prefix "FIREWALL:"
```

then saved the table 
```
sudo sh -c "iptables-save > /etc/iptables"
```

and set the preup script in WICD network manager to 
```
iptables-restore < /etc/iptables
```

I set rsyslogd to filter debug (level 7) to it's own firewall file
```
kern.=debug     /var/log/firewall
```

then wrote a bash script to tidy that file up so I end up with just a list of unique hosts the box has visited. Lots of gawks, sort -u and greps

---

### Post by StuartN on 2009-12-06
> **pabc said:**
> I ended up setting up an iptables rule to log all output from all interfaces as log-level 7

I looked at the man entry for iptables and was too embarrassed to ask how to set it up! Many thanks.

1) Could you post a snippet of what the log looks like?

2) How might you generate a meaningful list of unacceptable web site urls, using the ip addresses in the log?

---

### Post by kidders on 2009-12-06
Just a quick suggestion ...

> **pabc said:**
> ```
sudo iptables -A OUTPUT -o + -j LOG --log-level 7 --log-prefix "FIREWALL:"
```

That might be overkill. You *could* try something more conservative like ...```
iptables -I OUTPUT -o eth+ -p tcp --dport 80 -m state --state NEW -j LOG --log-level 7 --log-prefix "FIREWALL: "
```
Only recording new TCP connections that don't terminate at a local network interface should significantly reduce the amount of disk I/O associated with internet usage, and stop your logs getting horribly bloated. Limiting logging to port 80 is possibly a bit over the top, but you get the idea.

Also, inserting the log rule at the beginning of a chain is better than sticking it on the end, to be sure you catch everything.

----

For StuartN ...

You might expect to see something like this in your logs ...

```
[1816303.316456] FIREWALL: IN= OUT=eth2 SRC=192.168.6.200 DST=216.239.59.147 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=21506 DF PROTO=TCP SPT=51458 DPT=80 WINDOW=5840 RES=0x00 SYN URGP=0
```

Then, you could do something like the following ...

```
$ grep 'FIREWALL:' /var/log/syslog | sed 's/.*DST=\([0-9.]*\) .*/\1/' | sort | uniq | xargs resolveip
Host name of 216.239.59.147 is gv-in-f147.1e100.net
```

You can't use the logs to produce a list of URLs though.

---

### Post by pabc on 2009-12-06
this is the tail of the log on my laptop

tail /var/log/firewall
```

Dec  6 15:06:45 AAO kernel: [  136.556140] FIREWALL:IN= OUT=wlan0 SRC=192.168.1.104 DST=174.36.30.67 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=51183 DF PROTO=TCP SPT=50017 DPT=443 WINDOW=225 RES=0x00 ACK URGP=0 
Dec  6 15:06:45 AAO kernel: [  136.844084] FIREWALL:IN= OUT=wlan0 SRC=192.168.1.104 DST=91.189.94.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=48105 DF PROTO=TCP SPT=54738 DPT=80 WINDOW=992 RES=0x00 ACK URGP=0 
Dec  6 15:06:49 AAO kernel: [  140.774931] FIREWALL:IN= OUT=wlan0 SRC=192.168.1.104 DST=91.189.94.12 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=48106 DF PROTO=TCP SPT=54738 DPT=80 WINDOW=997 RES=0x00 ACK FIN URGP=0 
Dec  6 15:06:52 AAO kernel: [  143.375945] FIREWALL:IN= OUT=wlan0 SRC=192.168.1.104 DST=98.136.113.251 LEN=156 TOS=0x00 PREC=0x00 TTL=64 ID=51285 DF PROTO=TCP SPT=57470 DPT=5050 WINDOW=214 RES=0x00 ACK PSH URGP=0 
Dec  6 15:06:52 AAO kernel: [  143.494863] FIREWALL:IN= OUT=wlan0 SRC=192.168.1.104 DST=98.136.113.251 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=51286 DF PROTO=TCP SPT=57470 DPT=5050 WINDOW=214 RES=0x00 ACK URGP=0 
Dec  6 15:06:52 AAO kernel: [  143.612096] FIREWALL:IN= OUT=wlan0 SRC=192.168.1.104 DST=87.248.114.32 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=63396 DF PROTO=TCP SPT=36931 DPT=80 WINDOW=992 RES=0x00 ACK URGP=0 
Dec  6 15:06:58 AAO kernel: [  149.524134] FIREWALL:IN= OUT=wlan0 SRC=192.168.1.104 DST=87.248.114.32 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=55582 DF PROTO=TCP SPT=36961 DPT=80 WINDOW=499 RES=0x00 ACK URGP=0 
Dec  6 15:07:04 AAO kernel: [  155.775147] FIREWALL:IN= OUT=wlan0 SRC=192.168.1.104 DST=87.248.114.32 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=55583 DF PROTO=TCP SPT=36961 DPT=80 WINDOW=499 RES=0x00 ACK FIN URGP=0 
Dec  6 15:07:04 AAO kernel: [  155.775381] FIREWALL:IN= OUT=wlan0 SRC=192.168.1.104 DST=87.248.114.32 LEN=52 TOS=0x00 PREC=0x00 TTL=64 ID=63397 DF PROTO=TCP SPT=36931 DPT=80 WINDOW=997 RES=0x00 ACK FIN URGP=0 
Dec  6 15:07:11 AAO kernel: [  162.373254] FIREWALL:IN= OUT=wlan0 SRC=192.168.1.104 DST=224.0.0.251 LEN=68 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=48
``` 

and I use this VERY clunky script to get the URLS  - i know it's poor but I'm learning

```

# remove non FIREWALL, DNS and internal
cat /var/log/firewall | grep FIREWALL  | grep -v DST=194.168 | grep -v DST=192.168 >~/temp1
# record IP and port in temp2
gawk '{print $11,$20}' ~/temp1 > ~/temp2
# record IP in temp3
gawk '{print $11}' ~/temp1 > ~/temp3
# Remove DST= from temp3 
gawk -F'=' '{print $2}' ~/temp3 > ~/temp4
# Remove duplicate IPs and store in ips
sort -u ~/temp4 > ~/ips
# do hosts look up on ips. hosts wont take std_out from cat ips so loop
for i in $(cat ~/ips); do
host $i >> ~/temp5
done
# remove duplicate URLS 
sort -u ~/temp5 > ~/temp6
# remove all the 'not found:' from the host look up
cat ~/temp6 | grep -v found: > ~/temp7
# only store the URL from std_out from host 
gawk -F' ' '{print $5}' ~/temp7 > ~/temp8
# remove duplicates and store in urls
sort -u ~/temp8 > ~/urls
# remove temp files
rm ~/temp*
# optional delete log files - must look into log rotation daemons
# sudo rm -f /var/log/firewall


```

The host command does a reasonable job at returning URLs from IPs but reports a lot of NOT FOUNDs - there probably is a better way.

Thanks for the better iptables command as well

---

### Post by StuartN on 2009-12-06
[QUOTE=pabc;8450244]```
for i in $(cat ~/ips); do
host $i >> ~/temp5
done
```

That is neat, and actually very quick. I saved IP connections from netstat every 15 or 30 minutes, then matched those against a list that I found somewhere. I added my own identifiable sites and occasionally manually checked unknown IP addresses using whois.

I suppose you could run an exclusion on a whitelist before that loop. 

My problem, as I recall, was that MSN and Facebook were hard to keep up with and difficult to block. I was more concerned about time spent on social networking and idle surfing, less about the content.

---

### Post by StopAddict on 2010-01-17
We have a bunch of speciality filters that may be of help.  Visit stopaddict.com

---

