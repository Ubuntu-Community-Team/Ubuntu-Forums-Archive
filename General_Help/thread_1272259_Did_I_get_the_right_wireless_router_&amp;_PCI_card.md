---
title: "Did I get the right wireless router &amp; PCI card?"
date: 2009-09-21
forum: General Help
---

### Post by PsychedelicWonders on 2009-09-21
I bought a Netgear wireless router WGR614NA & PCI card WN311B-100NAS, but I'm not sure if it was the right choice.  

What do you guys think?  Did I get the right one or should I take it back and get another one?  

Is it fast enough?  I dont understand anything about wireless cards & what to look for.

I'm going to have to take back the PCI card & get the USB, I have 2 PCI slots that will accept this card but one is being blocked by one of the fans of my video card.

Is there any issues with running wireless via the USB?  Does it have this big giant transmitter like the PCI card does?

---

### Post by PsychedelicWonders on 2009-09-22
They did have a Belkin there too, or should I stick with the netgear?

---

### Post by swoody on 2009-09-22
> **PsychedelicWonders said:**
> I bought a Netgear wireless router WGR614NA & PCI card WN311B-100NAS, but I'm not sure if it was the right choice... 
From what I can tell, your router only supports WEP encryption. This is much less secure than WPA or WPA2 encryption, but it will be better than nothing. If you do return/exchange it, I would suggest going with one that offers WPA2 encryption, as it is the strongest encryption on the market right now. The router works for speeds up to 54mb/s. This should be more than adequate for nearly all users' needs. It supports 802.11 b/g which is good. There is a faster version out now, which is 802.11 n. This does increase the speed on your network, but unless you transfer *large* amounts of info between computers on your network, I don't think you'll see much/any gain from it. It is usually quite a bit more expensive, too.

Your PCI adapter supports 802.11 n/b/g and WPA2 encryption, so it appears to be a good choice, but again may be more expensive than you really need, since your router won't broadcast WPA2 or 802.11 n. You said you will be returning this adapter? What is the model of the USB device you will be replacing it with?

Overall, I think whether or not you keep your router is completely up to you. If you live in a rural area, where you're not going to have to worry about people trying to crack your WEP encryption and access your network, WEP encryption should be fine for you. However, if you're in a busier urban environment, with lots of other wireless networks around that have WPA or WPA2 encryption, I would highly recommend going with a router that supports WPA2 encryption. Unless someone really doesn't like you, and targets you specifically, crackers will typically take advantage of the 'easiest targets'. Those are usually people with unencrypted or WEP encrypted networks. So you don't need to have the most elaborate security in the nation, but you just have to be sure you're not be the 'easiest target' in your area.

> Is it fast enough?  I dont understand anything about wireless cards & what to look for.
Typically at speeds of up to 54Mb/s the 802.11 g standard will be more than enough for *most* users' needs. I would make sure both router and PCI adapter support it, and not pay the extra to go for the faster 802.11 n, unless you really need it. Again, unless you transfer LARGE amounts of data between different computers on the network, 802.11 g should be all you need.


> I'm going to have to take back the PCI card & get the UhSB, I have 2 PCI slots that will accept this card but one is being blocked by one of the fans of my video card.

Is there any issues with running wireless via the USB?  Does it have this big giant transmitter like the PCI card does?

I did notice in the pictures online that your PCI adapter comes with a large external antenna. This is pretty rare to find even on PCI adapters, and I can understand that it is probably a bit cumbersome and awkward. Typically, PCI adapters will come with one or more small antennas that mount directly on the PCI card itself, but which are outside of your computer case. These are very small - usually 4-6" long - and are completely hidden behind your case. Since you said that you'll be trading in your PCI adapter for a USB card, I won't delve into that too much.

