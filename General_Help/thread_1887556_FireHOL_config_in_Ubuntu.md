---
title: "FireHOL config in Ubuntu"
date: 2011-11-27
forum: General Help
---

### Post by spec36 on 2011-11-27
I have been hacking around with fireHOL firewall configuration and have finally got something working, but I am a little confused on how exactly this is working. Any insight would be greatly appreciated.

I have installed fireHOL on one machine that does NOT run any servers (http, dns, etc...) The machine has only one interface eth0, which is connected to my router/gateway to access the internet. This machine is only a client for http requests, etc... Therefore, I only want this box to be able to access the services it will be using (HTTP, dhcp, etc....) 

fireHOL config
```

#LAN Traffic
#--------------------------------------------------------
# The purpose of this interface is to control the traffic on eth0
# interface with ip 192.168.1.102 
#--------------------------------------------------------
interface eth0 lan src "192.168.1.0/24" dst 192.168.1.102

        policy reject
        protection strong 10/sec 10
        client all accept


#Internet Traffic
#-----------------------------------------------------------------------------------
#The purpose of this interface is to control the traffic from/to unknown networks
#behind the default gateway 192.168.1.143.
#-----------------------------------------------------------------------------------
interface eth0 internet src not "${UNROUTABLE_IPS} 192.168.1.0/24" dst 192.168.1.102
        policy drop
        protection strong 10/sec 10

        client http accept
        client https accept

```With the below config I tried changing the "client all accept" line to "client http accept" to only allow http requests, but for some reason I cannot surf the internet when I do that. The only way I can surf the internet is to leave that line as "client all accept". I understand this as accept all incoming service requests from any host in network 192.168.1.0/24, but I don't want to accept all service requests, just the ones that the box uses. Any idea why this is happening? or am I reading the config logic incorrectly?
```

#LAN Traffic
#--------------------------------------------------------
# The purpose of this interface is to control the traffic on eth0
# interface with ip 192.168.1.102 
#--------------------------------------------------------
interface eth0 lan src "192.168.1.0/24" dst 192.168.1.102

        policy reject
        protection strong 10/sec 10
        client all accept

```With the below code I do not understand why the dst is 192.168.1.102. Should it not be 192.168.1.143, as this is the gateway (destination) of where my http traffic is going? Am I reading this config logic incorrectly?

```

#Internet Traffic
#-----------------------------------------------------------------------------------
#The purpose of this interface is to control the traffic from/to unknown networks
#behind the default gateway 192.168.1.143.
#-----------------------------------------------------------------------------------
interface eth0 internet src not "${UNROUTABLE_IPS} 192.168.1.0/24" dst 192.168.1.102
        policy drop
        protection strong 10/sec 10

        client http accept
        client https accept

```Any help would be greatly appreciated. I just got this working, but am super confused on why exactly it is working, and if it is properly secure/setup.

Thanks

---

### Post by spec36 on 2011-11-27
OK I figured it out. I was just thinking stupid.

The first box set of rules are for all LAN traffic hitting my box. so whatever I allow there will be able to communicate with my box. I did not have dns allowed, which is why the internet stopped working.

The second config controls all internet traffic that reaches my box.

FireHOL is so simple now that I see what I did. If any of you want a quick and easy firewall I recommend giving it a try.

---

