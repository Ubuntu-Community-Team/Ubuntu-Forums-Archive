---
title: "Cannot access server on port 80 or 8080"
date: 2010-12-15
forum: General Help
---

### Post by naijatexan on 2010-12-15
I installed Ubuntu Maverick 10.10 on an Amazon EC2 instance (micro).  This is the AMI used:
http://aws.amazon.com/amis/4349?_encoding=UTF8&jiveRedirect=1

I found that here:
https://help.ubuntu.com/community/EC2StartersGuide

So I created this instance with this command:
ec2-run-instances ami-508c7839 -k ec2-keypair --instance-type t1.micro

Via SSH I was able to install Java and Atlassian JIRA, and all I want to do with the instance is run JIRA on it.  I installed JIRA Standalone which has its own Tomcat bundled, and using wget I was able to pull the HTML from localhost:8080 and verify that JIRA was running.  The HTML contained the JIRA setup page, e.g. here's the title tag:

<title>Your Company JIRA - JIRA Setup</title>

From both the EC2 command line tools and the AWS web-based control panel, I've opened up ports 80 and 8080 for HTTP/TCP traffic.  However, I cannot get to JIRA in my web browser when I put in the Amazon host with port 8080 tacked onto the URL:

Oops! Google Chrome could not connect to 182.72.99.999:8080

(Note:  I changed part of the IP address).  I'm suspecting iptables is the issue, but I'm not sure and don't have much experience with that.  After all, SSH was already open even though iptables had no entries in it.  Here's what iptables has in it now that I've tried commands I've seen in various tutorials:

$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:http-alt 
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     all  --  anywhere             anywhere            ctstate RELATED,ESTABLISHED 

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         


Can you tell why I might not be able to get to 8080 from that?  

Thanks!

---

### Post by naijatexan on 2010-12-16
$ netstat -lt
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address Foreign Address State 
tcp 0 0 *:ssh : LISTEN 
tcp6 0 0 localhost:8005 :::* LISTEN 
tcp6 0 0 :::http-alt :::* LISTEN 
tcp6 0 0 :::ssh :::* LISTEN 


Does anyone know why the Tomcat bundled with Jira is only listening with ipv6? All I did was run Jira with the startup.sh script! I haven't done anything on this Ubuntu image except install Java and Jira.  Could something be blocking Tomcat on ipv4?

---

### Post by drdos2006 on 2010-12-16
This is from a previous thread I saved because it helped me.
> 
You may be having connection issues because of IPv6 even though it shows an IPv4 connection. 

 How do I prove ipv6 has been successfully disabled
There seems to be much disagreement between distros regarding how ipv6 is disabled, even between different versions of the same distro. Rather than just follow instructions for disabling ipv6 for a given distro, I would like to also test that ipv6 is not used any more. Any software or executable that relies on ipv6, that I can use to confirm that ipv6 has been successfully disabled?

cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf

Code:

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
ifconfig should not mention an IPV6 address on any interface after you have rebooted.

IPV6 should still be considered in your security setup on your machine, just in case it is, for example, re-enabled after an upgrade etc.

To check if IPv6 is enabled, just simply use netstat:

Code:

netstat -tlv

If you see any "tcp6" entries, then IPv6 is not disabled.

You may be also having IPv6 problems in your browser.
For Firefox, type about:config in the browser bar.
Filter with network.dns
Change IPv6disabled to true
Restart Firefox.


regards

---

### Post by qip on 2010-12-16
If I am not wrong, EC2 has its own firewall outside the instance. You may want to check it in your AWS Management Console.

---

### Post by aboutme475 on 2011-08-01
I'm using Ubuntu 9.04  and I'm not able to change /proc/sys/net/ipv6/conf/eth0/disable_ipv6 in order to set it to "1" instead of "0".  Currently no one can ssh to my machine, not even our system Admins.  This imposes a problem as the machine is at a remote location.  
When i vi the file /proc/sys/net/ipv6/conf/eth0/disable_ipv, i get the following error:

"/proc/sys/net/ipv6/conf/eth0/disable_ipv" E667: Fsync failed.  Please Enter a command.

Can someone please let me know how to shut off IPV6 on this verision?

---

### Post by soopastar on 2011-08-24
quoted from above:
Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf
# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
ifconfig should not mention an IPV6 address on any interface after you have rebooted.



/code
thanks for this post.  I was just looking into this today.

---

