---
title: "Transmission Speed"
date: 2010-08-12
forum: General Help
---

### Post by Dxlnc on 2010-08-12
Hello people!

I've just started using Linux, and not being too experienced with pretty much all of it, I of course need some assistance.

This is a matter of the Transmission program which comes along with the Ubuntu 10.04 version. I wonder if it is normal to only have between 60-150 KB/s speed download? I hear of people having a whopping 1 MB/s somewhere else but it seems that no matter what I do it stays pretty much the same. I've searched around for a while but it doesn't really seem to work for me. 

Anyone here who has experienced the same that might have the solution? Thank you:-)

---

### Post by earthpigg on 2010-08-12
1) make sure transmission's traffic isn't throttled by transmission itself. edit -> preferences -> uncheck 'limit download speed' or set it to a reasonable speed. make sure the little turtle in the lower left corner of transmision isn't active.

2) make sure you are using well-seeded torrents.

3) lastly, it could just be your ISP or where you live. when i lived in Finland, the standard broadband internet was fast as hell. downloads going over 1 meg per second was the norm - a 10 mb file would download in about 10 seconds. moving back in the states, ISP's have asinine tiered service and i never get above 250 KB/S because i don't want to pay for their 'elite' tier or whatever AT&T calls it.

when you look at your ISP's marketing brochures, be sure you divide the figure they provide by eight. they are telling you download speeds in megabits and kilobits per second, not the megabytes and kilobytes that people actually use. look for capital versus lower case letters. clever little devils, aren't they?

[Here is the handbook]("http://en.wikipedia.org/wiki/Data_rate_units") of how to mislead customers without lying to them.

---

### Post by Dxlnc on 2010-08-12
Dude... This advice helped me half way:-) I am now up to an average of 200-400 kb/s! But now here comes my still new beginner knowledge into the picture of torrents and the internet; what is ISP.? In a nutshell:-)

---

### Post by earthpigg on 2010-08-12
i edited my first post, above. be sure to re-read it.

your [ISP]("http://en.wikipedia.org/wiki/ISP") is who you pay for internet service.

Many places in the EU, the companies are not allowed to artifically cap your speeds. In the US, it is the norm. The people you see on ubuntuforums.org talking about downloading things at over 1 megabyte per second are either not in North America, or if they are American/Canadian... they are paying their ISP an exorbant monthly fee.

Alternatively, they are downloading at 1 mega***bit*** per second, which is the same as 125 kilo***bytes*** per second. if someone is just saying "x kb/s" then you dont know if they are saying "x kilobits per second" or "x kilobytes" per second. transmission uses kilobytes and megabytes, as do most people that aren't making marketing pamphlets. 

(Canada tends to follow America's lead in these things. The EU tends to follow the lead of the [Nordic Countries]("http://en.wikipedia.org/wiki/Nordic_country") in these things. Finland recently declared Broadband Internet to be a [fundamental legal right]("http://www.bbc.co.uk/news/10461048"), for example.)

---

### Post by Dxlnc on 2010-08-12
Hah, douchebags... I will check it out, but it seems pretty definite already that this is the case. Well, thanks a lot my friend! Now it is at least faster and you've saved me a lot of time. Once again thank you. Long live Linux:-)

- Dxlnc

---

