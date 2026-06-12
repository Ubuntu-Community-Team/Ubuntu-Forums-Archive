---
title: "Can locate someone who visits my website?"
date: 2011-10-03
forum: General Help
---

### Post by sofasurfer on 2011-10-03
I have a website. I can view the IP address of a visitor. Is this IP address the person visiting or the server that he uses to surf the web? When I look up the IP address and it shows a location of N.Y, New York for instance, is that the location of the server or the web surfer? Can I find the actual location of the person visiting my website?

---

### Post by 2F4U on 2011-10-03
That depends the ISP of the surfer. I would guess that most ISP's provide their customers with shared IP addresses, i.e. when the surfer goes online he gets a public IP addres out of a pool that is owned by the ISP. This pool is shared between all customers of this particular ISP. If this particular customer goes offline, the IP address will be released and another customer may obtain it.
So in this case the IP address is linked to the ISP and not to the customers. However, most customers will probably have an ISP in their own country but the location you get is not necessarily where the real customer lives.

---

### Post by SeijiSensei on 2011-10-03
Some ISPs like AOL in its dialup incarnation would proxy all their connections through a few caching servers.  So you'd see a visitor with an aol.com address, but that told you nothing about the actual source of the web request.  Nowadays most everyone has a unique IP address.  ISPs still cache a lot of traffic, but the source address is usually the IP of the visitor.  (Some ISPs will redirect things like misspelled server names to a page with advertising or otherwise try to [monetize]("http://yro.slashdot.org/story/08/02/18/2033202/uk-isps-to-start-tracking-your-surfing-to-serve-you-ads") their customers' web browsing.)

[IP geolocation]("http://en.wikipedia.org/wiki/Geolocation_software") can provide more specific information about where a visitor is located; this is a [growth business]("http://www.ip2location.com/").

---

### Post by Mark Phelps on 2011-10-03
As far as I know, the only way to get truly unique IP addresses is using IP version 6 -- and most, if not all, of the IP addresses you will see are still version 4.

Any geographical address associated with that IP is the address provided at the time the set of IP addresses was registered.  In the case of an ISP, it's typically one of the locations they use for their server farms, or their official office location.

So basically, the address info tells you almost nothing useful.

---

### Post by SeijiSensei on 2011-10-03
> **Mark Phelps said:**
> So basically, the address info tells you almost nothing useful.

I think that's a bit extreme, Mark.  Many US ISPs include the state or city in their reverse records, e.g., c-24-xx-xx-xx.hsd1.ma.comcast.net, and providers outside the US typically have reverse records with ISO country code domains like .ca or .uk.  There's also a free (LGPL) library called [GeoIP]("http://www.maxmind.com/app/c") that's used by many applications, KTorrent being one. 

Many websites accurately identify my city and state from my IP address.  I visited the T-Mobile site over the weekend, and it reports my city and state at the top of the screen without my giving it any additional information at all.

---

### Post by Dangertux on 2011-10-03
As it's been stated before it is possible but depends entirely on the ISP. Most will at least offer a general idea (within 30 miles or so), of where they are. 

In terms of a building or street address, not likely that's a pretty big privacy issue.

---

