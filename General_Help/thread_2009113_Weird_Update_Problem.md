---
title: "Weird Update Problem"
date: 2012-06-24
forum: General Help
---

### Post by nonedrinkwater on 2012-06-24
W:Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/sevenmachines/flash/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I'm getting these errors on update manager, how do I fix this?

---

### Post by Bucky Ball on 2012-06-24
1/ Are you really using 8.o4 LTS? It is no longer supported.
2/ Those repositories (sevenmachin ...) are either down or dead. You might try removing or unticking them in Software Sources.

---

### Post by blackflame2996 on 2012-06-24
Use a different mirror for these sources. this is a common connection problem. Here is how to switch mirrors:
[http://www.ubuntugeek.com/how-to-select-fastest-mirror-in-ubuntu.html](http://www.ubuntugeek.com/how-to-select-fastest-mirror-in-ubuntu.html)

---

### Post by Bucky Ball on 2012-06-24
> **blackflame2996 said:**
> Use a different mirror for these sources. this is a common connection problem. Here is how to switch mirrors:
[http://www.ubuntugeek.com/how-to-select-fastest-mirror-in-ubuntu.html](http://www.ubuntugeek.com/how-to-select-fastest-mirror-in-ubuntu.html)

Yes and no. It is only these sources that are problematic so the mirror works fine for all others. Your link shows how to change the mirror for all updates. Everything else is fine so not necessary. I would say server that is hosting repo may have issues which may be fixed before too long.

@OP: Is this the first time this repository has given an error? Have you only just added it and this is the first update since adding?

---

### Post by nonedrinkwater on 2012-06-24
> **Bucky Ball said:**
> Yes and no. It is only these sources that are problematic so the mirror works fine for all others. Your link shows how to change the mirror for all updates. Everything else is fine so not necessary. I would say server that is hosting repo may have issues which may be fixed before too long.

@OP: Is this the first time this repository has given an error? Have you only just added it and this is the first update since adding?



i have unticked them and now everything is fine, the select best server said that i should use the eu.kernel.org in the netherlands for some reason, either way, i'm only having issues with the 64bit version, and not on the 32 bit.... weird no?

---

### Post by stinkeye on 2012-06-24
Outdated ppa for installing flash that no longer exists and not needed.

---

### Post by Bucky Ball on 2012-06-24
> **nonedrinkwater said:**
> ... the select best server said that i should use the eu.kernel.org in the netherlands for some reason, either way, i'm only having issues with the 64bit version, and not on the 32 bit.... weird no?

Check with your ISP and see if they have an unmetered mirror for Ubuntu. Then you can use that for your server (should be there) and you won't get metered for Ubuntu content. ISPs usually have a bunch of unmetered content as part of the deal. 

If your problem is solved please mark it that way to help others. ;)

PS: As for having trouble with 64bit not 32; you might be attempting to use the 32bit repo in 64bit and, though this should theoretically be okay, there could also theoretically be some glitch ...

---

### Post by stinkeye on 2012-06-24
> **Bucky Ball said:**
> Check with your ISP and see if they have an unmetered mirror for Ubuntu. Then you can use that for your server (should be there) and you won't get metered for Ubuntu content. ISPs usually have a bunch of unmetered content as part of the deal. 

If your problem is solved please mark it that way to help others. ;)
That's a good tip.
I found my isp had an unmetered mirror for Ubuntu.

---

### Post by Bucky Ball on 2012-06-24
> **stinkeye said:**
> That's a good tip.
I found my isp had an unmetered mirror for Ubuntu.

Yep, and me ... ;)

---

### Post by nonedrinkwater on 2012-06-25
> **stinkeye said:**
> That's a good tip.
I found my isp had an unmetered mirror for Ubuntu.


what does unmetered mean?

---

### Post by stinkeye on 2012-06-25
> **nonedrinkwater said:**
> what does unmetered mean?
Most ISP's have certain websites where the downloads don't count
towards your download quota.
Here in Australia I have a 25Gb download limit on my plan, before it is shaped.
My ISP has an Ubuntu mirror where all my Ubuntu updates and installations are 
not included in my quota.
Has most popular linux distros.

