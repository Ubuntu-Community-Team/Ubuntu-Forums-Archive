---
title: "Ubuntu Based Server For All Ubuntu Heads !!"
date: 2006-02-15
forum: General Help
---

### Post by wannabelinuxconvert on 2006-02-15
Hi guys,

I'm in the process of setting up an internet and mail server for the sole purpose of offering it to the Ubuntu community.

I will initially allow 400 users with 250mb of space each, to be used however you wish, be it for mail (*unlimited mail accounts*), web pages, databases or a mixture of all three!

You will be able to register your own domain names, and redirect them to the server, or have your own subdomain at the one I just registered, **[http://www.ubuserver.co.uk](http://www.ubuserver.co.uk)** :-D 

The server will allow PHP5, HTML, Perl, Python and Ruby on Rails all to be served as well as Java web apps. And will house both MySQL and PostgreSQL databases. You will be able to access the mail via any client supporting IMAP (ie. Thunderbird) and I will also have a webmail package hosted aswell.

If there are any other apps or technologies people would like to see then post them here and I'll look into it, as I will try to support almost all requests that are feasible.

Now to the cost ... obviously I would like to offer this service for free, but with the electric charge, and the wish to keep expanding the server for more users, there will be a very small charge, of between £1 and £2 per month.

Remember, this is only going to be offered to the Ubuntu community, as I'd like to give something back to all those that have offered me help and guided me through my journey to become a devout Ubuntu user :mrgreen: 

The server is not operational yet, probably a couple of weeks off, but I would just like to get a feel of whether people would be up for using it, there thoughts and suggestions etc

Thanks for your time guys.

Mic

---

### Post by wannabelinuxconvert on 2006-02-15
Sorry for bumping up the line but I would really like to get some peoples thoughts on this !?

---

### Post by wannabelinuxconvert on 2006-02-15
Anyone got any thoughts at all !?

Would anyone even use the service !?

---

### Post by Garyu on 2006-02-15
Seems like a good idea to me, but I already have my own domain hosted at b-one.net for 12 SEK/month (less than 1£). With domain costs and everything I pay a little bit more than 300 SEK a year (20£ or so), and that is with my own domain name and lots of neat little services. So my opinion is that if you really want this to be a contribution to the community: lower the prices or set the server accounts up for free, as there are cheaper options out there already.

Good on you for making the effort and trying to contribute. :)

---

### Post by wannabelinuxconvert on 2006-02-15
Thanks Garyu for the response.

If the cost was £1 per month, then it would cost £12 per year, add in this domain registration through 1 and 1 for £4.98 for two years and you get a total cost over the two years of £28.98 or £14.49 per year ... Is this not good value for money !?

Also, you mention 'lots of neat little services' ... could you list a few for me, as this is the kind of feedback I'm after so that I can improve the service I want to offer.

Also please bear in mind that this will be a single server will all costs covered by me, hence the small charge. If I could I would defo offer it for free, but I think the missus would kill me when she saw the 'leccy bill :confused: 

Thanks

Mic

---

### Post by wannabelinuxconvert on 2006-02-16
Anyone else !?

---

### Post by Garyu on 2006-02-16
[QUOTE=wannabelinuxconvert]Also, you mention 'lots of neat little services' ... could you list a few for me, as this is the kind of feedback I'm after so that I can improve the service I want to offer.[/QUOTE]

I have statistics on visitors and their behaviour and OSs and browsers and whatever since I started my homepage in 2003. That's pretty neat.

PHP5 of course, and MySQL with phpmyadmin.

DNS forwarding, so I can setup for example "http://home.dan-erik.com/" to point to my own computer at home instead of my server host.

Simple tools for adminestering e-mail accounts and spam filters.

24 hour support, who for example helped me get the coppermine picture gallery to work.

Now, I am not a serious web designer, I only do crazy stuff for fun. But I still wouldn't consider any other alternative for my web hosting. You've got a good thing going, but you haven't won me over. And you wouldn't actually even if you would offer the service for free, since I want my own domain and I want to keep my statistics. Anyhow, good luck to you. =)

---

### Post by Revolution on 2006-02-16
After reading your initial post am I right in assuming you'll be running this server on a high capacity network (>10Mbps) with redundant network providers?
Will it be sited in a datacenter?
At least with a UPS?

I have hundreds of customers paying me $5 US a month each for what you are offering.

While I appreciate your gesture to the Ubuntu community, I wouldnt host in anything less than a datacenter - and they cost real money.

Cheers

---

### Post by wannabelinuxconvert on 2006-02-16
So how much did it set you back then to setup hosting in your datacentre, on a high capacity network with redundant network providers, to be able to host 100's of customers !?

I am currently wanting to setup using a Dell PowerEdge 2800.

---

### Post by Revolution on 2006-02-16
[QUOTE=wannabelinuxconvert]So how much did it set you back then to setup hosting in your datacentre, on a high capacity network with redundant network providers, to be able to host 100's of customers !?

I am currently wanting to setup using a Dell PowerEdge 2800.[/QUOTE]
There are several ways to run servers.
We originally leased servers until we were established then started to move to Colocation.

**Datacenter Colocation**
1) Datacenters will 'usually' only take Rack servers. Space is at a premium.
1a ) Rackservers start at around $500 US up to $3K for a nice Xeon based machine.
2) A Rackspace is priced per 'U' - A one U rack slot works out around $50 US per month. Not sure about Datacenter pricing in the UK. Maybe similar.
3) Datacenters provide (for that rackspace fee) uninteruptible power. Usually backed up with a deisel generator.
4) Network fees have two kinds. Speed rated or Volume rated. If you are hosting many sites on several servers then speed rated data is preferable. The cheapest I've seen is around $100 US per Megabit/second per month.
Volume rated is cheaper and varies greatly depending on who is offering it.

Setting up your own datacenter is of course out of the question, at least until you learn something about server administration.

**Leased Servers**
You could lease a server from one of hundreds of different providers.
These can be anywhere from $40 US per month for an old P4/Athlon 1.7Ghz machine with 256Mb ram and an 80Gb drive with CPanel and maybe 500GB data up to $350 US per month for a Dual Xeon 3Ghz with a few SCSI drives and 2GB ram with 2TB data.

Good luck

PM me if you want any more information.

---

