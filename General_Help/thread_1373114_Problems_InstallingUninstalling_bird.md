---
title: "Problems Installing/Uninstalling bird"
date: 2010-01-05
forum: General Help
---

### Post by Avidanis on 2010-01-05
In my search for a security solution I came across bird,which is an [Internet Routing Daemon]("http://bird.network.cz/?get_doc&f=bird-1.html#ss1.2").
When I attempted to install using Synaptic Package Manager I got an error on install . When I attempted to uninstall , I still got  an error and the packages are still apparently installed. 

I took a look at the syslog and the error says syntax error line 20 . 

Here is a look at bird.conf

```
/*
 *    This is an example configuration file.
 */

# Yes, even shell-like comments work...

# Configure logging
#log syslog { debug, trace, info, remote, warning, error, auth, fatal, bug };
#log stderr all;
#log "tmp" all;

# Override router ID
#router id 62.168.0.1;

# You can define your own symbols...
#define xyzzy = 120+10;

# Define a route filter...
filter test_filter {
  **  if net ~ 10.0.0.0/16 then accept;**
    else reject;
}

#filter sink { reject; }
#filter okay { accept; }

# Define another routing table
#table testable;

# Turn on global debugging of all protocols
#debug protocols all;

# The direct protocol automatically generates device routes to
# all network interfaces. Can exist in as many instances as you wish
# if you want to populate multiple routing tables with device routes.
protocol direct {
#    interface "-eth*", "*";    # Restrict network interfaces it works with
}

# This pseudo-protocol performs synchronization between BIRD's routing
# tables and the kernel. If your kernel supports multiple routing tables
# (as Linux 2.2.x does), you can run multiple instances of the kernel
# protocol and synchronize different kernel tables with different BIRD tables.
protocol kernel {
#    learn;            # Learn all alien routes from the kernel
    persist;        # Don't remove routes on bird shutdown
    scan time 20;        # Scan kernel routing table every 20 seconds
#    import none;        # Default is import all
    export all;        # Default is export none
#    kernel table 5;        # Kernel table to synchronize with (default: main)
}

# This pseudo-protocol watches all interface up/down events.
protocol device {
    scan time 10;        # Scan interfaces every 10 seconds
}

# Static routes (again, there can be multiple instances, so that you
# can disable/enable various groups of static routes on the fly).
protocol static {
#    disabled;        # Disable by default
#    table testable;        # Connect to a non-default table
#    preference 1000;    # Default preference of routes
#    debug { states, routes, filters, interfaces, events, packets };
#    debug all;
#    route 0.0.0.0/0 via 62.168.0.13;
#    route 62.168.0.0/25 reject;
#    route 10.0.0.0/8 reject;
#    route 10.1.1.0:255.255.255.0 via 62.168.0.3;
#    route 10.1.2.0:255.255.255.0 via 62.168.0.3;
#    route 10.1.3.0:255.255.255.0 via 62.168.0.4;
#    route 10.2.0.0/24 via "arc0";
}

# Pipe protocol connects two routing tables... Beware of loops.
#protocol pipe {
#    peer table testable;
# Define what routes do we export to this protocol / import from it.
#    import all;        # default is all
#    export all;        # default is none
#    import none;        # If you wish to disable imports
#    import filter test_filter;        # Use named filter
#    import where source = RTS_DEVICE;    # Use explicit filter
#}

# RIP aka Rest In Pieces...
#protocol rip MyRIP {    # You can also use an explicit name
#    preference xyzzy;
#    debug all;
#    port 1520;
#    period 7;
#    infinity 16;
#    garbage time 60;
#    interface "*" { mode broadcast; };
#    honor neighbor;        # To whom do we agree to send the routing table
#    honor always;
#    honor never;
#    passwords { password "ahoj" from 0 to 10;
#        password "nazdar" from 10;
#    }
#    authentication none;
#    import filter { print "importing"; accept; };
#    export filter { print "exporting"; accept; };
#}

#protocol ospf MyOSPF {
#       tick 2;
#    rfc1583compat yes;
#    area 0.0.0.0 {
#        stub no;
#        interface "eth*" {
#            hello 9;
#            retransmit 6;
#            cost 10;
#            transmit delay 5;
#            dead count 5;
#            wait 50;
#            type broadcast;
#            authentication simple;
#            password "pass";
#        };
#        interface "arc0" {
#            rx buffer large;
#            type nonbroadcast;
#            poll 14;
#            dead 75;
#            neighbors {
#                10.1.1.2 eligible;
#                10.1.1.4;
#            };
#            strict nonbroadcast yes;
#        };
#        interface "xxx0" {
#                       passwords {
#                password "abc" {
#                    id 1;
#                    generate to "22-04-2003 11:00:06";
#                    accept to "17-01-2004 12:01:05";
#                };
#                password "def" {
#                    id 2;
#                    generate from "22-04-2003 11:00:07";
#                    accept from "17-01-2003 12:01:05";
#                };
#                       authentication cryptographic;
#        };
#    };
#    area 20 {
#        stub 1;
#        interface "ppp1" {
#            hello 8;
#            authentication none;
#        };
#               interface "fr*";
#               virtual link 192.168.0.1 {
#                       password "sdsdffsdfg";
#                       authentication cryptographic;
#               };
#    };
#}
        

#protocol bgp {
#    disabled;
#    local as 65000;
#    neighbor 62.168.0.130 as 5588;
#    multihop 20 via 62.168.0.13;
#    hold time 240;
#    startup hold time 240;
#    connect retry time 120;
#    keepalive time 80;    # defaults to hold time / 3
#    start delay time 5;    # How long do we wait before initial connect
#    error wait time 60, 300;# Minimum and maximum time we wait after an error (when consecutive
#                # errors occur, we increase the delay exponentially ...
#    error forget time 300;    # ... until this timeout expires)
#    disable after error;    # Disable the protocol automatically when an error occurs
#    next hop self;        # Disable next hop processing and always advertise our local address as nexthop
#    path metric 1;        # Prefer routes with shorter paths (like Cisco does)
#    default bgp_med 0;    # MED value we use for comparison when none is defined
#    default bgp_local_pref 0;    # The same for local preference
#    source address 62.168.0.14;    # What local address we use for the TCP connection
#    password "secret"    # Password used for MD5 authentication
#    rr client;        # I am a route reflector and the neighor is my client
#    rr cluster id 1.0.0.1    # Use this value for cluster id instead of my router id 
#    export where source=RTS_STATIC;
#    export filter {
#        if source = RTS_STATIC then {
##            bgp_community = -empty-; bgp_community = add(bgp_community,(65000,5678));
##            bgp_origin = 0;
#            bgp_community = -empty-; bgp_community.add((65000,5678));
##            if (65000,5678) ~ bgp_community then
##                bgp_community.add((0, 1));
#            if bgp_path ~ [= 65000 =] then
#                bgp_path.prepend(65000);
#            accept;
#        }
#        reject;
#    };
#}
```Line 20 is bolded. It looks like most all of the program statements are commented out. 

I guess my question is , how do I either
 a.) get bird configured ?    or 
b.) uninstall it and look for something a bit more easier to setup. 

The reason I became a bit concerned is this morning I was googling for some information . I ended up here , holaloha.iespana.es and got redirected to what i suspect was  a malware site . This --> ```
computerscanm0.com
```This site in turn activated a pop-up saying my computer might be at risk for a virus and do I want to scan for a virus. 

[ATTACH]142563[/ATTACH]

The pop-up somehow got around the pop-up blocker and locked firefox. So I opened another firefox and disabled javascript and java . Then I opened up System moniter and killed firefox. I know , not very  elegant . Then I ran KlamAV . Nothing found. 

Summary. 

Since that episode i looked for Firefox add-ons that might serve as a buffer against this type of thing. I found WOT and installed it . I then revisted that web site and sure enough WOT popped up a warning message. 

Anyone have any experience with a good way to lock down the laptop (wireless) that does'nt require a sys admin with a degree in computer science to install and configure I would be glad to hear from you. 

Also the original question about bird . Why can't I uninstall that thing ?

---

