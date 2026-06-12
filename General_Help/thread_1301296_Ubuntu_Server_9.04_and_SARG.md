---
title: "Ubuntu Server 9.04 and SARG"
date: 2009-10-25
forum: General Help
---

### Post by Jarr0d on 2009-10-25
I have a Tiny proxy, squid, DG, Webmin and SARG built on Ubuntu Server 9.04 server. With older versions this seemed to be fine, but since the update to 9.04, it seems that the generate script included with sarg, isn't functioning properly.

I have been using the '/usr/sbin/sarg-reports daily' script, and from what I can see, this isn't giving the correct output. If I go to [http://server/squid-reports/](http://server/squid-reports/) all I can is a dead picture link, and empty daily, weekly and monthly links.

Now, if I use the "Generate Report Now" link in Webmin, it executes and out puts fine. If I go to the same URL, I see the picture and the daily logs.

If I run the /usr/sbin/sarg-reports script again and go to the URL, I see the same as before, dead links and empty folders.

Anyone got an idea on what would cause this?

---

### Post by Jarr0d on 2009-10-26
Sorted it out. I had to set visible_hostname in squid. The hostname it was using was not in DNS records

---

