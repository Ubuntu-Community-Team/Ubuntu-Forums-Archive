---
title: "Firefox Connection Problem on Mobile Broadband"
date: 2010-01-12
forum: General Help
---

### Post by PhilipD on 2010-01-12
Dear Forum - I have just upgraded to Ubuntu 9.1 and now my mobile broadband connection will not work.  The dongle says it is connected to my provider but Firefox is telling me it cannot find the web page. Any suggestions? Everything was working perfectly before the upgrade!

Error message: The browser could not find the host server for the provided address.




    *

---

### Post by GeorgeVita on 2010-01-12
Hi **PhilipD**, welcome to this forum!
Update your Ubuntu 9.10 with other method if possible.

Regarding your problem do some tests to determine if this is a DNS problem:

After connection established, open a terminal window and try: ```
nm-tool
``` Last lines will show your IP address and the current DNS. Search internet to find the 'default DNS' for your provider. If not match the possible problem is: 'Are you unable to browse other sites?  Check your network connection and DNS server settings.'

Some other tests from terminal: ```
ping -c 1 www.canonical.com
``` must show ```
g@sd:~$ ping -c 1 www.canonical.com
PING www.canonical.com (91.189.90.40) 56(84) bytes of data.
64 bytes from avocado.canonical.com (91.189.90.40): icmp_seq=1 ttl=50 time=346 ms

--- www.canonical.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 346.390/346.390/346.390/0.000 ms
g@sd:~$ 
``` if above did not work, try to 'ping' the IP of canonical: ```
ping -c 1 91.189.94.12
``` if last test works then it is a DNS problem.

Right click network-manager icon > edit connections > mobile broadband > click on your provider > edit
click on IPv4 tab and select: 'Automatic PPP' (and NOT addresses only).

In any case search ubuntuforums.org using 'your provider name', 'broadband', 'settings' as keys to get more ideas.

Regards,
George

---

### Post by roderickf on 2010-04-25
I had exactly the same problem just now. It is DNS problem.
I guess this issue is caused by system update, since I updated my system last night.
Solution is pretty easy and straight-forward.
open your mobile broadband tab in network connection. delete your existing mobile broadband profile and add it again manually (because when u plugged it in, my ubuntu shows the previous network ID) and everything works! (for me at least.)

---

