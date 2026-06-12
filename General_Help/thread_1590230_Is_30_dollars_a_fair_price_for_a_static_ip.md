---
title: "Is 30 dollars a fair price for a static ip?"
date: 2010-10-07
forum: General Help
---

### Post by rcayea on 2010-10-07
My hosting company sells ip addresses for 30 dollars a year and I have no experience in ip address pricing. So does this sound fair or at least not a total rip-off?

thanks,
Randy

---

### Post by davidmohammed on 2010-10-07
no idea - but if you are just after a static DNS name that you can access your PC from anywhere then I use no-ip.org.  Its free.  I've set up my router to update no-ip when my hosting company changes my IP address.  Thus, I can contact my server from anywhere by just the DNS name.

---

### Post by rcayea on 2010-10-07
Would that solve this problem as described by my brother-in-law? He and I are going to set up my email server this weekend...


"if your IP changes, then you won't get email for 24-48 hours
while your new IP address is propagated to your server name across the internets."



thanks,
Randy

---

### Post by davidmohammed on 2010-10-07
I've never noticed this 24-48hrs interval - just a few minutes for me.

---

### Post by WorMzy on 2010-10-07
Static IP addresses are the way to go if you're planning on using a registered domain name, because of the way that domain name servers work. If your IP address changes, then name servers will continue to direct traffic to the old IP until they get updated with the new IP address, which can take, as you said, between 24-48 hours.

---

### Post by pricetech on 2010-10-07
30 bucks a year for a fixed IP is a good deal.  If I were running servers that I HAD to connect to, I'd get a fixed IP myself.

---

### Post by rcayea on 2010-10-07
Thanks for the feedback!

Randy

---

### Post by efflandt on 2010-10-07
How long it takes to propagate a DNS change depends upon DNS settings for that name or domain.  Some may have a TTL (time to live) of a day or week or longer.  But from **dig** my_no-ip.com_name **ns**, when that name was not in my cache, it appears that no-ip.com names expire from DNS cache in 10 minutes (600 seconds), so a change will propagate relatively quickly.

;; AUTHORITY SECTION:
no-ip.com.        600    IN    SOA    ns2.no-ip.com. hostmaster.no-ip.com. 2035606853 600 300 604800 600

However, many smtp servers may not accept mail from anything that appears to be a dynamic IP (to minimize spam, worms, etc.).  So it would be best to have a static IP and $30/yr sounds reasonable to me.  It is also best if your smtp server identifies itself by a name that resolves as a public DNS A record to your public IP (even though not a requirement).

---

