---
title: "Apache 2.2.20"
date: 2011-08-31
forum: General Help
---

### Post by hgernhardt on 2011-08-31
I just read that Apache had released 2.2.20, which fixes a rather nasty DOS vulnerability.  Any ideas on release schedules for the supported Ubuntu versions?

Thanks,

Henry

---

### Post by snek on 2011-09-02
Yes I would like to know about this as well, this is a pretty serious security update!

---

### Post by lR2D2l on 2011-09-02
[CVE-2011-3192]("http://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2011-3192")

5 sec, with virtual hosts and server will die =\

---

### Post by pvledoux on 2011-09-06
+1

---

### Post by hansliss on 2011-09-06
Apparently fixed in version 2.2.17-1ubuntu1.2 which is already out:

[http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.17-1ubuntu1.2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.17-1ubuntu1.2/changelog)

/H

---

### Post by upengan78 on 2011-09-06
Hi,

Per [https://launchpad.net/ubuntu/lucid/+source/apache2](https://launchpad.net/ubuntu/lucid/+source/apache2)

installing apache-2.2.14-5ubuntu8.6  on Lucid (10.04LTS) the CVE-2011-3192 vulnerability should be taken care of , correct? However in my case, even after fully updating 10.04 system when I try the killapache script against that system, that system's load average goes up and up and system eventually becomes unresponsive.

```
127.0.0.1 - - [06/Sep/2011:10:31:30 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [06/Sep/2011:10:31:31 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [06/Sep/2011:10:31:32 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [06/Sep/2011:10:31:33 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [06/Sep/2011:10:31:34 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [06/Sep/2011:10:31:35 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [06/Sep/2011:10:31:36 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [06/Sep/2011:10:31:37 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [06/Sep/2011:10:31:38 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)"
127.0.0.1 - - [06/Sep/2011:10:31:39 -0500] "OPTIONS * HTTP/1.0" 200 152 "-" "Apache/2.2.14 (Ubuntu) (internal dummy connection)
```How should I take care of this issue?

Thanks.
Up

---

### Post by Dangertux on 2011-09-06
Also, you can enable the headers module and add this code

```


<IfModule mod_headers.c> # Drop the Range header when more than 5 ranges. 
# CVE-2011-3192 
SetEnvIf Range (?:,.*?){5,5} bad-range=1 
RequestHeader unset 
Range env=bad-range 
# We always drop Request-Range; as this is a legacy 
# dating back to MSIE3 and Netscape 2 and 3. 
RequestHeader unset Request-Range 
# optional logging.
 CustomLog /var/log/apache2/range-CVE-2011-3192.log common env=bad-range 
CustomLog /var/log/apache2/range-CVE-2011-3192.log common env=bad-req-range 
</IfModule>

```source : [http://jon.sprig.gs/blog/2011/08/26/quick-fix-for-apache-cve-2011-3192-ubuntudebian/](http://jon.sprig.gs/blog/2011/08/26/quick-fix-for-apache-cve-2011-3192-ubuntudebian/)
This is the workaround I have been using and works very well.

Also : limiting resource usage for the apache processes does curb it a little bit. The server will not become unresponsive, it will just become extremely slow. You can also mitigate a little by implementing mod QOS

---

### Post by upengan78 on 2011-09-06
Hi Dangertux, thanks for helping me out.

I added that code to headers.conf
a2enable headers
/etc/init.d/apache2 restart

However I am still getting load on system going high.

```
top - 13:32:57 up 3 days, 23:51,  1 user,  load average: 21.74, 9.46, 3.58
Tasks: 147 total,  12 running, 135 sleeping,   0 stopped,   0 zombie
Cpu(s): 28.9%us, 21.2%sy,  0.0%ni,  2.9%id,  0.0%wa,  7.7%hi, 39.2%si,  0.0%st
Mem:    505496k total,   400440k used,   105056k free,    37260k buffers
Swap:   192504k total,     2824k used,   189680k free,   207760k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
31699 www-data  20   0  157m 6780 1760 S  3.9  1.3   0:00.22 apache2                                                                                         
31662 www-data  20   0  157m 6776 1760 R  3.5  1.3   0:01.50 apache2                                                                                         
31687 www-data  20   0  157m 6780 1760 R  3.5  1.3   0:00.68 apache2                                                                                         
31702 www-data  20   0  157m 6772 1760 S  3.5  1.3   0:00.11 apache2                                                                                         
31673 www-data  20   0  157m 6776 1760 S  3.2  1.3   0:01.19 apache2                                                                                         
31655 www-data  20   0  157m 6780 1760 S  2.9  1.3   0:01.68 apache2                                                                                         
31670 www-data  20   0  157m 6784 1764 R  2.9  1.3   0:01.18 apache2                                                                                         
31690 www-data  20   0  157m 6772 1760 S  2.9  1.3   0:00.64 apache2                                                                                         
31648 www-data  20   0  157m 6780 1760 S  2.6  1.3   0:01.94 apache2                                                                                         
31654 www-data  20   0  157m 6780 1760 S  2.6  1.3   0:01.49 apache2                                                                                         
31657 www-data  20   0  157m 6780 1760 S  2.6  1.3   0:01.58 apache2                                                                                         
31658 www-data  20   0  157m 6776 1760 S  2.6  1.3   0:01.59 apache2                                                                                         
31663 www-data  20   0  157m 6780 1760 S  2.6  1.3   0:01.46 apache2                                                                                         
31676 www-data  20   0  157m 6780 1760 S  2.6  1.3   0:01.09 apache2                                                                                         
31695 www-data  20   0  157m 6780 1760 S  2.6  1.3   0:00.25 apache2                                                                                         
31638 www-data  20   0  157m 6780 1760 S  2.3  1.3   0:02.72 apache2                                                                                         
31646 www-data  20   0  157m 6780 1760 S  2.3  1.3   0:02.03 apache2                                                                                         
31650 www-data  20   0  157m 6780 1760 S  2.3  1.3   0:01.66 apache2                                                                                         
31652 www-data  20   0  157m 6780 1760 R  2.3  1.3   0:01.48 apache2                                                                                         
31660 www-data  20   0  157m 6780 1760 S  2.3  1.3   0:01.55 apache2                                                                                         
31664 www-data  20   0  157m 6780 1760 S  2.3  1.3   0:01.51 apache2                                                                                         
31681 www-data  20   0  157m 6772 1760 R  2.3  1.3   0:00.97 apache2                                                                                         
31685 www-data  20   0  157m 6780 1760 S  2.3  1.3   0:00.77 apache2                                                                                         
31689 www-data  20   0  157m 6776 1760 R  2.3  1.3   0:00.56 apache2                                                                                         
31692 www-data  20   0  157m 6772 1760 S  2.3  1.3   0:00.43 apache2                                                                                         
31693 www-data  20   0  157m 6780 1760 R  2.3  1.3   0:00.35 apache2                                                                                         
31694 www-data  20   0  157m 6776 1760 S  2.3  1.3   0:00.33 apache2                                                                                         
31698 www-data  20   0  157m 6772 1760 S  2.3  1.3   0:00.14 apache2                                                                                         
31700 www-data  20   0  157m 6772 1760 S  2.3  1.3   0:00.09 apache2                                                                                         
31637 www-data  20   0  157m 6780 1760 R  1.9  1.3   0:02.75 apache2                                                                                         
31640 www-data  20   0  157m 6780 1760 R  1.9  1.3   0:02.51 apache2                                                                                         
31651 www-data  20   0  157m 6776 1760 S  1.9  1.3   0:01.58 apache2                                                                                         
31671 www-data  20   0  157m 6780 1760 S  1.9  1.3   0:01.25 apache2                                                                                         
31677 www-data  20   0  157m 6780 1760 S  1.9  1.3   0:00.94 apache2                                                                                         
31679 www-data  20   0  157m 6776 1760 S  1.9  1.3   0:00.95 apache2                                                                                         
31680 www-data  20   0  157m 6780 1760 S  1.9  1.3   0:00.87 apache2                                                                                         
31696 www-data  20   0  157m 6772 1760 S  1.9  1.3   0:00.21 apache2                                                                                         
31697 www-data  20   0  157m 6776 1760 R  1.9  1.3   0:00.16 apache2                                                                                         
31701 www-data  20   0  157m 6772 1760 S  1.9  1.3   0:00.06 apache2    
```        

       /var/log/apache2/range-CVE-2011-3192.log  didn't catch anything :o

---

### Post by nestoru on 2011-10-01
[http://thinkinginsoftware.blogspot.com/2011/10/upgrade-ubuntu-apache-to-latest-version.html](http://thinkinginsoftware.blogspot.com/2011/10/upgrade-ubuntu-apache-to-latest-version.html)

---

### Post by Dangertux on 2011-10-01
Alternatively another work around would be utilizing mod_qos , since it's a similar style attack to slowloris it should work.

A mod_qos config like this should be useful

```
[FONT=monospace]
[/FONT]QS_ClientEntries 100000     
QS_SrvMaxConnPerIP 12     
MaxClients              256     
QS_SrvMaxConnClose      180     
QS_SrvMinDataRate       150 1200

```

---

