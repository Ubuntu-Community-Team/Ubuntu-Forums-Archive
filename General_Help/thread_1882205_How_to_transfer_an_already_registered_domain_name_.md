---
title: "How to transfer an already registered domain name from a host to ubuntu server"
date: 2011-11-16
forum: General Help
---

### Post by bignixs on 2011-11-16
How do I transfer my 10 hosting provider registered domain names, and host them myself on ubuntu server 11.10. because I keep getting suspended for CPU overload.

---

### Post by jim_deadlock on 2011-11-17
You need access to your domain records to either change the nameservers (to point to your own) or else change the A records in the zone files to point to your IP. You'll probably need to ask your current host for this access and then you may discover that they won't let you. If so then you can either hassle them about it or else just go to godaddy.com and buy a new domain, they are dirt cheap.

Check the Whois tab in the Network Tools package for full details about your domains - who they actually belong to, who has admin privileges for them etc.

---

### Post by bignixs on 2011-11-17
> **jim_deadlock said:**
> You need access to your domain records to either change the nameservers (to point to your own) or else change the A records in the zone files to point to your IP. You'll probably need to ask your current host for this access and then you may discover that they won't let you. If so then you can either hassle them about it or else just go to godaddy.com and buy a new domain, they are dirt cheap.

Check the Whois tab in the Network Tools package for full details about your domains - who they actually belong to, who has admin privileges for them etc.


IS there anyway I can keep domain at my current host but have the domain name linked to my ip?

---

### Post by Cyclane on 2011-11-17
Yes, IF they allow you to change the nameserver records.

###EDIT:
Wait I just reread your question and its possible that you asked something different than I presumed.

What kind of server are you planning to set up behind the domain name?

---

### Post by bignixs on 2011-11-17
> **Cyclane said:**
> Yes, IF they allow you to change the nameserver records.

###EDIT:
Wait I just reread your question and its possible that you asked something different than I presumed.

What kind of server are you planning to set up behind the domain name?

Not 100% sure what you mean by that, can you clarify?

would this be the DNS records?

They have a area that says 

**Custom DNS Records**

and they let you edit.

Also, is there anyway I can be my own host and not have to deal with my paid host? Just deal with myself?

---

### Post by Mazate on 2011-11-17
Your domain has to be with a domain registrar, you can't register your own domains to yourself.  However, I don't know of any domain registrar that doesn't give people access to change their nameservers or DNS in general.  That's the point of having a domain in the first place.  However, it's a little complicated if you want to point nameservers to your own server.  You will have to create your own nameservers with one of your domains.  That requires having two ip addresses on your server.  Alternatively, you can point the A record on your DNS to a singular ip address that works on your server.  But, if you want to manage the DNS for your domain on your server, then you have to point the nameservers.

Feel free to ask for clarification if this didn't make sense.  ):P

---

### Post by bignixs on 2011-11-17
> **Mazate said:**
> Your domain has to be with a domain registrar, you can't register your own domains to yourself.  However, I don't know of any domain registrar that doesn't give people access to change their nameservers or DNS in general.  That's the point of having a domain in the first place.  However, it's a little complicated if you want to point nameservers to your own server.  You will have to create your own nameservers with one of your domains.  That requires having two ip addresses on your server.  Alternatively, you can point the A record on your DNS to a singular ip address that works on your server.  But, if you want to manage the DNS for your domain on your server, then you have to point the nameservers.

Feel free to ask for clarification if this didn't make sense.  ):P

What I want to accomplish is to put all my files onto my server and make the domain pick up the files that are in my server and display them.

I keep getting banned for too much cpu used on my host.

---

### Post by Mazate on 2011-11-17
> **bignixs said:**
> What I want to accomplish is to put all my files onto my server and make the domain pick up the files that are in my server and display them.

I keep getting banned for too much cpu used on my host.


Well, I'm not sure what part, if any, the cpu usage plays in this but to use your domain on your website hosted on your server, you will need to point the A record to the IP address of your server.  The A record is part of your DNS on your domain.

---

### Post by bignixs on 2011-11-17
> **Mazate said:**
> Well, I'm not sure what part, if any, the cpu usage plays in this but to use your domain on your website hosted on your server, you will need to point the A record to the IP address of your server.  The A record is part of your DNS on your domain.


So do I point it to this ip 192.168.1.104 or to the ip that is visible to all which is 96.41.82.107


I got this ip from my servers computer: 192.168.1.104

This ip shows on whatismyip.com: 96.41.82.107

Here is a screen of what I see:

If I change then it will pick up the files on my self hosted server?

[IMG]http://freebies4real.com/dns.png[/IMG]

---

