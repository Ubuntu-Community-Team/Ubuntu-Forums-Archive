---
title: "MSN Not working with Gaim, aMSN, KMess"
date: 2006-06-18
forum: General Help
---

### Post by Elmo7 on 2006-06-18
G'day

I used to run Fedora Core 4 on this PC and msn worked with both Gaim and aMSN fine.

Last night I installed Ubuntu 6.06 and I can't access my msn account using Gaim, aMSN or KMess.

I've tried both with an old hotmail account that still works and my newer gmail email account that is tied to an MSN Passport and works with Messenger on XP and on webmessenger using IE under Ubuntu and Wine.

I've looked around these forums and found similar problems but nothing that works for me.

Any help would be greatly appreciated, as the ability to access the MSN messenger network is something I really need and I don't want to have to go back to XP just for that.

---

### Post by donar73 on 2006-06-18
MSN is working fine with Gaim 1.5 here, maybe something is wrong with your settings?

---

### Post by Elmo7 on 2006-06-18
I'd say so... Although I haven't changed any settings. When I had my Fedora install it worked from its basic setup without having to set anything. I've tried the same with Gaim (and other clients) on Ubuntu and it's not working, and I haven't changed any settings.

---

### Post by treris on 2006-06-18
Both gaim and amsn seem to work just fine here, and I can't say I've had to do anything to make that happen.
You could check your firewall settings just to make sure gaim or amsn can use port 1863 to connect to the msn network.

---

### Post by Elmo7 on 2006-06-18
I went to the accout options and chose "Use HTTP Method" and now when it connects my contacts list flashes for a second, I get a "Reading Error" and it says I am disconnected. So the connection is being made, ruling out any firewall problems.

Running gaim using "gaim -d" shows some generic connecting messages, as well as my contact list being loaded, and then: 

```
msn: HTTP: Read error
msn: Connection error from Notification server (messenger.hotmail.com): Reading error
g_log: msn_session_disconnect: assertion `session->connected' failed
account: Disconnecting account 0x81d3290
connection: Disconnecting connection 0x868a090
connection: Deactivating keepalive.
msn: destroy httpconn (0x86a57b8)
connection: Destroying connection 0x868a090
```

After this it just repeats the whole process.

---

### Post by Elmo7 on 2006-06-19
Still not working today.

On XP Msn Messenger reckons that it is connected through my browser's default HTTP Proxy settings, so I assume that using the "HTTP Method" in both Gaim and aMSN is the right thing to do. Still not working though and giving same error as yesterday.

---

### Post by Johnsie on 2006-06-19
Try using Wengophone 2 to get on msn.... [http://wengo.com](http://wengo.com)

---

### Post by Elmo7 on 2006-06-19
Because I can't access it with every client I've tried so far I'm guessing its a problem with connecting to the MSN Protocol as a whole, so trying other clients isn't going to work. I'll have a look later on when I'm in Ubuntu though.

---

### Post by Lord Illidan on 2006-06-19
[quote=Johnsie]Try using Wengophone 2 to get on msn.... [http://wengo.com]("http://wengo.com")[/quote]

Is it any good compared to Gaim, Kopete and aMSN? Cos` I might switch, myself.

Regarding your MSN troubles, have you tried Kopete?

---

### Post by Elmo7 on 2006-06-19
I've tried about all the Clients I know of. It doesn't appear to be a problem with any one client, but a problem with connecting to msn in general from my ubuntu.

---

### Post by Lord Illidan on 2006-06-19
Are you using a router?

---

### Post by lorenzo on 2006-06-19
I'm facing a similar problem. 

When at home, gaim 1.5, gaim 2.0 beta3 and amsn works (msn protocol).

At work i'm behind a proxy and I have to use an http protocol through port 8080. Here only gaim 1.5 works. Nor gaim2 beta3 nor amsn works.... :( 

Ciao,
Lo

---

### Post by Dr.Fix on 2006-06-21
[QUOTE=lorenzo]I'm facing a similar problem. 

When at home, gaim 1.5, gaim 2.0 beta3 and amsn works (msn protocol).

At work i'm behind a proxy and I have to use an http protocol through port 8080. Here only gaim 1.5 works. Nor gaim2 beta3 nor amsn works.... :( 

Ciao,
Lo[/QUOTE]

The same here.
Using HTTP method aMSN keeps saying my username/password are wrong...

---

### Post by Elmo7 on 2006-06-21
I am behind a router which allows me to use MSN Messenger on XP.

I also have the username/password problem when using HTTP method with aMSN that Dr. Fix is having.

---

### Post by panurge77 on 2006-06-21
Gaim must be lacking the ssl authentication for http. Amsn had this problem, but I think it's corected on the development version

---

### Post by tubo on 2006-06-21
i had that problem before, and solved it - here is what works for me for MSN, in HTTP mode:

 - Gaim 2.0 beta 2 (!! important, beta3 does NOT work)
 
Can't remember where i found the DEB, but i am sure you ll be able to find it, or compile it from source.

best
Emanuel

---

### Post by Dr.Fix on 2006-06-21
Gaim works with HTTP method, is aMSN that doesn't work!

---

### Post by Elmo7 on 2006-06-22
It's now working with Gaim and HTTP method selected. I had to reinstall Ubuntu for a different reason and after that it's now working. Something musn't have installed properly the first time.

---

### Post by lorenzo on 2006-06-28
Elmo7: which version of gaim are you using? Standard Dapper comes with gaim 1.5...


Update: I do confirm that Gaim 2.0 beta 2 works behind a proxy/firewall while gaim 2.0 beta 3 does not!.

---

### Post by tubo on 2006-07-05
yup. i locked the GAIM package in Synaptic at 2.0beta2, so it doesn't auto update. Maybe you should do the same until they make a release that works on MSN with HTTP method again.

best
Emanuel

---

### Post by gizmoarena on 2006-08-04
i'm still having problems with all aMSN, Gain 1.5, KMess and kopete. 

i can log-in into msn easily by aMSN, it shows contact list and whom are online, but i cant send or receive messagee. my contacts on the otherside informed me the same, they can see me online, messages are bouncing back.

Gaim says proxy fobids 1863 tunelling.

Kopete and Kmess says connection actively refuesd.

i'm behind a firewall [10.0.0.30:3128]

any solution?

---

