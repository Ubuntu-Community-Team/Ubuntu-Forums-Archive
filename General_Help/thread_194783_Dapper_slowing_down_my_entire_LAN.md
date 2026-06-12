---
title: "Dapper slowing down my entire LAN"
date: 2006-06-11
forum: General Help
---

### Post by halo five on 2006-06-11
It seems lots of people have been having a terrible time with networking in Dapper, and I'm no exception.  Typical symptoms, Internet on my Ubuntu box is terribly slow, across the board, not just in firefox. 

host [http://www.google.com](http://www.google.com) takes several seconds to respond.

Hoary worked fine.  Breezy worked fine.

As well, as soon as I turn on my Ubuntu box, my two Windows machines on the same network are affected as well, with terrible network throughput.  I suspected IPV6, and performed all of the changes here -> [https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4) as well as commenting out all references to IPV6 in my /etc/hosts file. I also did the about:config bit in firefox, which shouldn't be necessary given the other changes I've made.

My router is a TrendNet TEW432.

So what's left? DNS? Strange that the Windows boxes are perfectly speedy when the Ubuntu box is off.   Does anyone know any DNS-related settings I could check?  

My next step is plugging my Ubuntu box directly into my cable modem and seeing if it's any faster.  I read somewhere that I could try to remove the name servers from /etc/something something and replace them with public ones.. I'm not going to pretend I know what I'm talking about here, or understand why I'd need to do this with Dapper but not Breezy.

Please help!

---

### Post by ltmon on 2006-06-11
Have you seen if the Avahi daemon is running?  I don't think it is installed by default, so you would have had to install it yourself at some time.

I just ask because I know a badly setup avahi can cause this kind of behaviour in a LAN.

Have a look in Synaptic for any package beginning with "avahi" or "libnss-mdns" to check.

---

### Post by polt on 2006-06-12
I'm having this problem too.  It is having an especially bad effect on my email which times out before downloading the new emails.  It seems to be effecting everyone else on the LAN too.

---

### Post by Chris03 on 2006-06-12
Not sure about LANs, but to disable IPv6, do this:

sudo gedit /etc/modprobe.d/bad_list

Then, enter this into the text:

alias net-pf-10 off

[More information]("http://www.google.com/search?q=alias+net-pf-10+off")

---

### Post by cwwitt on 2006-06-12
If you are using Bit Torrent or P2P or whatever to download files, then this may help you.

Hopefully this will help some people who may be suffering from really really slow slow internet. I'm just glad I finally figured it out. I was about to change internet providers. Now my internet seems much much faster.

If you download files with BitTorrent or P2P or whatever.
Make sure that you cap your UPLOAD speed to about 7 kiloBYTES (56 kilobits).
I am using Adelphia cable internet.
They apparently drastically throttle down my download speed the more I upload.
I was getting 27 to 35 kiloBYTES download (and occasionally near 0 kiloBYTES - oh the headaches it gave me) with no cap on my upload (was averaging 70 kiloBYTES upload).
Now with my upload capped at 7 kiloBYTES
I now get easily surges up to 200 kiloBYTES or higher.

Summary:
Cap your upload speed near 7 kiloBYTES to drastically increase your download speed.

---

### Post by mattkenn4545 on 2006-06-12
I wouldn't recommend the above post instead switch to another providor.  Capping uploads to such a low rate stifles what makes P2P so great.

Remember the download speed comes from somewhere if you arn't uploading you are a LEACH no-one likes a leach.

---

### Post by halo five on 2006-06-12
[QUOTE=Chris03]Not sure about LANs, but to disable IPv6, do this:

sudo gedit /etc/modprobe.d/bad_list

Then, enter this into the text:

alias net-pf-10 off

[More information]("http://www.google.com/search?q=alias+net-pf-10+off")[/QUOTE]

I have that in /etc/modprobe.d/aliases, as well as having ipv6 blacklisted in /etc/modprobe.d/aliases.  Do I have to update it in bad_list as well?  I don't think so, maybe someone can clarify.

If I don't get this fixed up soon, it's back to Windows.  Sigh.  :-({|=

---

### Post by Fedup on 2006-06-12
[quote=mattkenn4545]I wouldn't recommend the above post instead switch to another providor.  Capping uploads to such a low rate stifles what makes P2P so great.

Remember the download speed comes from somewhere if you arn't uploading you are a LEACH no-one likes a leach.[/quote] 
But you DO want to cap your upload on P2P to approx 75% of your max upload speed or you'll suffer from terrible download speeds etc.

---

### Post by halo five on 2006-06-12
Thanks for the p2p-related tips, but this is affecting my lan with no p2p services running.  It does get worse if I run BitTorrent or similar, but p2p is definitely not the root cause.

---

### Post by Chris03 on 2006-06-14
[QUOTE=halo five]I have that in /etc/modprobe.d/aliases, as well as having ipv6 blacklisted in /etc/modprobe.d/aliases.  Do I have to update it in bad_list as well?  I don't think so, maybe someone can clarify.

If I don't get this fixed up soon, it's back to Windows.  Sigh.  :-({|=[/QUOTE]
Not sure on the other files, all I have is the bad_list file here.

---

