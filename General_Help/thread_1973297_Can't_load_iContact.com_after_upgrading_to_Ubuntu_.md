---
title: "Can't load iContact.com after upgrading to Ubuntu 12.04"
date: 2012-05-04
forum: General Help
---

### Post by mlfa on 2012-05-04
I can load all other websites, but I can't load [www.icontact.com](www.icontact.com) no matter what I do. I've modified my DNS settings in my network manager, my /etc/resolvconf/resolv.conf.d/base file and even modified /etc/default/grub with the following:

GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 quiet splash"

and then back again to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

All other computers on my network can access this website. I'm the only computer that can't. 

I added Google's public DNS 8.8.8.8 and 8.8.4.4 and no luck. 

I've rebooted. I've rebooted the router. I have done just about everything I can think of. 

When I try to access the site via their IP address, it only partially loads because all the stylesheets are references through the domain name. 

I actually got the website to load a couple of times, but after a little while I couldn't load the site anymore. 

Sometimes I can load the http homepage, but can't get any https pages to load (which is pretty much the rest of the site). 

I tried disabling dnsmasq in /etc/NetworkManager/NetworkManager.conf

I followed the instructions found on this post:
[http://ubuntuforums.org/showthread.php?t=1968061](http://ubuntuforums.org/showthread.php?t=1968061)

This worked for a little while (minutes), but then I was unable to reach icontact.com after that little while was up. 

Any ideas?

I'm running Ubuntu 12.04 on a Dell Vostro 200.

---

### Post by CharlesA on 2012-05-04
Hi,

Are you able to ping them? I was able to ping them fine.

You could try uninstalling dnsmasq completely and seeing if that fixes the problem but if it is just one site, I doubt it's entirely a DNS issue.

---

### Post by mlfa on 2012-05-04
I can ping. I think I might be having trouble with just the https portion of the site, which is pretty much the entire site (except the homepage if I specifically type in http instead of https).

When I type in [http://www.icontact.com](http://www.icontact.com) I see a broken-up page (see screenshot attached). 

When I type in [https://www.icontact.com](https://www.icontact.com) I can't even load the site (see screenshot attached).

So far, this is the only site I cannot load. It makes no sense.

---

### Post by CharlesA on 2012-05-04
I can load it fine, do other https sites work?

If you want to eliminate dnsmasq, just remove it and reboot and see what happens.

---

### Post by mlfa on 2012-05-04
Yes, other https sites work just fine. No problems... only with icontact.com.

---

### Post by CharlesA on 2012-05-04
Ok.

Edit /etc/resolv.conf to read:

```
8.8.8.8
8.8.4.4
```

Then try reloading the website.

---

### Post by mlfa on 2012-05-04
Yes, I've tried using those DNS servers, too. No luck.

---

### Post by CharlesA on 2012-05-04
> **mlfa said:**
> Yes, I've tried using those DNS servers, too. No luck.
Ok, then it is not a problem with DNS.

Are the computers where it works fine using Chrome too?

---

### Post by mlfa on 2012-05-04
Yes. I can't load it with Chrome or Firefox on my computer. So, it's not a Chrome issue.

---

### Post by CharlesA on 2012-05-04
Try booting off a livecd and see if you can access the site.

---

### Post by mlfa on 2012-05-04
I'll try that... it'll be a while. I'm at work. It's my work computer that's having the problem. My personal laptop running 12.04 can access the site with no problem.

---

### Post by CharlesA on 2012-05-04
> **mlfa said:**
> I'll try that... it'll be a while. I'm at work. It's my work computer that's having the problem. My personal laptop running 12.04 can access the site with no problem.
That will rule out a problem with the OS, and it should load fine.

---

### Post by mlfa on 2012-05-05
I was able to load and log into icontact.com using a 12.04 Live CD/DVD. So, does that mean I have a problem with the OS? And if so, what could it be? How would I fix it (without having to reinstall the OS)?

---

### Post by CharlesA on 2012-05-05
> **mlfa said:**
> I was able to load and log into icontact.com using a 12.04 Live CD/DVD. So, does that mean I have a problem with the OS? And if so, what could it be? How would I fix it (without having to reinstall the OS)?
Yeah, it's a problem with the OS, but it shouldn't be there as that is the only site you have problems with. Have you added any programs lately?

---

### Post by mlfa on 2012-05-07
No. The latest thing I've done is upgrade to 12.04. 

I deleted everything in /etc/resolvconf/resolv.conf/base and restarted network-manager and I could access icontact.com for a little while, then it went unavailable again (https) or broken-looking (http). 

What could be causing this in the OS, and how would I fix it without a fresh re-install?

---

### Post by CharlesA on 2012-05-07
You might try a new firefox/chrome profile and see it the problem still occurs.

---

### Post by mlfa on 2012-05-07
I disconnected my work profile and logged into my personal profile and it worked for a while... then... back to "unable to load website" type errors. 

Then, I logged back into my work profile... still not working.

---

### Post by mlfa on 2012-05-07
Sorry... Chrome profile (Google)

---

### Post by CharlesA on 2012-05-07
Try creating a whole new profile and see what happens.

If that doesn't work, it might be a good idea to back up your stuff and reinstall.

---

### Post by mlfa on 2012-05-09
I had to reinstall everything... was up until 3am... not happy about that, but happy that I can now access the website. 

Now, my printing is not working. I'll start a new post to address that issue. 

Thank you for your help.

---

### Post by feeyonge on 2012-05-09
Basically, is this an OS problem, or web browser problem?
 
--------------
Try Littleye [parental control software]("http://www.littleye.com/") for iphone free now

---

### Post by CharlesA on 2012-05-09
> **feeyonge said:**
> Basically, is this an OS problem, or web browser problem?
Sounds like a bit of both cuz the livecd worked fine.

---

### Post by mlfa on 2012-05-09
The site wouldn't load on Firefox or Chrome.

---

### Post by topartnewz on 2012-06-12
sounds like more of browser problem to me

---

