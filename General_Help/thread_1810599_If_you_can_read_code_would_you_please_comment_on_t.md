---
title: "If you can read code would you please comment on this."
date: 2011-07-23
forum: General Help
---

### Post by stevennlv on 2011-07-23
I couldn't code my way out of a wet paper bag with a bazooka. 

I've been looking for a tool to do a very specific job. I couldn't find a program. But I did find this on a web site. Since it is from an unknown source and I can't read it I would greatly appreciate it if lots of folks would put eyes on it and tell me if it will blow up my machine!

>  ...here is my solution, that includes notifying you when someone attempts  to connect to your port (this is a feature missing in all of the Linux  firewalls I have found and seems to be a common complaint)  the finished  product will look something like the photo above.

Ingredients:

[LIST]
[*]Ubuntu / Distro of your choice.
[*][iptables]("https://help.ubuntu.com/community/IptablesHowTo") (installed by default in Ubuntu 10.10)
[*][gufw]("http://gufw.tuxfamily.org/") (sudo apt-get install gufw)
[*]notify-send / espeak / xmessage / zenity / other communication interface
[/LIST]

Instructions:

[LIST=1]
[*] Install all of the above.
[*]Under System > Administration > Firewall Configuration, set Incoming to Reject; and turn on the Firewall.
[*]Copy the shell script below to your machine:#!/bin/bash

lastlog=$(dmesg | grep UFW\ BLOCK | tail -1)

while [ 1 -gt 0 ]; do
 
    sleep 1
    
    curlog=$(dmesg | grep UFW\ BLOCK | tail -1)
    
    if [ "$curlog" != "$lastlog" ]; then
        #get information.
        ip=$( echo $curlog | cut -d = -f5 | cut -d \  -f1)
        port=$( echo $curlog | cut -d = -f14 | cut -d \  -f1)
        portfrom=$( echo $curlog | cut -d = -f13 | cut -d \  -f1)
        lastlog=$(dmesg | grep UFW\ BLOCK | tail -1)
        
        #send message.
        notify-send "Src: $ip:$portfrom Dest: $port" -u critical -i security-low
    fi

done
[*]For this to work though, you will need the program  notify-send, if it is not installed, you could replace it with espeak  (to have your computer announce that you dropped a connection),  xmessage, or zenity.
[/LIST]
And even if it is good I'm have no idea how to implement it.

I've been here about week now,

I greatly appreciate any and all help.

Thanks.

---

### Post by Dangertux on 2011-07-23
All it does is check log files to determine if someone attempted to connect to your machine. 

It then gives the output to you including source port destination port source ip etc.

---

