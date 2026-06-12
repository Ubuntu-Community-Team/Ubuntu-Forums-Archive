---
title: "Internet extremely slow in Ubuntu but fine in Windows XP"
date: 2006-05-23
forum: General Help
---

### Post by AirRaven on 2006-05-23
I've been getting unbelievably slow page load times on my Ubuntu installation with every browser I've used. It's not just the browsers- everything internet related is extremely sporadic. A page sometimes loads in a second, and other times it takes a minute- whether they're plain text pages or graphic-heavy pages.

This problem extends to Instant Messenging- Kopete can take up to ten seconds to actually send a message to the contact in question.

I've tried it on Breezy and Dapper, but there's no difference. 

I'm running the latest Dapper release, and I'm connecting to the internet via a Wireless network (BT Voyager 2100 router) using a Ralink chipset wireless card. I've got a 512kb/s ADSL connection.

Internet access is fine in Windows XP- it's just exasperatingly slow in Linux. 

Any ideas at all about what's going wrong? It's been like this since I first installed Breezy, and remained when I upgraded to Dapper. I'd really appreciate a way of fixing the problem. ](*,)

---

### Post by steve.horsley on 2006-05-23
Ine thing that often seems to work is to disable IPv6 in firefox. Enter **about:config** into the address bar and click Go. search on **v6** and double-click the remaining line to set disable-ipv6 to True. Then try the internet again.

---

### Post by AirRaven on 2006-05-23
[QUOTE=steve.horsley]Ine thing that often seems to work is to disable IPv6 in firefox. Enter **about:config** into the address bar and click Go. search on **v6** and double-click the remaining line to set disable-ipv6 to True. Then try the internet again.[/QUOTE]
Seems to have worked. I'm hoping this stretch of speed's not just another blip in the endless saga.

Fingers crossed.

---

### Post by AirRaven on 2006-05-24
Okay. It's not worked as well as I hoped. 

It's improved in Firefox, but I've been getting consistent problems with both Gaim and Kopete. I get disconnected from all the IM networks quite regularly- with MSN going down first, then Aim, ICQ and the rest following about 10 seconds afterwards.

It's strange- I had no problems while downloading the Dapper Drake dist-upgrade earlier, but I keep having problems with this kind of thing. 

Perhaps it's just the fact it doesn't have a constant connection or something?

Any ideas what could be causing this problem?

---

### Post by Shay Stephens on 2006-05-24
If you see a boost in firefox but not other app's then try turning off ipv6 globally:

```
sudo gedit /etc/modprobe.d/aliases
```

Then find the line:

```
alias net-pf-10 ipv6
```

And replace it with:  

```
alias net-pf-10 off
```

Save the file and restart your computer.  All the other app's that access the net will no longer be slowed down by ipv6.

---

### Post by AirRaven on 2006-05-25
It doesn't seem to have made any difference at all.

IPv6 isn't the problem, I think. I think it's more that I get disconnected randomly.

I have absolutely no clue what's going on at all. 

I get this problem when signing onto Gaim:
[img]http://img479.imageshack.us/img479/6404/improblem5ep.png[/img]

It just sticks at that stage and doesn't do anything. It's still perfectly fine in Windows- the problem's entirely confined to Ubuntu.

Any more ideas for what could possibly be causing the problem? Thanks for all the help so far.

---

### Post by jvictor on 2006-05-26
HI 
Can u use the DNS server of ur ISP instead of ur router

you can modify it in /etc/resolv.conf

plz try and get bac to us

---

### Post by AirRaven on 2006-05-27
I've changed the DNS like you said. Nothing- I still get Internet problems after a while.

I tried changing it in the GNOME Network config as well- still no change at all.

Any other ideas for what could be going wrong? It's a huge source of frustration- other than the internet problem, K/Ubuntu's a far better solution for my needs than Windows. Thanks for the help so far.

EDIT: Thanks very much, Scenestar. It's working fantastically now. Perfect.

You're a lifesaver. :D

---

### Post by scenestar on 2006-05-28
This is definately a dns issue.

Internet takes ages because it is trying to resolve (non existing) DNS adresses.

a quick work around would be commenting out (disabling) all ipv6 hostnames in /etc/hosts/

The solution that worked for me though was using a static ip adress instead of dhcp and using my isp's DNS servers instead of using my router as a gateway.

This fixed most latency issues with wget , firefox and connecting to remote hosts in general.

**to stop your box from trying to resolve nonexisting ipv6 adresses in general.**

[PHP]sudo cp /etc/hosts /etc/hosts.backup [/PHP]

[PHP]sudo gedit /etc/hosts [/PHP]

and replace
[PHP]# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
[/PHP]

with

[PHP]

# The following lines are desirable for IPv6 capable hosts
#::1 ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts
[/PHP]

---

### Post by sadjack on 2006-05-29
scenestar

What a great tip! its improved my browsing no end, cheers!!

---

