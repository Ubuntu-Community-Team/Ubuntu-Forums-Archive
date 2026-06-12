---
title: "Slow speed with Azureus (Ratio/Nat both green!?)"
date: 2006-06-03
forum: General Help
---

### Post by shawnrgr on 2006-06-03
My NAT is GREEN along with my Ratio. My Connection seems fine. However my torrents never get a green smile, only yellow or red. And the speeds are painful. I also have the correct UDP Port forwarded in my router. No extra firewall of ati-virus program running either. Any suggestions? I've included a pic what what I mean.

---

### Post by bjc on 2006-06-03
What Java are you using? I saw slow speeds and torrents not completing correctly when using GCJ, but the Sun version works fine.

(To find out run:```
update-alternatives --config java
```).

---

### Post by jaymode on 2006-06-03
It might be a problem with some of your other settings. Azureus works fine on my machine running Dapper. One thing I have done is allow an unlimited number of peer connections, among others that I cannot remember. It could also be torrent based.

---

### Post by shawnrgr on 2006-06-03
```
There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/lib/j2re1.5-sun/bin/java
      2        /usr/bin/gij-wrapper-4.0
      3        /usr/bin/gij-wrapper-4.1
 +    4        /usr/lib/jvm/java-gcj/jre/bin/java
```

seems like im using sun java...

How do i set it to unlimited peer connections, I cannot find it in the options?

---

### Post by Stolie on 2006-06-03
One thing you may take into consideration is the torrent health. Bad torrents (e.g., not enough seeds/peers, bandwidth usage of tracker) can have an adverse effect on transfer speeds. 

Just my $0.02

---

### Post by jaymode on 2006-06-03
[QUOTE=shawnrgr]```
There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*     1        /usr/lib/j2re1.5-sun/bin/java
      2        /usr/bin/gij-wrapper-4.0
      3        /usr/bin/gij-wrapper-4.1
 +    4        /usr/lib/jvm/java-gcj/jre/bin/java
```

seems like im using sun java...

How do i set it to unlimited peer connections, I cannot find it in the options?[/QUOTE]

I am using Azureus in Intermediate mode I believe. Go to Tools->Options. Then click Transfer. There u will see 2 options: Max Connections Per Torrent Default and Max Connections Globally. I have both of these set to 0 which is unlimited and it helped with speeds. But as said before it could be torrent health.

---

### Post by NiksaVel on 2006-06-06
I have only GJC java installed it would seem...   

my prob with azureus is it starts up okay, gets to about 25kps and than hangs there.  every now and than all the downloading files drop to zero speed and start building up again...

that goes on for some 5 minutes and than both my upload and download drop to 0 and stay that way...


how do I remove gjc and install sun java? if that might be the problem...?


torrents are healthy

---

### Post by mlind on 2006-06-06
check that you haven't capped your download
Options > Transfer > "KB/s max download speed"

set that value to zero (unlimited)

Torrents look good, and you're connected to quite many seeds & peers.
Could be just luck, torrents usually start out slowly because none is intrested about
your share (you don't have any yet). One other reason could be that you're on a
blocklist ip range, and peers are not accepting your connections, but that's unlikely.

Don't use default Azureus port, change it to 6891 for example. And plug hole on iptables, 
if you're using it.

---

### Post by dpicker on 2006-06-06
You actually need to cap your upload speed or else you can damage your connection or slow the torrents.

It needs to be capped anywhere or just below your maximum upload speed. I heard if you are uploading at full speed whilst downloading, it can damage your connection permanently

---

### Post by dpicker on 2006-06-06
Try downloading an OpenOffice.org torrent just to test it. These torrents usually have plenty of seeders just waiting to upload very fast.

---

### Post by mlind on 2006-06-06
[QUOTE=dpicker]I heard if you are uploading at full speed whilst downloading, it can damage your connection permanently[/QUOTE]

lol :mrgreen:

---

### Post by dpicker on 2006-06-06
:) Seriously. If you saturate your connection i.e. Downloading and uploading at full speed for long periods of time it can damage your connection speeds permanently. I cant find any evidence to prove it but I have read it on the internet before. It might only effect people who use adsl connections, I'm not sure.

---

### Post by malkaven on 2006-06-11
im having the same issues.  its something w/ azerues.  if I use the default bit torrent app with dapper the torrent file downloads fine.

---

### Post by Glendon on 2006-06-11
I was seeing similar problems. My speeds would drop to zero after about 5 mintues and I would get a message that something was wrong with my NAT. I switched to the Sun JRE and now I'm smoking.

Thanks for the help.

---

### Post by NiksaVel on 2006-06-12
do I need to unintstall the other java after I install the sun java?

---

### Post by mlind on 2006-06-12
[QUOTE=NiksaVel]do I need to unintstall the other java after I install the sun java?[/QUOTE]

No.
```

sudo update-alternatives --config java

```
and choose Sun's java should do it.

---

### Post by cwwitt on 2006-06-12
I am using Azureus.  Cap your UPLOAD to 7 KiloBYTES (56 kilobits) to drastically increase your internet speed.

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

### Post by mlind on 2006-06-12
[QUOTE=cwwitt]Summary:
Cap your upload speed near 7 kiloBYTES to drastically increase your download speed.[/QUOTE]

That's not very good sport for p2p networks, if everybody would limit their upload
like that, what would happen do your download speed? Also, more you upload,
better ratio you get for download. 

Capping upload for 2 kbps below maximum is better.

---

### Post by NiksaVel on 2006-06-12
after azureus gave me some much headaches I tried Ktorrent and it works sweet...  downloads approx. 10gigs a day and uploads about double that...   that's more downloading power than I can spend time burning to dvd-s....  I would recommend it to anyone...

---

### Post by gusto5 on 2006-09-09
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java

that's the java i'm currently using and it works great. Thanks for the update-alternatives command!

---

### Post by rcatman on 2006-09-19
I've been having the same problem with torrents in ubuntu. I have port-forwarding setup on my Linksys WRT54G router (forwarding ports 6881-6889 to my computer). I've used torrent on another computer in my network(mac os x/azureus) and it works perfect. 

I've tried KTorrent and Azureus. Both were very very slow and the torrents stalled constantly.

I'm installing sun java 5 and will post whether it fixes azureus or not. But i doubt it. The only way I was able to install java is thru automatix.

---

