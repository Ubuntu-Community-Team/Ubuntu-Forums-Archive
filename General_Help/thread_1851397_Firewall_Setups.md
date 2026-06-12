---
title: "Firewall Setups"
date: 2011-09-28
forum: General Help
---

### Post by goodvikings on 2011-09-28
Hey everyone

I have a webserver I want to set up a firewall on. At this stage, it seems like I'll end up going with ufw, but lets have a bit of an explanation first...

The end goal is to have SSH and HTTPS only accessible from predefined IP addresses which should be simple enough for any firewall. However there is a trickier goal I'd like

I want to be able to have something that actively monitors the apache2 logs and if it sees a certain number of 404's from a given source ip, to add a rule to the firewall blocking that IP for all ports. I hear fail2ban might be suitable, but I don't know much about it, ie how active it is among other things.

The method of detection doesn't have to be monitoring logs, that just seems like a basic way of doing it.

Suggestions?

Cheers

Ramo

---

### Post by haqking on 2011-09-28
> **goodvikings said:**
> Hey everyone

I have a webserver I want to set up a firewall on. At this stage, it seems like I'll end up going with ufw, but lets have a bit of an explanation first...

The end goal is to have SSH and HTTPS only accessible from predefined IP addresses which should be simple enough for any firewall. However there is a trickier goal I'd like

I want to be able to have something that actively monitors the apache2 logs and if it sees a certain number of 404's from a given source ip, to add a rule to the firewall blocking that IP for all ports. I hear fail2ban might be suitable, but I don't know much about it, ie how active it is among other things.

The method of detection doesn't have to be monitoring logs, that just seems like a basic way of doing it.

Suggestions?

Cheers

Ramo

Well UFW/GUFW, Firestarter etc etc are not firewalls themselves, they are merely Interfaces to interact with the Linux Built in Firewall which is in the kernel called IPTables/Netfilter.

I would look at IPTables directly from the command line if i was you it is much more powerful.

Also remember if you are behind a router then there will be a firewall function on that

---

### Post by goodvikings on 2011-09-28
Hmmm ok thanks, thats very useful to know.

So i guess the question then becomes "Whats a good way to actively monitor apache, and what will work well with that to add firewall rules the best?"

I only looked very quickly at ufw, and it seems that its very easy to add rules with it.

---

### Post by Frogs Hair on 2011-09-28
If you choose to go with an interface , Firestarter is an old program and though it is in the repository I would avoid it  .

---

### Post by haqking on 2011-09-28
> **goodvikings said:**
> Hmmm ok thanks, thats very useful to know.

So i guess the question then becomes "Whats a good way to actively monitor apache, and what will work well with that to add firewall rules the best?"

I only looked very quickly at ufw, and it seems that its very easy to add rules with it.

you might wanna take a look at apachetop for apache monitoring or just the old fashioned way in the apache logs themselves.

---

### Post by haqking on 2011-09-28
> **Frogs Hair said:**
> If you choose to go with an interface , Firestarter is an old program and though it is in the repository I would avoid it  .

+1 yeah avoid that at all costs.

CLI for IPTables is much more powerful though not as user friendly as the GUI's

---

### Post by goodvikings on 2011-09-28
Meh its a server anyway, so GUI is out of the question.

I'll give apachetop a look. Is it able to detect something like several 404's from one IP and run a script / command when it does? If thats the case then we can forget about fail2ban

---

### Post by hsweet on 2011-09-28
First part should be doable with ufw, but the bit about monitoring the log and automatically updating the iptables rules would require writing iptables rules directly.

It were me, I would write a perl script to parse the error log,  and spit out a rule revision in my iptables file for any ip with too many 404's. Run the script via cron with enough permission to write iptables rules

iptables -A INPUT -s 64.90.32.6 -j DROP  (something like this)

Rules can be added on the fly if I remember correctly  -A adds the new rule to the end of the list.

But I'm a bit rusty.  One thing, you can lock yourself out of a remote computer playing with iptables so it's good to learn on a local text box.

---

### Post by goodvikings on 2011-09-28
Yeah i did think of that but I want it to be much more active. You know, without telling cron to run that job every 5 seconds or so...

---

### Post by hsweet on 2011-09-28
How about an Apache module?  No idea how to do that, but it would be part of the apache process, maybe good enough for other folks to use.

---

### Post by goodvikings on 2011-09-28
Haha yeah that'd be good if I knew how to write my own apache modules :P

Maybe there's something in mod_security?

---

### Post by Dangertux on 2011-09-28
iptables is not really designed to do any type of log monitoring in and of itself, there are kernel module add ons and IDS/IPS solutions that can monitor inbound traffic and outbound responses and tell iptables what to do about it, however you're not going to be able to build a DPI firewall out of iptables.

That being said, I'm assuming you're looking to block enumeration and web vulnerability scanning against your Apache server. The easiest way I know how to do that is by using mod_security. There are some pre-made rules that are actually quite good based on the OWASP top 10 , also you can write your own rules (this gets complicated fast)

