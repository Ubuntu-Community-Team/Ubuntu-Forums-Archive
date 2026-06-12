---
title: "Slowly but surely losing my ability to Browse the internet"
date: 2009-12-22
forum: General Help
---

### Post by focwiz on 2009-12-22
I'm a Linux Noob...but I installed UNR on my netbook a couple of weeks ago. Everything has been going great...UNTIL yesterday. First, I lost the ability to access Google, E-bay, and Craigslist (although the Local Craiglist worked). Other sites were not affected. Now it's worse. I am having to acces Ubuntu.com through my old M$ box. Both machines are on the same router (wireless). I have even booted them separately to swap assigned IP addresses with no success. I have isolated the problem to the netbook with Ubuntu loaded. Hopefully, one of you pros can help me solve this problem.
 
here is what I know;
 
1. It is NOT a DNS issue
2. It is not a router issue
3. It is not a DSL modem issue
4. It is not a local network issue
5. The behavior was demonstrated on both Chrome and Firefox
6. Chrome has been uninstalled
 
Please HELP!!! :confused:

---

### Post by =not4prophet= on 2009-12-22
does the problem exist when your netbook is plugged in with a wired connection?

---

### Post by Seq on 2009-12-22
> **focwiz said:**
> I'm a Linux Noob...

[...]
 
1. It is NOT a DNS issue
2. It is not a router issue
3. It is not a DSL modem issue
4. It is not a local network issue
5. The behavior was demonstrated on both Chrome and Firefox
6. Chrome has been uninstalled

How did you verify the above? Can you post some output for us? Such as the contents of /etc/resov.conf, the output of a `ping` and `traceroute` to both an affected and an unaffected site (you have to install traceroute, so that may be problematic. You can use tracepath instead, but I've had mixed results with that actually working).

The output of `ifconfig -a` and `route` would also be handy.

---

### Post by focwiz on 2009-12-22
> **=not4prophet= said:**
> does the problem exist when your netbook is plugged in with a wired connection?
 
Yes, the problem exists when on a wired connection as wel.  It even exists when plugged directly into my DSL modem rather than the router.

---

### Post by my_key on 2009-12-22
Does your router/modem has a dns server? Maybe it has dns issues. (Sorry but it sounds like a dns issue to me ...:confused:)

You can try if it is by specifying opendns's servers in ubuntu.

---

### Post by cpplinux on 2009-12-22
Can you read this page: [http://64.233.169.103/](http://64.233.169.103/) ? It is the ip of [www.google.com]("http://www.google.com").

---

### Post by focwiz on 2009-12-22
> **Seq said:**
> How did you verify the above? Can you post some output for us? Such as the contents of /etc/resov.conf, the output of a `ping` and `traceroute` to both an affected and an unaffected site (you have to install traceroute, so that may be problematic. You can use tracepath instead, but I've had mixed results with that actually working).
 
The output of `ifconfig -a` and `route` would also be handy.
 
I compared the DNS entries of the working Win box to the non working UNR box...both the same.  I also plugged UNR box directly into DSL modem, thus eliminating local network and router from the scene.
 
I attached some of the output you asked for...Had to do as an attachment due to this forum not being accessible.

---

### Post by focwiz on 2009-12-22
> **cpplinux said:**
> Can you read this page: [http://64.233.169.103/](http://64.233.169.103/) ? It is the ip of [www.google.com]("http://www.google.com").
 
Interesting...Yes, the direct IP works.

---

### Post by Seq on 2009-12-22
> **focwiz said:**
> I compared the DNS entries of the working Win box to the non working UNR box...both the same.  I also plugged UNR box directly into DSL modem, thus eliminating local network and router from the scene.
 
I attached some of the output you asked for...Had to do as an attachment due to this forum not being accessible.

It appears you can resolve domains and are able to actually connect to remote hosts (such as google).

What happens if you move your firefox profile out of the way? Either create a new one via "firefox -P", or move your mozilla profiles aside aside.
```
mv ~/.mozilla ~/dot-mozilla-old
```

Do you have any proxy settings entered in through Gnome's relavant settings dialog? I'm not at a machine running Gnome right now, so I can't tell you what it is called Maybe "Proxies", or within the main network GUI configuration... Firefox (and I'm assuming chrome as well) can pick up and use Gnome's proxy settings. These may or may not be applied system-wide (if they are not, they would not affect ping, etc).

---

### Post by Seq on 2009-12-22
Also, as an aside. It appears you are using CTRL+Z to "kill" your pings instead CTRL+C. You know this just backgrounds them, right? 

They are just now a sleeping process waiting to be resumed with `fg`. If you want to actually kill them, CTRL+C is the way to do it.

---

### Post by focwiz on 2009-12-22
> **Seq said:**
> Also, as an aside. It appears you are using CTRL+Z to "kill" your pings instead CTRL+C. You know this just backgrounds them, right? 
 
They are just now a sleeping process waiting to be resumed with `fg`. If you want to actually kill them, CTRL+C is the way to do it.
 
I did not know that...thank you.:)

---

### Post by focwiz on 2009-12-22
> **my_key said:**
> Does your router/modem has a dns server? Maybe it has dns issues. (Sorry but it sounds like a dns issue to me ...:confused:)
 
You can try if it is by specifying opendns's servers in ubuntu.
 
OK...I manually configured my wireless connection using static ip and dns servers from opendns.  IT WORKS!!!
 
Thank you sooo much!!!:guitar:
 
It appears that my ISP (Qwest) has some bad routes?  Not sure why they work on Win box, but not Linux?
 
Thanks to everyone who replied...all replies were helpful in pointing me in the right direction. Especially the tracepath.

---

### Post by =not4prophet= on 2009-12-22
Windows employs some crazy long timeouts for dns caching.  Its likely that it is still using old DNS records from before you ISP started having problems.

---

