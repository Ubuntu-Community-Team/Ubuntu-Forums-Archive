---
title: "bash shell script for iptables"
date: 2011-01-02
forum: General Help
---

### Post by icelogic on 2011-01-02
i can copy and paste all the commands in the terminal to get it to work but wanted to have a bash shell script available as well.  i just want it to run the commands and exit the terminal when i run the script in the terminal.  But i don't know how to really make sure its right.  can some one please help, thanks in advance.

#!/bin/bash

while true
do

sudo iptables -A INPUT -s 173.0.0.0/20 -j DROP ; 
sudo iptables -A INPUT -s 173.192.0.0/15 -j DROP ; 
sudo iptables -A INPUT -s 184.82.0.0/16 -j DROP ; 
sudo iptables -A INPUT -s 72.20.37.208/28 -j DROP ; 
sudo iptables -A INPUT -s 67.228.112.64/27 -j DROP ; 
sudo iptables -A INPUT -s 173.244.192.0/19 -j DROP ; 
sudo iptables -A INPUT -s 67.162.0.0/17 -j DROP ; 
sudo iptables -A INPUT -s 188.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 204.12.247.216/29 -j DROP ; 
sudo iptables -A INPUT -s 76.73.0.0/17 -j DROP ; 
sudo iptables -A INPUT -s 204.74.208.0/20 -j DROP ; 
sudo iptables -A INPUT -s 217.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 94.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 85.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 78.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 74.86.0.0/16 -j DROP ; 
sudo iptables -A INPUT -s 38.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 66.55.128.0/19 -j DROP ; 
sudo iptables -A INPUT -s 89.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 110.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 213.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 174.143.144.0/21 -j DROP ; 
sudo iptables -A INPUT -s 173.234.56.0/21 -j DROP ; 
sudo iptables -A INPUT -s 77.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 174.16.0.0/12 -j DROP ; 
sudo iptables -A INPUT -s 97.112.0.0/12 -j DROP ;
sudo iptables -A INPUT -s 71.32.0.0/13 -j DROP ; 
sudo iptables -A INPUT -s 71.208.0.0/12 -j DROP

done
exit

---

### Post by jgedeon on 2011-01-02
Why not set up a firewall rule that only allows the access you want?

/etc/init.d/firewall
```

#!/bin/sh
	 
	iptables=/sbin/iptables
	ip6tables=/sbin/ip6tables
	
	### BEGIN INIT INFO
	# Provides:          	iptables firewall
	# Required-Start:    	$network $remote_fs $syslog
	# Required-Stop:   	
	# Default-Start:     	2 3 4 5
	# Default-Stop:      	
	# Short-Description:	Host based firewall
	# Description:		This is the host based firewall
	### END INIT INFO
	
	## BEGIN Objects
	
	ADMINACCESS='
	LIST OF ADDRESS
	PLACED HERE FOR
	ADMIN ACCESS
	'
	
	HTTPACCESS='
	LIST OF IPS
	FOR WEB ACCESS
	'
	

	## END Objects
	
	## BEGIN Script
	
	# Disable routing
	echo 0 > /proc/sys/net/ipv4/ip_forward
	
	# Defaults
	$iptables -F
	$iptables -X
	$iptables -Z
	
	$ip6tables -F
	$ip6tables -X
	$ip6tables -Z
	
	$iptables -t nat -F
	$iptables -t nat -X
	$iptables -t nat -Z
	
	# Default Policy
	$iptables -P INPUT DROP
	$iptables -P FORWARD DROP
	$iptables -P OUTPUT ACCEPT
	$ip6tables -P INPUT DROP
	$ip6tables -P FORWARD DROP
	$ip6tables -P OUTPUT DROP
	
	# Allow local and related traffic
	$iptables -A INPUT -i lo -j ACCEPT
	$iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
	
	# Allow remote admin and backups
	for i in ${ADMINACCESS}; do
	        $iptables -A INPUT -s $i -p icmp -j ACCEPT
	        $iptables -A INPUT -s $i -p tcp --dport 22 -m state --state NEW -j ACCEPT
	done
	
	# Allow HTTP Access
	for i in ${HTTPACCESS}; do
	        $iptables -A INPUT -s $i -p icmp -j ACCEPT
	        $iptables -A INPUT -s $i -p tcp --dport 80 -m state --state NEW -j ACCEPT
	        $iptables -A INPUT -s $i -p udp --dport 443 -m state --state NEW -j ACCEPT
	done
	
	## END Script

```

