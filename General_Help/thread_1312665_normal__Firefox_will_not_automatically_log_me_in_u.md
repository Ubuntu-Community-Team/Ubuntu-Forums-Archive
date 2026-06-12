---
title: "normal  Firefox will not automatically log me in upon restart."
date: 2009-11-03
forum: General Help
---

### Post by missbliss on 2009-11-03
Here's my issue:

I want Firefox to automatically log me in upon restart but it does not. In Edit>Preferences>Privacy>Clear Recent History the "Active Logins" and "Cookies" boxes are unchecked. In Edit>Preferences>Security the "Remember Passwords for Sites" box is checked with no exceptions. I have done restarts of both Firefox and the laptop, but I am not being automatically logged in upon restarting Firefox.


Extensions installed

Site Launcher, ColofulTabs, AddThis, FoxyTunes, ISOHunt Toolbar, SkipScreen, Tab Mix Plus, xMarks, Ubuntu Firefox Modifications


Firefox version - 3.5.4

Operating system - Linux


User Agent

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9.1.4) Gecko/20091028 Ubuntu/9.10 (karmic) Firefox/3.5.4
Plugins installed



Any help?  8.10 was fine.  This is really annoying!!

---

### Post by winotree on 2009-11-03
I may be confusing this with something else but I was thinking that cookies had to be enabled for what you want to do.  Have you tried it that way, too?

---

### Post by Giblet5 on 2009-11-03
Are the permissions correct in your ~/.mozilla folder?

These two commands will set reasonable (and secure) permissions and ownership for all of your web browser data.

Exit firefox. Open a terminal window.

```
sudo find $HOME/.mozilla -type d -exec chmod 700 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
sudo find $HOME/.mozilla -type f -exec chmod 600 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
```

Once those commands complete, start firefox. It will behave the way it is supposed to now. If you still have to log in to a site manually, it is now because that was the website developer's intention and not because of a permissions problem.

---

### Post by missbliss on 2009-11-03
> **Giblet5 said:**
> Are the permissions correct in your ~/.mozilla folder?

These two commands will set reasonable (and secure) permissions and ownership for all of your web browser data.

Exit firefox. Open a terminal window.

```
sudo find $HOME/.mozilla -type d -exec chmod 700 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
sudo find $HOME/.mozilla -type f -exec chmod 600 {} \; -exec chown $LOGNAME:$LOGNAME {} \;
```

Once those commands complete, start firefox. It will behave the way it is supposed to now. If you still have to log in to a site manually, it is now because that was the website developer's intention and not because of a permissions problem.


I copied and pasted the first command after closing Firefox but after prompting me for my sudo password it didn't do anything.  Just says _____@_____:~$





Also, I have cookies enabled and am not behind a firewall.  Firefox is much slower and choppier than it was in 8.10.  That's part of why I never upgraded to 9.04, but I figured the problem would be fixed with this release.

I know it's not my connection that is making it slow b/c bittorrent runs great and in 8.10 Firefox was running very fast.  

My passwords even "time out."  I don't even have to shut down Firefox for the passwords to expire.

---

### Post by Giblet5 on 2009-11-03
> **missbliss said:**
> I copied and pasted the first command after closing Firefox but after prompting me for my sudo password it didn't do anything.  Just says _____@_____:~$


It won't display anything. It's just setting permissions and ownership to your account on the ~/.mozilla directory tree. What's to display?

You can add ```
echo "It's all mine now! Bwah ha ha!"
``` to the end. ;)

Running one of two will do about half of what needs doing, and it won't do the important half...



> Also, I have cookies enabled and am not behind a firewall.  Firefox is much slower and choppier than it was in 8.10.  That's part of why I never upgraded to 9.04, but I figured the problem would be fixed with this release.

I know it's not my connection that is making it slow b/c bittorrent runs great and in 8.10 Firefox was running very fast.  

My passwords even "time out."  I don't even have to shut down Firefox for the passwords to expire.


That might be a network config problem. It could be that your primary DNS is down and it's timing out before succeeding on the secondary DNS.

