---
title: "Can no longer view nmap xml in any browser [hardy]"
date: 2009-07-28
forum: General Help
---

### Post by arsenic23 on 2009-07-28
I needed to do a quick bit of network troubleshooting this morning so I ssh'd into the server at work and ran nmap to get an idea on what had been done to the network.  When I was done I was surprised to see that I would get a blank screen in firefox when trying to view the xml log data from nmap.  I got the same blank screen in both epiphany and Opera as well.

Also none of my old nmap logs display either, even though I've always been able to view them.  Anyone have any clue what the problem might be ?

Using Hardy.

Sample xml file using google.com:
[HTML]<?xml version="1.0" ?>
<?xml-stylesheet href="/usr/share/nmap/nmap.xsl" type="text/xsl"?>
<!-- Nmap 4.53 scan initiated Tue Jul 28 11:29:19 2009 as: nmap -v -A -P0 -oX tmp www.google.com -->
<nmaprun scanner="nmap" args="nmap -v -A -P0 -oX tmp www.google.com" start="1248794959" startstr="Tue Jul 28 11:29:19 2009" version="4.53" xmloutputversion="1.01">
<scaninfo type="connect" protocol="tcp" numservices="1714" services="1-1027,1029-1033,1040,1043,1050,1058-1059,1067-1068,1076,1080,1083-1084,1103,1109-1110,1112,1127,1139,1155,1158,1178,1212,1214,1220,1222,1234,1241,1248,1270,1337,1346-1381,1383-1552,1600,1650-1652,1661-1672,1680,1720,1723,1755,1761-1764,1827,1900,1935,1984,1986-2028,2030,2032-2035,2038,2040-2049,2053,2064-2065,2067-2068,2105-2106,2108,2111-2112,2120-2121,2201,2232,2241,2301,2307,2401,2430-2433,2500-2501,2564,2600-2605,2627-2628,2638,2766,2784,2809,2903,2998,3000-3001,3005-3006,3025,3045,3049,3052,3064,3086,3128,3141,3264,3268-3269,3292,3299,3306,3333,3372,3389,3397-3399,3421,3455-3457,3462,3531,3632,3689,3900,3984-3986,3999-4000,4002,4008,4045,4125,4132-4133,4144,4199,4224,4321,4333,4343,4444,4480,4500,4557,4559,4660,4662,4672,4899,4987,4998,5000-5003,5009-5011,5050,5060,5100-5102,5145,5190-5193,5232,5236,5300-5305,5308,5400,5405,5432,5490,5500,5510,5520,5530,5540,5550,5555,5560,5631-5632,5679-5680,5713-5717,5800-5803,5900-5903,5977-5979,5997-6009,6017,6050,6101,6103,6105-6106,6110-6112,6141-6148,6222,6346-6347,6400-6401,6502,6543-6544,6547-6548,6558,6588,6662,6665-6670,6699-6701,6881,6969,7000-7010,7070,7100,7200-7201,7273,7326,7464,7597,7937-7938,8000,8007,8009,8021,8076,8080-8082,8118,8123,8443,8770,8888,8892,9040,9050-9051,9090,9100-9107,9111,9152,9535,9876,9991-9992,9999-10000,10005,10082-10083,11371,12000,12345-12346,13701-13702,13705-13706,13708-13718,13720-13722,13782-13783,14141,15126,15151,16080,16444,16959,17007,17300,18000,18181-18185,18187,19150,20005,22273,22289,22305,22321,22370,26208,27000-27010,27374,27665,31337,31416,32770-32780,32786-32787,38037,38292,43188,44334,44442-44443,47557,49400,50000,50002,54320,61439-61441,65301" />
<verbose level="1" />
<debugging level="0" />
<taskbegin task="Parallel DNS resolution of 1 host." time="1248794959" />
<taskend task="Parallel DNS resolution of 1 host." time="1248794959" />
<taskbegin task="Connect Scan" time="1248794959" />
<taskend task="Connect Scan" time="1248795002" extrainfo="1714 total ports" />
<taskbegin task="Service scan" time="1248795002" />
<taskend task="Service scan" time="1248795015" extrainfo="2 services on 1 host" />
<host><status state="up" reason="localhost-response"/>
<address addr="66.102.1.147" addrtype="ipv4" />
<hostnames><hostname name="he-in-f147.google.com" type="PTR" /></hostnames>
<ports><extraports state="filtered" count="1711">
<extrareasons reason="no-responses" count="1711"/>
</extraports>
<port protocol="tcp" portid="80"><state state="open" reason="syn-ack" reason_ttl="0"/><service name="http" product="Google httpd" version="2.0" extrainfo="GFE" ostype="Linux" method="probed" conf="10" /></port>
<port protocol="tcp" portid="113"><state state="closed" reason="conn-refused" reason_ttl="0"/><service name="auth" method="table" conf="3" /></port>
<port protocol="tcp" portid="443"><state state="open" reason="syn-ack" reason_ttl="0"/><service name="http" product="Google httpd" version="2.0" extrainfo="GFE" ostype="Linux" tunnel="ssl" method="probed" conf="10" /></port>
</ports>
<times srtt="168801" rttvar="129311" to="686045" />
</host>
<runstats><finished time="1248795015" timestr="Tue Jul 28 11:30:15 2009"/><hosts up="1" down="0" total="1" />
<!-- Nmap done at Tue Jul 28 11:30:15 2009; 1 IP address (1 host up) scanned in 56.064 seconds -->
</runstats></nmaprun>[/HTML]

---

### Post by lsop on 2009-11-21
Hello there
 
Did you ever work this out?
Having the same problem trying to view nmap xml output using firefox on the same machine that the scans were done.
It would appear that FF does not load the nmap stylesheet to filter the XML source.
 
One difference: 
using nmap 5.0 (self compiled and installed to /usr/local) on Ubuntu 9.04 with FF v3.0.15 the path to the stylesheet (embedded in the XML) is [file:///usr/local/share/nmap/nmap.xsl](file:///usr/local/share/nmap/nmap.xsl)
 
When I copy the XML output files and a copy of the stylesheet to a samba share and edit the XML to point to <?xml-stylesheet href="./nmap.xsl" type="text/xsl"?> then open the XML in IE8 on an XP box, all is well.
I guess there must be a setting in FF to enable this behaviour too. Next step: working out what it is...
MTIA for any pointers...
 
 
WELL! Waddayaknow:  opening the XML with FF ON the Ubuntu box FROM the Samba share works fine and dandy!  
It's a work-around at least...

---

### Post by fabianp on 2010-02-19
The issue definitively involves the <?xml-stylesheet href="./nmap.xsl" type="text/xsl"?> line.

I'm not really clear how to fix it, but as a work around that works just fine is to use:

 xsltproc nmaplog.xml -o nmaplog.html 

That *.html page is open without issues. I hope this helps,

---

### Post by cprofitt on 2010-09-07
Well, the last bit helps, but makes for an extra step. I am not sure what the issue is, but it would be nice to figure this out.

---

### Post by ecron on 2012-08-03
Although this post is old I ran into a similar problem. It was solved by changing the permissions of the nmap.xsl file and copying it to my local working directory.

---

### Post by wildmanne39 on 2012-08-04
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