---

### Post by WorMzy on 2011-01-02
What on earth are you trying to do by spamming iptables with redundant rules? :confused:

You only need to add a rule once, there's no need to keep adding them over and over.

---

### Post by icelogic on 2011-01-02
well to be honest i am new to Ubuntu GNU/Linux i am a noob really.  i really appreciate your reply but i dont know much at the moment once i learn a little more i will try to digest what you wrote.  At the moment i blocking those proxy server ips is working great at keeping the unwanted traffic off my server.  It may be crude but it works and i just want to get the script i wrote working.  once i can get that working i will educate my self a little more but i don't think i am even close to your level of understanding Ubuntu at the moment :p

---

### Post by icelogic on 2011-01-02
> **WorMzy said:**
> What on earth are you trying to do by spamming iptables with redundant rules? :confused:

You only need to add a rule once, there's no need to keep adding them over and over.
\


can i please see an example

---

### Post by jgedeon on 2011-01-02
> **icelogic said:**
> \


can i please see an example

iptables -P INPUT DROP

Will set to drop all the incoming traffic.

---

### Post by QLee on 2011-01-02
And icelogic, a default installation of Ubuntu doesn't have anything listening for connection on any of your ports so they wouldn't get in anyway.

---

### Post by icelogic on 2011-01-02
> **jgedeon said:**
> iptables -P INPUT DROP

Will set to drop all the incoming traffic.




thanks for the command its good to know but unfortunately i am running a public server and i don't want to drop all the incoming traffic just the spammer from those ranges.

---

### Post by jgedeon on 2011-01-02
What services do you want accessible publicly?

---

### Post by icelogic on 2011-01-02
http (AKA port 80) and another port is accessible publicly but i have a spammer i need to block.  i already have it all taken care of i just want to get my script running thats all.  i can paste it all in to a terminal and it works, but i want to have a script just to learn how to do the same think with a script thats all really.

---

### Post by jgedeon on 2011-01-02
Just add the IP's that you will be administrating the server from in he ADMNINACCESS section at the top then place in /etc/init.d/firewell then chmod +x /etc/init.d/firewall  then update-rc.d firewall defaults then run /etc/init.d/firewall  And they shall be blocked.  If you need to add more add them to the THEBANNED section.

```

#!/bin/sh
         
iptables=/sbin/iptables
ip6tables=/sbin/ip6tables

### BEGIN INIT INFO
# Provides:             iptables firewall
# Required-Start:       $network $remote_fs $syslog
# Required-Stop:   
# Default-Start:        2 3 4 5
# Default-Stop:      
# Short-Description:    Host based firewall
# Description:          This is the host based firewall
### END INIT INFO

## BEGIN Objects

        ADMINACCESS='
        LIST OF ADDRESS
        PLACED HERE FOR
        ADMIN ACCESS
        '

        THEBANNED='
        173.0.0.0/20 
        173.192.0.0/15 
        184.82.0.0/16 
        72.20.37.208/28 
        67.228.112.64/27 
        173.244.192.0/19 
        67.162.0.0/17 
        188.0.0.0/8 
        204.12.247.216/29 
        76.73.0.0/17 
        204.74.208.0/20 
        217.0.0.0/8 
        94.0.0.0/8 
        85.0.0.0/8 
        78.0.0.0/8 
        74.86.0.0/16 
        38.0.0.0/8 
        66.55.128.0/19 
        89.0.0.0/8 
        110.0.0.0/8 
        213.0.0.0/8 
        174.143.144.0/21 
        173.234.56.0/21 
        77.0.0.0/8 
        174.16.0.0/12 
        97.112.0.0/12
        71.32.0.0/13 
        71.208.0.0/12
        '

## END Objects

## BEGIN Script

        # Disable routing
        echo 0 > /proc/sys/net/ipv4/ip_forward

        # Defaults
        $iptables -F
        $iptables -X
        $iptables -Z

        $ip6tables -F
        $ip6tables -X
        $ip6tables -Z

        $iptables -t nat -F
        $iptables -t nat -X
        $iptables -t nat -Z

        # Default Policy
        $iptables -P INPUT DROP
        $iptables -P FORWARD DROP
        $iptables -P OUTPUT ACCEPT
        $ip6tables -P INPUT DROP
        $ip6tables -P FORWARD DROP
        $ip6tables -P OUTPUT DROP

        # Allow local and related traffic
        $iptables -A INPUT -i lo -j ACCEPT
        $iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

        # Allow remote admin and backups
        for i in ${ADMINACCESS}; do
                $iptables -A INPUT -s $i -p icmp -j ACCEPT
                $iptables -A INPUT -s $i -p tcp --dport 22 -m state --state NEW -j ACCEPT
        done

         # Drop Banned Traffic
        for i in ${THEBANNED}; do
                $iptables -A INPUT -s $i -j DROP
        done

        # Production Traffic
        # Allow WEB Traffic
                $iptables -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT
                $iptables -A INPUT -p tcp --dport 443 -m state --state NEW -j ACCEPT


## END Script
```

