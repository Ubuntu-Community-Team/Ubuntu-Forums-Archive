---
title: "apache logs question..."
date: 2011-07-24
forum: General Help
---

### Post by mikejonesey on 2011-07-24
if a request does not appear in the logs (and logs are switched on), does this 100% mean apache did not receive that particular request? 

or could it mean apache failed to process that log?

to the best of my knowledge apache would log with 400 or 500 if it could not process a request or the server generated an error...???

---

### Post by galvatron408 on 2011-07-24
That's correct unless you have multiple sites then you would want to check the other logs too.

---

### Post by mikejonesey on 2011-07-24
many thanks, now i have to work out why apache does not receive a certain request, but the server does...

anyone have an idea where i can look?

---

### Post by WorMzy on 2011-07-24
Hey, Mike.

The only things I can think of that would stop Apache receiving a request are a) your ISP, b) your router, or c) your firewall.

Since you're sure (somehow, I'm not sure how) that your requests are reaching the server, that rules out a) and b), and I can't see how c) could be causing problems unless you've specifically told it to.

I haven't replied to your other thread because this is all I can think of, and all three seem equally unlikely. I'm only posting this so that you know why I haven't replied. Whether it's enough for you to diagnose the problem on your own, is up to you.

---

### Post by mikejonesey on 2011-07-24
> **WorMzy said:**
> Hey, Mike.

The only things I can think of that would stop Apache receiving a request are a) your ISP, b) your router, or c) your firewall.

Since you're sure (somehow, I'm not sure how) that your requests are reaching the server, that rules out a) and b), and I can't see how c) could be causing problems unless you've specifically told it to.

I haven't replied to your other thread because this is all I can think of, and all three seem equally unlikely. I'm only posting this so that you know why I haven't replied. Whether it's enough for you to diagnose the problem on your own, is up to you.

many thanks, much appreciated...

I know the server is recieving the request using somthing along the lines of;

```
watch -n 1 "netstat -tn | grep myip | grep 80"
```normal request...
tcp        0      0 ::ffff:46.252.194.67:80     ::ffff:??.??.??.??:44566   TIME_WAIT
funny request...
tcp        0      0 46.252.194.67:80 ??.??.??.??:44567          SYN_RECV

which is a problem in it's own (iv'e had to setup to prevent floods..., (in place))

but no trace through apache of the bad request...

a. isp, maybe although i think unlikley... if the request were to be blocked at this level i'd expect to whole request to bounce...

b. router, i can rule this one out...

c. firewall, deffo none of mine, I have tested this setting up rules to allow any data between me and the server ip-ip base, which proved to not be the problem...

I can also confirm the server can handle these requests, as when requested localy work fine...

My thoughts now... I can only imagine it's a isp firewall server end... (godaddy's firewall)...

I guess i send a tcp packet that reqests comm, server replies ok, send me data, i send packet with request for bad page (which is blocked), server does not reply causing a wait on both ends...

If this is the case, shouldn't this level of filtering be left to server users/owners not isp...

godaddy tech help said they don't know and can't help... great lol!

---

### Post by mikejonesey on 2011-07-24
laptop external bad request:
> tcp        0    690 192.168.1.10:37241      46.252.194.67:80        ESTABLISHEDserver receiving bad request:
> tcp        0      0 46.252.194.67:80 ??.??.??.??:37241          SYN_RECV

(??=my ip (privacy :) ))

---

### Post by mikejonesey on 2011-07-24
[http://www.godaddy.co.uk/perl.exe](http://www.godaddy.co.uk/perl.exe)

also does not load rather than a 400 or 404 or 500...

i think is a conclusion it's a godaddy firewall?

---

### Post by WorMzy on 2011-07-24
Same here. [http://www.godaddy.co.uk/perl.exe]("http://www.godaddy.co.uk/perl.exe") results in a constant loop/timeout.

I can kinda see why they'd block .exe requests. But your other request, "cgi-914/pollit/Poll_It_SSI_v2.0.cgi?data_dir=\etc\passwd%00", I don't see why.

It may be worth giving them a grilling over this. But what is the likelihood of you using .exe as a page extension? .cgi, maybe; but there's no need for you to use .cgi as an extension. You can tell apache to treat .abcdefghijklmnop as a cgi extension if you so desire.

---

### Post by mikejonesey on 2011-07-24
> **WorMzy said:**
> Same here. [http://www.godaddy.co.uk/perl.exe](http://www.godaddy.co.uk/perl.exe) results in a constant loop/timeout.

I can kinda see why they'd block .exe requests. But your other request, "cgi-914/pollit/Poll_It_SSI_v2.0.cgi?data_dir=\etc\passwd%00", I don't see why.

It may be worth giving them a grilling over this. But what is the likelihood of you using .exe as a page extension? .cgi, maybe; but there's no need for you to use .cgi as an extension. You can tell apache to treat .abcdefghijklmnop as a cgi extension if you so desire.

yea i went slightly off track here... i always go at something till i understand exactly why something works or in this case doesn't...

Want I want to know most is what exactly is getting blocked, and how...

I think godaddy are a bit silly for this because it is a security risk, my server is secure now i have taken measures to cover this hole, but not ideal...

I think the urls that get caught are ones that script kiddies check with... thus;

[http://www.godaddy.co.uk/daddy.exe](http://www.godaddy.co.uk/daddy.exe)
loads;
[http://www.godaddy.co.uk/perl.exe](http://www.godaddy.co.uk/perl.exe)
does not...

I can also assume from a tech perspective they thought this would slow down malicious crawlers, or at least lessen their load, which i suppose would work to an extent...


ps many thanks for responses...

---