---

### Post by Bucky Ball on 2012-06-25
> **stinkeye said:**
> Most ISP's have certain websites where the downloads don't count
towards your download quota.
Here in Australia I have a 25Gb download limit on my plan, before it is shaped.
My ISP has an Ubuntu mirror where all my Ubuntu updates and installations are 
not included in my quota.
Has most popular linux distros.

Same. I am also in Aus. (I'm off to never never land but I might already be there!) ;)

---

### Post by nonedrinkwater on 2012-06-27
> **stinkeye said:**
> Most ISP's have certain websites where the downloads don't count
towards your download quota.
Here in Australia I have a 25Gb download limit on my plan, before it is shaped.
My ISP has an Ubuntu mirror where all my Ubuntu updates and installations are 
not included in my quota.
Has most popular linux distros.

i dont think the US has that same design, i'm on usenet a lot and i download about 60 to 100 gigs a month, sometimes terabytes depending on what im looking for. 

im shocked to see oz give users a limit on DL.

---

### Post by nonedrinkwater on 2012-06-28
> **stinkeye said:**
> Outdated ppa for installing flash that no longer exists and not needed.

How do you know that? 

And how do you know so much about linux, i want to eat your brains.

---

### Post by Bucky Ball on 2012-06-28
> **nonedrinkwater said:**
> im shocked to see oz give users a limit on DL.

You choose a plan and that has a quota; 5Gb, 25Gb, 50Gb, whatever. This is then 'shaped' to a slower speed (generally 64kbps) when the quota is reached. You pay accordingly. You can get unlimited plans but very expensive. Yes, we lag behind the US on account quotas, not sure about speeds.

The National Broadband Network is the big thing here. Being rolled out at the moment and speeds expected to be 100Mbps, when the cable eventually arrives in the street, which could be a decade away or when these speeds are obsolete and old hat.

I've got my fingers crossed for sooner. The NBN is not expected to change pricing, though. ;)

PS: We are talking about your ISP provider having unmetered content here, not Usenet itself. Who do you actually have your internet access provided by? Who do you pay for the cable, satellite, phone line to be connected and operational?

They should have a list of unmetered sites/mirrors.  :)

---

### Post by nonedrinkwater on 2012-06-30
> **Bucky Ball said:**
> You choose a plan and that has a quota; 5Gb, 25Gb, 50Gb, whatever. This is then 'shaped' to a slower speed (generally 64kbps) when the quota is reached. You pay accordingly. You can get unlimited plans but very expensive. Yes, we lag behind the US on account quotas, not sure about speeds.

The National Broadband Network is the big thing here. Being rolled out at the moment and speeds expected to be 100Mbps, when the cable eventually arrives in the street, which could be a decade away or when these speeds are obsolete and old hat.

I've got my fingers crossed for sooner. The NBN is not expected to change pricing, though. ;)

PS: We are talking about your ISP provider having unmetered content here, not Usenet itself. Who do you actually have your internet access provided by? Who do you pay for the cable, satellite, phone line to be connected and operational?

They should have a list of unmetered sites/mirrors.  :)

what good is speed if there is a limit? 

i pay time warner $30 USD a month for tested speeds of 10 to 20Mbps depending on time of day, for usenet, i use verizon, and pay for a business static IP account on their fiber optic service $120 USD a month and I get a constant 50Mbps speed. it's fast. I Download stuff at 4MB/sec, the fastest home internet that i have ever seen. 

now.... at work we have multiple ATM lines, which run at 155Mbps, and it's supppperrrrrr fast. I host dbase servers off my work desktop for personal use, web-server for a personal portfolio, and a number of game servers and the admin at work can't even tell that there is lag. 

my first connection, when i was in 7th grade, was a 9.6 Kbps modem. lol. my my... how times have changed...

---