USB adapters are typically made to be small and sleek, as they are not only geared towards desktop users, but laptop users as well. They are normally small, and discrete, and appear to be no larger than a USB thumb drive. The antenna is most often internal, which helps prevent damage, and keeps the adapter's measurements minimal. Some higher-powered USB adapters, however can include an externally mounted antenna. This can either be in the case of something similar to your PCI adapter's large antenna, or just a small plastic antenna (again 4-6" long and looks like a pen) that attaches to the USB device itself. To determine what kind of antenna your USB adapter uses, you would just have to look at pictures or reviews on your specific model online.

Again, I'd leave it up to you to choose whether you'd want to trade in your router, but if you did, I would highly suggest one that supports 802.11 g, and WPA2 encryption. As far as your USB adapter goes, I would also recommend that it supports 802.11 g, and has WPA2 compatibility. I would avoid paying too much for the newer 802.11 n at this time, unless you need faster speeds between networked computers, and save money in the process. When it comes to brands or specific models, they are typically all the same. I would make sure whatever adapter you choose is supported in Linux, and would recommend buying the USB adapter and router from the same manufacturer. Some people have had issues mixing and matching manufacturers, while many people have not. Again this would be something I would just play it safe with, and be able to avoid the possibility of any issues from arising in the future.

---

### Post by P4man on 2009-09-22
how far will be the AP be from the computer? USB dongles are handy, but their range very much sucks compared to PCI cards with an antenna (even a small one, most have like 10cm antenna). The difference can be as much as 2x the range.

The same applies to 802.11g versus the newer and faster 802.11n. Not only is it faster, its range is also very much better. Might not be an issue if the access point and PC are in adjacent rooms, but if they are far apart, it could be money well spent to have an access point and wireless card/dongle that support the newer n standard

---

### Post by swoody on 2009-09-22
Yes, thank you for mentioning range, P4man. You are correct in your statements - I have no issue there. However, if range were an issue, I would recommend using a stronger antenna on the router to acquire more range. While the price difference for upgrading from an 802.11g to an 802.11 n router and adapter may cost upwards of $100, a simple higher dB antenna on the router could increase range dramatically for $5-$15. I would still recommend going with 802.11g, and if range is an issue, purchasing an antenna with higher gain before necessitating going with n.

But that is just my $.02 :)

Edit: Here is an example of a 9dBi antenna for $8 USD after shipping. From the specs, you can see that at 2.4GHz it has a range of up to 1148ft (500M). If you are more than 500 meters from your wireless access point, I think you may have other issues to worry about than just range ;)

