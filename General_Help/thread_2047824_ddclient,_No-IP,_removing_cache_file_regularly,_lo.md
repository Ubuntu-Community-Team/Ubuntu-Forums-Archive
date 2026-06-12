---
title: "ddclient, No-IP, removing cache file regularly, logical way to keep account active?"
date: 2012-08-25
forum: General Help
---

### Post by Roasted on 2012-08-25
I have ddclient running on my server, which is a 12.04 box. My DDNS service is through No-IP. I received an email today from No-IP that my account will be deactivated due to inactivity. I did some more reading because I thought I had ddclient running perfectly, as it's given me no issue for months. Some further research suggests that ddclient creates a cache file, located in /var/cache/ddclient/ddclient.cache. It then checks your IP with some sort of "whatismyip" type of service, and then cross references it versus the cache file. If your IP hasn't changed, it doesn't call out to No-IP to update you... which may very well be why they emailed me thinking I don't use my account anymore.

My plan was to simply run a cron job that removes this cache file... I'm thinking maybe weekly?? That way (I assume) it would have to intentionally call out to No-IP in order to generate the cache file, which would inadvertently update my account, thus removing any fear into the future that my account may get disabled due to a false sense of inactivity.

I'm questioning if there may be any repercussions to messing with that cache file, or if there's a better way to force ddclient to do a "full update" on the go. I would think this would work, but if there's a better way, I'm all ears.





```
Side Note: For those of you having trouble using DDclient with No-IP services, this ddclient.conf worked for me:

protocol=dyndns2
use=web, web=dyndns
server=www.noip.com
login=YOUREMAILADDRESS@HERE.COM
password='yourpasswordhereforyourddnsservice'
your.ddnsdomain.org
```

---

