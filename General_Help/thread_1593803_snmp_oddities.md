---
title: "snmp oddities"
date: 2010-10-11
forum: General Help
---

### Post by digitalramble on 2010-10-11
So, I have three machines, all running Ubuntu, one is 9.10 the others 10.4.  I can't upgrade the 9.10 one, but I really doubt the version difference is what's giving me a headache.  Well, I really HOPE that's not what is going on :(

So basically, I have installed snmp on all three machines using the same set of steps:

apt-get install snmpd snmp;
edit the /etc/snmp/snmpd.conf file for the communities, execs and procs that I want;
edit the /etc/default/snmpd to remove the local host in the snmpd invocation so that remote hosts can query it;
restart snmpd with the revised conf files

Upshot: I can do a basic snmpwalk query to and from the 10.4 machines (both ways), and I can do the snmpwalk from 9.10 to the other two, but no one can reach the 9.10 (it just times out).

tcpdump -s0 -v port snmp shows that the snmpwalk query comes TO the 9.10 machine just fine, the 9.10 machine as far as I can see just ignores it and does not respond at all.

Now, one thing going on with the 9.10 (and the reason I can't reboot or upgrade it or whatever) that is absent from the 10.04 machines is that there's more than one IP address linked to eth0 and there are various udp services using the second ip address (although, none on port 161, as verified thru netstat -an | grep udp). 

I suspect that it might be either listening to the wrong IP address and/or responding to the wrong IP address.  (I have tried the snmpwalk with the alternate IP address with the same timeout result, though.)

But regardless, I've tried the following in the snmpd.conf file and either this isn't the answer, or this isn't the right invocation:

rocommunity tester default

#interface eth0 2
interface eth0 regular1822
#agentaddress xx.xx.xx.xx:161

(where xx.xx.xx.xx is the IP address of 9.10 that I *want* to use)
I've experimented with different values for interface (it's hard to find documentation on it, it wants interface name type speed.  Speed seems to be optional, but values for type are hard to determine.

If anyone can tell me how to force an snmpd daemon to listen to a particular port or give me some other suggestions for things to troubleshoot given this scenario, I'd be deeply appreciative.  Have been batting my head on this for a while.

Thanks,
--Cindy

---

