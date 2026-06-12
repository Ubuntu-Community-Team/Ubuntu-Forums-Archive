---
title: "bizzar apt-ivity?? and other problems"
date: 2006-04-27
forum: General Help
---

### Post by bobbymcsteels on 2006-04-27
ok Started a few months ago while i was using the AMD64 ver of Kubuntu so i figured that that was the problem, but I just installed the 386 ver and having the same problems.....
if I ```
apt-get update
``` terminal time outs and I'm none the wiser, but if i open [http://security.ubuntu.com/](http://security.ubuntu.com/) [http://gb.archive.ubuntu.com/](http://gb.archive.ubuntu.com/) and [http://archive.ubuntu.com/](http://archive.ubuntu.com/) in konqueror it works fine..... same thing if I ```
apt-get install ........ 
```things aswell, also have installed opera and firefox and both only display a web page if I am browsing it in konqueror first.... Is this a bug that has been noted before(I have searched) or am I a pioneer of wierdness??
Any help would be great
Bobby

---

### Post by gingermark on 2006-04-27
You really do seem to be a pioneer of weirdness!!

I'm using Opera, that problem seems odd.

As far as apt stuff goes, do you get the same problems with Adept?

---

### Post by bobbymcsteels on 2006-04-27
yeah, same thing times out, kinda annoying i have to keep refreshing the pages..... Complete pain.....

---

### Post by bobbymcsteels on 2006-04-28
bump

---

### Post by bobbymcsteels on 2006-04-28
anyone have any idea about this?

---

### Post by dejitarob on 2006-04-28
What do you mean by "terminal times out"? Nothing happens at all when you type the command? No error messages?

---

### Post by Ensnared on 2006-04-28
This sort of thing only makes sense if you're using a proxy-server for internet access... are you?

If so, you have to do this to get apt working:```
kdesu kwrite /etc/apt/apt.conf
```...and add the following line (the file is probably empty/doesn't exist, but that's ok - you'll create it now):```
Acquire::http::Proxy "http://proxy.server.here:8080/";;
```Just make sure the host (proxy.server.here) and port (8080) are the correct ones for your proxy. Save the file and exit, then run apt again.

You'll also need to configure Firefox/Opera to use the proxy, of course - Konqueror probably gets it's settings from the KDE control center settings, while the other two have their own setting - maybe they "remember" the setting if you've activated it with Konqueror first or something - hell if I know, but still... gotta start to look somewhere ;)

---

### Post by bobbymcsteels on 2006-04-29
Not got a proxy server on, but tried what you said (by adding a proxy) got the same error msg
```
apt-get update
Err http://archive.ubuntu.com breezy Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://security.ubuntu.com breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to archive.ubuntu.com (1.0.0.0)]

```
Also tried firefox and opera and they still didnt work.....
Any other suggestions?

---

### Post by bobbymcsteels on 2006-04-30
anyone?

---

### Post by Ensnared on 2006-04-30
This looks like a DNS-error - the address resolves incorrectly (1.0.0.0 isn't a proper IP-address).

How is your network interface configured? If it's a DHCP-server on your network, make sure it sends out the proper DNS-servers.

Also, check what the contents of your /etc/resolv.conf is - it lists the DNS-servers you're using, and I've had problems with built-in DNS-servers in various routers not actually doing proper DNS lookups when requested. It's therefore better to either have the router (if that's what's providing the DHCP-service) give out the actual DNS-servers, or configure your computer to always use your ISP's DNS-servers.

You can do this by editing the file /etc/dhcp3/dhclient.conf and add your ISP's DNS-servers in the "prepend domain-name-servers" entry. Make sure you uncomment the line (e.g. remove the # in front of the line) as it's commented out (e.g. not active) by default.

---

### Post by bobbymcsteels on 2006-05-01
right thats half the problem sorted thanx -D edited /etc/dhcp3/dhclient.conf and like you said it was # out. then tried apt get update and worked straight away... Still got the problem with firefox and opera tho any idea how to sort that out?](*,)

---

### Post by bobbymcsteels on 2006-05-01
[QUOTE=Still got the problem with firefox and opera tho any idea how to sort that out?](*,)[/QUOTE]
Kinda.... loading pages but very slow
:???:

---

