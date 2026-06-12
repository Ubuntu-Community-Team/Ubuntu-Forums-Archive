---
title: "IRC SSL help"
date: 2009-10-03
forum: General Help
---

### Post by ROY.G.BIV on 2009-10-03
I cannot connect to any irc channel via ssl. I get no error message, just nothing ever happens. I thought maybe it was my firewall, but i have those ports allowed now, still not working.

I'm using irssi as a client, on Jaunty. I've set my channels to autoconnect to the ssl port, but it never works. I've tried it manually with /connect -ssl <server> <port>, but it hangs up too. I've tried all combinations availabe to me in the help pages. 

I tried adjusting the config file to accept ssl on those servers, but it just defaults back to 6667 when it connects. I'm at a loss here... can any offer any help? Perhaps my firewall is blocking it? Using guarddog firewall.

Thanks for any help you can give.

---

### Post by andrew.46 on 2009-10-04
Hi ROY,

> **ROY.G.BIV said:**
> I cannot connect to any irc channel via ssl. I get no error message, just nothing ever happens. I thought maybe it was my firewall, but i have those ports allowed now, still not working.

Although I am a keen irssi user I will admit that I have never used irssi with ssl. I have had a page bookmarked though that speaks of the setup required *before* your -ssl command will work:

[http://www.mixxnet.net/wiki/?title=Ssl#Irssi](http://www.mixxnet.net/wiki/?title=Ssl#Irssi)

My apologies if you have already followed these steps :).

Andrew

---

### Post by ROY.G.BIV on 2009-11-05
Oh my goodness, I am so sorry. I completely forgot I made this thread here.. I actually have tried those steps, but my irssi doesn't recognize use_ssl or ssl_verify as valid commands. I think this could be the problem. My irssi version is 0.8.14, if that is helpful. I actually now think that my ISP is simply stopping me from using those ports, because I can't even connect to ssl servers with webchat clients. :(

---

### Post by andrew.46 on 2009-11-05
Hi ROY.G.BIV,

Don't worry :). I am only a little sorry that I don't have access to a server that offers ssl connection so I can actually test such a connection with irssi...

Andrew

---

### Post by ROY.G.BIV on 2009-11-06
Just wanted to add that I do have openssl... just realized I didn't mention that before.

---

### Post by andrew.46 on 2009-11-06
Hi Roy,

> **ROY.G.BIV said:**
> Just wanted to add that I do have openssl... just realized I didn't mention that before.

Can I ask which service you are connecting to that has ssl available? I would be keen to try an ssl connection with irssi.

Andrew

---

### Post by ROY.G.BIV on 2009-11-07
Try this one: irc.irchighway.net port 9999 for SSL. Let me know what happens. :)

---

### Post by andrew.46 on 2009-11-07
Hi Roy,

> **ROY.G.BIV said:**
> Try this one: irc.irchighway.net port 9999 for SSL. Let me know what happens. :)

I had no difficulty connecting to this with:

```
/connect -ssl irc.irchighway.net 9999
```

and I could not connect without the *-ssl* option at all, which I gather is by design?

All the best,

Andrew

---

### Post by ROY.G.BIV on 2009-11-08
Here's what happens when I try:

```

 -!- Irssi: Looking up irc.irchighway.net
 -!- Irssi: Connecting to irc.irchighway.net [66.111.35.104] port 9999

About 8 minutes later:

-!- Irssi: warning SSL handshake failed: Connection timed out
-!- Irssi: Connection lost to irc.irchighway.net

```

That's with the -ssl option..

Any ideas?

---

### Post by andrew.46 on 2009-11-09
Hi ROY,

> **ROY.G.BIV said:**
> Any ideas?

Hmmm.... I am less than an expert with irssi and ssl. What happens with:

```
/connect -ssl irc.irchighway.net 6667
```

**Edit:** Some of my colleagues on the Ubuntu Beginners Team kindly tested this channel and could log on with no problems. So I am not sure what the problem could be. Try another server:

```
/connect -ssl irc.mozilla.org 6697
```

and see if this one connects. Can ask what version of irssi you are using? I am testing all this on:

```
andrew@skamandros~$ irssi --version
irssi 0.8.14 (20090728 1938)
```


Andrew

---

### Post by ROY.G.BIV on 2009-11-09
I use same version. And no matter what server I use, this happens. :( 

That mozilla server almost worked... it connected, but when I did a /wi, i wasn't using ssl. it did go through port 6697 though.

---

### Post by andrew.46 on 2009-11-10
Hi ROY,

> **ROY.G.BIV said:**
> That mozilla server almost worked... it connected, but when I did a /wi, i wasn't using ssl. it did go through port 6697 though.

Mind you it seems a little hit and miss with actually making an ssl connection. I never failed with this one:

```
/connect -ssl anjuna.il.us.mixxnet.net 6697 
```

as demonstrated here:

```

17:25 [anjuna] !anjuna.il.us.mixxnet.net *** You are connected using SSL cipher 
          "DHE-RSA-AES-256-CBC-SHA1"
[...]
17:26 [anjuna] -!- andrew_46 ~andrew@C-59-101-48-199.hay.connect.net.au
17:26 [anjuna] -!-  ircname  : andrew
17:26 [anjuna] -!-  hostname : ~andrew@C-59-101-48-199.hay.connect.net.au 59.101.48.199 
17:26 [anjuna] -!-  server   : anjuna.il.us.mixxnet.net MIXXnet Chicago - 
                               Hosted By  IDDX.net
**[COLOR="Red"]17:26 [anjuna] -!-           : is using a secure connection[/COLOR]**
17:26 [anjuna] -!-  idle     : 0 days 0 hours 0 mins 7 secs signon: Tue Nov 10 17:25:46 
                               2009
```

But I am none the wiser I am afraid so perhaps we should both wait for somebody who actually knows a little about ssl connections and irssi :). **Edit:** Mind you the correct syntax seems to actually be:

```
/connect -ssl irc.mozilla.org 6697
```

note the shifted position of the -ssl opition which I have corrected in my previous posts so as to not look like a complete idiot :). This certainly guarantees me an ssl connection with mozilla:

```

17:41 [mozilla2] !sand.mozilla.org *** You are connected to sand.mozilla.org with 
          TLSv1-AES256-SHA-256bits
[...]
17:41 [mozilla2] -!- andrew_47 andrew@moz-E378C435.hay.connect.net.au
17:41 [mozilla2] -!-  ircname  : andrew
17:41 [mozilla2] -!-  hostname : C-59-101-48-199.hay.connect.net.au 59.101.48.199 
17:41 [mozilla2] -!-  server   : sand.mozilla.org San Jose, California
17:41 [mozilla2] -!-           : is using a Secure Connection
17:41 [mozilla2] -!-  idle     : 0 days 0 hours 0 mins 24 secs signon: Tue Nov 10 17:41:22 2009
17:41 [mozilla2] -!- End of WHOIS

```

All the best,

Andrew

---

### Post by ROY.G.BIV on 2009-11-10
Hehe.. yeah, I was going about it the right way. I was using /server rather than /connect though- am trying that now. Wish me luck. Thanks for your help! Maybe someone who knows will come along, though the rate this forum moves, that seems unlikely. :( I'll have to try other too, I guess.

Edit: got the same error on that server. :( Oh well..

---

