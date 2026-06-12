---
title: "Google chrome (dev) sources.list problem"
date: 2010-03-15
forum: General Help
---

### Post by ubername on 2010-03-15
Can someone post the right entry for /etc/apt/sources.list for google chrome (development) please?

I have been getting 
```
Failed to fetch http://dl.google.com/linux/deb/dists/stable/main/i18n/Translation-en_GB.bz2  
Failed to fetch http://dl.google.com/linux/deb/dists/stable/Release
```  

whenever I update my repo's in synaptic for the past couple of weeks. (three lucid installs and two karmic installs)

---

### Post by ubername on 2010-03-16
bump

Ths is simply a request for a sources.list which has an entry for the google chrome repo please?

---

### Post by cengelbrecht on 2010-03-17
Synaptic's HTTP code doesn't talk to the Google servers correctly.

I really don't see why Synaptic has to have it's own HTTP client code, but that's how it currently is.

To solve the problem, configure Synaptic to use an HTTP proxy, by going to Settings | Preferences | Network from within Synaptic.

---

### Post by ubername on 2010-03-18
> **cengelbrecht said:**
> Synaptic's HTTP code doesn't talk to the Google servers correctly.

I really don't see why Synaptic has to have it's own HTTP client code, but that's how it currently is.

To solve the problem, configure Synaptic to use an HTTP proxy, by going to Settings | Preferences | Network from within Synaptic.

Thanks

What do I put in the Network tab after selecting 'manual configure proxy'?

---

### Post by cengelbrecht on 2010-03-18
You put in the address of an HTTP proxy server.

If you don't have one installed, then you can use Squid, which IMO is the best one. Squid is available from within Synaptic.

I recommend finding a HOWTO guide on configuring Squid for easy setup.

Just a note: If you are going to do this, and also use Squid as your proxy server for Firefox, then remember to access Squid as 127.0.0.1 from within Firefox, or else Java applets won't load on web pages that use Java.

---

### Post by ubername on 2010-03-20
Thanks for the reply

I have done a bit of reading and it looks like a bit of an undertaking to setup squid.

I am amazed that this problem hasn't been raised before - my google ppa worked fine until a couple of weeks ago. Is no-one else having this problem, or is everyone else using a proxy?

---

### Post by kerry_s on 2010-03-20
no, your not alone i had that problem. i removed google-chrome cause it was so annoying, i'm using chromium for now.

---

### Post by cengelbrecht on 2010-03-20
It worked until a few weeks ago until the Google servers stopped supporting HTTP pipelining.

To set up squid is really easy:
1. sudo apt-get install squid
2. sudo vi /etc/squid/squid.conf
3. search for acl-localnet
4. uncomment the one that matches your local lan, or modify one and use that

That's it.

Is that really difficult?

---

### Post by ubername on 2010-03-21
> **cengelbrecht said:**
> It worked until a few weeks ago until the Google servers stopped supporting HTTP pipelining.

To set up squid is really easy:
1. sudo apt-get install squid
2. sudo vi /etc/squid/squid.conf
3. search for acl-localnet
4. uncomment the one that matches your local lan, or modify one and use that

That's it.

Is that really difficult?

Ok, I am trying that. Some of the stuff I read seemed to imply I had to install it on a LAMP server which is a bit more of a mission.

Installing squid - no probs

Configuring:

I had to search for 'acl localnet' - there is no hyphen.

Next questions, revealing just how little underlying knowledge I have (the shame!)

I have set
acl localnet src 192.168.2.0/24

Will this cover addresses in the range 192.168.2.0 to 192.168.2.255?

I guess I need to restart squid to get it to acknowledge that? 

Most importantly, what do I put in Synaptic Manual proxy configuration?

I need something for HTTP proxy: what should I put (is it an IP address, the word 'squid' or something else? I'm guessing the default port of 3128 will work?

Also, I take it I don't need to mess with other internet facing apps - they can work as they are unless I specifically want them to use the proxy?

---

### Post by kerry_s on 2010-03-21
the daily chromium has the same features as the google-chrome dev.

```
sudo add-apt-repository ppa:chromium-daily
```

---

### Post by ubername on 2010-03-21
Yay! Done it!

I had to use the hostname of this machine as the value in the HTTP field

and after some digging, I discovered I needed to add 
acl localhost src 127.0.1.1/32
acl to_localhost dst 127.0.1.0/8

to squid.conf

I've certainly overdone it there (I only need 127.0.1.1 I'm sure) and I don't know whether I need both those lines, but I am now not freezing on the google repo when I 'reload' in synaptic!

---

### Post by cengelbrecht on 2010-03-21
I take it that Synaptic works now?

You can put the IP of the machine into Synaptic as the HTTP proxy address as well, you don't have to use the hostname.

Happy installing :)

---

### Post by ubername on 2010-03-21
> **cengelbrecht said:**
> I take it that Synaptic works now?

You can put the IP of the machine into Synaptic as the HTTP proxy address as well, you don't have to use the hostname.

Happy installing :)

Yep, I'm happy!

---

### Post by Cyan_Fire on 2010-03-27
FYI, Google recognizes this as a problem, but "there is no timeframe yet" for fixing it. ([Source.]("http://groups.google.com/group/google-linux-repositories-help-basics/browse_thread/thread/fa3b4e26685d31f3"))

---

### Post by krige on 2010-04-09
I have fixed it by creating the file "/etc/apt/apt.conf.d/90localsettings" with the following content:

```
Acquire::http::Pipeline-Depth "0";
```

---

### Post by ubername on 2010-04-12
> **krige said:**
> I have fixed it by creating the file "/etc/apt/apt.conf.d/90localsettings" with the following content:

```
Acquire::http::Pipeline-Depth "0";
```

That is cool!

Thanks - much easier than the struggles I had with squid!

---

### Post by ubername on 2010-05-09
I have just used

```
 echo "Acquire::http::Pipeline-Depth "0";" | sudo tee /etc/apt/apt.conf.d/90localsettings
```

as a quick way to do this.

---

### Post by krige on 2010-05-09
I think they have fixed this: I didn't need to create that file on a fresh Ubuntu 10.04 and updates installation doesn't get stalled anymore.

---

