---
title: "UBUNTU 9.10 - using rsyslog to log router activity in separate file"
date: 2009-12-08
forum: General Help
---

### Post by bionicdude on 2009-12-08
Hey,

I've enabled the syslog daemon to receive external comms (-r).
I'm getting my router activity show up in the /var/log/syslog file.

Now all i want to do is separate out these logs into /var/log/router.log

I added
local0.debug    /var/log/router.log
to my rsyslog.conf, but to no avail.

using the logger util, i can successfully post to local0 and it appears in my router.log.

So it just sounds like i need to find the right facility to use for my D-LINK DIR-635 router, right?

I've had no luck in google or official docs.

So my two questions are:
1. anyone know what facility these messages are sent with or how i would find out?
2. Am I even on the right path here?

Thanks in advance to anyone that can help..

---

### Post by encore2097 on 2010-01-25
This is already assuming you modified your router to send logging to a remote server.

In */etc/rsyslog.conf* uncomment the following lines

```

# provides UDP syslog reception
$ModLoad imudp
$UDPServerRun 514

# provides TCP syslog reception
$ModLoad imtcp
$InputTCPServerRun 514

```

Then append into the end of */etc/rsyslog.conf* or into */etc/rsyslog.d/50-default.conf*

```

# Router logging
:source, isequal, "router_address" /var/log/<log_file_name>
& ~

```

Finally,
```
sudo restart rsyslog
```

---

### Post by bionicdude on 2010-01-26
Hey,

Thanks for your reply. I added the following to my rsyslog.conf

```

# Router logging
:source, isequal, "192.168.11.1" /var/log/router.log
:source, isequal, "192.168.11.1" ~

```

but it still didn't seem to work. Thankfully though, your tip gave me the lead i was looking for and managed to track down other examples in the documentation.
in the end i've managed to use

:msg, contains, "routername", /var/log/router.log

This works well as my router sends its name with every message and is now writing to the router.log.

My bad news is that it's still also writing to syslog. Any idea how to stop this? In the meantime i'll go back to the documentation and see if i can spot the answer.

Thanks again for your help.

---

### Post by bionicdude on 2010-01-26
Hey,

I now understand the ~ on the second line you gave me.

It seems that the default conf files are read in first, so i just had to add that stuff to the top of that file so that we logged to router.log and then discarded the message from further processing.

You've been most helpful. Thank you.

---

### Post by encore2097 on 2010-01-26
The second line should have been 
```
& ~
```
I updated the original post.

It seems you got it working, if you want you can also try 
```
:fromhost-ip, isequal, "router_address" /var/log/<log_file_name>
```

This page is also extremely helpful
[http://www.rsyslog.com/doc-multi_ruleset.html](http://www.rsyslog.com/doc-multi_ruleset.html)

You also should look into adding a logrotate script, here's mine.
```

/var/log/<log_file_name>
{
        rotate 12
        monthly
        missingok
        notifempty
        compress
        delaycompress
        postrotate
                reload rsyslog >/dev/null 2>&1 || true
        endscript
}

```

---

### Post by el.demiurgo on 2010-04-19
Hi,
I did this but it seems that I am not being able to log all events.

If I compare my router's web configuration against the log in my PC I find that I am missing some lines. For example:

INSIDE ROUTER:
Mon Apr 19 20:46:10 2010 Unallowed access from WLAN 00-05-CD-14-4F-57

Mon Apr 19 20:46:10 2010 Unallowed access from WLAN 00-05-CD-14-4F-57

Mon Apr 19 20:46:14 2010 Unallowed access from WLAN 00-05-CD-14-4F-57

Mon Apr 19 20:46:22 2010 Unallowed access from WLAN 00-05-CD-14-4F-57

Mon Apr 19 20:46:25 2010 ICMP: type 3 code 1 from 115.163.251.157
Mon Apr 19 20:46:26 2010 Unallowed access from WLAN 00-05-CD-14-4F-57

Mon Apr 19 20:46:26 2010 Unallowed access from WLAN 00-05-CD-14-4F-57

Mon Apr 19 20:46:38 2010 Unallowed access from WLAN 00-05-CD-14-4F-57

INSIDE LOG:
Apr 19 21:21:55 192.168.0.1 ICMP: type 3 code 1 from 90.28.156.212#015
Apr 19 21:23:55 192.168.0.1 ICMP: type 3 code 1 from 115.163.251.157#015
Apr 19 21:26:55 192.168.0.1 ICMP: type 3 code 1 from 86.28.225.204#015
Apr 19 21:27:10 192.168.0.1 ICMP: type 3 code 1 from 88.223.0.119#015


I find that:
1) time stamps are different (check the event with IP 115.163.251.156)
2) No unallowed access is registered in LOG (and that's what I need).

Any thoughts?

Thank you!

---

### Post by dcstar on 2010-04-20
> **el.demiurgo said:**
> Hi,
I did this but it seems that I am not being able to log all events.
......
Any thoughts?

Thank you!

Most systems have different settings for internal and external logging.

Telnet into your router and see if you can access the external logging setup.

---

### Post by bionicdude on 2010-04-20
My router always sends its name in each message, so i was able to follow encore's suggestion.

It looks like your router is always sending its IP, so could you not filter on that?

```

# Router logging
:msg, contains, "192.168.0.1" /var/log/router.log
:msg, contains, "192.168.0.1" ~

```

Adding the above to your /etc/rsyslog.d/50-default.conf file might then work (although you might want to change the log path to suit your needs..)

---

### Post by dumezil on 2011-12-01
thanks for this!  this also works for 11.10.

this is what I added to /etc/rsyslog.d/40-router.conf:

```
:msg, contains, "DIR-655" /var/log/router.log
& ~
```

notice I used 40-router.conf.  the number prefix needs to be below 50 to apply before 50-default.conf which will log your router logs into /var/log/syslog

hope this helps someone

> **bionicdude said:**
> My router always sends its name in each message, so i was able to follow encore's suggestion.

It looks like your router is always sending its IP, so could you not filter on that?

```

# Router logging
:msg, contains, "192.168.0.1" /var/log/router.log
:msg, contains, "192.168.0.1" ~

```

Adding the above to your /etc/rsyslog.d/50-default.conf file might then work (although you might want to change the log path to suit your needs..)

---

### Post by oldos2er on 2011-12-02
Closed, necromancy.

---

