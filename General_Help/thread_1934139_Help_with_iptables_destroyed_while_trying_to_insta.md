---
title: "Help with iptables destroyed while trying to install a proxy"
date: 2012-03-01
forum: General Help
---

### Post by Kissell on 2012-03-01
I got Tor installed, and verified it works, but I had read that a proxy server used with Tor really speeds things up.  Unfortunately I've just made a really big mess.  I could never get any proxy server to work with Tor, and now not only did the proxy server never work, but my laptop can't web browse without running through Tor.  

I have no idea why proxies don't work, I followed this guide which seems like it covers everything.
[http://bodhizazen.net/Tutorials/TOR]("http://bodhizazen.net/Tutorials/TOR")

I originally installed Tor using apt-get and editing /etc/tor/torrc.  That worked fine...  but later I installed Vidalia so I could turn it off and on easily, and it said my Tor was out of date.  So I updated my version by adding the repository "add-apt-repository ppa:ubun-tor/ppa" which worked.

I disabled my firewall completely "ufw disable"

but nothing worked to get either privoxy or polipo working.  anytime I changed to use their ports nothing would work, and I had them set to use 9050 which is what Tor is listening on.

What really messed things up, was the transparent proxy using iptables at the bottom of that tutorial...  I had given up on anything working, and just decided to try using iptables to permanently forward all HTTP traffic through...  so it tried the commands at the bottom of the website...  
```
sudo iptables -t nat -A OUTPUT -m owner --uid-owner root -j ACCEPT
sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -m ! --uid-owner tor -j REDIRECT --to-port 8123

```
The second command didn't work...  so I modified it until it did.
```

 1663  sudo iptables -t nat -A OUTPUT -m owner --uid-owner root -j ACCEPT
 1664  sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -m ! --uid-owner tor -j REDIRECT --to-port 8118
 1665  sudo iptables -t nat -A OUTPUT -p tcp --dport 80 --uid-owner tor -j REDIRECT --to-port 8118
 1666  sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -m ! --uid-owner root -j REDIRECT --to-port 8118
 1667  sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-port 8118
 1668  sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-port 9050

```
The I was in trouble, HTTPS traffic was working, but HTTP wasn't...  I don't know much about iptables, so started looking for answers.
```
 1671  iptables -L
 1672  sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -j ACCEPT
 1673  sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-port 80

```
Then started to try to remove what I did.
```

 1675  sudo iptables -X -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-port 80
 1676  sudo iptables -X REDIRECT --to-port 80
 1677  sudo iptables -t nat -X OUTPUT -p tcp --dport 80 -j REDIRECT --to-port 80
 1678  sudo iptables -t nat -X OUTPUT tcp --dport 80 -j REDIRECT --to-port 80
 1679  sudo iptables -t nat -X OUTPUT -j REDIRECT --to-port 80
 1680  sudo iptables -t nat -X OUTPUT TCP -j REDIRECT --to-port 80
 1681  sudo iptables -t nat -X OUTPUT TCP 80
 1682  sudo iptables -t nat -X OUTPUT TCP:80
 1683  sudo iptables -t nat -X OUTPUT TCP 80
 1684  sudo iptables -t nat -X TCP 80
 1685  sudo iptables -t nat -X TCP
 1686  sudo iptables -t nat -X OUTPUT
 1691  sudo iptables -F

```
Nothing was working...  webpages on port 80 were telling me I had an invalid header.  So I rebooted as a last resort...  

Now HTTP works fine when I'm going through Tor with proxy settings on port 9050..  but the polipo or privoxy proxies are still not working, and more importantly, no HTTP traffic works at all when I'm not using Tor, because instead of going to port 9050 they are going to port 80, which obviously is hosed with iptables.

Is there a way I can reset IPtables to the default?  I did an iptables save on another computer, and restored it on this one, but it didn't fix my problem, which makes me think it only adds rules, doesn't replace or delete existing ones.
```
sudo sh -c "iptables-restore < /myfile/iptables.rules"

```

---

### Post by nothingspecial on 2012-03-01
Removed the solved prefix.

---

### Post by Kissell on 2012-03-01
extra

---

### Post by Kissell on 2012-03-01
Okay, I think I got back to square one by changing my network proxy settings back to none and doing these commands.

```

sudo iptables -F
sudo sh -c "iptables-restore < /myfile/iptables.rules"
sudo apt-get purge ufw gufw privoxy polipo tor vidalia
sudo apt-get autoremove

```

I got the iptable.rules file from another computer..  

Now everything appears to be back to normal...  Time to start over and see if I can get privoxy to work..

---

