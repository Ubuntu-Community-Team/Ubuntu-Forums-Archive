---
title: "How to allow outgoing traceroute through UFW"
date: 2012-02-23
forum: General Help
---

### Post by jim_deadlock on 2012-02-23
I use gnome-nettools to run outgoing traceroutes but I have to manually disable my firewall whenever I run it because I can't find a way to set a rule to allow traceroute (I use gufw). Is there a way to allow outgoing traceroutes? Googling the problem tells me it's something to do with ICMP packets but I can't find any settings for it in gufw.

---

### Post by Dangertux on 2012-02-23
> **jim_deadlock said:**
> I use gnome-nettools to run outgoing traceroutes but I have to manually disable my firewall whenever I run it because I can't find a way to set a rule to allow traceroute (I use gufw). Is there a way to allow outgoing traceroutes? Googling the problem tells me it's something to do with ICMP packets but I can't find any settings for it in gufw.

If you could do the following and post its output , it would be helpful.

```

sudo grep 'icmp' /etc/ufw/before.rules

```

It should look something like this

```

# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT

```

If you are seeing those end in DROP or REJECT instead of ACCEPT, then you might have a problem.

Hope this helps.

---

### Post by winh8r on 2012-02-23
post retracted

---

### Post by jim_deadlock on 2012-02-23
```
# ok icmp codes
-A ufw-before-input -p icmp --icmp-type destination-unreachable -j ACCEPT
-A ufw-before-input -p icmp --icmp-type source-quench -j ACCEPT
-A ufw-before-input -p icmp --icmp-type time-exceeded -j ACCEPT
-A ufw-before-input -p icmp --icmp-type parameter-problem -j ACCEPT
-A ufw-before-input -p icmp --icmp-type echo-request -j ACCEPT
-A ufw-before-output -p icmp --icmp-type echo-request -j ACCEPT

```

That last line I added myself to allow outgoing ping but my traceroute is still blocked (note it's OUTBOUND traceroute I'm interested in).

---

### Post by Dangertux on 2012-02-23
Traceroute relies on three ICMP codes 0 (echo-reply), 3 (destination-unreachable), and 11 (time-exceeded).

You can try adding the following rules

```

-A ufw-before-input -p icmp --icmp-type 0 -j ACCEPT
-A ufw-before-output -p icmp --icmp-type 0 -j ACCEPT
-A ufw-before-output -p icmp --icmp-type 3 -j ACCEPT
-A ufw-before-output -p icmp --icmp-type 11 -j ACCEPT


```

Maybe this will work. Let me know.

---

### Post by jim_deadlock on 2012-02-23
Still blocked...

---

### Post by Dangertux on 2012-02-23
I'm assuming you're restarting ufw between these changes right?

```

sudo ufw reload

```If you don't it won't parse the changes in that file.

Also traceroute works just fine with the default UFW rules... Did you change something in sysctl or your ufw rules?

Can you post the output of the following

```

cat /proc/sys/net/ipv4/icmp_echo_ignore_all

```

Thanks.

---

### Post by jim_deadlock on 2012-02-23
Yes I did reload ufw and I even tried rebooting.

My UFW is set to DENY ALL IN/OUT and then I have loads of ALLOW rules for the stuff I want to use, so it's certainly not the default settings.

The output of cat /proc/sys/net/ipv4/icmp_echo_ignore_all is just 0

---

### Post by Dangertux on 2012-02-23
> **jim_deadlock said:**
> Yes I did reload ufw and I even tried rebooting.

My UFW is set to DENY ALL IN/OUT and then I have loads of ALLOW rules for the stuff I want to use, so it's certainly not the default settings.

The output of cat /proc/sys/net/ipv4/icmp_echo_ignore_all is just 0


Okay so here's the kicker with traceroute, you're going to have to loosen up your outbound rules in order to traceroute. Traceroute uses sequential ports for every additional hop...So for instance... If there are 26 hops and you're starting on port 33434 (default) it would be 33434:33460

Since this can be random , you may wish to just disable the firewall to do the traceroute, since I'm not assuming you're consistently tracerouting and if you are, why? 

Hope this helps.

---

### Post by jim_deadlock on 2012-02-23
Well that's what I've been doing, I just manually switch off the outbound blocking before a traceroute, it's just that I'm very lazy and trying to find a rule for it. So what you're saying is I'm on a wild goose chase and I should give it up. Fair enough :D

Thanks for your efforts anyway.

---

### Post by Dangertux on 2012-02-23
Well... Not necessarily... You can CHEAT if you want... But this is probably worst for your overall system security than just disabling it temporarily. Since traceroute is setuid... You can do the following with restrictive outbound rules, and it will work. (I just tested this)

Add the following to /etc/ufw/before.rules

```

-A ufw-before-output -m owner --uid-owner root -j ACCEPT

```Restart ufw and traceroute till your heart's content.

Hope this helps.

NOTE : This will allow ALL outbound packets created by root.

---

### Post by jim_deadlock on 2012-02-25
This works a treat, thanks! I'll probably heed your warning and stick to doing it manually but my quest for a solution is over, that's the main thing :D

---

### Post by abuamir on 2012-12-08
> **Dangertux said:**
> Well... Not necessarily... You can CHEAT if you want... But this is probably worst for your overall system security than just disabling it temporarily. Since traceroute is setuid... You can do the following with restrictive outbound rules, and it will work. (I just tested this)

Add the following to /etc/ufw/before.rules

```

-A ufw-before-output -m owner --uid-owner root -j ACCEPT

```Restart ufw and traceroute till your heart's content.

Hope this helps.

NOTE : This will allow ALL outbound packets created by root.



Guys, the commands for ufw rules, is it just simple shell script or it's coupled with something, and what's the best way to learn them.
Thanks for ur help

---

### Post by jim_deadlock on 2012-12-09
For normal usage you would use the GUI which is gufw in the Software Centre. You can add and remove rules and switch the firewall on and off, it's all you really need.

What I was talking about in this thread is something unusual and consists of editing the config file.

---

