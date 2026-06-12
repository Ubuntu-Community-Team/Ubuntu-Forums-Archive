---
title: "Problem with painfully slow access to a particular website"
date: 2011-08-16
forum: General Help
---

### Post by mlyter on 2011-08-16
Hello all,

I'm having difficulty accessing [http://egrants.ed.state.pa.us/v2/default.asp](http://egrants.ed.state.pa.us/v2/default.asp) while using Ubuntu 11.04 and Ubuntu 10.04.  I've tried chrome, firefox and opera as well as three different ISPs.  My Windows machines don't seem to have this problem.

A little background:
My agency has several offices, some with different ISPs, but with essentially the same setup:  ISP router/modem --> Ubuntu Server with Squid/Dansguardian -->  Switches, etc.
When we first started encountering this problem I thought I had to have had something going on with Squid/IP Tables or something of that sort.  I connect my laptop (running Ubuntu 11.04) directly the ISPs modem/router and have the same slowness.  I figure that maybe the site is having problems.  I ask the other tech in my office to try it out (he's running Windows 7) and he has no slowness with the site when connected directly to the ISPs modem/router.

For the time being I've circumvented the filter box for the Windows users who need access to this site, but I'm not certain that's the best solution.

I contacted the site's tech support several times and just gotten a "we'll call you back".

Any suggestions on things I can check/change with my setup to get this working?

Thank you,
Mike

---

### Post by galvatron408 on 2011-08-16
so what happens when you run these commands...

nslookup $url (your testing to see how fast you can resolve the dns name)

telnet $url 80 (your testing to see how fast it takes to connect)

curl $url (your testing to see how fast you're able to pull the content)

Let us know what you find.

---

### Post by mlyter on 2011-08-17
_**At location 1:**_
**nslookup result:**
Server:        172.21.65.70
Address:    172.21.65.70#53

Non-authoritative answer:
Name:    [http://egrants.ed.state.pa.us](http://egrants.ed.state.pa.us)
Address: 207.223.0.140

**telnet result:**
telnet: could not resolve [http://egrants.ed.state.pa.us/80:](http://egrants.ed.state.pa.us/80:) Name or service not known
[B]
curl result:[/B]
Approximately 16 seconds using a stop watch from command begin until command complete.

_**At Location 2:**_
**nslookup result:**
Server:        192.168.1.1
Address:    192.168.1.1#53

Non-authoritative answer:
Name:    [http://egrants.ed.state.pa.us](http://egrants.ed.state.pa.us)
Address: 8.15.7.117
Name:    [http://egrants.ed.state.pa.us](http://egrants.ed.state.pa.us)
Address: 63.251.179.13

**telnet result:**
telnet: could not resolve [http://egrants.ed.state.pa.us/80:](http://egrants.ed.state.pa.us/80:) Name or service not known

**curl result:**
Approximately 96 seconds using a stopwatch

I should be heading to at least one other location today, I'll edit the post with info from those locations as well.

I'm assuming you are using Ubuntu or other variant as well - how does the page load for you?

---

### Post by Wim Sturkenboom on 2011-08-17
That page loads in about 5 seconds (using IceEasel in CrunchBang); faster than ubuntuforums ;)

---

### Post by sbraz on 2011-08-17
apparently i have the same problem:

```
sbraz@sbraz-netbook:~$ wget -c http://egrants.ed.state.pa.us/v2/images/e-grant_top.gif
--2011-08-17 16:32:41--  http://egrants.ed.state.pa.us/v2/images/e-grant_top.gif
Resolving egrants.ed.state.pa.us... 164.156.218.100
Connecting to egrants.ed.state.pa.us|164.156.218.100|:80... connected.
HTTP request sent, awaiting response... 200 OK
**Length: 10401 (10K)** [image/gif]
Saving to: `e-grant_top.gif'

100%[======================================>] 10,401       **397B/s   in 24s**     

2011-08-17 16:33:05 (441 B/s) - `e-grant_top.gif' saved [10401/10401]

```
397B/s???? =;

here's a traceroute (i've masked unrelevant hops only..):
```
traceroute to 164.156.218.100 (164.156.218.100), 100 hops max, 60 byte packets
 1  -private--ip- * * *
 2  -private--ip- 12.967 ms  13.731 ms  14.209 ms
 3  -private--ip- 15.594 ms  16.029 ms  18.352 ms
 4  -private--ip- 18.478 ms  18.748 ms  19.209 ms
 5  -private--ip- 21.157 ms  21.960 ms  22.077 ms
 6  -private--ip- 23.131 ms  12.240 ms  10.002 ms
 7  -private--ip- 14.387 ms  14.594 ms  14.637 ms
 8  -private--ip- 15.032 ms  15.976 ms  16.012 ms
 9  -private--ip- 16.708 ms  19.078 ms  19.161 ms
10  -private--ip- 20.369 ms  22.919 ms  23.083 ms
11  -private--ip- 29.275 ms  29.798 ms  30.318 ms
12  -private--ip- 24.565 ms  17.387 ms  19.025 ms
13  93-63-100-29.ip27.fastwebnet.it (93.63.100.29)  19.875 ms  22.057 ms  22.138 ms
14  93-63-100-89.ip27.fastwebnet.it (93.63.100.89)  22.205 ms  22.620 ms  23.504 ms
15  93-63-100-6.ip27.fastwebnet.it (93.63.100.6)  104.134 ms  105.250 ms  105.560 ms
16  89.96.200.114 (89.96.200.114)  26.927 ms 89.96.200.21 (89.96.200.21)  28.955 ms 89.96.200.114 (89.96.200.114)  32.676 ms
17  i79zhb-025-ten0-9-0-6.bb.ip-plus.net (164.128.33.169)  46.946 ms i79zhb-025-ten0-5-0-12.bb.ip-plus.net (164.128.34.13)  43.352 ms  44.117 ms
18  i79zhb-005-gig2-0-0.bb.ip-plus.net (138.187.129.114)  26.309 ms  23.216 ms  23.198 ms
19  i00nye-005-pos11-0-0.bb.ip-plus.net (138.187.159.0)  108.565 ms  109.011 ms  109.903 ms
20  xe-5-0-0.edge3.NewYork1.Level3.net (4.26.35.57)  123.972 ms  126.382 ms  128.206 ms
21  vlan79.csw2.NewYork1.Level3.net (4.68.16.126)  131.815 ms vlan99.csw4.NewYork1.Level3.net (4.68.16.254)  128.734 ms *
22  ae-81-81.ebr1.NewYork1.Level3.net (4.69.134.73)  128.598 ms ae-61-61.ebr1.NewYork1.Level3.net (4.69.134.65)  130.099 ms  131.060 ms
23  ae-4-4.ebr1.NewYork2.Level3.net (4.69.141.18)  121.057 ms  119.309 ms ae-10-10.ebr2.Washington12.Level3.net (4.69.148.50)  129.449 ms
24  ae-5-5.ebr2.Washington1.Level3.net (4.69.143.221)  133.012 ms ae-3-3.ebr2.Washington1.Level3.net (4.69.132.89)  126.042 ms ae-5-5.ebr2.Washington1.Level3.net (4.69.143.221)  132.158 ms
25  ae-62-62.csw1.Washington1.Level3.net (4.69.134.146)  132.651 ms ae-82-82.csw3.Washington1.Level3.net (4.69.134.154)  132.297 ms ae-92-92.csw4.Washington1.Level3.net (4.69.134.158)  132.730 ms
26  ae-32-80.car2.Washington1.Level3.net (4.69.149.132)  132.149 ms ae-42-90.car2.Washington1.Level3.net (4.69.149.196)  133.508 ms ae-22-70.car2.Washington1.Level3.net (4.69.149.68)  132.500 ms
27  COPA-6.car2.Washington1.Level3.net (4.59.146.62)  143.621 ms  144.615 ms  145.538 ms
28  164.156.3.106 (164.156.3.106)  142.703 ms  144.081 ms  134.803 ms
29  * * *
30  * * *
31  * * *
32  * * *
33  * * *
34  * * *
35  * * *
36  * * *
37  * * *
38  * * *
39  * * *
40  * * *
41  * * *
42  * * *
43  * * *
44  * * *
45  * * *
46  * * *
47  * * *
48  * * *
49  * * *
50  * * *
51  * * *
52  * * *
53  * * *
54  * * *
55  * * *
56  * * *
57  * * *
58  * * *
59  * * *
60  * * *
61  * * *
62  * * *
63  * * *
64  * * *
65  * * *
66  * * *
67  * * *
68  * * *
69  * * *
70  * * *
71  * * *
72  * * *
73  * * *
74  * * *
75  * * *
76  * * *
77  * * *
78  * * *
79  * * *
80  * * *
81  * * *
82  * * *
83  * * *
84  * * *
85  * * *
86  * * *
87  * * *
88  * * *
89  * * *
90  * * *
91  * * *
92  * * *
93  * * *
94  * * *
95  * * *
96  * * *
97  * * *
98  * * *
99  * * *
100  * * *
```
notice that i tried to set the ttl higher than 30 hops to complete the trace.

i couldn't ping 164.156.218.100.

i am no expert but sounds like 164.156.3.106 (same company, different location according to whois) doesn't route packets correctly.

---

### Post by mlyter on 2011-08-17
When I do tracert on a windows machine it times out as well.  However, on the windows machine the site is working very quickly and telnet connects.

Is it possible that packets are being routed correctly for windows, or maybe windows has a tolerance to incorrectly routed packets?  Sorry for the obvious ignorance on the topic.

Thank you,
Mike

---

### Post by WyleECoyote on 2011-08-17
not sure if this will fix ur problem, but I always disable IPV6 I know there are going to be MANY users saying "Don't disable something that will 'someday' be default" keyword there is "someday" I have never in all the years of disabling it had any slow net speeds and in most cases speeds it up, but every time I do leave it enabled I have multiple problems with some websites.

bottom line I really don't care that "someday" IPV6 will be default, I care about what fixes "My" system may not work for all but it is a painless test. here is the link:

[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

I use the grub fix, just add:
```
GRUB_CMDLINE_LINUX_DEFAULT=&#8221;[color=#FF0000]ipv6.disable=1[/color] quiet splash&#8221;
```

in /etc/default/grub like this:
```
gksudo gedit /etc/default/grub
```

then just:
```
sudo update-grub
```

if it works, you know the fix at least until you change net companies or hardware ;)

oh, almost forgot maybe you can try this first it may not change anything but if it does then that is definitely your problem:

in firefox:
about:config in address bar
search for:
network.dns.disableIPv6 set it true

still I think you should also try the grub route to make it system wide

---

### Post by mlyter on 2011-08-17
Tried both methods for disabling IPv6, saved and rebooted.  Didn't seem to make any difference in access or nslookup, traceroute, curl or telnet tests.

The information is much appreciated - making note of it for any future issues.

Thank you,
Mike

---

### Post by galvatron408 on 2011-08-18
omg, something is terribly wrong with your web site. My guess is that, the slowness is caused by your IIS server looking specifically for windows machines. 

Initially, I thought my curl was lagging because of the screen so I redirected the output to a file and it said.... the total time to load was 36 seconds! Yikes!

curl egrants.ed.state.pa.us > samplesite.out
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 19640  100 19640    0     0    538      0  0:00:36  0:00:36 --:--:--   542


Then, I did...
telnet egrants.ed.state.pa.us 80
GET /

Then, it just sat there... Now, if I did the same thing to [www.yahoo.com](www.yahoo.com), it just flys by like nothing. Go ahead, try it and you'll see.

First step: type "telnet egrants.ed.state.pa.us 80"
At the prompt type "GET /"

After that, replace it with [www.yahoo.com](www.yahoo.com).

This was performed on Centos 5.6 with Firefox 3.6.13

---

### Post by WyleECoyote on 2011-08-18
I really wish you could find the problem, but doesn't seem to be an issue to me

> curl egrants.ed.state.pa.us > samplesite.out
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 19640  100 19640    0     0   4342      0  0:00:04  0:00:04 --:--:--  4820

but yeah doing with yahoo.com

> curl [www.yahoo.com](www.yahoo.com) > samplesite.out
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100  160k    0  160k    0     0   205k      0 --:--:-- --:--:-- --:--:--  236k

I don't understand why the website has so much of a payload when yahoo has much more info with very small payload. Guess they just don&#8217;t know website optimization.

I hope you can figure out what the difference between the windblows machine and Linux so this will be fixed for everyone in future update

---

### Post by mlyter on 2011-08-18
> **galvatron408 said:**
> omg, something is terribly wrong with your web site. My guess is that, the slowness is caused by your IIS server looking specifically for windows machines. 

Initially, I thought my curl was lagging because of the screen so I redirected the output to a file and it said.... the total time to load was 36 seconds! Yikes!

curl egrants.ed.state.pa.us > samplesite.out
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 19640  100 19640    0     0    538      0  0:00:36  0:00:36 --:--:--   542


Then, I did...
telnet egrants.ed.state.pa.us 80
GET /

Then, it just sat there... Now, if I did the same thing to [www.yahoo.com]("http://www.yahoo.com"), it just flys by like nothing. Go ahead, try it and you'll see.

First step: type "telnet egrants.ed.state.pa.us 80"
At the prompt type "GET /"

After that, replace it with [www.yahoo.com]("http://www.yahoo.com").

This was performed on Centos 5.6 with Firefox 3.6.13

This isn't my agency's site - this site is owned/maintained by the Commonwealth of PA, my agency is required to use the site. 

As odd as it may seem, I was hoping that this issue was something with the Ubuntu configurations for my agency's sites - much easier for me to fix something myself than it is to get the Commonwealth to change something on their end.

I have absolutely 0 experience with IIS servers - can they really be set to look for Windows clients only?

Thank you,
Mike

---

### Post by sbraz on 2011-08-19
> **mlyter said:**
> can they really be set to look for Windows clients only?
not exactly, i think it could easily be just *untested*. there are good and bad sysadmins after all. :)
there's a good chance this is an issue with a packet-filter/ids blocking packets on a data pattern base, marking linux sources as "bad"... you know, people use it to crack computers sometimes. :D

i can't help much at this point: the only test i'd do would be trying with internet exploder on wine. it's a longshot i know... :)

---

### Post by galvatron408 on 2011-08-20
I have a good guess as to why your web page loads spool slow.

So, I did a tcpdump and I see that my client acks every single object. So imagine this...

Get line one
--ok here is line one
Get line two
--ok here is line two

This happens all the down until the whole page is served.

With [www.yahoo.com](www.yahoo.com), the conversation is more like...
Get page
--here is the whole page
Done

So, this looks like a misconfiguration on your web server. Why is your web server serving one object at a time? The strange thing is, why does your server totally ignore this if the os is windows?

---

### Post by mlyter on 2011-08-22
I don't know how/if the server is set to serve single pages.

I'll contact the support people for the Commonwealth of PA and see what they say.

I'm guessing because it is working correctly on Windows and Mac, they are going to tell me it is something with my configurations, whether or not that is the true fact.

Thanks again,
Mike

---

### Post by sbraz on 2011-08-22
> **mlyter said:**
> they are going to tell me it is something with my configurations
yes they will, i'd do the same. :)
if you think it's cool, mail them the link to this topic so you have some proof plus some technical data. :KS

---

### Post by galvatron408 on 2011-08-23
I've been doing some research and, tell them to turn on keep-alive. send them this link

[http://www.microsoft.com/technet/prodtechnol/WindowsServer2003/Library/IIS/d7e13ea5-4350-497e-ba34-b25c0e9efd68.mspx?mfr=true](http://www.microsoft.com/technet/prodtechnol/WindowsServer2003/Library/IIS/d7e13ea5-4350-497e-ba34-b25c0e9efd68.mspx?mfr=true)

The behaviour we see all points to them having keep-alive turned off.

---

### Post by mlyter on 2011-09-01
Sorry for the delay.
I contacted about the keep-alive, awaiting a response.

Thanks again,
Mike

---

### Post by mlyter on 2011-09-02
Heard back from the Commonwealth today.  The staff say that HTTP keep-alive is set to on.

Any other ideas?

Thanks again,
Mike

---

### Post by galvatron408 on 2011-09-03
Yea, they sure are using keep-alive. I see it now that I'm running on wireshark. You really got me on this one. I don't know anymore.

you know, the 404 page serves really fast and [http://egrants.ed.state.pa.us/BrowserSetup.htm](http://egrants.ed.state.pa.us/BrowserSetup.htm) serves really fast.

So, my guess is going to be that whoever designed this web page didn't put much thought in to it. They didn't optimise it for the web.

----------------------------------------------------------------------------

GET / HTTP/1.1 
Host: egrants.ed.state.pa.us 
User-Agent: Mozilla/5.0 (X11; Linux i686; rv:6.0.1) Gecko/20100101 Firefox/6.0.1 
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8 
Accept-Language: en-us,en;q=0.5 
Accept-Encoding: gzip, deflate 
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7 
Connection: keep-alive 
Cookie: ASPSESSIONIDQASBDCTS=NAJLIPNADKOAJMJJHKAEJPMJ 
 
HTTP/1.1 200 OK 
Connection: Keep-Alive 
Content-Length: 19595 
Date: Sat, 03 Sep 2011 06:39:23 GMT 
Content-Type: text/html 
Server: Microsoft-IIS/6.0 
MicrosoftOfficeWebServer: 5.0_Pub 
X-Powered-By: ASP.NET 
Cache-control: private

---

