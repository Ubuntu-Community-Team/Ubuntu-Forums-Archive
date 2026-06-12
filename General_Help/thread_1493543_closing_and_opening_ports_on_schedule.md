---
title: "closing and opening ports on schedule"
date: 2010-05-26
forum: General Help
---

### Post by akrobert on 2010-05-26
Hello
Im trying to figure out how I can set up something to automatically open port 119 at 10pm and close it again at 3am..I have looked and am completely confused on how to get this done. Any advice how to do this would be appreciated

thanks
Robert

---

### Post by lovinglinux on 2010-05-26
A port is only open if there is a server listening to it. If you don't have any server listening to port 119, then all connection attempts on that port will be rejected. So you can add a script to cron to start the server at 10pm and shut it down at 3am.

---

### Post by dino99 on 2010-05-26
> **akrobert said:**
> Hello
Im trying to figure out how I can set up something to automatically open port 119 at 10pm and close it again at 3am..I have looked and am completely confused on how to get this done. Any advice how to do this would be appreciated

thanks
Robert

google around iptable, ipblock, moblock

---

### Post by jre on 2010-05-27
> **lovinglinux said:**
> So you can add a script to cron to start the server at 10pm and shut it down at 3am.

Or have the server running around the clock and add a
```
iptables -I INPUT -p tcp --dport 119 -j ACCEPT
iptables -D INPUT -p tcp --dport 119 -j DROP

```
in (is it?) /etc/crontab for 10pm and
```
iptables -I INPUT -p tcp --dport 119 -j DROP
iptables -D INPUT -p tcp --dport 119 -j ACCEPT

```
for 3am.

---

### Post by srs5694 on 2010-05-27
Another option is to run the server via xinetd, which includes access controls by time (check the access_times options in the xinetd.conf man page). This will enable *initial access* within the specified period, but it won't completely shut the port at "closing time." That is, if somebody accesses the port at, say, 2:58 AM, that person can stay connected well past 3:00 AM; but if another access attempt occurs at 3:01 AM, that access will be denied, even though the first user can keep using the server at this time. This approach may or may not be preferable to having a cron job shut down the server or enable iptables rules, as others have suggested; it depends on your purpose for enforcing these rules.

Also, not all servers can be run via xinetd, which is a super server similar to inetd. Some servers are designed to be run independently, some via a super server, and others in either way. You'll need to check you server's documentation to see which it uses. (Presumably you want to run some sort of news server, since port 119 is an NNTP port.)

---

### Post by bodhi.zazen on 2010-05-27
iptables will do this with the -m time option. It is a "one liner" , no need for scripts or cron ...

-m time --timestart HH:MM --timestop HH:MM

```
iptables -A INPUT -p tcp --dport 119 -m time --timestart 03:00 --timestop 22:00 -j DROP
```Assuming your default policy is ACCEPT , the above rule will drop all traffic incoming to port 119 from 3 am to 10 pm. The default policy , ACCEPT, will accept the traffic from 10pm to 3 am.

Modify the rule if you are using a drop policy (switch the time stamp and -J ACCEPT).

---

### Post by akrobert on 2010-05-29
I think I should be more specific.

I have satellite Internet and the free download period runs from 10pm to 3am. During that time I have Usenet going. What i would like to do is somehow set it up so that port 119 nntp is blocked during all times except that time period. I figured there must be come way to block that single port except during the allotted time period but I am unsure how to do it. I can set it up so it blocks all traffic easy enough but was looking for a more fine tuned solution.

thanks
Robert

---

### Post by srs5694 on 2010-05-29
I believe most of the responses you've received so far, including mine, made the incorrect assumption that you wanted to block incoming access to a server running on your system from external clients, rather than block outgoing access from a client running on your system to external servers. My own xinetd suggestion will not work at all for your needs, but a modification of the iptables solutions will work. Instead of modifying the INPUT chain, though, you'd want to adjust the OUTPUT chain. I'm a little rusty on my iptables specifics, so I won't post a specific example.

If you want to access Usenet text-mode (non-binary) newsgroups, you might also consider running [Leafnode,](http://www.leafnode.org) which is a small Usenet server you run locally. It can connect to external servers to download a subset of Usenet newsgroups for local storage and reading at any time you like. You can configure it to connect to outside servers at whatever times are convenient for you. I ran Leafnode for several years myself, as a way of working around flaky Usenet servers run by the ISPs I used at the time; but it's been a while since I used it, so I don't recall all the configuration details.

---

### Post by BoneKracker on 2010-05-30
> **akrobert said:**
> I think I should be more specific.

I have satellite Internet and the free download period runs from 10pm to 3am. During that time I have Usenet going. What i would like to do is somehow set it up so that port 119 nntp is blocked during all times except that time period. I figured there must be come way to block that single port except during the allotted time period but I am unsure how to do it. I can set it up so it blocks all traffic easy enough but was looking for a more fine tuned solution.

thanks
Robert

I think bodhi.zazen's suggestion is the right answer, you'll just have to adapt it.

Since you want it to block internal traffic going out, it would be better to REJECT, rather than DROP, the traffic.

Also, I believe this would go in the FORWARD (not INPUT) table (or, if the traffic is originating from the firewall machine itself, it would go in the OUTPUT table).

---

### Post by andrew.46 on 2010-06-21
Hi srs,

> **srs5694 said:**
>  I ran Leafnode for several years myself, as a way of working around flaky Usenet servers run by the ISPs I used at the time; but it's been a while since I used it, so I don't recall all the configuration details.

Getting away from the OP's question but there is a guide to the development version of leafnode here:

[http://ubuntuforums.org/showthread.php?t=676837](http://ubuntuforums.org/showthread.php?t=676837)

Andrew

---

