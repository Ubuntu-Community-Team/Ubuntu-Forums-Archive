---
title: "Can't access yahoo email or facebook on Ubuntu"
date: 2011-02-26
forum: General Help
---

### Post by madelman on 2011-02-26
I am having a very weird issue. I can't access the list of emails of my yahoo account and facebook just doesn't respond. They just hang and that's it. I am not sure what other webpages have same problem from my computer with Ubuntu, but I can access most of webpages I visit everyday. 

I thought first was an issue with those web sites, so I tried with my work laptop with Windows and I don't have any problems I can access everything. 

Both laptops are in the same network.  

Does anybody know why this might be happening. 

Was there any update to 8.04 that might be causing this issue?

---

### Post by madelman on 2011-02-26
I just tested on a another Ubuntu machine and same issue.

---

### Post by llawwehttam on 2011-02-26
Just tried from an ubuntu virtual machine and it works fine for me.

---

### Post by thefasterblueone on 2011-02-26
Post the results of:

```
ping yahoo.com -5
```

---

### Post by madelman on 2011-02-26
> **llawwehttam said:**
> Just tried from an ubuntu virtual machine and it works fine for me.


Thanks. I will try from a different network and see if something in my network is causing the issue, but it is really weird this is happening with only these 2 websites. 

Cheers.

---

### Post by madelman on 2011-02-26
> **thefasterblueone said:**
> Post the results of:

```
ping yahoo.com -5
```

I can access yahoo.com. With yahoo the problem is that clicking on the Inbox link it just hangs. Sometimes I get the download window of firefox with a .php file with options to save or open the file. 

With Facebook it just hangs. It doesn't get the website. I can ping it and it is reachable:

64 bytes from www-11-01-snc2.facebook.com (69.63.181.12): icmp_seq=4 ttl=242 time=94.3 ms
64 bytes from www-11-01-snc2.facebook.com (69.63.181.12): icmp_seq=5 ttl=242 time=94.2 ms
64 bytes from www-11-01-snc2.facebook.com (69.63.181.12): icmp_seq=6 ttl=242 time=93.7 ms
64 bytes from www-11-01-snc2.facebook.com (69.63.181.12): icmp_seq=7 ttl=242 time=105 ms


64 bytes from ir1.fp.vip.sk1.yahoo.com (72.30.2.43): icmp_seq=1 ttl=56 time=181 ms
64 bytes from ir1.fp.vip.sk1.yahoo.com (72.30.2.43): icmp_seq=2 ttl=56 time=102 ms
64 bytes from ir1.fp.vip.sk1.yahoo.com (72.30.2.43): icmp_seq=3 ttl=56 time=179 ms


I thought it was cache or something in the browser, but I have tried with Chrome and Firefox, same results. I just tested on a deskptop with Ubuntu and same issue.

---

### Post by pqwoerituytrueiwoq on 2011-02-26
> **thefasterblueone said:**
> Post the results of:

```
ping yahoo.com -5
```
i think you mean 
```
ping yahoo.com -c 5
```

---

### Post by SavageWolf on 2011-02-26
Have you tried Chrom[e ium]? The problem could be with Fx.

---

### Post by thefasterblueone on 2011-02-26
Try clearing your DNS cache.

```
sudo /etc/init.d/dns-clean
```

also you could run firefox and check the Error Console. First clear all errors from Console then try your site.

Or try running Firefox from a terminal command to see any errors.


@ pqwoerituytrueiwoq Yes that was what I meant, thanks.

---

### Post by madelman on 2011-02-26
Well I went to the town library and tried from there, no problems. Their network is with Comcast. I went to another place where their network is Verizon Fios and facebook was accessible with my Ubuntu Laptop, but other websites can't be accessed. Yahoo is accessible, but the link to the email and folders still can't be accessed through Fios.  Even Verizon Fios  "Contact Us" webpage can't be accessed. 

I think the issue is with Verizon and they did something that is affecting Linux.  I tried with windows and no problems found on any of the networks.

---

### Post by pqwoerituytrueiwoq on 2011-02-26
check your proxy settings
you can also use google's nds service instead of verizon's one 
8.8.8.8,8.8.4.4

---

### Post by 3177 on 2011-02-26
Ive had a problem exactly like this before, turned out to be I couldnt use AdBlockPlus or NoScript.
If your using these they need to be turned off on those pages. :D

---

### Post by madelman on 2011-02-27
I changed to Google DNS my Verizon router and still same problem. 

SO , searching in internet I found something about MTU. 

I entered: ifconfig eth1 mtu 1454

(eth1 is my wireless network)

.. and that made the trick. I am not sure but it was in 1500. 
I don't understand why without changing something everything worked in the Comcast network, but in Verizon network looks like there is a problem. I don't know if something changed or not in my laptop, but I tried on a desktop and got same issue. I haven't checked on the desktop yet but I am sure that would be same case if I change the MTU. 

So either Verizon changed something or yahoo and facebook changed something in their websites. Or an Ubuntu update changed it, don't know and don't understand. 

Does anybody have any idea why this might have happened?


thanks.

---

### Post by sticmann on 2011-03-22
Thank you madelman. That MTU thing did the trick for me also. What changed, I wonder?

---

### Post by graffiX on 2011-11-13
Thanks... the MTU thing worked for me too.

---

### Post by silverwolf636 on 2011-12-02
Wow! I've been having the same problem with my wired connection. I ran the eth1 but changed it to eth0 and it worked.
thanks

---

### Post by silverwolf636 on 2011-12-08
Where can I put this script so that I don't have to enter it everytime I want to get on the net?

---

