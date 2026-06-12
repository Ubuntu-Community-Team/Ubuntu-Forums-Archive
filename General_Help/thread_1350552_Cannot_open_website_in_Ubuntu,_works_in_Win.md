---
title: "Cannot open website in Ubuntu, works in Win"
date: 2009-12-09
forum: General Help
---

### Post by viktorzk on 2009-12-09
Hello,

I cannot open [http://www.funambol.com/opensource/](http://www.funambol.com/opensource/) in Firefox (3.5.5) and Konqueror in Ubuntu 9.10. The browser keeps "waiting for ...". The website opens on another computer with Firefox (3.5.2, with many plugins) and IE6 on Windows. Also [http://www.funambol.com]("http://www.funambol.com/") does not cause any problems.

Most other websites work fine, there were a few other similar cases which I cannot remember.

Installing Java and Flash plugins (as suggested elsewhere) did not help.

Thanks.

EDIT: I've tried to make a summary of pages 1-3 in the end of page 3.

---

### Post by viktorzk on 2009-12-10
bump

---

### Post by Physical Hook on 2009-12-10
Works fine from here. Can you access it by opening [COLOR=Gray]204.16.105.142[/COLOR] ?

[[IMG]http://i46.tinypic.com/mt2tdt_th.png[/IMG]]("http://i46.tinypic.com/mt2tdt.png")

---

### Post by lisati on 2009-12-10
Works fine here, FF 3.0.15, Ubuntu 9.04 32-bit. Seemed to be a *slight *pause loading though.

---

### Post by lmarmisa on 2009-12-10
Install the package lynx (a text www browser) with Synaptic and try to access to that page with this browser.

Best regards,

Luis

---

### Post by viktorzk on 2009-12-10
@Physical Hook, it again waits for "www.forge.funambol.org".

@Luis, lynx went unresponsive, still displaying the previous page. None of the shortcut keys worked, had to ctrl+c it.

Edit: just noticed that Facebook also does not work. The welcome page is fine, but when logged on, only the top blue menu strip gets displayed.

---

### Post by lmarmisa on 2009-12-10
Open a terminal and type

```

telnet www.funambol.com 80
# Wait until Escape character is...
get

```

Tell me if you get some output to this commands.

---

### Post by scouser73 on 2009-12-10
The page opens fine, but redirects to [https://www.forge.funambol.org/DomainHome.html](https://www.forge.funambol.org/DomainHome.html)

---

### Post by lmarmisa on 2009-12-10
Ping service is available in [www.funanbol.com]("http://www.funanbol.com")

```

lmarmisa@UBUNTU910:~$ ping www.funambol.com
PING www.funambol.com (12.158.189.92) 56(84) bytes of data.
64 bytes from msedesign.ve.servadmin.com (12.158.189.92): icmp_seq=1 ttl=41 time=499 ms
64 bytes from msedesign.ve.servadmin.com (12.158.189.92): icmp_seq=2 ttl=41 time=511 ms
64 bytes from msedesign.ve.servadmin.com (12.158.189.92): icmp_seq=3 ttl=42 time=552 ms
64 bytes from msedesign.ve.servadmin.com (12.158.189.92): icmp_seq=4 ttl=42 time=478 ms
64 bytes from msedesign.ve.servadmin.com (12.158.189.92): icmp_seq=5 ttl=41 time=424 ms
64 bytes from msedesign.ve.servadmin.com (12.158.189.92): icmp_seq=6 ttl=41 time=477 ms
64 bytes from msedesign.ve.servadmin.com (12.158.189.92): icmp_seq=8 ttl=43 time=567 ms
64 bytes from msedesign.ve.servadmin.com (12.158.189.92): icmp_seq=9 ttl=43 time=469 ms
64 bytes from msedesign.ve.servadmin.com (12.158.189.92): icmp_seq=10 ttl=42 time=559 ms
64 bytes from msedesign.ve.servadmin.com (12.158.189.92): icmp_seq=11 ttl=43 time=402 ms
64 bytes from msedesign.ve.servadmin.com (12.158.189.92): icmp_seq=12 ttl=43 time=512 ms
^C
--- www.funambol.com ping statistics ---
12 packets transmitted, 11 received, 8% packet loss, time 11231ms
rtt min/avg/max/mdev = 402.216/495.846/567.085/50.484 ms

```Check the ping command too. So, yo will check DNS and connectivity.

Regards,

Luis

---

### Post by viktorzk on 2009-12-10
@Luis,

[www.funambol.com](www.funambol.com) opens without problems in Firefox, and telnet returned its HTML source.
Then I tried with 204.16.105.142, and it returned the following:

viktor@ubuntu:/etc$ telnet 204.16.105.142 80
Trying 204.16.105.142...
Connected to 204.16.105.142.
Escape character is '^]'.
get
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="https://www.forge.funambol.org/">here</a>.</p>
<hr>
<address>Apache Server at forge.funambol.org Port 80</address>
</body></html>
Connection closed by foreign host.

@scouser73, yes, it does and should redirect, I hadn't noticed. Does it make a difference?

---

### Post by viktorzk on 2009-12-10
viktor@ubuntu:/etc$ ping [www.funambol.com](www.funambol.com)
PING [www.funambol.com](www.funambol.com) (12.158.189.92) 56(84) bytes of data.
64 bytes from msedesign.ve.servadmin.com (12.158.189.92): icmp_seq=1 ttl=37 time=184 ms
^C
--- [www.funambol.com](www.funambol.com) ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4004ms
rtt min/avg/max/mdev = 183.892/185.155/188.892/1.880 ms

viktor@ubuntu:/etc$ ping 204.16.105.142
PING 204.16.105.142 (204.16.105.142) 56(84) bytes of data.
64 bytes from 204.16.105.142: icmp_seq=1 ttl=38 time=224 ms
64 bytes from 204.16.105.142: icmp_seq=2 ttl=38 time=224 ms
^C
--- 204.16.105.142 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 224.212/224.396/224.631/0.185 ms

---

### Post by lmarmisa on 2009-12-10
The redirected page is a secure page ([https://www.forge.funambol.org/](https://www.forge.funambol.org/)).

Any problems with other secure pages?.

Regards,

Luis

---

### Post by viktorzk on 2009-12-10
Yes. After trying with the first few Google autocomplete results for https:

Working:
[https://www.guardiananytime.com/](https://www.guardiananytime.com/)
[https://www.consumercardaccess.com/main/mygiftcardsite/Home](https://www.consumercardaccess.com/main/mygiftcardsite/Home) //here I clicked a different https link which redirected to this page.

Not working:
[https://www.esnapw.com/rses/ESnapServlet?MerchantNumberSent=08881&cmd_PopUp=ContactUs&userOptForDual=N&LanguageIndicator=en](https://www.esnapw.com/rses/ESnapServlet?MerchantNumberSent=08881&cmd_PopUp=ContactUs&userOptForDual=N&LanguageIndicator=en)
[https://my.t-mobile.com/Login/?rc=&dest=https%3a%2f%2fmy.t-mobile.com%3a443%2fDefault.aspx]("https://my.t-mobile.com/Login/?rc=&dest=https%3a%2f%2fmy.t-mobile.com%3a443%2fDefault.aspx")

Should I try with more?

---

### Post by lmarmisa on 2009-12-10
Do you think that wrong pages are always secure pages (a subset, of course)?.

---

### Post by viktorzk on 2009-12-10
I cannot remember the other pages that did not load. But I have been browsing with Ubuntu for over a week and had problems only with a handful of pages. Now after you asked, half of the secure pages I try don't load.
Another page that causes trouble is Facebook.  The welcome page is fine, but when logged on, only the top blue menu strip gets displayed. But one would expect from them to stream the main contents through a secure connection.

---

### Post by viktorzk on 2009-12-10
Perhaps I should have mentioned earlier that the Windows computer (on which everything opens fine) is connected with a cable to the home LAN, while the Ubuntu laptop is connected (to the same LAN) through a wireless network.

---

### Post by lmarmisa on 2009-12-10
You could check if there is a problem with DNS using a public proxy.

Verify that the Firefox configuration supports  SSL 3.0 and TLS 1.0.

---

### Post by lmarmisa on 2009-12-10
I think that this problem is not related with Ethernet or WiFi.

---

### Post by lmarmisa on 2009-12-10
The public DNS servers of google are 8.8.8.8 and 8.8.4.4 

May be you could try to use them in order to check if this is a problem related with the DNS resolution. Read this page for changing your DNS servers for this test: 

[http://shibuvarkala.blogspot.com/2009/12/how-to-setup-google-public-dns-in.html](http://shibuvarkala.blogspot.com/2009/12/how-to-setup-google-public-dns-in.html)

---

### Post by viktorzk on 2009-12-10
Both  SSL 3.0 and TLS 1.0 are checked in the preferences page.

Doesn't open with a public SOCKS 5 proxy (proxy tested on other pages), nor with Google's DNS servers.

---

### Post by lisati on 2009-12-10
> **viktorzk said:**
> Another page that causes trouble is Facebook.  The welcome page is fine, but when logged on, only the top blue menu strip gets displayed.

I *sometimes* get a similar effect when navigating to [http://spamcop.net](http://spamcop.net), not a secure page. Usually fixed by refreshing the page. (ff 3.0.15)

---

### Post by lmarmisa on 2009-12-10
I suppose that you have made the test with a secure proxy (Proxy SSL), right?

---

### Post by viktorzk on 2009-12-10
> **viktorzk said:**
> Yes. After trying with the first few Google autocomplete results for https:

Not working:
[https://www.esnapw.com/rses/ESnapServlet?MerchantNumberSent=08881&cmd_PopUp=ContactUs&userOptForDual=N&LanguageIndicator=en](https://www.esnapw.com/rses/ESnapServlet?MerchantNumberSent=08881&cmd_PopUp=ContactUs&userOptForDual=N&LanguageIndicator=en)
[https://my.t-mobile.com/Login/?rc=&dest=https%3a%2f%2fmy.t-mobile.com%3a443%2fDefault.aspx](https://my.t-mobile.com/Login/?rc=&dest=https%3a%2f%2fmy.t-mobile.com%3a443%2fDefault.aspx)

Both of these and Facebook work with the public SOCKS 5 proxy. So far I have not found another website not to open through the proxy.

---

### Post by viktorzk on 2009-12-10
> **lmarmisa said:**
> I suppose that you have made the test with a secure proxy (Proxy SSL), right?

Probably not. I pasted the IP address and port (212.227.107.220:10080) of a public SOCKS 5 proxy in the SOCKS Host field of Firefox's advanced network settings.

I will try to find a SSL proxy.

---

### Post by lmarmisa on 2009-12-10
Try to define a new user account and check if the problem is limited to your account or if it is common to all the users of your Ubuntu system.

---

### Post by viktorzk on 2009-12-10
Common to all users it seems.

---

### Post by lmarmisa on 2009-12-10
Hmmm. The problem seems really elusive.

---

### Post by john newbuntu on 2009-12-10
Update your software esp your kernel and see if that helps.

---

### Post by viktorzk on 2009-12-16
John, complete reinstall and update did not help.


I will try to summarize what we know so far.

I cannot open certain https websites from Ubuntu. The browser keeps "waiting for ...". I can open them from Windows.
Examples:
-https://forge.funambol.com (the ip is different from funambol.com's)
-https://my.t-mobile.com
-Facebook, after logging in only the top menu bar shows.

The problem is not browser-dependent (even lynx hangs).
The problem is not DNS-related, because I can't open the corresponding IP addresses either.
The problem occurs with both ethernet and wireless connections, so it is probably not related to the eth/wlan card drivers?
The problem also occurs in a Windows virtual machine connected through NAT.
The problem does not occur in a Windows virtual machine with bridged connection.
The problem also occurs when connected through a public SOCKS 5 proxy.

---- this is the ip of forge.funambol.com
viktor@ubuntu:/etc$ telnet 204.16.105.142 80
Trying 204.16.105.142...
Connected to 204.16.105.142.
Escape character is '^]'.
get
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="https://www.forge.funambol.org/">here</a>.</p>
<hr>
<address>Apache Server at forge.funambol.org Port 80</address>
</body></html>
Connection closed by foreign host.
----

EDIT: added bridged vm case, which works.

---

### Post by lmarmisa on 2009-12-16
[I]The problem also occurs in a Windows virtual machine connected through NAT.

[/I]Do you use VirtualBox?.

In this case, try to swith from NAT to Bridge mode and check if the problem continues. This configuration is equivalent to a different physical computer. So, if the problem continues, perhaps it is external to your machine.

Best regards,

Luis

---

### Post by viktorzk on 2009-12-16
Yes, I use VirtualBox, and there is no problem in Bridge mode.

---

### Post by lmarmisa on 2009-12-16
Perhaps a problem with openssl module or something like that?. Sorry, I am not an expert. It is only an idea.

---

### Post by running_rabbit07 on 2009-12-16
Did you reinstall with the same disk or a new one? This is a really odd issue that doesn't click with being any problem within the OSI stack. TCP/IP is used for that site's communication and all seems well. 

Install Wireshark from the repository and see if you get any problematic packets when connecting to that site.

I only had one bad packet that had to be retransmitted, so there would have to be a problem on your end. 

I do find it notable that NoScript blocks that site by default.

---

### Post by viktorzk on 2009-12-16
I re-downloaded the image and burnt it on a new CD, but it was the same image.

I installed Wireshark, but I'm still figuring out what to do with it. I tried to open forge.funambol.com while capturing packets, it said 0 dropped. What else?

Did you try opening the link in your thumbnail? My Firefox shows 'page not found' immediately, instead of waiting for the site, as it does for forge.funambol.com, without the www. Maybe the www link is broken? Could this, combined with redirection, cause the trouble?

---

### Post by viktorzk on 2009-12-16
Luis, I already reinstalled the openssl package. What else could I do to test this hypothesis? Perhaps a browser that uses another ssl module?

---

### Post by lmarmisa on 2009-12-16
Sorry Viktor, but I am not an expert in security.

This is the Ubuntu documentation for openssl:

[https://help.ubuntu.com/community/OpenSSL](https://help.ubuntu.com/community/OpenSSL)

The problem is really odd. 

I have been thinking about the different behavour between NAT and bridge modes on your XP VM. I think that your host computer does not offer any services related to security in both cases. So, openssl is probably innocent. DNSs services are solved by the XP OS. So, DNS seems innocent too. So the problem is limited to the TCP/IP stack and, maybe, to NAT and IP routing functions. Do you use iptables and have you defined some not standard routing rules?.

A different question. Have you the same problem running Ubuntu from a Live CD?.

Best regards,

Luis

---

### Post by viktorzk on 2009-12-16
I don't know what iptables and routing rules are. I have not knowingly used any.

I have the same problem when running Ubuntu from its installation CD.

I have attached a screenshot of Wireshark after capturing while attempting to load forge.funambol.com. I don't know what to do with it.

---

### Post by lmarmisa on 2009-12-16
*I have the same problem when running Ubuntu from its installation CD.*

So, I believe that nothing is corrupted in your installation.

I would move my suspicions to your router (if you have any router, of course :)).

Possibly your router is not working properly with Ubuntu or with your specific IP address in your LAN.

---

### Post by viktorzk on 2009-12-16
You are right. After disabling the router's firewall, everything works great. Is it safe to keep it off?
Many thanks for all the help! You saved my Ubuntu!

---

### Post by lmarmisa on 2009-12-16
My router is a Lynksys WRT54GL running the Tomato firmware. Its firewall menu shows only security options (Respond to ICMP ping, Allow multicast, NAT loopback, Enable SYN cookies). As you can see, this is very different to the classic firewall function on a host.

In my humble oppinion, the firewall function is made in a router by means of the NAT function. NAT is the best barrier for defending your LAN from external attacks. Of couse, you have to close all or almost all ports (some services may require to open some ports, but this is the exception to the general rule).

Therefore, my comment is that NAT is the best firewall for your router. Try to investigate what means "firewall" for your router manufacturer :-).

Best regards,

Luis

---

### Post by running_rabbit07 on 2009-12-17
The only protection I use in my router is the NAT function. Each host has its own firewall protection. To get past NAT, one would have to know your LAN addressing scheme, which can be very hard to do. Be sure to keep access to your router password protected.

---