### Post by SeijiSensei on 2011-11-17
Try adding a custom record for "www.example.com" using one of your existing domain names.  Point it at the external IP of your router, 96.41.82.107.  (If you're on a residential connection chances are that your IP will change periodically.  If so, you need to look into a different solution like dyn.com.  It's also possible that your ISP blocks inbound connections to port 80.  If so, you'll need to find another hosted solution or pony up the dough for a business-class Internet connection.)

Make sure your router is configured to forward port 80 back to the internal web server's port 80.  Make sure there's a web server like Apache running on that machine and that it's configured to accept requests for [www.example.com](www.example.com).

Now see what happens if you connect to [http://www.example.com/](http://www.example.com/) from an external location.  Do you see anything at all?  If you don't get the page you expected, or if you see the "It Works!" page, you probably don't have name-based virtual hosting configured correctly.  Read the [Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html") for help.

---

### Post by bignixs on 2011-11-17
> **SeijiSensei said:**
> Try adding a custom record for "www.example.com" using one of your existing domain names.  Point it at the external IP of your router, 96.41.82.107.  (If you're on a residential connection chances are that your IP will change periodically.  If so, you need to look into a different solution like dyn.com.  It's also possible that your ISP blocks inbound connections to port 80.  If so, you'll need to find another hosted solution or pony up the dough for a business-class Internet connection.)

Make sure your router is configured to forward port 80 back to the internal web server's port 80.  Make sure there's a web server like Apache running on that machine and that it's configured to accept requests for [www.example.com]("http://www.example.com").

Now see what happens if you connect to [http://www.example.com/](http://www.example.com/) from an external location.  Do you see anything at all?  If you don't get the page you expected, or if you see the "It Works!" page, you probably don't have name-based virtual hosting configured correctly.  Read the [Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html") for help.


It is asking me to enter a username and password to access my ip

**my host says:**

Hello,

kindly note that the CPU load that you'll receive won't have  nothing to  do with our monitoring system result. Your web server are running on  modified Apache web server. It's simply not possible to reproduce this  environment on your web server. 
I'd advice you to check the web site, which is using the  bignixs1_f4r_new database. According to the information provided into  the > MySQL Stats menu:

[https://supremecenter48.com/mysql/stats/](https://supremecenter48.com/mysql/stats/)

most of the MySQL queries have been generated by this database.

Please also consider reducing the web crawlers rate, which run on the  5-on-it.com domain. I noticed that most of the 5-on-it.com hits and  visits came from this IP address:

66.249.68.117

This will significantly reduce the CPU usage as well.

Best Regards,
Andy Peterson

---

### Post by SeijiSensei on 2011-11-17
I can neither ping 96.41.82.107 nor connect to its port 80.  

The IP address you were given, 66.249.68.117, is one of Google's crawlers.  (I'm a bit surprised the hosting support person didn't recognize that right away from the address.  All addresses in 66.249 are crawlers.)  

Do you use Google's Webmaster Tools?  If so, you can adjust the frequency with which it crawls your domains.

If you're paying a hosting fee per domain, you'd be better off renting a virtual server at a place like [Linode]("http://www.linode.com/") and moving all your DNS and web services there.

---

### Post by bignixs on 2011-11-17
> **SeijiSensei said:**
> I can neither ping 96.41.82.107 nor connect to its port 80.  

The IP address you were given, 66.249.68.117, is one of Google's crawlers.  (I'm a bit surprised the hosting support person didn't recognize that right away from the address.  All addresses in 66.249 are crawlers.)  

Do you use Google's Webmaster Tools?  If so, you can adjust the frequency with which it crawls your domains.

If you're paying a hosting fee per domain, you'd be better off renting a virtual server at a place like [Linode]("http://www.linode.com/") and moving all your DNS and web services there.


will linode let me link my domains to the files on my server? 

I am a complete noob at this, not sure how to do this dns stuff :( is their a video tutorial?

Is there any place that will set up my server and point my domain name servers to my server for me? and I pay them to do so?

---

### Post by jim_deadlock on 2011-11-17
If you want to just get it working and go from there then you need to:

a) Have a look at [http://192.168.1.104](http://192.168.1.104) - if your Apache server is running then you should see a default page saying it works.

b) Go to your "Custom DNS Records" of your current host, find the A record for your domain and change the IP to 96.41.82.107

c) Access your router admin page (try [http://192.168.1.1]("http://192.168.1.1")) and go to the Port Forwarding section. From there, set port 80 to IP address 192.168.1.104 - you can find instructions for your individual router at [http://portforward.com]("http://portforward.com")

d) Have a look at [http://96.41.82.107]("http://96.41.82.107") - if it works then you're halfway there. Next try [http://yourdomain.com](http://yourdomain.com) - if it doesn't work right away then wait a few hours and try again.

Even if you have success with all of the above, you still have further issues to address:

e) The upload speed of your internet connection is probably only a fraction of your download speed, which is the opposite of what you need for a server, so your websites will be slow.

f) Your internet connection has a dynamic IP address (DHCP) so it will change regularly. You can combat this with a service like dyn.com as suggested previously, but it's not ideal.

g) You will need to familiarise yourself with httpd.conf and Virtualhosts which will be another learning curve.

All in all I agree with previous posters, I think you're better off finding another host. If you look for a VPS account that has cPanel you should find it very easy to use, you just click a link to set up a domain and fill in the boxes. You will still need to do b) initially, but with cPanel you can look into setting up your own nameservers eventually.

PS. I recommend [ServInt]("http://www.servint.net/index.php?refid=FDD706911024")

---

