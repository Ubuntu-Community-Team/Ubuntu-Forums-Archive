---
title: "laptop struggling with wireless connections"
date: 2010-07-19
forum: General Help
---

### Post by surrealillusions on 2010-07-19
Hi all,

Took my laptop with me on a trip away and it didnt connect to the internet.

- Its running Ubuntu 10.04.
- It connects to my wireless here at home, but didn't connect properly to the internet in the b'n'b i stayed at.
- I have connected to that wireless before, but using windows, the last time i stayed there and the owners say they haven't had any problems with others using it.
- Although it was a weak signal, even moving the laptop right next to the router didnt help. The signal was stronger but no web pages loading, or any programs relying on an internet connection didnt work properly or at all.
- I took a seperate wireless USB thingy with me, but that wasn't recognised by Linux, its a Belkin USB adaptor, with N strength.

What could cause this? How come my laptop was the odd one out? How come it didnt recognise the Belkin USB adapter?

Any answers or help would be appreciated.

:)

---

### Post by dcollier on 2010-07-19
Don't take this the wrong way, but was the wireless adapter turned on? The Belkin usb adapter that you are trying to use may need the proper drivers installed.  Check for restricted drivers.  Where u able to ping to an outside location while connected to the access point? U say that you were close to the router, where u close enough to connect via Ethernet?

---

### Post by onilink422 on 2010-07-19
What I did was attach the computer to an Ethernet cable to install my wireless drivers and then i was able to use wireless Internet. Sorry if this has nothing to do with your post, but I do think this may help.

---

### Post by surrealillusions on 2010-07-19
> **dcollier said:**
> Don't take this the wrong way, but was the wireless adapter turned on? The Belkin usb adapter that you are trying to use may need the proper drivers installed.  Check for restricted drivers.  Where u able to ping to an outside location while connected to the access point? U say that you were close to the router, where u close enough to connect via Ethernet?

The first thing I checked was that the wireless was turned on, on the front of the laptop :)
Didnt ping any location, how do you do that (for future reference) ?
Probably was close to connect via ethernet but no cables to hand to try it, didnt really think of that either.

Although it did connect to the wireless network, thats the weird thing, but yet anything internet related didnt.

> **onilink422 said:**
> What I did was attach the computer to an Ethernet cable to install my wireless drivers and then i was able to use wireless Internet. Sorry if this has nothing to do with your post, but I do think this may help.

Might be worth installing the Belkin drivers though while Im here at home, ready for next time.

---

### Post by valbaca on 2010-07-19
To ping, put the following in a terminal
```
ping [http://www.google.com](http://www.google.com)
```
or whatever website you prefer.
```
man ping
```
will give more info
 
In my experience, lots of places that provide "free" wireless internet have some sort of login home page that is supposed to come up in your browser the first time you try to go to a site on their network. Unfortunately, this doesn't always work with linux. (My experience has been at a Hastings store nearby.)
 
I was able to get around this problem by putting 192.168.0.1 as the address in your browser. This address is usually the router's address (and on some networks you can begin changing settings here ;) ) but for these "free" wireless places this is where their login-homepage is. If that doesn't work you can also try 192.168.0.2, 192.168.2.1, etc. etc.

---

### Post by surrealillusions on 2010-07-19
Cool, thanks.

Will keep this info handy for next time.

:)

---