---

### Post by icelogic on 2011-01-02
> **jgedeon said:**
> Just add the IP's that you will be administrating the server from in he ADMNINACCESS section at the top then place in /etc/init.d/firewell then chmod +x /etc/init.d/firewall  then update-rc.d firewall defaults then run /etc/init.d/firewall  And they shall be blocked.  If you need to add more add them to the THEBANNED section.

```

#!/bin/sh
         
iptables=/sbin/iptables
ip6tables=/sbin/ip6tables

### BEGIN INIT INFO
# Provides:             iptables firewall
# Required-Start:       $network $remote_fs $syslog
# Required-Stop:   
# Default-Start:        2 3 4 5
# Default-Stop:      
# Short-Description:    Host based firewall
# Description:          This is the host based firewall
### END INIT INFO

## BEGIN Objects

        ADMINACCESS='
        LIST OF ADDRESS
        PLACED HERE FOR
        ADMIN ACCESS
        '

        THEBANNED='
        173.0.0.0/20 
        173.192.0.0/15 
        184.82.0.0/16 
        72.20.37.208/28 
        67.228.112.64/27 
        173.244.192.0/19 
        67.162.0.0/17 
        188.0.0.0/8 
        204.12.247.216/29 
        76.73.0.0/17 
        204.74.208.0/20 
        217.0.0.0/8 
        94.0.0.0/8 
        85.0.0.0/8 
        78.0.0.0/8 
        74.86.0.0/16 
        38.0.0.0/8 
        66.55.128.0/19 
        89.0.0.0/8 
        110.0.0.0/8 
        213.0.0.0/8 
        174.143.144.0/21 
        173.234.56.0/21 
        77.0.0.0/8 
        174.16.0.0/12 
        97.112.0.0/12
        71.32.0.0/13 
        71.208.0.0/12
        '

## END Objects

## BEGIN Script

        # Disable routing
        echo 0 > /proc/sys/net/ipv4/ip_forward

        # Defaults
        $iptables -F
        $iptables -X
        $iptables -Z

        $ip6tables -F
        $ip6tables -X
        $ip6tables -Z

        $iptables -t nat -F
        $iptables -t nat -X
        $iptables -t nat -Z

        # Default Policy
        $iptables -P INPUT DROP
        $iptables -P FORWARD DROP
        $iptables -P OUTPUT ACCEPT
        $ip6tables -P INPUT DROP
        $ip6tables -P FORWARD DROP
        $ip6tables -P OUTPUT DROP

        # Allow local and related traffic
        $iptables -A INPUT -i lo -j ACCEPT
        $iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

        # Allow remote admin and backups
        for i in ${ADMINACCESS}; do
                $iptables -A INPUT -s $i -p icmp -j ACCEPT
                $iptables -A INPUT -s $i -p tcp --dport 22 -m state --state NEW -j ACCEPT
        done

         # Drop Banned Traffic
        for i in ${THEBANNED}; do
                $iptables -A INPUT -s $i -j DROP
        done

        # Production Traffic
        # Allow WEB Traffic
                $iptables -A INPUT -p tcp --dport 80 -m state --state NEW -j ACCEPT
                $iptables -A INPUT -p tcp --dport 443 -m state --state NEW -j ACCEPT


## END Script
```


