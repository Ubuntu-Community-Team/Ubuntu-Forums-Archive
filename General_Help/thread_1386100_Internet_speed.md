---
title: "Internet speed"
date: 2010-01-20
forum: General Help
---

### Post by sean_M on 2010-01-20
Hello I have a question dealing with the speed of my internet. First let me say that I'm using a netgear wn111v2, to pull in a wireless signal. On ubuntu it says I'm getting about (79%) on the connection. On Windows it say I'm getting about (40%). But when downloading from the same site on both Ubuntu, and Windows. Windows is downloading the files quicker. I'm a little confused as to why, when Ubuntu is saying it has a better signal, then Windows gets?

---

### Post by Grenage on 2010-01-20
Signal strength doesn't generally have a lot to do with transfer speed (as long as you are getting one).  What kind of speed difference is it?

---

### Post by n0dix on 2010-01-20
It's a torrent download or a direct one?

---

### Post by wojox on 2010-01-20
What happens if you connect via Ethernet cable? It might be the driver. Try disabling IPv6

[http://wojox.homelinux.net/?p=4](http://wojox.homelinux.net/?p=4)

---

### Post by sean_M on 2010-01-20
> **n0dix said:**
> It's a torrent download or a direct one?

direct download I'm able to download 13- 40MB files in under 7 mins windows, on ubuntu it's taking 15 mins just to download one of the 40mb files. But I have tested on torrents to and windows is able to pull in 1mb/s as to 50kb/s on the same file.


Also I'm unable to test on Ethernet cable right now. I share the internet with my friend next door. So I would have to wait for him to be home to see.

---

### Post by n0dix on 2010-01-20
What about your wireless card??

---

### Post by sean_M on 2010-01-20
> **n0dix said:**
> What about your wireless card??

That is what I have been talking about :P

---

### Post by Grenage on 2010-01-20
> **sean_M said:**
> That is what I have been talking about :P

He wants to know what card you have ;)

---

### Post by n0dix on 2010-01-20
> **Grenage said:**
> He wants to know what card you have ;)

Yes, sorry for be very general in the question ;)

---

### Post by sean_M on 2010-01-20
> **n0dix said:**
> Yes, sorry for be very general in the question ;)

Netgear WN111 V2 also stated in my first post :P

---

### Post by n0dix on 2010-01-20
Sorry, i thought the netgear was your router. ;)

---

### Post by sean_M on 2010-01-20
> **n0dix said:**
> Sorry, i thought the netgear is your router. ;)

Nope I'm using a netgear WN111 v2 wireless adapter, to connect to my friend, and I shared internet. Sorry for the confusion.

---

### Post by Grenage on 2010-01-20
I am guessing that the driver being used isn't so hot.  Unfortunately I don't know what to suggest here.  If you boot using a live CD, what's the download speed like then?

---

### Post by pasqualino31 on 2010-04-10
> **sean_M said:**
> Netgear WN111 V2 also stated in my first post :P

Could you please tell me how you got the wn111 to work?  I've tried all the suggestions in the forum. (please see my wn111 post)I really would appreciate the help.

---

### Post by misterbk on 2010-04-10
Wireless transfers can be difficult.  You're sure it's Ubuntu? i.e. you've done the transfer multiple times, rebooting between windows and linux, and it's absolutely repeatable that Ubuntu runs slower, beyond reasonable possibility of random interferences from other WAPs, cell phones, radio phones, peoples' microwaves etc?  (the 2.4ghz range is way overpopulated...)

Not sure how your wireless ecosystem is but where I live there are a good 25 WAPs within range that my laptop can pick up, all assigned to a horrible mess of overlapped channels.  If someone runs heavy transfers on Channel 5, that activity interferes with traffic on channels 4 and 6 as noise, so your issue could be someone on an adjacent channel sporadically trying to stream wireless HD through DLNA.

I solved my problem by switching to 802.11a where there is only one other WAP to compete with.

---