[http://www.eforcity.com/pothpcixant2.html?efprcggbadtf090605=pothpcixant2](http://www.eforcity.com/pothpcixant2.html?efprcggbadtf090605=pothpcixant2)

---

### Post by PsychedelicWonders on 2009-09-22
When you guys say 802.11 N is only for LARGE files between computers, how large is large? 

I checked out the N router by Netgear & it was like $30 more.  

I also noticed with the N it has 108 mb/s vs 54, thats a considerable difference.  And obviously the WPA2 security.

Are there N dongles? 

I have 2 regular PCI slots that are accessable, are there any wireless cards that will fit in them?  Or is a dongle a better idea?

---

### Post by FunkyRes on 2009-09-22
> **PsychedelicWonders said:**
> When you guys say 802.11 N is only for LARGE files between computers, how large is large? 

I checked out the N router by Netgear & it was like $30 more.  

I also noticed with the N it has 108 mb/s vs 54, thats a considerable difference.  And obviously the WPA2 security.

Are there N dongles? 

I have 2 regular PCI slots that are accessable, are there any wireless cards that will fit in them?  Or is a dongle a better idea?

802.11n is not only for large files. However, 802.11g is fast enough that it isn't the *internet access* bottleneck on most home networks. Large files downloaded from the web are more likely to be restricted by your connection than 802.11g.

Home Internet connection speeds keep improving, however, and I would probably go 802.11n if I was setting up a network now.

As far as network cards go, if you have PCI slot that's the way to go. Many (most?) PCI wifi cards are really just CardBus cards on a PCI adapter but they are in my experience better than USB devices.

Which card to get, I can't help you. I always go with Atheros based cards because my wireless network is 802.11g, and madwifi is a really good driver. What is good for 802.11n I don't know.

---

### Post by swoody on 2009-09-22
> **PsychedelicWonders said:**
> When you guys say 802.11 N is only for LARGE files between computers, how large is large? 

I also noticed with the N it has 108 mb/s vs 54, thats a considerable difference.  And obviously the WPA2 security.

I have 2 regular PCI slots that are accessable, are there any wireless cards that will fit in them?  Or is a dongle a better idea?


Sorry, let me clarify my previous post. The faster speeds associated with n is helpful if your internet and home computers can take advantage of the extra speed. I doubt your internet connection is faster than 54Mb/s, so going with the 'n' router won't improve your download/internet speeds at all. Your internet can run at full speed, and the g router will be able to handle it fine.

On the other hand, your router is also the gateway between multiple computers when you share files across your network. The faster connection of the n router  will allow you to transfer/share files across your network much faster - 108MB/s compared to the 54MB/s that they would transfer across a g network. What I was trying to get across, was that if you don't transfer data between multiple computers, or if you don't do it often, or if they are small files you may not want to bother paying the extra money for an n router and adapter. If you have a file server, or if you regularly transfer data/files/etc. between computers on your network you may be interested in going with the faster n router and adapter.

Does this clear things up? I hope I'm able to get my point across clearly :)

> I checked out the N router by Netgear & it was like $30 more.
Are there N dongles?

Yes, the 802.11n routers and adapters will cost more than 802.11g hardware. You also have to take into account, that you will need to purchase a 802.11n compatible adapter for your computer, which will also cost more than a similar 802.11g version. This is why I recommend going with 802.11g unless you have a need to transfer large amounts of info between computers on your home network. Also yes, there are n dongles available.

---

### Post by PsychedelicWonders on 2009-09-22
Yeah you guys helped out thanks.

Honestly I'm probably going to just go with the N technology.  It doesnt seem to be that much more expensive & will bring benefits at some point for me in the future.

I would prefer to hook it up via a PCI card, but the only available slot I have left is just a plain PCI, not PCI x1 which is what this current card requires. (Here is the mobo if you want to see it: [http://www.newegg.com/Product/Product.aspx?Item=N82E16813131277](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131277) )

So are there any N PCI cards that will plug into a plain PCI port?

If not, I'll be forced to get an N dongle.  

So as long as the stats are there, it doesnt matter the brand?  Because Belkin seemed to be cheaper than Netgear or Linksys.  I just dont remember the prices for their N system.  The N router was only $30 more with the Netgear products.

I think I did see some G routers that offer 108 mb/s, but I'm still gonna go with N I think.

---

### Post by swoody on 2009-09-22
> **PsychedelicWonders said:**
> Yeah you guys helped out thanks.

Honestly I'm probably going to just go with the N technology.  It doesnt seem to be that much more expensive & will bring benefits at some point for me in the future.

That's good. It's never a bad thing to 'future-proof' and get your money's worth out of your purchases.

> So as long as the stats are there, it doesnt matter the brand?  Because Belkin seemed to be cheaper than Netgear or Linksys.

For the most part - yes. The 802.11b/g/n standards are just that - internationally accepted standards for wireless networks. They are all producing the same thing. It's just as if you switched your internet service to another ISP, but kept the same internet speed. You're still getting the same thing, but it may cost you different prices from different companies. The build quality and reliability are the only things that should come into play at this point. As long as you stay away from the Walmart 'blue light special' or a company you have never heard of, you should be fine as far as quality goes. Most people have preferences for one manufacturer or another, but these are usually just biases, and are rarely based on any real facts. The most important thing to keep in mind is whether or not it's compatible with Linux. Before you buy anything I would do some quick searches on the Linux Hardware Compatibility List and the Ubuntu Hardware Compatibility list, as well as read as many Linux related reviews you can find for each adapter you're considering purchasing.

[http://www.ubuntuhcl.org/](http://www.ubuntuhcl.org/)
[http://www.linux-drivers.org/](http://www.linux-drivers.org/)

> So are there any N PCI cards that will plug into a plain PCI port?

You should be able to find some out there. You may want to try searching on NewEgg even if you're not from the US, as they have lots of photos and details about every product. It should be very easy to find a few that are exactly what you're looking for :)

---

### Post by PsychedelicWonders on 2009-09-22
I always have a hard time determining what hardware will work with linux.  Theres just so much to know and I'm not at that level yet.

Is it safe to say that Netgear is a pretty compatible hardware company for linux?  Or should I look at the LinkSys stuff?

I see Newegg has a bunch of wireless networking stuff via bluetooth.  Would I be better off getting bluetooth?

---

### Post by PsychedelicWonders on 2009-09-22
Also, all of these PCI cards still seem to big to fit into the plain PCI slot I have available.  It looks like it would fit more into the PCI 1x.

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2050410031+1133010139&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=31&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2050410031+1133010139&QksAutoSuggestion=&ShowDeactivatedMark=False&Configurator=&Subcategory=31&description=&Ntk=&CFG=&SpeTabStoreType=&srchInDesc=)

Am I just in the wrong section?

---

### Post by lisati on 2009-09-22
> **swoody said:**
> From what I can tell, your router only supports WEP encryption. This is much less secure than WPA or WPA2 encryption, but it will be better than nothing.

I can't speak for the "NA" variant but the WGR614v7 I have definitely supports WPA2

---

### Post by PsychedelicWonders on 2009-09-23
Bump

---

### Post by swoody on 2009-09-24
> **PsychedelicWonders said:**
> I always have a hard time determining what hardware will work with linux.  Theres just so much to know and I'm not at that level yet.

Is it safe to say that Netgear is a pretty compatible hardware company for linux?  Or should I look at the LinkSys stuff?

I see Newegg has a bunch of wireless networking stuff via bluetooth.  Would I be better off getting bluetooth?

I wouldn't recommend Bluetooth. While it seems to work well to connect devices, I don't think it would be the best way to go with networking. I would recommend a PCI card first, and if not, then a USB adapter with an external antenna for better range.

Again, I'm not super-familiar with what works or not in Linux, so I would highly recommend doing a quick search on the Linux HCL, and Ubuntu HCL I posted earlier. This will be the quickest way to get feedback from people who have tried the specific device you are considering.

> **PsychedelicWonders said:**
> Also, all of these PCI cards still seem to big to fit into the plain PCI slot I have available.  It looks like it would fit more into the PCI 1x.

Looking around NewEgg, it does seem that they are lacking what you're looking for in a PCI card. I'm not sure where you would be able to find one, but I know they've been slowly phasing out the original, small PCI standard in favor of others, so it may become increasingly difficult to find.

> **lisati said:**
> I can't speak for the "NA" variant but the WGR614v7 I have definitely supports WPA2

Well, I am only going off of what I could find about this model online:
[http://www.superwarehouse.com/Netgear_Cable_DSL_54_Mbps_Wireless_Router/WGR614NA/ps/247026](http://www.superwarehouse.com/Netgear_Cable_DSL_54_Mbps_Wireless_Router/WGR614NA/ps/247026)

If that description is wrong, and it does have WPA2, then that would be a horse of a different color :)

---

### Post by PsychedelicWonders on 2009-09-24
Ok I'll try and check those sites and see what I come up with.

I'm going to end up with an N network router & a USB N dongle.  That seems like its going to work the best for my setup.

Thanks guys.

---

### Post by PsychedelicWonders on 2009-09-24
Ok I did some more checking at best buy today to see what I could switch to.

I would honestly prefer to go with Netgear because it is cheaper in price, yet still high quality like Linksys. 

Netgear had 3 different N routers:

The first one is my top choice based on specs & price so far.

WNR2000
79.99
WPA2
300 mbps
USB to match it: WN111 - 69.99

"GIGABIT" MODEL
WNR3500
WPA2, PSK
But this one doesnt list the mbps - why?
119.99

WNPR3300
99.99
Dual Band
WPA2
300 mbps
USB that links with it - 79.99

Look at this one, it says Open Source Linux wireless router - so does that mean the other Netgear routers wont work on Ubuntu & I would need to get this one? Its not N though...

[http://www.newegg.com/Product/Produc...82E16833122223](http://www.newegg.com/Product/Produc...82E16833122223)

Linksys:

WRT310N
99.99
Doesnt have WPA2
The usb that matches up with this is 84.99

So my question is, how important is WPA2 that I should get it?

When it comes to Netgear, do I need/want the Gigabit model? And is the dual band Netgear worth it? What are the real benefits?

Now according to this link: the Netgear USB dongle I want to use WN111 is supported? It says this:

Supported in installed system? No

Works "Out of the box": Follow the sticky on Ubuntu on how to setup ndiswrapper.

So does that mean the Netgear dongle I want will work with a little tweaking? I would assume that would mean the router would work also right?

---

### Post by akakingess on 2009-09-24
> **PsychedelicWonders said:**
> 
"GIGABIT" MODEL
WNR3500
WPA2, PSK
But this one doesnt list the mbps - why?
119.99


I can answer this one at least, the "GIGABIT"  is actually the speed, it means up to 1,000 MB/s, so it is by far and away the fastest choice of the list I believe, so, 1 question down, and just a few more to go, and I will see if I can find those answers for you.

---

### Post by akakingess on 2009-09-24
As far as the routers working with linux, that should not factor into your decision at all, the router is just the central connection point for all your computers, the OS you are using should have nothing to do with your router strictly from a connection standpoint. Any OS should be able to connect as long as they have the right adapter installed.

Edit: If I weren't at work right now, I would find the answers to the rest for you, but good luck, as I am sure there will be someone that will be willing to help out soon.

---

### Post by PsychedelicWonders on 2009-09-24
> **akakingess said:**
> I can answer this one at least, the "GIGABIT"  is actually the speed, it means up to 1,000 MB/s, so it is by far and away the fastest choice of the list I believe, so, 1 question down, and just a few more to go, and I will see if I can find those answers for you.

Thanks man.

Does that reference internet/download speed?  Or network speed?

Because right now my comp only shows im getting 48-54 mbps internet/download speed.

---

### Post by akakingess on 2009-09-25
when you get to those kinds of speed (i.e. 'gigabit'), the bottleneck is going to be your internet connection.  If you had a gigabit router and gigabit adapters on 2 computers off of that router, than transferring files back and forth would go much faster, although you would only really see a difference if you were transferring LARGE files, maybe over 1 GB or larger, otherwise you wouldn't see the advantage.  It is nice to have, and if you transfer a lot over your network it may be nice, but it is probably (almost definitely) overkill at this point.

---

### Post by PsychedelicWonders on 2009-09-25
yeah probably overkill.

The 1st one is still holding strong as far as price & specs.

But what about the dual band?  You think that is needed?

---

### Post by PsychedelicWonders on 2009-09-25
I would prefer to go with Netgear then since its cheaper than Linksys, so if it will work with Ubuntu then its a for sure.  

I'll end up having to go with the N router since I want WPA2 & more than 54mbps & it seems in order to get both they make you upgrade to the N.

I have read where the [Netgear WNR2000]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833122235") router that I want to upgrade to has issues with VOIP - does anyone know why this would be?  Was it just uswer error?  

VoIP is very important to me.

---

### Post by swoody on 2009-09-25
> **PsychedelicWonders said:**
> Look at this one, it says Open Source Linux wireless router - so does that mean the other Netgear routers wont work on Ubuntu & I would need to get this one?
Well, that link doesn't work, so I'm going to go out on a limb here, and make an assumption. Chances are, that the 'Open Source Linux' marking just means that the router itself uses open source, linux-based firmware. I know there was a very popular WRT54gL router that had the 'L' added onto the end of it's name to denote that it used linux-based firmware. To be honest, as a typical user, this will really not play into your day-to-day usage in any way.

> So my question is, how important is WPA2 that I should get it?
Again, if I were upgrading my network right now, I would be sure to have everything using WPA2 encryption. It is the strongest encryption on the market, and would provide a much more secure network than WPA or WEP encryption would.

> Now according to this link: the Netgear USB dongle I want to use WN111 is supported? It says this:
Supported in installed system? No
Works "Out of the box": Follow the sticky on Ubuntu on how to setup ndiswrapper.

So does that mean the Netgear dongle I want will work with a little tweaking? I would assume that would mean the router would work also right?
Yes, what I think that is trying to say, is that after installing Ubuntu, the wireless card won't work out of the box, but with 'ndiswrapper' you can get it to work. This is not hard to setup, and is what I have to do for the adapter in my laptop. For some more info check out the wiki page:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Again, you shouldn't come across any issues with the router. Routers just broadcast/receive a signal. It's your computer's job (with the help of the wireless adapter) to interpret that signal, make use of it, and send back signals that the router will understand. The only part you have to make sure is compatible is the adapter that will be connected to your computer.

> But what about the dual band?  You think that is needed?
If you are referring to the 802.11g/n dual-band then that is just a compatibility thing. It will be able to work with wireless 'n' or 'g' adapters. If your computers are only going to be using the 'n' adapters, and you're not going to be having people drop by all the time and want to connect to your network (most common adapters today are still b/g) then you shouldn't have much of an issue going with an 'n' router, and not needing a dual-band g/n router. If that makes sense? 

> I have read where the router that I want to upgrade to has issues with VOIP - does anyone know why this would be?  Was it just user error?
VoIP is very important to me.
Well, I have heard of people having issues with routers who use VOIP, but it's very hard to tell which ones would cause issue. The best way to find out would be to call your VOIP provider, or find a good voip forum, and ask about that specific model. I'm sure you can find someone who is either using it without a problem, or who tried it, and can verify that it's not compatible with VOIP.

---

### Post by PsychedelicWonders on 2009-09-25
> **swoody said:**
> 
If you are referring to the 802.11g/n dual-band then that is just a compatibility thing. It will be able to work with wireless 'n' or 'g' adapters. If your computers are only going to be using the 'n' adapters, and you're not going to be having people drop by all the time and want to connect to your network (most common adapters today are still b/g) then you shouldn't have much of an issue going with an 'n' router, and not needing a dual-band g/n router. If that makes sense? 

No the dual band router actually refers to the 2.4 ghz & the new 5 ghz frequencies.  They are saying the 2.4 is too crowded with too many devices & the 5 ghz is going to be taking over?


> Well, I have heard of people having issues with routers who use VOIP, but it's very hard to tell which ones would cause issue. The best way to find out would be to call your VOIP provider, or find a good voip forum, and ask about that specific model. I'm sure you can find someone who is either using it without a problem, or who tried it, and can verify that it's not compatible with VOIP.

You know any really good VoIP forums?

---

### Post by swoody on 2009-09-25
> **PsychedelicWonders said:**
> No the dual band router actually refers to the 2.4 ghz & the new 5 ghz frequencies.  They are saying the 2.4 is too crowded with too many devices & the 5 ghz is going to be taking over?

Ah, ok. Well that makes sense. At this point, I probably wouldn't go with it, but again, this is completely up to you. If you like somewhere where you only pick up a couple of other people's wireless networks, I wouldn't worry too much about over-crowding, and having to use the 5GHz. If you're in the heart of a busy urban area, and you can see many, many networks around you, I would consider it. This is the first time that I've heard of this, so I can't really give you too much info on it.


> You know any really good VoIP forums?

What provider do you have? I would recommend looking up their website or try Googling "Provider forum". I know my voip provider (VOIP.com) has their own online forums, so your provider's website would be the first place I'd tell you to look. If you can't find any that are specifically geared towards your provider, you could try:
[VoipForums.com]("http://www.voipforums.com/")
[VoIP User]("http://www.voipuser.org/forum_index.html")
[VonageForum.com]("http://www.vonage-forum.com/forums.html")

I haven't used any of these, so I can't remark towards one that I would recommend, but give them a shot, and see what turns up :)

---