OK thanks a lot i will save this script.

---

### Post by icelogic on 2011-01-02
i figured it out it was probably not the right way but works like a charm for a noob like my self. thanks to all for your help especially jgedeon.  May be in the new future i will use your script once i learn a little more.  [B]but here is what i did

in gedit i put this in there, made it executable and named it ban.sh

i right click it to run it in the [/B]terminal and put in my sudo pass and its runs then dissapears in a second. i dont know if it qualifys as a shell script but it works.

here is what it is in its entirety

sudo iptables -A INPUT -s 173.0.0.0/20 -j DROP ; 
sudo iptables -A INPUT -s 173.192.0.0/15 -j DROP ; 
sudo iptables -A INPUT -s 184.82.0.0/16 -j DROP ; 
sudo iptables -A INPUT -s 72.20.37.208/28 -j DROP ; 
sudo iptables -A INPUT -s 67.228.112.64/27 -j DROP ; 
sudo iptables -A INPUT -s 173.244.192.0/19 -j DROP ; 
sudo iptables -A INPUT -s 67.162.0.0/17 -j DROP ; 
sudo iptables -A INPUT -s 188.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 204.12.247.216/29 -j DROP ; 
sudo iptables -A INPUT -s 76.73.0.0/17 -j DROP ; 
sudo iptables -A INPUT -s 204.74.208.0/20 -j DROP ; 
sudo iptables -A INPUT -s 217.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 94.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 85.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 78.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 74.86.0.0/16 -j DROP ; 
sudo iptables -A INPUT -s 38.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 66.55.128.0/19 -j DROP ; 
sudo iptables -A INPUT -s 89.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 110.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 213.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 174.143.144.0/21 -j DROP ; 
sudo iptables -A INPUT -s 173.234.56.0/21 -j DROP ; 
sudo iptables -A INPUT -s 77.0.0.0/8 -j DROP ; 
sudo iptables -A INPUT -s 174.16.0.0/12 -j DROP ; 
sudo iptables -A INPUT -s 97.112.0.0/12 -j DROP ;
sudo iptables -A INPUT -s 71.32.0.0/13 -j DROP ; 
sudo iptables -A INPUT -s 71.208.0.0/12 -j DROP

---

### Post by WorMzy on 2011-01-02
You don't need a script, just declare the rules once, then run
```
sudo /etc/init.d/iptables save
```
To store them in the IPTables config file. They will then be loaded when IPtables starts up.

---

### Post by icelogic on 2011-01-02
> **WorMzy said:**
> You don't need a script, just declare the rules once, then run
```
sudo /etc/init.d/iptables save
```To store them in the IPTables config file. They will then be loaded when IPtables starts up.

Thanks for showing me how to save the rules and letting me know that it will auto load them when the comp is rebooted.  If i do a iptables -F which is the flush command to flush everything will it still work? 

the solution with a little shell script works for me because i have to frequently add new ranges and occasionally remove old ranges.  it makes it easy to edit and execute in the fly.

---

### Post by icelogic on 2011-01-02
I am marking this thread as solved thanks all for you feed back and suport.

---

### Post by WorMzy on 2011-01-02
I don't think I've ever flushed my rules.. but I'd expect that, unless you "save" after a flush, the rules will be re-loaded after the daemon (or PC) is restarted.

---

### Post by icelogic on 2011-01-02
> **WorMzy said:**
> I don't think I've ever flushed my rules.. but I'd expect that, unless you "save" after a flush, the rules will be re-loaded after the daemon (or PC) is restarted.

ok thanks, i got a better understanding of things over all now.

---

