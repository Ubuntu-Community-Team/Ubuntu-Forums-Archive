---
title: "Recomendations for VOIP application?"
date: 2012-09-07
forum: General Help
---

### Post by oxf on 2012-09-07
Hi,

I have previously used Empathy for a "Skype like" application. That worked reasonably well on my old email address. I never used it that much though.

I am now in a situation where I quickly need to set up a VOIP call facilllity with someone else. I need to do it using a hotmail address. We both messed around for hours last night and had major problems. I don't know how much was my/our fault in the set up but also it seemed Empathy was being a bit erratic.

So I know there's a number of VOIP type clients out there. What do you recomend for  one that works easily  using hotmail adddress?

Thanks
Veronica

---

### Post by oxf on 2012-09-07
Further to my initial question. I've been doing a bit of googling around and read of various issues with Empathy. Is this normal? i.e. is it more buggy than other VOIP clients and does it have an issue with hotmail accounts.

What about Ekiga? I read some good comments about that but am wondering if it still being maintained? Didn't Ekiga used to be the default in older versions of Ubuntu?

Thanks
Veronica

---

### Post by TheFu on 2012-09-07
I don't know what hotmail has to do with anything VoIP unless you want to use some sort of microsoft "voice chat" through MSN.

Yahoo! and Google have competing free offerings, but those will require accounts on those systems.

There are also free SIP services like [http://www.internet2.edu/sip.edu/](http://www.internet2.edu/sip.edu/) or FreeConferenceCallHD that will let people from anywhere in the world join a conference using SIP clients for free.  These are not tied to any specific email service.

If you want to run your own VoIP server that means you should install Asterisk or FreeSwitch to host the calls and then any SIP client can be used to connect from any platform, assuming you have enough bandwidth to support the selected codec (usually g.711u/a) for each person calling in.   Most broadband internet connections easily have this today.  It is about 128Kbps per person and lots of headroom is needed on the upstream.

There are lots of SIP clients ... Twinkle, Linphone, Ekiga, [https://en.wikipedia.org/wiki/Comparison_of_VoIP_software#General_softphone_clients](https://en.wikipedia.org/wiki/Comparison_of_VoIP_software#General_softphone_clients) has more.  They all suck about the same, but I haven't given them a fair shot recently due to other mandated OS requirements.

Is there a reason not to use Skype?

---

### Post by oxf on 2012-09-07
> **TheFu said:**
> I don't know what hotmail has to do with anything VoIP unless you want to use some sort of microsoft "voice chat" through MSN.


There are lots of SIP clients ... Twinkle, Linphone, Ekiga, [https://en.wikipedia.org/wiki/Comparison_of_VoIP_software#General_softphone_clients](https://en.wikipedia.org/wiki/Comparison_of_VoIP_software#General_softphone_clients) has more.  They all suck about the same, but I haven't given them a fair shot recently due to other mandated OS requirements.

Is there a reason not to use Skype?

Well you have to enter an email address to create an account and of course to call the other person. It has nothing to do with hotmail per se.  

Previously I used an old gmail address and Empathy worked fine. I no longser have that address and would like to use my hotmail.

Yes I could use Skype I suppose but there seem to be plenty of open source options so that would be my first choice. Ideally I'd prefer to stay with Empathy as its installed but if its going to cause too much hassle I'll try something else. Hence my question

Veronica

---

### Post by TheFu on 2012-09-07
Thanks for explaining. I understand the F/LOSS desire and the desire not to sign up for any accounts.

[http://ihu.sourceforge.net/](http://ihu.sourceforge.net/) appears to be a direct-to-direct audio communications tool.  I've never used it. No middle servers.  I installed it **sudo apt-get install ihu** - only 2 dependencies on a 12.04 box.  It is Linux only, so the other side will need to install it too. Inbound calls are on port 1793 either TCP or UDP.  Your choice. udp would have lower overhead.  Only works for 2 people, no conference dialing. Supports strong encryption.

[https://live.gnome.org](https://live.gnome.org) seems to allow any email address to be used. That's the back end server Empathy uses.

With some SIP clients, you can just call each other directly. No 3rd party in the middle at all.  The caller just needs to know the current public IP address of the callee.  The callee has to open the SIP port(s) to receive the direct call and a way to handle NAT.  Caller can use either:
* sip:xxx.xxx.xxx.xxx
* h323:xxx.xxx.xxx.xxx

However, that doesn't seem possible with Empathy.

SIP hates NAT, so extra steps need to be taken to make any SIP endpoint safely traverse NAT.

---

### Post by oxf on 2012-09-08
Thanks for that information. 
As an interim measure last night I installed skype and sure enough it worked first time with my hotmail account. Which says something about the present state  of Empathy.
Anyway I will look at the alternatives. My friend is also using Ubuntu btw

Veronica

---

### Post by rmstock2 on 2012-11-09
I adapted twinkle-1.4.2 to run on ubuntu 12.10 :

[http://crashrecovery.org/twinkle/ubuntu1210/](http://crashrecovery.org/twinkle/ubuntu1210/)

```

total 4472
-rw-r--r--  1 root root    4349 Nov  9 14:42 libccrtp2.patch
-rw-r--r--  1 root root    1178 Nov  9 17:39 localtime_r.patch
-rw-r--r--  1 root root     586 Nov  9 20:06 MD5SUM
-rw-r--r--  1 root root  165019 Nov  9 18:42 twinkle_1.4.2-2.2_amd64.build
-rw-r--r--  1 root root    1644 Nov  9 18:42 twinkle_1.4.2-2.2_amd64.changes
-rw-r--r--  1 root root 1735966 Nov  9 18:42 twinkle_1.4.2-2.2_amd64.deb
-rw-r--r--  1 root root  132089 Nov  9 18:35 twinkle_1.4.2-2.2.diff.gz
-rw-r--r--  1 root root    1555 Nov  9 18:35 twinkle_1.4.2-2.2.dsc
-rw-r--r--  1 root root 1601100 Dec  3  2011 twinkle_1.4.2.orig.tar.gz
-rw-rw-r--  1 root root  597959 Nov  9 19:49 twinkle-ubuntu1210.jpg
-rw-rw-r--  1 root root  287146 Nov  9 20:02 twinkle-ubuntu1210-s.jpg

``````

ba2c2e979124ba578cdaf4cc20b33da5  libccrtp2.patch
3dddb91df7682257e98e817dd81e7778  localtime_r.patch
9ae25e159cb21f3d4edc0fc46f23a6e0  twinkle_1.4.2-2.2_amd64.build
2bce5929000aa32be85c5346ced8d0c9  twinkle_1.4.2-2.2_amd64.changes
7e7ac95852be06e795934c3a2d462f57  twinkle_1.4.2-2.2_amd64.deb
4a1406d18856fdb96ffda20ec671bf13  twinkle_1.4.2-2.2.diff.gz
b09fa5464823bb3978d62e69bf94d230  twinkle_1.4.2-2.2.dsc
d70c8972f296ffd998c7fb698774705b  twinkle_1.4.2.orig.tar.gz
c86ae7f1f1e615121307a8f705ebeddc  twinkle-ubuntu1210.jpg
7bd99c970e4b07fc0660ea3ab6d26f09  twinkle-ubuntu1210-s.jpg

```[IMG]http://crashrecovery.org/twinkle/ubuntu1210/twinkle-ubuntu1210-s.jpg[/IMG]

---

