---
title: "Please help, badly in need"
date: 2010-10-05
forum: General Help
---

### Post by alice06 on 2010-10-05
Hi all

I am a Ph.D physics student and have started programing in C language in Ubuntu. But when I am in Ubuntu, my web browsers shows **'Page load error, Address not found'** page.
Actually it all started after my brother started downloading a lot of movies from the net.
In Windows it is all fine but I have to do my programing in Ubuntu and need a lot of help from the web, Thus I am badly stuck with the web browsers not working.

[B]Please help me, I have a lot of work but can't do anything. Please help somebody.

[/B]Alice

---

### Post by bonixavier on 2010-10-05
> **alice06 said:**
> Hi all

I am a Ph.D physics student
I'm afraid of you. lol;
> But when I am in Ubuntu, my web browsers shows **'Page load error, Address not found'** page.
Actually it all started after my brother started downloading a lot of movies from the net.
Just out of curiosity, how do you download them? If you're using Transmission, those things will happen because it eats all your bandwitdth. It has happened to me before.

If that's not the case, I wouldn't know. Sorry.

---

### Post by cloyd on 2010-10-05
It really looks like you have lost your Internet connection. It appears you are off line. What does the network manager icon on the top panel show you?

---

### Post by HereInOz on 2010-10-05
First thing to do is to open a terminal and type:

ping google.com

If you get a result, and the google server answers, then it is probable that you have an internet connection, and it is your browser playing up.

If you don't get a response, then stop that process and type: 

ping 66.102.11.104

If that works, but ping google.com does not, then you have a DNS issue.

If it doesn't work, then indeed you probably have no network connection to your Internet modem, and hopefully we can take it from there.

---

### Post by alice06 on 2010-10-06
Hi all of you

Thanks a lot for ur replies and now I am certain that I with ur help I will come out of this.

On ubuntu (8.04), my internet is workin, google is working many sites are working, but there are many many other sites which are giving **page load error**. Like this ubuntuforums.org itself is not working.
In my windows each and every site is working.

Ping google.com gives

```
64 bytes from maa03s01-in-f104.1e100.net (209.85.231.104): icmp_seq=1 ttl=55 time=71.2 ms
64 bytes from maa03s01-in-f104.1e100.net (209.85.231.104): icmp_seq=2 ttl=55 time=74.4 ms

```

ping 66.102.11.104 gives

```
ping 64 bytes from 66.102.11.104: icmp_seq=1 ttl=49 time=278 ms
64 bytes from 66.102.11.104: icmp_seq=2 ttl=49 time=277 ms
64 bytes from 66.102.11.104: icmp_seq=3 ttl=47 time=278 ms

```

I also should tell u all that sometimes (but very rarely) it happens that all the sites in ubuntu start running and then again the problem appears.

Alice

---

### Post by mastablasta on 2010-10-06
again, how did you download the movies? was it torrents that they were used? if so they can clog up your connection and you would get it like that (some sites will load others won't at all). 
 
To avoid this you need to throttle your max upload and download speed as well as set max connecitons.

---

### Post by alice06 on 2010-10-06
Hi all of you

Thanks a lot for ur replies and now I am certain that I with ur help I will come out of this.

On ubuntu (8.04), many sites are working, but there are **many many** other sites which are giving **page load error**. Like this ubuntuforums.org itself is not working.

**In my windows each and every site is working.**

Ping google.com gives

```
64 bytes from maa03s01-in-f104.1e100.net (209.85.231.104): icmp_seq=1 ttl=55 time=71.2 ms
64 bytes from maa03s01-in-f104.1e100.net (209.85.231.104): icmp_seq=2 ttl=55 time=74.4 ms
```

and ping 66.102.11.104 gives

```
ping 64 bytes from 66.102.11.104: icmp_seq=1 ttl=49 time=278 ms
64 bytes from 66.102.11.104: icmp_seq=2 ttl=49 time=277 ms
64 bytes from 66.102.11.104: icmp_seq=3 ttl=47 time=278 ms

```

I also should tell u all that sometimes (but very rarely) it happens that all the sites in ubuntu start running and then again the problem appears.

This problem is occurring after my brother watched a number of movies online.

Is there a problem in the settings of the firefox??

Please help

Regards
Alice

---

### Post by natasa on 2010-10-06
Do you modem's lights blink fast when you're unable to open the websites that aren't working?

Try to see if the websites work when your brother's PC is off.

Are the websites that aren't working something special or specific? If so, you might be behind a firewall.

Can you access your modem's web configuration? Try [http://192.168.1.1/](http://192.168.1.1/) or [http://192.168.0.1/](http://192.168.0.1/)

---

### Post by SeijiSensei on 2010-10-06
If you're using something like a wifi router, disconnect the router from the power line, wait thirty seconds, then reconnect it.  

Tell your brother that your Ph.D. is a hell of a lot more important than his movie viewing and to knock it off.

If he's using a Bittorrent client, you can mitigate this problem by throttling the bandwidth it uses, and more importantly, cutting back on the number of connections it uses.  If he can't figure out how to do this, then he needs to be nice and power-cycle the router each time he downloads a torrent.

---

### Post by alice06 on 2010-10-06
Thanks u **mastablasta** and **natasa** for replying.

In reply to **mastablasta**, My brother actually saw online movies on my laptop, not torrents.

In reply to **natasa**, It is acually on my laptop that my brother watched the movies. I cant observe anything special in the modem, but one important observation that 

192.168.1.1 is pinging well, as it shows 
```
alice@alice-laptop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.377 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.369 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.349 ms

```
on the terminal,
but when I put it on the url address bar, then it asks for a username and password.

when i ping 192.168.0.1, it shows 
```
alice@alice-laptop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.

```
AND NOTHING AFTER THAT.

and when I put it on the url bar of firefox, it runs forever without showing anything.

Also I would like to share my windows network setings:

```
ip address- 192.168.1.5
subnet mask-255.255.255.0
default gateway-192.168.1.1
preffered dns server-202.159.219.229
alternate dns server-202.159.217.198
```

Please help
Regards
alice

---

### Post by etdsbastar on 2010-10-06
> **alice06 said:**
> Hi all

I am a Ph.D physics student and have started programing in C language in Ubuntu. But when I am in Ubuntu, my web browsers shows **'Page load error, Address not found'** page.
Actually it all started after my brother started downloading a lot of movies from the net.
In Windows it is all fine but I have to do my programing in Ubuntu and need a lot of help from the web, Thus I am badly stuck with the web browsers not working.

[B]Please help me, I have a lot of work but can't do anything. Please help somebody.

[/B]Alice

Have you played with any proxy settings in your browser; it yes then please reply if not then first of all tell us the browser type and model and the connection type you are using to connect to the internet.

---

### Post by alice06 on 2010-10-07
Thank u **all**. Thank u for being concerned for me.
 
But I reinstalled a newer version of firefox yesterday and since then  things are working great. Haven't had any problems after that.
 
If I have problems again, I will get back to u.
 
 **Thanks a lot.** This forum is great.
 
Regards 
Alice

---