Please open a terminal window, if you don't have one up, and post the output of this command (again, hiding any sensitive info as you wisely did before) ```
ifconfig
```

Also post the contents of /etc/resolv.conf (your DNS servers).

---

### Post by missbliss on 2009-11-03
I should have said it before but I did do both commands for Firefox, I was just expecting like a "done" line or something.  lol :-)

However, it didn't help.  :-(

Here's my info from ifconfig:

```
___@____:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1f:16:57:2c:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3584 (3.5 KB)  TX bytes:3584 (3.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:4e:76:9f:c7  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4eff:fe76:9fc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1764110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1611443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1648837580 (1.6 GB)  TX bytes:854231011 (854.2 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-23-4E-76-9F-C7-37-36-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

I don't know if I should be hiding any of that info.

For this: /etc/resolv.conf   Permission is denied.  Hmmmmmm.....

---

### Post by Giblet5 on 2009-11-03
> **missbliss said:**
> Here's my info from ifconfig:

For this: /etc/resolv.conf   Permission is denied.  Hmmmmmm.....

Your network config is fine.

The permission denied is because you're trying to edit it and you aren't allowed. You should only have read permission, so that error is normal.

Just open a terminal window and execute ```
cat /etc/resolv.conf
``` and select, copy, and paste the info here.

---

### Post by missbliss on 2009-11-03
That last code got me:

```
# Generated by NetworkManager
domain neo.rr.com
search neo.rr.com
nameserver 209.18.47.61
nameserver 209.18.47.62

```

---

### Post by Giblet5 on 2009-11-03
Hmmm. It all seems good.

Open a terminal window and enter ```
ping ftp.x.org
```

It will just keep running. Let it run for 30 minutes or so, then hit Ctrl-C to stop it. It will print the min/max/avg as well as the number of transmitted and dropped packets.

Could you post those values, please?

It sends a packet to a server (ftp.x.org) which bounces it back. The round-trip time is estimated from how long that takes. It's a good measure of network latency - how responsive a network connection appears.

If there are dropped packets, that would explain the login timeouts you're seeing. Web traffic is pretty retarded compared with torrent apps or other network tools; it doesn't retry a connection attempt as quickly as those apps do.

One dropped packet on a web page can equal a timeout that takes months¹ to occur.

Note ¹: exaggerated a bit

---

### Post by missbliss on 2009-11-03
> **Giblet5 said:**
> Hmmm. It all seems good.

Open a terminal window and enter ```
ping ftp.x.org
```

It will just keep running. Let it run for 30 minutes or so, then hit Ctrl-C to stop it. It will print the min/max/avg as well as the number of transmitted and dropped packets.

Could you post those values, please?

It sends a packet to a server (ftp.x.org) which bounces it back. The round-trip time is estimated from how long that takes. It's a good measure of network latency - how responsive a network connection appears.

If there are dropped packets, that would explain the login timeouts you're seeing. Web traffic is pretty retarded compared with torrent apps or other network tools; it doesn't retry a connection attempt as quickly as those apps do.

One dropped packet on a web page can equal a timeout that takes months¹ to occur.

Note ¹: exaggerated a bit

Gotta go to work now, but I will do this when I get home at 10:00 pm EST.  Thanks so much for helping me out.  I hope we can fix it!

---

### Post by Giblet5 on 2009-11-03
> **missbliss said:**
> Gotta go to work now, but I will do this when I get home at 10:00 pm EST.  Thanks so much for helping me out.  I hope we can fix it!

No promises. This *might* be your ISP's fault... I can't do anything about your ISP but maybe you have a baseball bat somewhere... ;)

---

### Post by winotree on 2009-11-03
[Not to hijack the thread but to understand what's just happened]

**Giblet5**, to say that I received an education this morning would certainly be an understatement.  ;)  How did you know to go straight to permissions in a situation like this?

---

### Post by Giblet5 on 2009-11-03
> **winotree said:**
> [Not to hijack the thread but to understand what's just happened]

**Giblet5**, to say that I received an education this morning would certainly be an understatement.  ;)  How did you know to go straight to permissions in a situation like this?


Well ... it was a guess.

If you have a persistent login account on a "Remember Me" type web site eg, Fark.com, then that site will attempt to install a cookie that doesn't expire as a very basic form of authentication.

If you have to log in every time, then maybe firefox can accept the cookie, but doesn't have permission to save it.

That's a permissions problem.

It's easy and safe to force good permissions, and home folder permissions tend to get a little screwy over time with normal use, so it's a good/safe way to start troubleshooting from a known point.

---

### Post by missbliss on 2009-11-03
```
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=836 ttl=51 time=474 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=837 ttl=51 time=854 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=838 ttl=51 time=1221 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=839 ttl=51 time=1301 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=840 ttl=51 time=1489 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=841 ttl=51 time=1783 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=842 ttl=51 time=1620 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=843 ttl=51 time=1474 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=844 ttl=51 time=1423 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=845 ttl=51 time=1472 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=846 ttl=51 time=1405 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=847 ttl=51 time=1726 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=848 ttl=51 time=1823 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=849 ttl=51 time=1454 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=850 ttl=51 time=1012 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=851 ttl=51 time=1051 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=852 ttl=51 time=2000 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=853 ttl=51 time=1647 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=854 ttl=51 time=1546 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=855 ttl=51 time=1205 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=856 ttl=51 time=740 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=857 ttl=51 time=516 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=858 ttl=51 time=827 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=860 ttl=51 time=985 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=861 ttl=51 time=1313 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=862 ttl=51 time=1596 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=863 ttl=51 time=1365 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=864 ttl=51 time=1127 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=865 ttl=51 time=654 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=866 ttl=51 time=486 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=867 ttl=51 time=601 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=868 ttl=51 time=939 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=869 ttl=51 time=1263 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=870 ttl=51 time=1233 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=871 ttl=51 time=1084 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=872 ttl=51 time=891 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=873 ttl=51 time=1247 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=874 ttl=51 time=1657 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=875 ttl=51 time=1544 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=876 ttl=51 time=1541 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=877 ttl=51 time=1222 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=878 ttl=51 time=1456 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=879 ttl=51 time=915 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=880 ttl=51 time=1659 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=881 ttl=51 time=1859 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=882 ttl=51 time=1202 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=883 ttl=51 time=1210 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=884 ttl=51 time=1344 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=885 ttl=51 time=1153 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=886 ttl=51 time=248 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=887 ttl=51 time=523 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=888 ttl=51 time=1298 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=889 ttl=51 time=808 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=890 ttl=51 time=815 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=891 ttl=51 time=1040 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=892 ttl=51 time=1366 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=893 ttl=51 time=1148 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=894 ttl=51 time=574 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=895 ttl=51 time=451 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=896 ttl=51 time=1023 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=897 ttl=51 time=949 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=898 ttl=51 time=1512 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=899 ttl=51 time=1048 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=900 ttl=51 time=1453 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=901 ttl=51 time=1169 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=902 ttl=51 time=897 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=903 ttl=51 time=1381 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=904 ttl=51 time=1503 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=905 ttl=51 time=1287 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=906 ttl=51 time=1346 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=907 ttl=51 time=1309 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=908 ttl=51 time=629 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=909 ttl=51 time=1502 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=910 ttl=51 time=1555 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=911 ttl=51 time=744 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=912 ttl=51 time=932 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=913 ttl=51 time=1123 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=914 ttl=51 time=1101 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=915 ttl=51 time=1043 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=916 ttl=51 time=645 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=917 ttl=51 time=750 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=918 ttl=51 time=1146 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=919 ttl=51 time=988 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=921 ttl=51 time=1453 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=922 ttl=51 time=1839 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=923 ttl=51 time=704 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=924 ttl=51 time=737 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=925 ttl=51 time=1179 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=926 ttl=51 time=866 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=927 ttl=51 time=783 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=928 ttl=51 time=1823 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=929 ttl=51 time=1479 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=930 ttl=51 time=1124 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=931 ttl=51 time=1243 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=932 ttl=51 time=1101 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=933 ttl=51 time=1569 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=934 ttl=51 time=1837 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=935 ttl=51 time=1922 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=936 ttl=51 time=774 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=937 ttl=51 time=1263 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=938 ttl=51 time=1121 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=939 ttl=51 time=915 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=940 ttl=51 time=1638 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=941 ttl=51 time=1927 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=942 ttl=51 time=1013 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=943 ttl=51 time=605 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=944 ttl=51 time=1556 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=945 ttl=51 time=1607 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=946 ttl=51 time=930 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=947 ttl=51 time=652 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=948 ttl=51 time=759 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=949 ttl=51 time=930 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=950 ttl=51 time=1364 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=951 ttl=51 time=1614 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=952 ttl=51 time=706 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=953 ttl=51 time=1411 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=954 ttl=51 time=1407 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=955 ttl=51 time=1347 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=956 ttl=51 time=1127 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=957 ttl=51 time=1928 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=958 ttl=51 time=1845 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=959 ttl=51 time=1477 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=960 ttl=51 time=1743 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=961 ttl=51 time=1290 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=962 ttl=51 time=1147 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=963 ttl=51 time=1196 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=964 ttl=51 time=1109 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=965 ttl=51 time=973 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=966 ttl=51 time=973 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=967 ttl=51 time=1334 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=968 ttl=51 time=1302 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=969 ttl=51 time=1874 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=970 ttl=51 time=1936 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=971 ttl=51 time=1587 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=972 ttl=51 time=1142 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=973 ttl=51 time=1610 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=974 ttl=51 time=946 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=975 ttl=51 time=1789 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=976 ttl=51 time=1675 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=977 ttl=51 time=1096 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=978 ttl=51 time=1133 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=979 ttl=51 time=987 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=980 ttl=51 time=797 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=981 ttl=51 time=1216 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=982 ttl=51 time=1410 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=983 ttl=51 time=1749 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=984 ttl=51 time=1747 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=985 ttl=51 time=1014 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=986 ttl=51 time=1486 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=987 ttl=51 time=1174 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=988 ttl=51 time=1204 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=989 ttl=51 time=1341 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=990 ttl=51 time=1715 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=991 ttl=51 time=1648 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=992 ttl=51 time=1836 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=993 ttl=51 time=1619 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=994 ttl=51 time=1448 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=995 ttl=51 time=2122 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=996 ttl=51 time=1915 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=997 ttl=51 time=2108 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=998 ttl=51 time=1418 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=999 ttl=51 time=1479 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1000 ttl=51 time=2026 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1001 ttl=51 time=2164 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1002 ttl=51 time=1756 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1003 ttl=51 time=2204 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1004 ttl=51 time=1871 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1005 ttl=51 time=2025 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1006 ttl=51 time=1896 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1007 ttl=51 time=1506 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1008 ttl=51 time=1830 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1009 ttl=51 time=1793 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1011 ttl=51 time=2276 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1012 ttl=51 time=2015 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1013 ttl=51 time=1672 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1014 ttl=51 time=1489 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1015 ttl=51 time=1228 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1016 ttl=51 time=1055 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1017 ttl=51 time=1252 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1018 ttl=51 time=1455 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1019 ttl=51 time=1817 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1020 ttl=51 time=1999 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1021 ttl=51 time=1999 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1022 ttl=51 time=944 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1023 ttl=51 time=625 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1024 ttl=51 time=879 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1025 ttl=51 time=887 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1026 ttl=51 time=1438 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1027 ttl=51 time=1371 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1028 ttl=51 time=1140 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1029 ttl=51 time=1091 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1030 ttl=51 time=1814 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1031 ttl=51 time=1878 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1032 ttl=51 time=1807 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1033 ttl=51 time=1933 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1034 ttl=51 time=1033 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1035 ttl=51 time=1258 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1036 ttl=51 time=1226 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1037 ttl=51 time=1147 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1038 ttl=51 time=1460 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1039 ttl=51 time=2032 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1041 ttl=51 time=1732 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1042 ttl=51 time=1126 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1043 ttl=51 time=856 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1044 ttl=51 time=792 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1045 ttl=51 time=1190 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1046 ttl=51 time=1472 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1048 ttl=51 time=1888 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1049 ttl=51 time=1632 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1050 ttl=51 time=970 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1051 ttl=51 time=1032 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1052 ttl=51 time=1047 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1053 ttl=51 time=793 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1054 ttl=51 time=1899 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1056 ttl=51 time=1927 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1057 ttl=51 time=1758 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1058 ttl=51 time=1452 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1059 ttl=51 time=1337 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1060 ttl=51 time=2098 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1061 ttl=51 time=2162 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1062 ttl=51 time=1697 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1063 ttl=51 time=1393 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1064 ttl=51 time=1431 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1065 ttl=51 time=1624 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1066 ttl=51 time=1633 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1067 ttl=51 time=1362 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1068 ttl=51 time=522 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1069 ttl=51 time=1790 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1070 ttl=51 time=1863 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1071 ttl=51 time=947 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1072 ttl=51 time=1539 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1073 ttl=51 time=1462 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1074 ttl=51 time=1475 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1075 ttl=51 time=972 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1076 ttl=51 time=934 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1077 ttl=51 time=1221 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1078 ttl=51 time=1191 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1079 ttl=51 time=1794 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1080 ttl=51 time=1500 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1081 ttl=51 time=2022 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1082 ttl=51 time=1700 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1083 ttl=51 time=1698 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1084 ttl=51 time=1658 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1085 ttl=51 time=1845 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1086 ttl=51 time=1220 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1087 ttl=51 time=1121 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1088 ttl=51 time=1838 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1089 ttl=51 time=1907 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1090 ttl=51 time=817 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1091 ttl=51 time=399 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1092 ttl=51 time=622 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1093 ttl=51 time=691 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1094 ttl=51 time=826 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1095 ttl=51 time=788 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1096 ttl=51 time=998 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1097 ttl=51 time=893 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1098 ttl=51 time=1497 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1099 ttl=51 time=1458 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1100 ttl=51 time=1496 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1101 ttl=51 time=1365 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1102 ttl=51 time=712 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1103 ttl=51 time=1276 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1104 ttl=51 time=1838 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1105 ttl=51 time=1377 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1106 ttl=51 time=1238 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1107 ttl=51 time=1281 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1108 ttl=51 time=1194 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1109 ttl=51 time=1802 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1110 ttl=51 time=1837 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1111 ttl=51 time=1318 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1112 ttl=51 time=1026 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1113 ttl=51 time=849 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1114 ttl=51 time=1315 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1115 ttl=51 time=1285 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1116 ttl=51 time=1650 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1117 ttl=51 time=2119 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1118 ttl=51 time=1736 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1119 ttl=51 time=1416 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1120 ttl=51 time=1020 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1121 ttl=51 time=1063 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1122 ttl=51 time=1363 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1123 ttl=51 time=1790 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1124 ttl=51 time=1767 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1125 ttl=51 time=1231 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1126 ttl=51 time=1918 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1127 ttl=51 time=1730 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1128 ttl=51 time=993 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1129 ttl=51 time=529 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1130 ttl=51 time=397 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1131 ttl=51 time=792 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1132 ttl=51 time=689 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1133 ttl=51 time=827 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1134 ttl=51 time=1032 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1135 ttl=51 time=1275 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1136 ttl=51 time=1462 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1137 ttl=51 time=1536 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1138 ttl=51 time=1777 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1139 ttl=51 time=801 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1140 ttl=51 time=173 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1141 ttl=51 time=165 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1142 ttl=51 time=311 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1143 ttl=51 time=686 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1144 ttl=51 time=1254 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1145 ttl=51 time=1005 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1146 ttl=51 time=1212 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1147 ttl=51 time=970 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1148 ttl=51 time=825 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1149 ttl=51 time=129 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1150 ttl=51 time=1035 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1151 ttl=51 time=1149 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1152 ttl=51 time=587 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1153 ttl=51 time=182 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1154 ttl=51 time=582 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1155 ttl=51 time=610 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1156 ttl=51 time=460 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1157 ttl=51 time=714 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1158 ttl=51 time=911 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1159 ttl=51 time=1143 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1160 ttl=51 time=1285 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1161 ttl=51 time=1346 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1162 ttl=51 time=1351 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1163 ttl=51 time=1085 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1164 ttl=51 time=1262 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1165 ttl=51 time=1254 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1166 ttl=51 time=1096 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1167 ttl=51 time=578 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1168 ttl=51 time=514 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1169 ttl=51 time=920 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1170 ttl=51 time=1456 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1171 ttl=51 time=1278 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1172 ttl=51 time=1171 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1173 ttl=51 time=814 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1174 ttl=51 time=704 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1175 ttl=51 time=1146 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1176 ttl=51 time=1262 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1177 ttl=51 time=800 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1178 ttl=51 time=746 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1179 ttl=51 time=1119 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1180 ttl=51 time=957 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1181 ttl=51 time=973 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1182 ttl=51 time=812 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1183 ttl=51 time=293 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1184 ttl=51 time=30.5 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1185 ttl=51 time=38.0 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1186 ttl=51 time=540 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1187 ttl=51 time=467 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1188 ttl=51 time=919 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1189 ttl=51 time=376 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1190 ttl=51 time=1128 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1191 ttl=51 time=1139 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1192 ttl=51 time=1204 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1193 ttl=51 time=1295 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1194 ttl=51 time=1457 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1195 ttl=51 time=1049 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1196 ttl=51 time=811 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1197 ttl=51 time=558 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1198 ttl=51 time=430 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1199 ttl=51 time=646 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1200 ttl=51 time=917 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1201 ttl=51 time=1851 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1202 ttl=51 time=1364 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1203 ttl=51 time=784 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1204 ttl=51 time=564 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1205 ttl=51 time=582 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1206 ttl=51 time=932 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1207 ttl=51 time=1128 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1208 ttl=51 time=1094 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1209 ttl=51 time=1088 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1210 ttl=51 time=1373 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1211 ttl=51 time=1488 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1212 ttl=51 time=913 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1213 ttl=51 time=839 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1214 ttl=51 time=947 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1215 ttl=51 time=466 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1216 ttl=51 time=265 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1217 ttl=51 time=31.8 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1218 ttl=51 time=29.9 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1219 ttl=51 time=327 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1220 ttl=51 time=651 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1221 ttl=51 time=322 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1222 ttl=51 time=716 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1223 ttl=51 time=645 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1224 ttl=51 time=696 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1225 ttl=51 time=245 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1226 ttl=51 time=117 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1227 ttl=51 time=38.4 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1228 ttl=51 time=116 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1229 ttl=51 time=509 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1230 ttl=51 time=525 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1231 ttl=51 time=1029 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1232 ttl=51 time=743 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1233 ttl=51 time=835 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1234 ttl=51 time=863 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1235 ttl=51 time=462 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1236 ttl=51 time=970 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1237 ttl=51 time=976 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1238 ttl=51 time=1052 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1239 ttl=51 time=817 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1240 ttl=51 time=789 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1241 ttl=51 time=1014 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1242 ttl=51 time=1196 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1243 ttl=51 time=530 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1244 ttl=51 time=655 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1245 ttl=51 time=278 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1246 ttl=51 time=681 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1247 ttl=51 time=1329 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1248 ttl=51 time=1306 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1249 ttl=51 time=426 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1250 ttl=51 time=828 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1251 ttl=51 time=1733 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1252 ttl=51 time=1689 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1253 ttl=51 time=1059 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1254 ttl=51 time=695 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1255 ttl=51 time=771 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1256 ttl=51 time=538 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1257 ttl=51 time=1449 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1258 ttl=51 time=1492 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1259 ttl=51 time=1328 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1260 ttl=51 time=1239 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1261 ttl=51 time=1214 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1262 ttl=51 time=814 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1263 ttl=51 time=490 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1264 ttl=51 time=652 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1265 ttl=51 time=599 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1266 ttl=51 time=1353 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1267 ttl=51 time=557 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1268 ttl=51 time=647 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1269 ttl=51 time=285 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1270 ttl=51 time=491 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1271 ttl=51 time=789 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1272 ttl=51 time=1118 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1273 ttl=51 time=869 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1274 ttl=51 time=599 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1275 ttl=51 time=949 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1276 ttl=51 time=1275 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1277 ttl=51 time=1291 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1278 ttl=51 time=1396 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1279 ttl=51 time=457 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1280 ttl=51 time=1037 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1281 ttl=51 time=1237 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1282 ttl=51 time=873 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1283 ttl=51 time=580 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1284 ttl=51 time=1106 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1285 ttl=51 time=897 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1286 ttl=51 time=1195 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1287 ttl=51 time=1492 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1288 ttl=51 time=649 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1289 ttl=51 time=913 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1290 ttl=51 time=1034 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1291 ttl=51 time=1106 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1292 ttl=51 time=1550 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1293 ttl=51 time=1520 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1294 ttl=51 time=1197 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1295 ttl=51 time=1132 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1296 ttl=51 time=881 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1297 ttl=51 time=1147 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1298 ttl=51 time=1400 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1299 ttl=51 time=1017 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1300 ttl=51 time=1136 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1301 ttl=51 time=964 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1302 ttl=51 time=1393 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1303 ttl=51 time=1327 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1304 ttl=51 time=1285 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1305 ttl=51 time=1274 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1306 ttl=51 time=839 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1307 ttl=51 time=838 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1308 ttl=51 time=478 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1309 ttl=51 time=230 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1310 ttl=51 time=525 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1311 ttl=51 time=526 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1312 ttl=51 time=636 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1313 ttl=51 time=84.8 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1314 ttl=51 time=278 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1315 ttl=51 time=45.9 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1316 ttl=51 time=39.9 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1317 ttl=51 time=467 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1318 ttl=51 time=641 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1319 ttl=51 time=867 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1320 ttl=51 time=948 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1321 ttl=51 time=467 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1322 ttl=51 time=642 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1323 ttl=51 time=878 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1324 ttl=51 time=525 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1325 ttl=51 time=573 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1326 ttl=51 time=314 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1327 ttl=51 time=221 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1328 ttl=51 time=822 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1329 ttl=51 time=801 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1330 ttl=51 time=1153 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1331 ttl=51 time=1377 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1332 ttl=51 time=609 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1333 ttl=51 time=661 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1334 ttl=51 time=409 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1335 ttl=51 time=425 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1336 ttl=51 time=571 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1337 ttl=51 time=416 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1338 ttl=51 time=457 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1339 ttl=51 time=341 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1340 ttl=51 time=614 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1341 ttl=51 time=678 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1342 ttl=51 time=1101 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1343 ttl=51 time=1208 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1344 ttl=51 time=1129 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1345 ttl=51 time=1606 ms
^C64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1346 ttl=51 time=1233 ms
64 bytes from EXPO.MIT.EDU (18.7.25.161): icmp_seq=1347 ttl=51 time=1575 ms

--- expo.x.org ping statistics ---
1347 packets transmitted, 1332 received, 1% packet loss, time 2623444ms
rtt min/avg/max/mdev = 29.987/1185.167/2840.860/480.946 ms, pipe 3

```

---

### Post by Giblet5 on 2009-11-04
The automatic login thing is not due to any problem on your system at least. Only file permissions would cause a fault like that and we have ensured that permissions are perfect for firefox. This is either correct behavior or a fault in the version of firefox you're running.

Try installing Google Chrome and compare behavior between the two. That's a decent test of expectations v intended behavior.

```
sudo apt-get install chromium-browser chromium-codecs-ffmpeg
```


Your internet connectivity is kind of mediocre: better than really bad dialup, but far worse than typical low-end DSL service.

Your average ping time is > 1 second. Are you connected via a satellite uplink?

You're dropping packets. That *will* result in web page timeouts.

If you're not on dialup or satellite uplink, it would be worth contacting your ISP and complaining about this. Share the last three lines of your ping output with their service rep.

I got nothin' else.

---

### Post by missbliss on 2009-11-04
> **Giblet5 said:**
> The automatic login thing is not due to any problem on your system at least. Only file permissions would cause a fault like that and we have ensured that permissions are perfect for firefox. This is either correct behavior or a fault in the version of firefox you're running.

Try installing Google Chrome and compare behavior between the two. That's a decent test of expectations v intended behavior.

```
sudo apt-get install chromium-browser chromium-codecs-ffmpeg
```


Your internet connectivity is kind of mediocre: better than really bad dialup, but far worse than typical low-end DSL service.

Your average ping time is > 1 second. Are you connected via a satellite uplink?

You're dropping packets. That *will* result in web page timeouts.

If you're not on dialup or satellite uplink, it would be worth contacting your ISP and complaining about this. Share the last three lines of your ping output with their service rep.

I got nothin' else.

Thanks for the help.  It couldn't find package "chromium-browser" so I did "sudo apt-get install chromium"  That yielded:

```
 sudo apt-get install chromium
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  chromium-bsu chromium-bsu-data libalut0 libglc0 libglpng libopenal1
  libsdl-image1.2 ttf-uralic
The following NEW packages will be installed:
  chromium chromium-bsu chromium-bsu-data libalut0 libglc0 libglpng libopenal1
  libsdl-image1.2 ttf-uralic
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 2,310kB of archives.
After this operation, 4,653kB of additional disk space will be used.
Do you want to continue [Y/n]? y
0% [Connecting to us.archive.ubuntu.com]y
Get:1 http://us.archive.ubuntu.com karmic/universe libopenal1 1:1.8.466-2 [94.1kB]
Get:2 http://us.archive.ubuntu.com karmic/universe libalut0 1.1.0-2 [32.3kB]   
Get:3 http://us.archive.ubuntu.com karmic/universe libglc0 0.7.2-1 [77.0kB]    
Get:4 http://us.archive.ubuntu.com karmic/universe libglpng 1.45-5 [9,996B]    
Get:5 http://us.archive.ubuntu.com karmic/main libsdl-image1.2 1.2.7-1 [32.2kB]
Get:6 http://us.archive.ubuntu.com karmic/universe chromium-bsu-data 0.9.14-1 [1,241kB]
Get:7 http://us.archive.ubuntu.com karmic/universe ttf-uralic 0.0.20040829-1ubuntu2 [684kB]
Get:8 http://us.archive.ubuntu.com karmic/universe chromium-bsu 0.9.14-1 [126kB]
Get:9 http://us.archive.ubuntu.com karmic/universe chromium 0.9.14-1 [13.9kB]  
Fetched 2,310kB in 37s (62.0kB/s)                                              
Selecting previously deselected package libopenal1.
(Reading database ... 115081 files and directories currently installed.)
Unpacking libopenal1 (from .../libopenal1_1%3a1.8.466-2_i386.deb) ...
Selecting previously deselected package libalut0.
Unpacking libalut0 (from .../libalut0_1.1.0-2_i386.deb) ...
Selecting previously deselected package libglc0.
Unpacking libglc0 (from .../libglc0_0.7.2-1_i386.deb) ...
Selecting previously deselected package libglpng.
Unpacking libglpng (from .../libglpng_1.45-5_i386.deb) ...
Selecting previously deselected package libsdl-image1.2.
Unpacking libsdl-image1.2 (from .../libsdl-image1.2_1.2.7-1_i386.deb) ...
Selecting previously deselected package chromium-bsu-data.
Unpacking chromium-bsu-data (from .../chromium-bsu-data_0.9.14-1_all.deb) ...
Selecting previously deselected package ttf-uralic.
Unpacking ttf-uralic (from .../ttf-uralic_0.0.20040829-1ubuntu2_all.deb) ...
Selecting previously deselected package chromium-bsu.
Unpacking chromium-bsu (from .../chromium-bsu_0.9.14-1_i386.deb) ...
Selecting previously deselected package chromium.
Unpacking chromium (from .../chromium_0.9.14-1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Setting up libopenal1 (1:1.8.466-2) ...

Setting up libalut0 (1.1.0-2) ...

Setting up libglc0 (0.7.2-1) ...

Setting up libglpng (1.45-5) ...

Setting up libsdl-image1.2 (1.2.7-1) ...

Setting up chromium-bsu-data (0.9.14-1) ...
Setting up ttf-uralic (0.0.20040829-1ubuntu2) ...
Updating fontconfig cache for /usr/share/fonts/truetype/uralic
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for ZenHei, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for ZenHei-CNS, defaulting to 0.
No CIDSupplement specified for Batang-Bold, defaulting to 0.

Setting up chromium-bsu (0.9.14-1) ...

Setting up chromium (0.9.14-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

Anyway, I'm well aware of the problems with my connection.  It has ALWAYS been like this.  I have had techs out to the house from my isp probably 30 times in the last 3 years.  2 times just in the last 2 weeks.  It's complete BS that we don't at least get a discount.  They improve it for a while then it will get worse and then they come out and fix it up a bit, then repeat.

---

### Post by Giblet5 on 2009-11-04
> **missbliss said:**
> Thanks for the help.  It couldn't find package "chromium-browser" so I did "sudo apt-get install chromium"  That yielded:


Anyway, I'm well aware of the problems with my connection.  It has ALWAYS been like this.  I have had techs out to the house from my isp probably 30 times in the last 3 years.  2 times just in the last 2 weeks.  It's complete BS that we don't at least get a discount.  They improve it for a while then it will get worse and then they come out and fix it up a bit, then repeat.


Well, try and see if chrome remembers your web logins. If not, then that is the web designer's intention and only some sneaky scripting will get around it.

Contact Earthlink and see if they will agree to provide better service for the same price. They're pretty aggressive about taking other ISP's business away from them and it sends the right message to your current ISP.

---