If you are interested in installing the latest version of mod_security and core rules for apache I wrote a procedure here : [http://dangertux.wordpress.com/tutorials/ubuntu-10-04-apache-current-mod-security/](http://dangertux.wordpress.com/tutorials/ubuntu-10-04-apache-current-mod-security/)

There is also an older tutorial here , that utilizes repos if you're not familiar with building from source however it is using an older rule set and the current rule set doesn't really work that well with this one : [http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/](http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/)

As far as iptables and allowing only specific services to be accessible from certain ip's etc, I would recommend using iptables over ufw or any other management system, they are much more robust and can do a lot of interesting things that ufw and the like can not.

Also I know denyhosts won't do what you're looking for and I'm fairly certain fail2ban won't either (not positive)

Hope that helps.

---

### Post by goodvikings on 2011-09-28
Yeah thanks that does help. I always knew that iptables, or any of ufw, firestarter, etc wouldn't directly monitor apache and react to it, so I needed something in between them to do all the work. Perhaps mod_security is the way to go, i'll have to do a lot of research on it though...

---

### Post by archolman on 2011-10-02
> **Frogs Hair said:**
> If you choose to go with an interface , Firestarter is an old program and though it is in the repository I would avoid it  .


Firestarter has more settings than UFW, so a more accurate control over iptables is possible, as well as the ability to control, amongst other variables, ICMP filtering, DHCP config & service prioritising, all in one place. The PDF manual was updated last year, & excellent support is available via the user mailing list, (last entry 5 days ago).

Does its age really matter?
  I've not heard of it having an age-related vulnerability, have I missed something important? because I've just set-up a neighbour's laptop with Lucid, with Firestarter as the firewall-GUI.

As to experimenting with settings, virtualise a copy of your installation, & then play until you break it... noting the settings you used each time.

---

### Post by haqking on 2011-10-02
> **archolman said:**
> Firestarter has more settings than UFW, so a more accurate control over iptables is possible, as well as the ability to control, amongst other variables, ICMP filtering, DHCP config & service prioritising, all in one place. The PDF manual was updated last year, & excellent support is available via the user mailing list, (last entry 5 days ago).

Does its age really matter?
  I've not heard of it having an age-related vulnerability, have I missed something important? because I've just set-up a neighbour's laptop with Lucid, with Firestarter as the firewall-GUI.

its just out of date as a project thats all.

Personally if you want configurability then just IPTables from CLI, but if FS works for ya then by all means use it.  Last stable was 1.0.3 i think and plenty of Bugs on launchpad for it

---

### Post by archolman on 2011-10-02
Tally Ho! It's bughunting time here in sunny Huddersfield! ;) 
 Thanks for the advise... it's not the first of yours I've followed. :mrgreen: 
 
I always use Firestarter, mostly so that I can show converts how to use the GUI to get the best benefit for them.
 As most of them just want to surf, & are used to MS security-apps having a GUI to do everything, they haven't been interested in the back-end, just in how to train the firewall. Maintaining a Firestarter mind-set helps in teaching its use.

---

### Post by goodvikings on 2011-10-02
Thanks for all the tips guys. Gonna go with writing a module for apache to do it. Figure that'd be a good way to brush up on my C/C++

---

### Post by Dangertux on 2011-10-02
Not sure why you'd bother reinventing the wheel. When you're dealing with things like SQLi, CSRF, XSS , etc.. You're going to have to write all your definitions too. Which means you have have to understand every single methodology used in that type of attack.

This is why I recommended mod-security. For instance you will probably easily be able to pick out

```

dangertux` or 1=1` - 

```as a SQLi attempt. but what about timing attacks?

```

1 AND 1=IF(2>1,BENCHMARK(5000000,MD5(CHAR(115,113,108,109,97,112))),0)

```OR 

```

%2d%31%20%41%4e%44%20%31%3d%49%46%28%32%3e%31%2c%42%45%4e%43%48%4d%41%52%4b%28%35%30%30%30%30%30%30%2c%4d%44%35%28%43%48%41%52%28%31%31%35%2c%31%31%33%2c%31%30%38%2c%31%30%39%2c%39%37%2c%31%31%32%29%29%29%2c%30%29

```
I don't think web application security is the proper place to brush up on your C skills , at least not if this is being used for any type of production system.

---

### Post by bodhi.zazen on 2011-10-02
On a server I use iptables.

Why would you block an ip simply because of a 404 ?

I think you should look at tools such as psad, snort, and mod_security.

---

### Post by goodvikings on 2011-10-04
My reasons are here: [http://www.security4noobs.com/2011/09/discovery-in-apache/](http://www.security4noobs.com/2011/09/discovery-in-apache/)

I'm not trying to absolutely harden the server (now at least) so this will do in the mean time, and give my hands something to do.

---

### Post by Dangertux on 2011-10-04
Well that's automated scanning for you. If you run a server publicly it's expected. They're just looking for webshells and or easily compromised sites. 

Mod-security can help you with this too. If you're worried about footprinting that much it can spoof server tokens as well. You can also recompile apache with different server tokens as well. 

Alternatively a custom 404 page will usually throw off most automated scanners.

---

### Post by bodhi.zazen on 2011-10-04
> **goodvikings said:**
> My reasons are here: [http://www.security4noobs.com/2011/09/discovery-in-apache/](http://www.security4noobs.com/2011/09/discovery-in-apache/)

I'm not trying to absolutely harden the server (now at least) so this will do in the mean time, and give my hands something to do.

That link is not to anything meaningful to apache security.

google search securing apache, read the security sticky, learn to use apparmor, secure php and mysql if you are using them as well, look at snort, look at mod security.

---

